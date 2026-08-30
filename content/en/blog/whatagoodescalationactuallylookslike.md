---
title: "What a Good Escalation Actually Looks Like"
date: 2026-04-14
draft: false
summary: "What I try to include when handing a technical issue to another team."
tags: ["IT Support", "Escalation", "Service Management"]
categories: ["Blog"]
showTableOfContents: false
---

There is a big difference between escalating a ticket and handing someone a problem they can actually work with.

Working in an MSP environment means that I'm often dealing with issues where I can investigate a long way, but the eventual fix belongs with another team. That is just part of working in a wider support structure.

What I've learned is that an escalation shouldn't mean I've simply moved the ticket somewhere else.

If I'm handing an issue to another team, I want to give them a useful starting point.

## The first thing is making sure they understand the problem

The person picking up an escalation wasn't necessarily involved when the issue was first reported, so I try to make sure they can understand what is actually happening without having to go back through the entire ticket themselves.

"User cannot access application" doesn't tell them very much.

What was the user trying to do? What happened when they tried? When did the problem start? Has it ever worked? Is it affecting one person or several? What is the actual impact?

Those details give the next engineer some context before they start looking at the technical side.

I've found this particularly important with issues where the original user description is fairly broad. A user might report that they can't sign in, for example, but the investigation might eventually show that the problem is related to a particular Conditional Access policy, device state or another part of the authentication process.

The escalation needs to reflect what I've actually found rather than just repeating the original ticket.

## I want the next team to know what I've already checked

This is probably the most important part of an escalation for me.

If I've already checked the sign-in logs, I want that recorded. If I've looked at Conditional Access, device compliance, licensing or application behaviour, I'll include that where it's relevant.

The reason isn't to prove how much investigation I've done.

It's to stop the next engineer having to repeat the same work.

If I've tested the user's account on another device and it works, that's useful information. If another user can access the same application, that's useful too. If I've found something in the logs that changes the direction of the investigation, that needs to be included.

Even when a test doesn't find the answer, it can still be useful because it rules something out.

That gives the next person a better place to start.

## Evidence is more useful than assumptions

When I'm investigating an issue, I try to work from what I can actually establish rather than what I think is probably happening.

That becomes even more important when I'm escalating something.

Depending on the problem, the useful evidence could be sign-in information, audit logs, application logs, Event Viewer information, screenshots, PowerShell output, network testing, device information or configuration details.

I don't think an escalation should just contain every piece of information you've collected.

More isn't necessarily better.

The useful question is whether the evidence helps explain the problem or supports something you've already established.

If a particular log entry shows the failure, include it.

If a test demonstrates that the issue only occurs on one device, explain that.

If you've ruled something out, say how you ruled it out.

That gives the receiving team something they can actually work with.

## The things that don't happen can be useful too

One thing I've become more conscious of is the value of knowing what has already been ruled out.

For example, if the same user can sign in successfully from another device, that tells me something.

If another user can access the same service, that tells me something else.

If the issue follows the user rather than the device, that changes where I would look next.

None of those tests necessarily fixes the problem, but they reduce the number of possibilities.

When I include that information in an escalation, I'm effectively passing on part of the investigation rather than handing over the original symptom and asking someone else to start from scratch.

## The impact matters as well

There's also a difference between understanding what is technically wrong and understanding what the problem means for the user.

If one person has an inconvenience, that's different from a whole department being unable to work.

If someone is completely blocked from doing their job, that needs to be understood by the team receiving the escalation.

I've become more conscious of capturing that context because the technical description doesn't always show the real impact.

The receiving team needs to understand not only what is happening, but why it matters.

That can help them make better decisions about what needs attention first.

## Escalating something doesn't mean giving up on it

I think this is an important distinction.

There are plenty of issues where the service desk isn't the team that owns the final fix. That doesn't mean the service desk hasn't taken ownership of the issue.

For me, ownership means doing what I reasonably can to understand the problem, gathering the right information and making sure it gets to the people who can take it further.

If I've investigated an issue properly and then escalated it with a clear explanation of what I've found, I still feel responsible for making sure the handover is useful.

I'm not passing the problem away and forgetting about it.

I'm moving it to the team that is better placed to resolve the next part.

## A good escalation should tell a story

When I look back at the escalations I've found most useful, they generally have a simple flow to them.

This is what the user was trying to do.

This is what happened.

This is what I've checked.

This is what the evidence shows.

This is what I've ruled out.

This is the impact.

And this is where I think the investigation needs to go next.

It doesn't need to be a huge amount of writing. It just needs to give the next person enough information to understand the situation and continue the investigation without starting again from the beginning.

That's particularly important in a busy support environment, where the difference between a useful escalation and a poor one can be another engineer spending an hour repeating checks that have already been done.

## It's something I'm still improving

I'm not going to pretend I've mastered the art of escalation.

There are always things that could have been explained better, and sometimes you only realise what information was missing after the next team comes back with another question.

That's part of learning.

The more technical investigations I've worked through, the more I've understood what information is likely to be useful to someone else.

I've also become more aware that a good escalation is part of good service delivery. The technical investigation might have happened at the service desk, but the quality of the handover affects what happens next.

For me, that's what a good escalation really comes down to.

I don't necessarily need to fix the problem myself.

I do need to make sure that when it moves to someone else, they have a clear understanding of what happened, what has already been investigated and what they need to look at next.

That is still taking ownership.
