---
title: "Building This Website With Hugo and Blowfish"
date: 2026-08-30
draft: false
summary: "How I planned, built and published this site using Hugo, the Blowfish theme, GitHub and Hostinger, with a full follow-along guide to set up the same auto-deploying pipeline yourself."
tags: ["Hugo", "Web Development", "Self-Hosting"]
categories: ["Projects"]
showTableOfContents: false
---

## Summary

This site itself is one of my projects. It's a static site built with Hugo, using the Blowfish theme as a base, with the source sitting in a GitHub repository. Every time I push a change to the main branch, a GitHub Actions workflow builds the site and the finished result ends up live on Hostinger within a minute or two, with no manual upload step in between.

I picked this setup over a full CMS or a drag-and-drop website builder for a few reasons. I wanted something lightweight to maintain long term, rather than a heavier platform with a database and an admin panel to keep patched and secure. I wanted the entire site, content included, to be version-controlled from day one, so nothing exists in a single unrecoverable place. And I wanted writing a new article to mean adding a text file and pushing it, not logging into a separate system every time.

It also meant I could build the whole thing without paying for anything beyond a domain name and a fairly basic hosting plan, since Hugo doesn't need a server running behind it. It just needs somewhere to serve the plain HTML, CSS and JavaScript it produces.

The rest of this write-up covers the process I actually followed, including a full follow-along section at the end for anyone who wants to set up the same GitHub-to-Hostinger auto-deploy pipeline for their own Hugo site.

## Stack

- **Hugo**, a static site generator that turns markdown content and Go templates into plain HTML at build time, rather than generating pages on every request
- **Blowfish**, an open-source Hugo theme, added as a Git submodule and customised through site-level overrides rather than by editing the theme directly
- **Git and GitHub**, used both for version control of the source and as the trigger for the deployment pipeline
- **GitHub Actions**, to install Hugo, build the site, and publish the compiled output to a dedicated branch on every push
- **Hostinger**, connected to that dedicated build branch through its Git integration, watching it for new commits and deploying automatically

## Follow-Along Guide

### 1. Decide what the site actually needs to do

Before touching any tooling, I worked out what the site was for: somewhere to write about IT, document a few homelab projects, and give a quick overview of my background. That decided the sections I'd need later, a home page, a blog, a projects area and an about page, rather than trying to work that out once I was already halfway through building something.

### 2. Install Hugo and scaffold a new site

Hugo is a single binary with no dependencies to install separately. Once it's installed, scaffolding a new site takes one command:

```bash
hugo new site mysite
cd mysite
git init
```

This gives you a working project structure straight away: folders for content, layouts, static assets, and configuration, all ready to be filled in.

### 3. Add a theme as a Git submodule

I added Blowfish as a submodule rather than downloading and copying its files into my own repository:

```bash
git submodule add https://github.com/nunocoracao/blowfish.git themes/blowfish
```

Keeping the theme as a submodule means it stays cleanly separated from my own content and configuration, and I can pull in theme updates later without that update touching anything I've written myself. Most themes, Blowfish included, ship with example configuration you can copy in as a starting point rather than configuring everything from a blank file.

### 4. Plan the content structure before writing anything

I set up the top-level sections next: `content/en/blog`, `content/en/projects`, and a couple of standalone pages for home and about. Getting this in place before writing meant every article had an obvious home as soon as I started writing it, rather than deciding where things belonged after the fact.

### 5. Write real content before customising the design

I wrote several blog posts using the theme's default styling before changing anything visually. That confirmed two things early: that I actually had enough to say, and that I enjoyed the process of writing it. Once there was real content in place, the visual decisions that followed were much easier, because I was designing around actual pages rather than guessing at layouts for content that didn't exist yet.

### 6. Push the source to GitHub

Once there was something worth keeping, I created a repository on GitHub and pushed the project to it:

```bash
git add .
git commit -m "Initial site content"
git branch -M main
git remote add origin https://github.com/yourusername/yourrepo.git
git push -u origin main
```

From this point, `main` holds the actual Hugo source, the content, templates, configuration and the theme submodule reference, not the finished website. That distinction matters for the next part.

### 7. Add a GitHub Actions workflow to build the site automatically

