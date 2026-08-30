---
title: "It's Always DNS... Until It Isn't"
date: 2026-05-26
bannerImage: "images/blog/Banner4.png"
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

Can't connect? Probably DNS.

Can't access an application? Probably DNS.

Something suddenly stopped working? Have you checked DNS?

Sometimes that instinct is useful. Experience gives you an idea of where to start.

The problem is when the likely answer becomes the assumed answer.

If I've already decided something is DNS before I've checked, I can end up looking for evidence that proves me right instead of finding out what is actually happening.

## I've learned to slow down at the beginning

When I'm working through a connectivity issue, I want to establish what is actually failing.

Can the device connect to the network?

Does it have the expected IP configuration?

Can it resolve the name?

Can it reach the destination?

Is the service itself responding?

Is it one device or several?

Those checks start narrowing things down.

If the evidence points towards DNS, great. I can investigate DNS.

If it doesn't, I can move on.

That sounds obvious, but when you're dealing with a busy support queue and a familiar-looking problem, it's easy to jump ahead.

## The same thing happens outside networking

I've seen the same assumptions with Microsoft 365, identity and endpoints.

A user can't sign in. It must be their password.

A device isn't accessing something. It must be Intune.

An application isn't working. It must be the application.

Sometimes it is.

But the symptom doesn't necessarily tell you the cause.

I've had an authentication issue where the user simply couldn't sign in. Looking at the Entra sign-in information showed that a specific Conditional Access policy was actually blocking the request.

The initial symptom was correct.

The assumption about the cause would have been wrong.

That's why I try to separate what the user is experiencing from what the system is telling me.

## Evidence keeps you honest

The more I've worked in support, the more I appreciate having something concrete to work from.

A log entry.
A policy result.
A device state.
A test result.
Something as simple as:

> It works on this device but not that one.

can completely change the direction of an investigation.

If the same account works elsewhere, that's useful.

If several users have the same problem, that's useful.

If something can be ruled out, that's useful too.

The aim isn't to collect every possible piece of information.

It's to find the information that helps narrow the problem down.

## Your first idea can still be right

I'm not against having a theory.

If I've seen a particular issue before, it makes sense that I might have an idea about where to start.

If I suspect DNS and the evidence confirms it, great.

The important part is that I checked.

Experience should help you know where to look first.

It shouldn't stop you looking elsewhere when the evidence tells you to.

## Don't investigate forever either

There's another side to this.

Not every connectivity issue needs a complete investigation into every possible layer of the network.

If the evidence clearly shows that DNS is the problem and fixing it resolves the issue, that's probably enough.

Fix it, make sure it works, record anything useful and move on.

The point isn't to investigate everything forever.

It's to investigate enough to be confident that you've understood what is happening and that the change you're making is appropriate.

## So yes, check DNS

Of course you should.

DNS really does cause plenty of problems.

But I've found that the better approach is to start with an idea without becoming attached to it.

Look at the symptom.

Gather the evidence.

Test what you can.

Follow where the investigation takes you.

Sometimes it really is DNS.

And sometimes it really, really isn't.
