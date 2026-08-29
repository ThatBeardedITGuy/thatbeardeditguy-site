---
title: "The Intune Rollout That Went Sideways"
date: 2026-07-10
draft: false
summary: "A compliance policy locked a chunk of a client's devices out of email on a Friday afternoon. Here's what I'd change."
tags: ["Intune", "Microsoft 365", "IT Support"]
categories: ["Blog"]
showTableOfContents: false
---

Not every story worth telling ends with me looking competent. This is a genuine mistake, close enough to one anyway, that taught me something about testing scope I hadn't properly internalised.

A client wanted a new compliance policy in Intune. BitLocker required, minimum OS version, before devices could access company email. Standard enough conditional access hardening.

I built the policy. Tested it against my own device. Confirmed it worked. Rolled it out to the assigned device group on a Friday afternoon.

Within twenty minutes I had four tickets. Users locked out of Outlook on mobile. None of it matched what I'd tested.

The issue was the device group. Set up months earlier, it included a handful of older company phones. Technically met the compliance policy's stated minimum, but hadn't checked in against Intune recently enough for compliance status to register properly.

My test device was current and had synced recently, so it sailed through. The older phones hadn't. As far as the policy was concerned, they failed compliance and lost access.

The technical fix was straightforward once I found it. Force a sync, re-enrol a couple of devices.

The actual mistake wasn't the policy logic. It was testing against a single clean device and assuming it represented the group. It didn't.

A five minute check of the assigned group's compliance and sync status before rollout would have caught this before it became four tickets and an irritated client on a Friday afternoon.

So now I check the actual state of the target group before rolling anything out. Not just the policy logic in isolation.

I roll out to a small pilot subset of the real target group first. Not just my own test device, especially for anything that could lock someone out of something they need.

I avoid Friday afternoon rollouts for exactly that reason. The response window before people notice and escalate is shorter than I'd like.

And I have the rollback step written down and ready before I start. Not worked out after something's already gone wrong.

It wasn't a disaster. Four tickets, about forty minutes to fully resolve. But it was avoidable, and the fix cost less time than writing this up.

It worked on my test device and it'll work on the actual target group are two different claims. Only one of them is the one that matters.
