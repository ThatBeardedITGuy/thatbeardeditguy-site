---
title: "It's Always DNS... Until It Isn't"
date: 2026-05-26
draft: false
summary: "Why familiar troubleshooting assumptions can sometimes send you in the wrong direction."
tags: ["Troubleshooting", "Networking", "Evidence"]
categories: ["Blog"]
showTableOfContents: false
---

There's a running joke in IT that every problem eventually turns out to be DNS.

It's funny because DNS does cause a lot of problems.

But there's another lesson in it that I think is more useful.

A familiar explanation can become a trap.

## The danger of the obvious answer

When you've seen the same sort of issue enough times, your brain starts filling in the gaps.

Can't connect?

Probably DNS.

Can't access an application?

Probably DNS.

Something suddenly stopped working?

Have you checked DNS?

Sometimes that instinct is useful.

Sometimes it's completely wrong.

The problem is when you stop investigating because you've already decided what the answer is.

## I've learned to be a little more deliberate

When I'm working through a connectivity problem, I want to establish what is actually failing.

Can the device reach the network?

Does it have the expected IP configuration?

Can it resolve the name?

Can it reach the destination by IP?

Is the service itself responding?

Is the problem limited to one device or affecting others?

Those checks start separating the possible causes.

If DNS is the problem, the evidence should eventually point that way.

If it isn't, I can move on.

## The same approach applies outside networking

This is probably the bigger lesson.

I've seen similar situations with Microsoft 365, identity and endpoints.

A user can't sign in.

It must be their password.

A device isn't accessing something.

It must be Intune.

An application isn't working.

It must be the application.

Sometimes it is.

But I've found that the best investigations are the ones where I don't decide too early.

## One example

The Conditional Access issue I wrote about elsewhere is a good example.

From the user's perspective, it was an access problem.

The temptation would have been to treat it as a generic authentication issue.

Looking at the sign-in information showed that a specific blocked-countries policy was involved.

The initial symptom was real.

The initial assumption would have been less useful.

## Evidence keeps you honest

The more I work in support, the more I appreciate having something concrete to work from.

A log entry.

A policy result.

A device state.

A test result.

A reproducible behaviour.

It doesn't have to be complicated.

Even something as simple as:

> It works on this device but not that one.

is useful evidence.

It changes the direction of the investigation.

## The other side of this is knowing when to stop

You can also go too far.

Not every connectivity issue needs a complete network investigation.

If the evidence quickly shows that the problem is DNS, then great.

Fix it.

Document it.

Move on.

The point isn't to investigate everything forever.

It's to investigate enough to be confident in what you're changing.

## Why I like this way of working

I think this is one of the things that has carried over into my interest in service management as well.

You want to understand what is actually happening.

Not what you expect to be happening.

That sounds like a small difference, but it changes how you approach problems.

Instead of:

> I think I know what this is.

It's:

> Here's what I know so far. What does that tell me?

That leaves room for the evidence to change your mind.

And sometimes it will.

## So yes, check DNS

Of course you should.

Just don't stop there.

Because sometimes it really is DNS.

And sometimes it really, really isn't.
