---
title: "Conditional Access: The Policy Isn't Always the Problem"
date: 2026-04-28
bannerImage: "images/blog/Banner2.png"
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

But I've found that the useful part of the investigation is not simply finding a policy that was involved.

It's understanding why it applied and what the rest of the sign-in information is telling you.

## Start with the sign-in

When I'm investigating an authentication issue, I want to see what Entra is actually reporting.

The message the user sees gives me the symptom.

The sign-in logs give me something much more useful to investigate.

I can look at the sign-in attempt, authentication details and the Conditional Access results to understand what happened.

That starts turning a vague access problem into something I can actually work with.

Instead of:

> The user can't sign in.

I'm trying to get to:

> This sign-in attempt was evaluated against these conditions, and this is what happened.

That gives me somewhere to go next.

## One investigation that stuck with me

I had an authentication issue where a user was unable to access what they needed.

It would have been easy to treat it as a general login problem.

Instead, I went into the sign-in information and looked at what was actually happening.

The results showed that a specific Conditional Access policy was affecting the request. In this case, it was the blocked-countries policy.

That changed the investigation completely.

It wasn't a mysterious authentication failure.

There was a control being applied, and the sign-in information showed me which one.

That meant I could investigate the actual reason for the denial rather than starting to change unrelated settings.

## The lesson wasn't that Conditional Access was the problem

The lesson for me was much simpler.

Follow the evidence.

Conditional Access can involve different conditions and policies, and the user isn't necessarily going to know which part of that process has stopped them.

If I simply assume the policy is wrong, I could end up changing something that is actually working exactly as intended.

The first question should be why the policy applied.

Then I can work out whether that behaviour is expected.

If it is, the solution might not involve changing the policy at all.

## Context matters

One of the things I find interesting about identity issues is how much can sit behind a very simple error message.

The user experiences:

> I can't sign in.

But behind that request there is information about the user, the device, the authentication attempt and the policies being evaluated.

There can also be information about the device's compliance state and the circumstances of the sign-in.

The user sees the outcome.

The logs help explain how that outcome was reached.

That's why I prefer looking at the actual sign-in information before making assumptions about what needs changing.

## Don't change the control just to make the error disappear

This is probably the biggest practical lesson I've taken from working with access issues.

If a security control is doing what it was designed to do, removing or weakening it simply because one user is being blocked isn't necessarily a solution.

First, understand why it applied.

Then establish whether that behaviour is expected.

If it isn't expected, investigate why.

If it is expected, the answer might be something else entirely.

The user may need a different access route.

There may be another way of meeting the requirement.

The policy may genuinely need reviewing.

Or nothing may need changing at all.

You can't really make that decision until you understand what happened.

## This is the part of troubleshooting I enjoy

I like problems where the first description doesn't give you the whole picture.

Not because I want to make things complicated.

Quite the opposite.

I want to take something vague and turn it into something I can understand.

A user can't sign in.

I look at the sign-in.

I see what happened.

I check the relevant policy result.

I work out whether the behaviour is expected.

Then I know what I'm actually dealing with.

That's much better than changing a setting and hoping the error disappears.

## The practical takeaway

When someone can't sign in, I try not to start with:

> Which setting should I change?

I start with:

> What does the sign-in tell me?

That small change in approach can save a lot of time.

More importantly, it means I'm trying to fix the actual problem rather than changing things until the error goes away.

Sometimes Conditional Access really is the reason someone can't get in.

But finding a policy involved in a failed sign-in isn't the end of the investigation.

It's the point where the useful investigation starts.
