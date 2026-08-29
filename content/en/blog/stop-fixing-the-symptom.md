---
title: "Stop Fixing the Symptom: A Lesson From a Ticket That Wouldn't Die"
date: 2026-08-25
draft: false
summary: "A repeat ticket taught me the difference between closing something fast and closing it properly."
tags: ["IT Support", "Root Cause Analysis", "Process"]
categories: ["Blog"]
showTableOfContents: false
---

A ticket landed in my queue a while back that I'd already seen closed twice before.

Same user. Same issue. Outlook kept asking for credentials every couple of hours.

Both previous fixes were the same. Clear the cached credentials. Sign back in. Close the ticket.

And both times, it came back.

By the third time it landed with me, I did something slightly different. I didn't touch the fix straight away.

I asked why this kept happening to this one user, and nobody else.

Turned out the answer wasn't in Outlook at all. It was in Entra ID. A legacy authentication policy, still applied from an old exclusion group that should have been cleaned up months earlier.

Clearing the cache "fixed" it every time. The symptom went away for a bit.

It just never fixed the actual problem, because nobody had gone looking for the actual problem.

Two techs. Two tickets. Two temporary patches.

This is the thing that took me a while to properly get my head around. Closing a ticket quickly isn't the same as closing it well.

There's a difference between the user stopped complaining and the underlying cause is gone.

Most of the time those line up. When they don't, and the same ticket keeps resurfacing under a different reference number, that's usually a sign the fix landed on the wrong layer.

So now if a ticket looks like a repeat, I check the history before I touch anything. Not just has this happened before. What was actually done last time.

I try to ask one extra why before applying the fix I already know works.

And I log the root cause even when the fix itself is quick. Not for me. For whoever picks it up next.

None of that is groundbreaking. But there's a real difference between being fast and being useful, and a lot of support work rewards fast because that's what gets measured.

The ticket count going down and the actual problem going away aren't always the same graph.
