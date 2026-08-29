---
title: "Incident vs Problem Management: The Distinction That Actually Matters"
date: 2026-08-20
draft: false
summary: "The difference between making something go away and stopping it coming back."
tags: ["ITIL", "Service Management", "Process"]
categories: ["Blog"]
showTableOfContents: false
---

Incident management and problem management get taught side by side, usually in a diagram that doesn't really explain why they're different.

Here's how I actually think about it.

An incident is something is broken right now, and I need to make it work again.

A problem is something is broken repeatedly, and I need to work out why.

That's most of it. But the useful part isn't the definition. It's what each one is actually optimising for.

Incident management is optimising for speed. Restore the service. If restarting a print spooler gets someone printing again, you restart it and move on. You're not trying to work out why it crashed. You're trying to get them printing.

Problem management is optimising for understanding. This spooler has crashed four times this month, across three users, always around 9am. What's actually going on there?

That question doesn't get answered by restarting a service quickly. It gets answered by someone stepping back from the individual incidents and looking at the pattern.

I wrote about a real example of this a while back. A repeat Outlook ticket, closed the same way twice, while the actual cause sat untouched in a Conditional Access policy.

Incident management did its job there. Nobody was doing problem management on top of it. So it kept coming back.

The other thing worth knowing is that problem management doesn't need a fix straight away. A known error is a problem where the cause is understood, but there isn't a permanent fix yet. Maybe it needs a change request, or a vendor patch, or budget.

In that case the value isn't the fix. It's the documentation. Someone can apply the known workaround and log the incident against the existing problem, instead of starting from scratch every time.

If you're early into this stuff, here's the practical version. Incident management asks how do I make this go away. Problem management asks how do I stop this coming back.

Most support desks are set up to do the first one well.

Fewer are set up to do the second one at all. That's usually where the actual value sits.
