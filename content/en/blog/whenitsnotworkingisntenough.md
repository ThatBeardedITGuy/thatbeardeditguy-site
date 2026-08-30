---
title: "When \"It's Not Working\" Isn't Enough"
date: 2026-03-17
bannerImage: "images/blog/Banner6.png"
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

A user might say they can't access something, but that can mean quite a few different things. They might not be able to sign in at all, they might be able to sign in but not open the application, or the application might open but a particular function isn't working. It might work perfectly well on another device, or it might have stopped working for everyone rather than just one person.

Those are all very different problems, even though the ticket might simply say "can't access the application".

The wording of the ticket is the starting point, not necessarily the diagnosis.

So I try to establish what the user is actually seeing. What were they trying to do? What happened? What did they expect to happen? When did it start? Has it ever worked? Is anyone else affected? What has already been tried?

That usually gives me something much more useful to work with.

It also gives me a better idea of where to start looking rather than immediately jumping to a particular cause.

## Then I start looking for evidence

This is where I prefer to slow down rather than immediately start changing things.

Depending on the problem, that might mean looking at sign-in logs, device state, Conditional Access results, Event Viewer, application logs, network information or PowerShell output.

The evidence is often more useful than the error message on its own.

For example, an access problem might look like a generic authentication failure from the user's point of view. But if I can see the sign-in attempt and the policies that were evaluated, I have something much more concrete to work with.

The same applies to endpoint problems. If a device says something isn't compliant, I want to understand what the device is reporting and which requirement isn't being met.

I'm not trying to collect every possible log or check every setting I can find. I'm trying to find the information that helps narrow down the problem.

That distinction is important because it's very easy to spend a lot of time looking at information that doesn't actually help you get any closer to an answer.

## Don't make five changes at once

This is one of those habits that sounds obvious until you're under pressure.

If I change five things and the problem disappears, I know the problem is gone. I don't necessarily know why.

That can make the next incident harder, particularly if one of those changes wasn't actually necessary.

Where possible, I prefer to test one thing at a time and use the result to decide what to do next. Sometimes the answer is obvious and sometimes it takes longer, but I'd rather understand what fixed something than accidentally stumble across the answer.

It also means that if the problem comes back, I've got a much better idea of what to look at.

I'm not saying you should never make multiple changes. Sometimes you have to, particularly when you're dealing with an issue that needs restoring quickly. But where I can, I like to understand the reason behind the change rather than just trying things until something works.

## The initial symptom isn't always the cause

I've had issues where the first description pointed in one direction and the investigation took me somewhere else.

That's normal.

A user sees the result of a problem. They don't necessarily see the thing causing it.

That's why I don't think troubleshooting should start with deciding what the cause is. It should start with understanding what is happening.

There is a subtle difference.

If I decide too early that something is a licensing problem, a network problem or a Conditional Access problem, I can end up looking only for evidence that supports that assumption.

If I start with the evidence, I have a better chance of finding what is actually happening.

I've seen this with authentication issues in particular. From the user's perspective, they simply can't get into something. Once you start looking at the sign-in information, though, you can sometimes see that there is a much more specific reason behind it.

The same thing happens with devices and applications. The first symptom gives you somewhere to start, but it doesn't necessarily tell you where you'll finish.

## A good investigation doesn't have to be complicated

There is sometimes a temptation in IT to make a problem sound more complicated than it is.

I don't think that's helpful.

The tools can be complicated. The environment can be complicated. The process of getting to the answer can take time.

But the explanation should be as simple as it can reasonably be.

If I can explain what happened, why it happened and what fixed it, that's much more useful than filling the explanation with technical detail that doesn't actually help anyone understand the issue.

This is something I've become more conscious of as I've gained experience. Knowing how to investigate something is important, but so is being able to explain what you've found to someone else.

That might be another engineer picking up the ticket, a resolver team you've escalated to, or the user themselves.

The technical detail should support the explanation, not become the explanation.

## What I've learned

Working in support has made me appreciate that the first few minutes of an investigation can make a big difference.

If I understand the problem properly, I can investigate it properly.

If I don't, I can spend a lot of time solving the wrong problem.

That's probably one of the reasons I enjoy troubleshooting. There is something satisfying about taking a vague problem, working through what you actually know, finding the evidence and gradually narrowing it down until the answer becomes clear.

It doesn't always happen quickly.

Sometimes you have to escalate it. Sometimes another team has information or access that you don't have. Sometimes the answer isn't obvious at all.

That's part of the job.

So when a ticket says "it's not working", I don't really see that as the problem.

It's the beginning.

The useful bit is finding out what "not working" actually means, and then working from there.
