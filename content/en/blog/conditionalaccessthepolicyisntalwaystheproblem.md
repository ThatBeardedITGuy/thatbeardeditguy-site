---
title: "Conditional Access: The Policy Isn't Always the Problem"
date: 2026-04-28
draft: false
summary: "A practical look at following the evidence through an authentication investigation."
tags: ["Microsoft 365", "Entra ID", "Conditional Access"]
categories: ["Blog"]
showTableOfContents: false
---

Conditional Access can be one of those things where a user says:

> I can't sign in.

And the immediate assumption is that a policy has blocked them.

Sometimes it has.

But the useful part of the investigation is finding out which policy, why it applied and what the rest of the sign-in information tells you.

## Start with the sign-in

When I'm investigating an authentication issue, I want to see what Entra is actually reporting.

The sign-in logs give me much more to work with than the message the user sees.

I can look at the sign-in attempt, authentication details and the Conditional Access results.

That starts turning a vague access problem into something I can investigate.

## One investigation I remember

I had an authentication issue where the user was unable to access what they needed.

It would have been easy to treat it as a general login problem.

Instead, looking at the sign-in information showed that the request was being affected by a specific Conditional Access policy.

In this case, the relevant policy was the blocked-countries policy.

That changed the investigation completely.

It wasn't a mysterious authentication failure.

There was a control being applied and the sign-in information showed why.

## The lesson wasn't "Conditional Access is bad"

The lesson for me was much simpler.

Follow the evidence.

Conditional Access can involve multiple policies and conditions, and a user doesn't necessarily know which part of that process has stopped them.

If I guess, I can end up changing something that doesn't need changing.

If I check the sign-in information, I have something concrete to work from.

## It also shows why context matters

A policy decision doesn't happen in isolation.

The sign-in has context around it.

The user.

The device.

The location information available to the service.

The authentication method.

The policies being evaluated.

The device's compliance state.

There can be a lot going on behind a fairly simple message saying access has been denied.

That's why I find identity troubleshooting interesting.

The user sees the outcome.

The logs can help explain the process that produced it.

## Don't change the policy just to make the error disappear

This is probably the biggest practical lesson.

If a policy is doing exactly what it was designed to do, removing or weakening it just to get one user through isn't necessarily a solution.

First understand why the policy applied.

Then understand whether that behaviour is expected.

If it isn't expected, that's a different problem.

That distinction matters, particularly when access controls are involved.

## This is where my ITIL learning fits in too

I'm not interested in forcing a framework into every troubleshooting session.

But studying service management has made me more conscious of the difference between the immediate symptom and the wider service.

The immediate request might be:

> Get this user signed in.

The useful investigation is:

> Why was access denied?

And if the answer is:

> A policy correctly blocked the request.

Then the outcome might be different again.

Maybe the user needs a different access path.

Maybe the policy needs reviewing.

Maybe nothing needs changing at all.

The important thing is that we know what happened.

## The practical takeaway

When someone can't sign in, I try not to start with:

> Which setting should I change?

I start with:

> What does the sign-in tell me?

That small change in approach can save a lot of time.

And it means I'm fixing the actual problem rather than trying random changes until the error goes away.
