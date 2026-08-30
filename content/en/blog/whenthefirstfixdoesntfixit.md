---
title: "When the First Fix Doesn't Fix It"
date: 2026-06-02
bannerImage: "images/blog/Banner6.png"
draft: false
summary: "What I do when my first idea about a technical problem turns out to be wrong."
tags: ["IT Support", "Troubleshooting", "Microsoft 365"]
categories: ["Blog"]
showTableOfContents: false
---

One of the things I've learned from working in IT support is that your first idea isn't always going to be the answer.

Sometimes you look at a problem and think you know where it's going.

You run a few checks.

It doesn't quite add up.

You try something reasonable.

Still not fixed.

That's usually the point where I think it's better to stop and take another look rather than just keep trying things.

## The first idea is still useful

When a user reports a problem, I normally have an idea of where I want to start.

That's part of troubleshooting.

If someone can't access something, I'll think about the obvious possibilities.

Is it the user?
The device?
The network?
The application?
Identity?
Permissions?

There isn't anything wrong with starting there.

The problem comes when you become too attached to the first theory.

If the evidence doesn't support it, I need to be willing to change direction.

## I've had issues where the obvious answer wasn't the answer

One example that comes to mind was an Excel co-authoring issue.

The problem was that users weren't getting the co-authoring behaviour we expected from the workbook.

There were plenty of possible places to start looking.

It could have been permissions.
It could have been SharePoint or Microsoft 365.
It could have been something with the user's setup.
It would have been quite easy to start investigating the wider environment.
But looking more closely at the actual file gave us something useful.

It was an `.xlsb` workbook.

Converting it to `.xlsx` resolved the issue.

The eventual fix was fairly simple.

Getting there wasn't necessarily about knowing some obscure technical trick.

It was about looking at the thing that was actually being used rather than assuming the problem had to be somewhere more complicated.

## Sometimes you need to step back

I've found that when the first thing I try doesn't work, there's a temptation to keep pushing in the same direction.

Maybe another setting will fix it.

Maybe another policy needs changing.

Maybe another restart will magically solve everything.

We've all been there.

But if the evidence isn't supporting the original theory, doing more of the same isn't necessarily going to help.

That's usually when I try to go back to the basics.

What do I actually know?
What have I ruled out?
What is different between the working example and the broken one?
Does the problem follow the user?
Does it follow the device?
Does it happen somewhere else?
What is the system actually reporting?

Those questions tend to be more useful than simply trying another fix.

## Comparing something that works can be really useful

One of the simplest troubleshooting techniques I've found useful is finding something that works and comparing it with something that doesn't.

It doesn't always give you the answer immediately.

But it can give you a difference to investigate.

If one device works and another doesn't, what is different?

If one user can access something and another can't, what is different?

If the same account works on another device, what does that tell you?

I've used this kind of comparison quite a lot in support.

Sometimes the difference is obvious.

Sometimes you have to dig a little further.

But having a working example gives you something concrete to compare against.

## The logs usually have something to say

This is another reason I've become quite comfortable working with the information available in Microsoft 365, Entra ID and Intune.

The user might only see:

> It doesn't work.

That's important, but it doesn't tell me very much about what happened underneath.

Depending on the problem, I can look at sign-in activity, Conditional Access results, device state, audit information or other technical evidence.

Sometimes that confirms what I expected.

Sometimes it sends me in a completely different direction.

That's fine.

I'd rather the evidence change my mind than spend an hour proving an assumption that was wrong.

## There's a difference between troubleshooting and changing things

This is probably something I've become more conscious of over time.

Changing something isn't the same as troubleshooting.

If I change a setting and the problem disappears, I know something changed.

I don't necessarily know why it fixed the problem.

If I've changed several things at once, I might not even know which change mattered.

Where possible, I prefer to make a change, test the result and use what I've learned to decide what happens next.

That gives me a much clearer investigation.

It also makes the eventual explanation much better.

## Sometimes the fix really is simple

I think there's a tendency in IT to assume that a complicated investigation should result in a complicated fix.

It doesn't.

The work involved in finding the answer can be much more complicated than the answer itself.

The Excel example is a good reminder of that for me.

The problem took investigation.

The eventual fix was simply converting the workbook to the appropriate format.

That doesn't make the investigation unnecessary.

It makes the investigation useful.

The goal isn't to find the most impressive fix.

It's to understand the problem well enough to fix the right thing.

## I've become more comfortable being wrong

Probably the biggest thing I've taken from troubleshooting is that being wrong about your first idea isn't a bad thing.

It's part of the process.

I'd much rather start with a sensible theory, test it and find out that I'm wrong than decide I've found the answer and stop looking.

Support gives you plenty of opportunities to practise that.

A ticket starts one way.

The investigation takes you somewhere else.

You find something you weren't expecting.

You adjust.

You keep going.

Eventually you get to the answer.

That's really what troubleshooting is.

Not knowing the answer immediately.

Working out how to find it.

## What I try to remember

When the first fix doesn't work, I try not to see that as failure.

It's information.

Something I expected to happen didn't happen.

That tells me something.

Maybe my original assumption was wrong.

Maybe I've missed something.

Maybe the problem is somewhere else entirely.

Either way, I have another piece of information to work with.

So rather than throwing another fix at it, I try to step back, look at what I actually know and work from there.

Sometimes that leads to a complicated answer.

Sometimes it leads to something surprisingly simple.

Either way, I'd rather understand why I'm fixing something than just get lucky and make the error disappear.
