---
title: "When the Fix Is Simpler Than the Investigation"
date: 2026-05-12
draft: false
summary: "A real Excel co-authoring issue where the investigation was more complicated than the final fix."
tags: ["Microsoft 365", "Excel", "Troubleshooting"]
categories: ["Blog"]
showTableOfContents: false
---

One of the things I like about troubleshooting is that the amount of work involved in finding an answer doesn't always have much to do with how complicated the eventual fix turns out to be.

I had a good example of this with an Excel co-authoring issue.

The eventual fix was fairly simple.

Getting to that fix took a bit more investigation.

## The problem

The issue was around users trying to co-author an Excel workbook.

They expected to be able to work on the file together, but the co-authoring behaviour wasn't working as expected.

At that point, there are quite a few places you could start looking.

Is it a Microsoft 365 issue?

Is it SharePoint or OneDrive?

Is it permissions?

Is there something wrong with the Office client?

Is the device causing the problem?

Or is there something about the actual file?

That's the problem with a fairly broad symptom. There are plenty of things that could potentially be responsible.

So rather than immediately changing something, I started narrowing it down.

## Start with the actual situation

I wanted to understand exactly what was happening rather than just treating it as "Excel co-authoring doesn't work".

What type of file was it?

Where was it stored?

Was the problem affecting everyone?

Was it happening with every workbook or just this particular one?

What happened when the users tried to work on it?

Those questions started to reduce the number of possibilities.

The file itself became more interesting as the investigation continued.

It was an `.xlsb` workbook.

That turned out to be an important detail.

## The eventual fix

The solution was to convert the workbook from `.xlsb` to `.xlsx`.

Once that was done, the co-authoring issue was resolved.

That's it.

No complicated script.

No major Microsoft 365 configuration change.

No rebuilding the user's machine.

Just changing the file format.

It would be easy to look at that afterwards and think the problem was simple.

In one sense, it was.

But that doesn't mean the investigation wasn't necessary.

## The fix isn't always the interesting part

This is something I've come to appreciate more as I've gained experience in IT support.

When you know the answer, the answer can look obvious.

Before you know the answer, there are usually several possible explanations.

If I'd immediately assumed this was a permissions issue, I could have spent time looking in the wrong place.

If I'd started changing Office settings, I could have made things more complicated.

If I'd rebuilt the user's device, I'd have been solving a completely different problem.

The investigation gave me enough information to make a sensible change rather than just trying things until something worked.

That's an important difference.

## I try not to change things just for the sake of changing them

There's a temptation in troubleshooting to feel like you need to be doing something all the time.

Click this.
Change that.
Restart something.
Reinstall something.
Clear something.

Sometimes that's exactly what you need to do.

But if you haven't established what you're trying to prove, you can easily end up making changes without really learning anything from them.

I've found it more useful to treat each check as a way of narrowing the problem down.

If something works on one device but not another, that's useful.

If another user can open the same file, that's useful.

If the issue follows the file rather than the user, that's useful.

You don't necessarily need a complicated troubleshooting methodology.

You just need to pay attention to what each result is telling you.

## The simple fix is still a good outcome

I actually think there is something quite satisfying about finding a simple answer to a problem that initially looked more complicated.

You haven't failed because the final fix was straightforward.

Quite the opposite.

The point of the investigation was to get to the right answer with as little unnecessary change as possible.

In this case, the final solution was simply using a file format that supported the co-authoring scenario properly.

The work was in figuring that out.

## It also reminded me not to get too attached to my first idea

This is probably the bigger lesson I took from it.

When you're troubleshooting something you've seen before, it's very easy to think you already know what the problem is.

Sometimes you do.

Sometimes you don't.

I've had plenty of situations where the initial description of an issue pointed me in one direction and the evidence took me somewhere else.

That's normal.

The important thing is being willing to change your mind when the evidence doesn't support your first assumption.

## That's something I've found useful beyond troubleshooting

This is also one of the reasons I've enjoyed studying service management.

I'm increasingly interested in the thinking behind the work rather than just the technical action that resolves the immediate issue.

What is actually happening?
Where is the problem occurring?
What is the impact?
What information do we have?
What do we need to change?
And, once it is fixed, is there anything useful we should take from it?

The Excel issue was just a support problem.

But it was a good reminder that a technical fix is only one part of the investigation.

## The best fix isn't necessarily the most complicated one

I think there's sometimes an assumption that a difficult problem needs an impressive solution.

I'm not sure that's true.

A good troubleshooting process should ideally make the final solution simpler, not more complicated.

In this case, the investigation started with a fairly broad Microsoft 365 problem and eventually came down to the format of a single Excel workbook.

That's a much better outcome than changing half the environment and hoping for the best.

So these days, when I come across a problem that looks complicated, I try not to make it more complicated than it needs to be.

Start with what I know.

Find out what I don't.

Use the evidence to narrow it down.

Then make the smallest sensible change.

Sometimes, after all that, the fix is surprisingly simple.
