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

I've spent a fair amount of time working with resolver teams, and one thing I've learned is that the quality of the handover matters.

If the next team has to start the investigation again, I've probably not done enough.

## What happened?

The first thing I want the next person to understand is what the actual issue is.

Not just:

> User cannot access application.

That doesn't tell them much.

What was the user trying to do?

What happened?

When did it start?

Is it one user or several?

What is the impact?

That gives the next team some context.

## What have I already checked?

This is probably the most important part.

If I've checked sign-in logs, I want to say that.

If I've tested another device, I want to say that.

If I've checked Conditional Access, device compliance or licensing, I want that recorded.

The aim is to show what has already been investigated.

That means the next person isn't spending their first hour repeating the same checks.

## Evidence matters

When an issue needs to be escalated, I'll use whatever evidence is useful for that particular problem.

That might be:

- Sign-in logs
- Audit logs
- Application logs
- Event Viewer
- Screenshots
- HAR files
- PowerShell output
- Network testing
- Device information
- Configuration details

It isn't about attaching everything I've collected.

It's about including the things that support the investigation.

If a screenshot proves something useful, include it.

If a log entry shows the failure, include it.

If a test rules something out, explain that too.

## What has already been ruled out?

This is often overlooked.

Knowing what isn't causing a problem can be just as useful as knowing what is.

For example, if I've tested the same account on another device and it works, that's useful.

If the issue follows the user, that tells me something.

If it stays with the device, that tells me something else.

Every useful test should narrow the problem down.

## Explain the impact

A technical issue isn't just a technical issue.

There is a person or business activity behind it.

If something affects one user, that's different from something affecting an entire department.

If someone is completely blocked from working, that's different from an inconvenience.

I've become more conscious of recording that information because it helps the receiving team understand what matters.

## Escalation isn't giving up

I think this is worth saying because escalation can sometimes be seen as passing the problem away.

It shouldn't be.

There are plenty of things in IT where the service desk isn't the team that owns the final fix.

That's normal.

My responsibility is to do as much useful investigation as I can and make the handover as good as possible.

That is still taking ownership.

## What I've learned

The best escalations I've sent are the ones where someone can read the summary and understand:

**What happened.**

**What was tested.**

**What the evidence shows.**

**What has been ruled out.**

**What the impact is.**

**What I think needs looking at next.**

That doesn't guarantee a quick resolution.

Some problems are genuinely complicated.

But it gives the next person a much better starting point.

And in a busy support environment, that matters.