Hugo needs a build step to turn that source into the plain HTML a browser can actually display, and Hostinger's own Git integration deploys whatever is committed to a branch without running a build command itself. So rather than deploying the raw source, I set up a GitHub Actions workflow that builds the site on every push to `main` and publishes the result to a separate branch, which I called `build`.

The workflow file lives at `.github/workflows/deploy.yml`:

```yaml
name: Build and deploy site

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          submodules: recursive

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: "latest"
          extended: true

      - name: Build site
        run: hugo --minify --gc

      - name: Publish build output to build branch
        uses: s0/git-publish-subdir-action@develop
        env:
          REPO: self
          BRANCH: build
          FOLDER: public
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          MESSAGE: "Build: ({sha}) {msg}"
```

A quick rundown of what each part does: checkout pulls the repository, including the Blowfish submodule; the Hugo setup step installs the extended version of Hugo, which Blowfish needs for its Sass/SCSS processing; the build step runs Hugo itself, producing a `public` folder full of finished HTML, CSS and JS; and the last step pushes just that `public` folder to the `build` branch, using the token GitHub provides automatically, so no separate credentials need setting up.

After this is in place, every push to `main` results in a fresh, built version of the site landing on the `build` branch a short while later, with the source and the compiled output kept clearly separate.

### 8. Connect the build branch to Hostinger

With the build branch producing a real, finished site on every push, the last piece is telling Hostinger to watch it:

1. In hPanel, go to **Websites**, select your site, and open its **Dashboard**.
2. In the sidebar, go to **Advanced → Git**.
3. Click **Continue with GitHub** and authorise the Hostinger GitHub App when prompted.
4. Choose the repository from the list, refreshing it if it doesn't appear straight away.
5. Set the **branch** to `build`, the one the Actions workflow publishes to, not `main`.
6. Leave the **deploy directory** as `public_html` unless you have a reason to target a subfolder.
7. Click **Deploy** to run the first deployment.

Once that initial deployment finishes, Hostinger sets up a webhook on the repository behind the scenes. From then on, any new commit that lands on the `build` branch triggers an automatic redeployment, no manual step required. Since the Actions workflow is what puts new commits on that branch, the end-to-end effect is that pushing to `main` is enough to update the live site a minute or two later.

The **Deployments** tab in the same panel shows a history of what's been deployed, including commit references and timestamps, and there's a manual **Redeploy** button if you ever need to force a redeploy without a new commit.

### 9. Customise the theme through overrides, not by editing it directly

Where I needed something the theme didn't do out of the box, I added site-level template overrides in my own `layouts/` folder rather than editing Blowfish's files directly. Hugo automatically prefers a site-level template over the theme's version of the same file, which means theme updates continue to work normally rather than silently wiping out my own changes.

### 10. Test properly before calling anything finished

Before treating a change as done, I checked it on a phone as well as a desktop, in both light and dark mode, and on the actual pages affected rather than just the home page. A good few small fixes, spacing, image sizing, contrast in dark mode, only turned up once I actually looked properly rather than assuming a change that looked fine in one place looked fine everywhere.

### 11. Keep iterating after launch

The site went live before it was "finished", and I don't think it's finished now either. I keep coming back to adjust layout, fix things that only became obvious once real content was in place, and add new sections as the site grows. The auto-deploy pipeline makes that easy, since every one of those changes is just a normal commit and push away from being live.

## Lessons Learned

Write real content before customising the design. It's far easier to design around something real than to guess at layouts for content that doesn't exist yet.

Keep the theme as a submodule and customise through overrides rather than editing it directly, so pulling in theme updates doesn't undo your own work.

Deploy a built, static output rather than raw source. Hostinger's Git integration deploys whatever is on the branch you point it at, so a dedicated build branch keeps the messy source separate from the finished site.

Publish early rather than waiting for a finished version. A live site you keep improving beats a perfect one that never leaves your laptop.

Test on more than your own screen and your own colour scheme before calling something done.

## What's Next

I want to add a proper preview step before changes go live, so I can catch issues on a draft build before they reach the real site rather than after. Longer term, I'd like to tie that into the homelab setup I've written about elsewhere, running checks on my own infrastructure rather than relying entirely on the hosting provider's pipeline.
