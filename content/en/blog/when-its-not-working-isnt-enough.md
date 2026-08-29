---
title: "When \"It's Not Working\" Isn't Enough"
date: 2026-03-17
draft: false
summary: "Why turning a vague support issue into something you can actually investigate matters."
tags: ["IT Support", "Troubleshooting", "Evidence"]
categories: ["Blog"]
showTableOfContents: false
---

One of the most common things you get in IT support is a ticket that basically says:

> It's not working.

Sometimes that's enough to get started.

Usually it isn't enough to solve it.

The first job is turning that statement into something you can actually investigate.

## What does "not working" mean?

A user might say they can't access something.

That could mean:

- They can't sign in.
- They can sign in but can't open the application.
- The application opens but a particular function doesn't work.
- It works on one device but not another.
- It worked yesterday but doesn't work today.
- Everyone is affected.
- One person is affected.

They're all very different problems.

The wording of the ticket is the starting point, not necessarily the diagnosis.

So I try to establish what the user is actually seeing.

What were they trying to do?
What happened?
What did they expect to happen?
When did it start?
Has it ever worked?
Is anyone else affected?
What has already been tried?

That usually gives me something much more useful to work with.

## Then I start looking for evidence

This is where I prefer to slow down rather than immediately start changing things.

Depending on the problem, that might mean looking at sign-in logs, device state, Conditional Access results, Event Viewer, application logs, network information or PowerShell output.

The evidence is often more useful than the error message on its own.

For example, an access problem might look like a generic authentication failure from the user's point of view.

But if I can see the sign-in attempt and the policies that were evaluated, I have something much more concrete.

The same applies to endpoint problems.

If a device says something isn't compliant, I want to understand what the device is reporting and which requirement isn't being met.

The aim isn't to collect every possible log.

It's to find the information that helps narrow down the problem.

## Don't make five changes at once

This is one of those habits that sounds obvious until you're under pressure.

If I change five things and the problem disappears, I know the problem is gone.

I don't necessarily know why.

That can make the next incident harder.

Where possible, I prefer to test one thing at a time and use the result to decide what to do next.

Sometimes the answer is obvious.

Sometimes it takes longer.

But I'd rather understand what fixed something than accidentally stumble across the answer.

## The initial symptom isn't always the cause

I've had issues where the first description pointed in one direction and the investigation took me somewhere else.

That's normal.

A user sees the result of a problem.

They don't necessarily see the thing causing it.

That's why I don't think troubleshooting should start with deciding what the cause is.

It should start with understanding what is happening.

There is a subtle difference.

If I decide too early that something is a licensing problem, a network problem or a Conditional Access problem, I can end up looking only for evidence that supports that assumption.

If I start with the evidence, I have a better chance of finding what is actually happening.

## A good investigation doesn't have to be complicated

There is sometimes a temptation in IT to make a problem sound more complicated than it is.

I don't think that's helpful.

The tools can be complicated.
The environment can be complicated.
The process of getting to the answer can take time.

But the explanation should be as simple as it can reasonably be.

What happened?
Why did it happen?
What fixed it?
Is there anything else we should do?

That's usually enough.

## What I've learned

Working in support has made me appreciate that the first few minutes of an investigation can make a big difference.

If I understand the problem properly, I can investigate it properly.

If I don't, I can spend a lot of time solving the wrong problem.

So when a ticket says "it's not working", I don't really see that as the problem.

It's the beginning.

The useful bit is finding out what "not working" actually means.
