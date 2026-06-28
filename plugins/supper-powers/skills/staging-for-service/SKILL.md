---
name: staging-for-service
description: Use when cooking for a specific event (dinner party, holiday, anything with a fixed serve time) - separate the build-ahead from the day-of finish the way releases separate from deployments. Do the slow, stable, reversible work the night before; leave only fast, fresh, irreversible finishing for service. Cut the release early; deploy calm on the day.
---

# Staging for Service

**Activates when you're cooking toward a fixed serve time** — a dinner party, a
holiday meal, anything where guests arrive at a known hour and the food must land
*then*. The failure mode here isn't bad food; it's a frantic cook doing
everything at once while guests watch, plating late and stressed because all the
work was scheduled for the worst possible moment.

The fix is the discipline that saved software from release-night heroics:
**separate the release from the deployment.** Building the artifact and shipping
it are two different acts that do not have to happen at the same time — and
shouldn't.

## The Iron Law

**Do the slow, stable work ahead. Leave only the fast, fresh, irreversible work
for service.** Anything that holds well is done before the day. The serve-time
window is reserved for what *cannot* be done early.

## Release the night before; deploy on the day

**Cutting the release** is all the work that produces a stable, finished
artifact that keeps: braises, stocks, sauces, doughs, marinades, components that
are as good (or better) a day later. You do this calm, the night before, with no
audience and full attention. The braise that needs to rest overnight isn't a
chore you're stuck with — it's a release you cut early, sitting tested and ready
in the fridge.

**Deploying** is the day-of finish: reheat the release, sear the thing that must
be hot off the pan, dress the salad that wilts, plate. Short, fast, fresh steps
only. A good deploy is boring — you're shipping an artifact you already built and
verified, not building under pressure while the clock runs.

The whole point of the split: when guests arrive, you are *deploying*, not
*building*. The hard, slow, failure-prone work already passed its tests
yesterday. Today is assembly and heat.

## What releases early vs. what deploys fresh

- **Release ahead (holds / improves):** braises, stews, stocks, confit, most
  sauces, doughs and batters that rest, marinades, roasted veg, components from
  `supper-powers:mise-en-container`, anything that benefits from time.
- **Deploy fresh (degrades if early):** anything seared or fried for crispness,
  dressed greens, herbs as garnish, soft-boiled/runny eggs, whipped things,
  bread you want warm, the final salt-and-acid adjustment. These wilt, sog,
  deflate, or dull — do them in the deploy window, not before.

When unsure which bucket something is in, ask: does this hold for a day without
loss? Holds → release it early. Degrades → deploy it fresh.

## Stage the deploy so it runs itself

Before service, lay out the deploy like a runbook: what comes out of the fridge
when, what oven temp, what order, what's the last thing to touch the plate. A
deploy you've sequenced in advance runs calm; one you're improvising mid-party
is the release-night heroics you were trying to avoid. The goal is a serve-time
window with no decisions left in it — just execute the steps you already wrote.

## Don't deploy untested

The release you cut ahead still has to pass `supper-powers:test-driven-dinner` —
taste it when you make it, not just at service. A braise you never tasted is an
unverified artifact; discovering at the table that it's under-seasoned is a
failed deploy with guests as the monitoring system. Test the release the night
before, while there's still time to fix it. (Seasoning often needs a final touch
on the day anyway — flavors mute in the cold — so re-taste at deploy, but the
big problems should already be caught.)

## Anti-Rationalization

- "I'd rather make it all fresh on the day." → Fresh is for the things that
  *need* fresh. For everything that holds, "fresh on the day" just means doing
  stable work in your most unstable hour, in front of an audience. That's not
  dedication; it's bad scheduling.
- "Prepping ahead means serving leftovers." → A released-ahead braise isn't a
  leftover; it's a finished artifact resting before deploy. Many dishes are
  *better* the next day. The night-before release is a feature, not a compromise.
- "I'll just start everything earlier on the day." → Compressing the same
  all-at-once cook into the morning doesn't separate release from deploy; it just
  moves the pile-up. The point is to move the *stable* work out of the serve
  window entirely, not to start the chaos sooner.
- "I don't have time to prep the night before." → You don't have time *not* to —
  the work doesn't shrink, it just lands during service if you defer it. A calm
  hour last night buys a calm hour tonight. Pay it early.

**About to schedule slow, hold-well work inside the serve window? Stop. Cut it
as a release the night before, and leave the window for fresh-only finishing.**
Violating the letter of this rule is violating the spirit of it.

## Boundary

This skill schedules a *specific event* by splitting build-ahead from day-of
finish. It differs from `supper-powers:mise-en-container`, which builds reusable
bases for *many* future meals; here you're staging *one* meal toward *one* serve
time (though a container you made earlier is a release you cut very early). It
does not plan the menu (`supper-powers:brainstorming-supper`), cook the
components (`supper-powers:test-driven-dinner`), or gate the final plate
(`supper-powers:requesting-table-review`). Stay in scope: release the stable work
early, deploy the fresh work on the day.

## User instructions always win

If your human partner wants to cook everything fresh on the day because that's
the joy of it for them — let them. The user is in control. Name the one or two
items that will suffer most from no make-ahead ("the braise really wants
overnight"), then cook it their way. Their kitchen, their call.
