---
title: "Change Management Isn't Bureaucracy"
date: 2026-07-31
draft: false
summary: "It's just asking what happens if this goes wrong, before it does."
tags: ["ITIL", "Change Management", "Process"]
categories: ["Blog"]
showTableOfContents: false
---

Change management is one of those terms that gets an eye-roll before people even understand what it does.

It sounds like a form-filling exercise designed to slow you down.

Having sat on both sides of it, requesting changes and cleaning up after an unrequested one, I think that reputation is mostly earned by bad implementations, not the idea itself.

Strip away the paperwork and change management is answering one question before something gets touched. What happens if this goes wrong, and who needs to know before it does.

That's it.

A change that's been thought through has a rollback plan, a rough idea of blast radius, and at least one other person who knows it's happening.

A change that hasn't been thought through has none of those things. And when it goes wrong, which it eventually will, nobody knows what changed, when, or how to undo it.

I've seen both versions.

A firmware update pushed to a switch stack outside of a change window, no rollback plan, that took a client's site offline for most of a morning. Nobody had confirmed compatibility with the existing config first.

Compare that to the same type of update done properly. Tested in a lab environment first. Scheduled out of hours. Rollback steps written down in advance. A heads up sent to the client beforehand.

Same type of change. Wildly different outcome. Because one had a five minute conversation before it happened, and the other didn't.

The bureaucracy complaint is fair when the process is disconnected from the actual risk. Restarting a service on a test VM doesn't need the same approval chain as changing firewall rules on a production gateway.

Treating them the same is what makes people start working around the process instead of through it.

Good change management scales the process to the size of the risk.

Before any change, I ask myself the same handful of things. What's the rollback if this doesn't work. Who else is affected, and do they know. Is there a safer window for this. Have I actually tested it somewhere that isn't production.

None of that is bureaucracy.

It's just the difference between an outage you planned for and one that happened to you.
