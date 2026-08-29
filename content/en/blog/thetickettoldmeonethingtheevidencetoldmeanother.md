---
title: "The Ticket Told Me One Thing. The Evidence Told Me Another."
date: 2026-07-07
draft: false
summary: "Why the first description of a problem is the starting point, not always the diagnosis."
tags: ["Troubleshooting", "IT Support", "Evidence"]
categories: ["Blog"]
showTableOfContents: false
---

One of the easiest traps in IT support is assuming the first description of a problem is the problem itself.

It isn't.

It's the starting point.

## The ticket is someone's view of the problem

A user isn't trying to give you a technical diagnosis.

They're trying to tell you what they were trying to do and what happened instead.

That's useful.

But there's a difference between:

> I can't sign in.

and:

> The sign-in attempt is being blocked by a specific Conditional Access policy.

The first is the experience.

The second is something we've established through investigation.

Getting from one to the other is the job.

## The Conditional Access example

I had an authentication issue where the initial symptom looked like a general access problem.

Looking at the Entra sign-in information changed the picture.

The Conditional Access results showed that a specific blocked-countries policy was responsible for the sign-in being denied.

That was much more useful than simply knowing the user couldn't sign in.

It told me what was happening and where to look next.

## Another example: Excel

The same thing happened with an Excel co-authoring issue.

The symptom was that co-authoring wasn't behaving as expected.

There were plenty of possible places to investigate.

But looking at the actual file showed that it was an `.xlsb` workbook.

Converting it to `.xlsx` resolved the issue.

Again, the initial description was accurate.

It just didn't contain the cause.

## That's why I like evidence-led troubleshooting

The more I work in support, the more I try to separate:

**What the user is seeing**

from

**What the system is telling me**

Both matter.

The user tells me about the experience and impact.

The technical evidence helps me understand what is happening underneath.

You need both.

## It also stops me jumping to conclusions

If someone says:

> My laptop can't access the application.

I could immediately start looking at the network.

But maybe the device is compliant.

Maybe the network is fine.

Maybe the application is working.

Maybe the user is being blocked by an access policy.

I don't know until I check.

That's why I like simple questions.

What works?

What doesn't?

Is it only this device?

Is it only this user?

Does it happen somewhere else?

What does the log show?

Each answer moves the investigation forward.

## Sometimes the evidence proves your first idea was right

That's fine too.

If I think it's DNS and the tests show it's DNS, great.

If I think it's a device compliance issue and the device state confirms it, great.

The point isn't to avoid assumptions completely.

It's to be willing to change them.

## This is also where documentation helps

If I've investigated something properly, I want the useful parts recorded.

That helps if the issue returns.

It helps another engineer.

It helps with escalation.

And it can help identify patterns later.

I've become much more interested in this through my work on knowledge articles and process documentation.

The investigation shouldn't disappear when the ticket closes if there is something useful to keep.

## What I've taken from this

I don't think the answer is to distrust every ticket.

The ticket is important.

It's where the problem starts.

But I try not to let the ticket decide the diagnosis for me.

Start with what the user is experiencing.

Then look at what the system is telling you.

Sometimes they match.

Sometimes they don't.

That's usually where the interesting part begins.
