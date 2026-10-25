---
title: "A Control Nobody Checks Is Just an Assumption"
date: 2026-10-25
bannerImage: "images/blog/Banner2.png"
draft: false
summary: "Two small things that weren't broken, and why 'it's automated' isn't the same as knowing it works."
tags: ["Information Security", "IT Support", "Continual Improvement"]
categories: ["Blog"]
showTableOfContents: false
---
A couple of things came up at work recently that I keep thinking about. Neither of them was broken, which is sort of the point.

## The distribution list

We had an all-staff distribution list that ran off a dynamic filter. New starters get added, leavers drop off, nobody has to touch it. Which is great, until you realise nobody has looked at it in ages either.

I got a ticket to tidy it up, so I exported the membership. It had shared mailboxes in it. Service accounts. A couple of people who'd already left.

When I dug into why, the filter was basically "anyone with a mailbox and a job title." Most real people have a job title, so that sort of works. But shared mailboxes and service accounts can have job titles too, and some of ours did. So in they went.

The filter wasn't wrong exactly. It did what it was set up to do. It just wasn't what everyone thought it was doing.

And yeah, it's only a distribution list. Worst case, a shared mailbox gets the Friday update. But if that same logic was deciding who could get into the finance share, I'd be a lot less relaxed about it.

## The enrolment guide

The second one was a guide I was updating for setting up phones. Screenshots, steps, and a QR code that enrols the device into the organisation.

It's a good guide. It works. Which is exactly the problem, because anyone who gets hold of a copy can enrol a device. It had been written as a how-to and was being passed around like any other Word doc, but really it's closer to a key.

Nobody had done that on purpose. When you write a guide, you're thinking about making it easy to follow. You're not usually thinking about who else might end up following it.

While I was in there I also noticed the token behind the QR code had a creation date that made me think it might have already expired. So the guide was potentially too powerful and potentially broken at the same time, and we wouldn't have found out either way until someone tried to use it.

## What they had in common

Neither of these was a big deal on its own. But they're the same kind of problem. Something gets set up, it seems to work, and from then on everyone just assumes it's still fine. Nobody's done anything wrong. It's just that nobody's checked.

I've noticed I ask myself a few things now that I didn't used to. What do we think this does? Is it actually doing that? And if someone asked, could we prove it?

The distribution list is a good example. If you'd asked anyone, they'd have said "leavers come off automatically." Totally confident. But to actually know, someone had to export it and read through it. Until then it was just something we believed.

## "It's fine, it's automated"

I've said this. Probably more than once. A lot of support runs on that sort of confidence. "That group's been right for years." "Only IT has that doc." "It's on a schedule, it'll be fine."

Most of the time it is fine. The problem is you don't know which times it isn't, and you won't find out until something goes wrong.

There's a difference between saying something is happening and being able to show it. "We check access regularly" is one thing. A dated list showing what was checked, what got removed and who did it is something else. I didn't really think about that distinction until fairly recently, and now I see it everywhere.

A lot of that has come from spending time with ISO 27001. It's not that the standard told me anything I didn't already half know. It's more that it keeps coming back to the same question: how do you know? Once you start asking that about the stuff you look after every day, it's hard to stop.

## What I do now

Nothing fancy. Mostly it's just little habits.

If something's automated, I look at what it actually produces rather than just reading how it's configured. The config can look perfect and the output still be wrong.

If a document or link would let someone get in, enrol something, reset something or approve something, I treat it differently. It's not really documentation at that point. I think about who actually needs it and where it lives, not just whether the steps are right.

I check dates. Tokens, certificates, secrets, they all expire, usually at the worst possible moment. A guide that was right in March might not be now.

And I write down what I found and what I changed. Partly for the next person, partly because if I can't show I checked it, I've only really said I did.

## Anyway

Both fixes ended up being small. Tweak a filter, clear a few fields, lock a document down, sort out a new token. The hard bit was noticing in the first place, and that only happened because I exported a list and actually read it, instead of trusting it.

That's probably the main thing I'd take from it. Automation's brilliant, but it's easy for it to become the reason nobody looks anymore.

If there's something in your environment that everyone's sure is fine, it might be worth a quick look. It probably is fine. But it's nice to actually know.
