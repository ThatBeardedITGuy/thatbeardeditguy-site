---
title: "What My Homelab Taught Me About Production Systems"
date: 2026-07-24
draft: false
summary: "Running Proxmox, Docker and Plex at home ended up teaching me more about production thinking than expected."
tags: ["Homelab", "Self-Hosting", "Proxmox"]
categories: ["Blog"]
showTableOfContents: false
---

I started my homelab to stop paying for streaming services and learn Proxmox properly.

What it actually turned into was a low stakes place to practice the same instincts I need at work. Without a client on the other end of the ticket if I get it wrong.

First real lesson came from not having backups. Nothing dramatic, a package conflict took a VM down, and I had no snapshot to fall back on. Cost me an evening rebuilding something I could have restored in five minutes.

Small stakes compared to a client environment. Still stung enough to make me set up scheduled snapshots properly before touching anything else.

It's easy to treat it's just my homelab as a reason to skip the boring stuff. It's actually the best place to feel the consequences of skipping it, before those consequences involve someone else's business.

I write full guides for my own setup now. Host config, container builds, network layout. Not because anyone else is reading them, but because six months later I'm effectively a different person who's forgotten exactly why I set something up a particular way.

Writing it down at the time is far easier than reverse engineering my own decisions later.

Running everything in Docker containers taught me to appreciate isolation in a way reading about it never did. If a container update breaks something, it's contained to that container, not the whole host.

That's change management in miniature. Smaller blast radius, easier rollback, less risk per change. I didn't set out to learn that. It just fell out of building things properly and watching what happened when I didn't.

None of this is stuff I couldn't have learned from a book. But doing it on infrastructure I actually own, with real consequences if I get it wrong, made it stick in a way reading about it never quite did.

My homelab is Proxmox, Docker and Plex at the moment, with a few other bits I'm slowly documenting on the Projects page.

If you're in IT and haven't set something like this up, I'd genuinely recommend it. Not for the CV line. For the practice of breaking things somewhere that doesn't matter, before you're doing it somewhere that does.
