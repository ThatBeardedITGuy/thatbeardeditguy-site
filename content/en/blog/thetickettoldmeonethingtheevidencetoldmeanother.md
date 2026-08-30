---
title: "The Ticket Told Me One Thing. The Evidence Told Me Another."
date: 2026-07-07
draft: false
summary: "Why the first description of a problem is the starting point, not always the diagnosis."
tags: ["Troubleshooting", "IT Support", "Evidence"]
categories: ["Blog"]
showTableOfContents: false
---

One of the easiest traps in IT support is assuming that the first description of a problem is the problem itself.

I've done it.

It's very easy to read a ticket, see a familiar symptom and immediately start thinking about what you believe the cause is.

The problem is that the person raising the ticket is describing what they are experiencing. They aren't necessarily describing what is happening underneath.

That distinction has become something I'm much more conscious of as I've gained experience in support.

## The ticket is someone's view of the problem

When someone raises a ticket saying they can't sign in, that's useful information.

They're telling me what they're experiencing.

They're not necessarily expected to know whether the problem is authentication, Conditional Access, device compliance, licensing or something else. That's part of what I'm there to investigate.

There's a difference between:

> I can't sign in.

and:

> The sign-in attempt is being blocked by a specific Conditional Access policy.

The first tells me about the user's experience.

The second is something I've established through investigation.

Getting from one to the other is where the actual troubleshooting starts.

## I saw this with a Conditional Access issue

I've had an authentication issue where the initial symptom looked like a fairly general access problem.

From the user's perspective, they simply couldn't sign in.

There are quite a few possible reasons for that, so rather than assuming it was an account or application problem, I looked at the Entra sign-in information.

That changed the picture.

The sign-in information showed that a specific Conditional Access policy was responsible for the request being blocked. In this case, it was the blocked-countries policy.

That was much more useful than simply knowing the user couldn't sign in.

It gave me something concrete to work with and explained why the sign-in was being denied.

The important part wasn't that I knew the name of the policy beforehand.

I didn't need to.

The investigation gave me the answer.

## The same thing happened with an Excel issue

I had a similar experience with an Excel co-authoring issue.

The initial problem was straightforward enough. Users were trying to work on a workbook together and the co-authoring behaviour wasn't working as expected.

There were plenty of things that could potentially have caused that.

It could have been related to the Microsoft 365 service, permissions, the user's device, the Office client or something about the file itself.

Rather than immediately changing something, I looked more closely at the workbook.

It was an `.xlsb` file.

Converting it to `.xlsx` resolved the issue.

The fix itself was simple.

The investigation was what established that it was the file format that mattered.

Again, the original ticket wasn't wrong.

The users really couldn't co-author the workbook.

It just didn't tell me why.

## That's why I like working from evidence

The more I've worked in support, the more I've tried to separate two things in my head.

What is the user experiencing?

And what is the system telling me?

Both are important.

The user gives me the context and the impact. They can tell me what they were trying to achieve, what happened and whether something has changed.

The technical information helps me understand what is actually happening underneath.

If I only look at one side, I'm missing part of the picture.

This is particularly useful when dealing with things like authentication and device issues, where the visible symptom can be fairly generic but the underlying reason can be much more specific.

## It also stops me getting too attached to my first idea

If someone tells me their laptop can't access an application, there are plenty of things I could immediately start checking.

I could look at the network.

I could look at the application.

I could look at the device.

I could look at the user's account.

I could look at Conditional Access.

But I don't know which one matters until I have something to support that direction.

So I try to start with relatively simple questions.

What actually works?

What doesn't?

Is it only this user?

Is it only this device?

Does the same thing happen somewhere else?

Has anything changed?

What does the relevant log show?

Each answer gives me another piece of information.

Sometimes it confirms the direction I was already thinking about.

Sometimes it sends me somewhere completely different.

## Sometimes your first assumption is right

There's nothing wrong with having an initial theory.

If I have seen a particular type of issue before, it makes sense that I might have an idea about where to start.

If I think something might be related to DNS and the testing supports that, that's useful.

If I think a device compliance issue might be responsible and the device state confirms it, that's useful too.

The problem isn't having an assumption.

The problem is treating the assumption as the answer before you've checked it.

I've found it much more useful to be willing to change direction when the evidence doesn't support my first thought.

That's part of troubleshooting.

You start somewhere, you test it, you learn something and then you decide where to go next.

## The investigation is useful even when someone else needs to fix it

This is also where it connects with the way I approach escalations.

Sometimes I'll investigate an issue as far as I can and find that another team needs to take it further.

That's fine.

The work I've already done still has value.

If I've established that the user can access the service from one device but not another, that's useful.

If I've found a Conditional Access result that explains why authentication is being blocked, that's useful.

If I've tested something and ruled it out, that's useful too.

It means the next team isn't just receiving the original symptom.

They're receiving part of the investigation.

That's one of the reasons I think evidence-led troubleshooting and good escalation go together.

## Documentation means the investigation doesn't have to disappear

If I've worked through something that could be useful again, I want the important parts recorded.

That doesn't mean writing a ten-page document every time something goes wrong.

Sometimes the useful information is simply the cause, the resolution and a couple of checks that helped identify it.

I've become more conscious of this through the documentation and knowledge work I've done.

If the same issue appears again, having something useful to refer back to can save time.

It can also help another engineer understand what happened without having to repeat the entire investigation.

And sometimes recording something helps reveal a pattern that wasn't obvious from one ticket alone.

## The first description is still important

I don't think the answer is to distrust tickets or assume that users don't know what they're talking about.

Quite the opposite.

The user's description is where the investigation starts.

They're the person experiencing the problem, so their description of what happened and what they were trying to do is important.

I just don't want that description to become the diagnosis automatically.

The user might say they can't sign in.

The evidence might show a Conditional Access policy blocking them.

They might say Excel co-authoring isn't working.

The investigation might show that the file format is the problem.

Both users described their problems accurately.

The investigation simply gave me a better understanding of what was happening underneath.

## What I've taken from this

I've become much more comfortable with the idea that I don't need to know the answer immediately.

I need to know how to find it.

That means starting with the user's experience, gathering the relevant information, testing what I can and being prepared to change direction when the evidence points somewhere else.

Sometimes the first idea will be right.

Sometimes it won't.

Either way, the important thing is that the investigation is based on what you can actually establish rather than what you think is probably happening.

The ticket tells me where to start.

The evidence tells me where to go next.
