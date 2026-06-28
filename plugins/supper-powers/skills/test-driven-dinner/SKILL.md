---
name: test-driven-dinner
description: Use when cooking any dish that will be eaten by a human - enforces taste-first RED-GREEN-REFACTOR so seasoning is verified by evidence, never by assumption. Activates the moment heat is applied to food.
---

# Test-Driven Dinner

**REQUIRED BACKGROUND:** You MUST understand `supper-powers:using-mise-en-place`
before using this skill. You cannot run a clean test cycle on a dirty counter
with unmeasured ingredients. Prep is the baseline. No baseline, no testing.

## The Iron Law

**Taste before you plate. Every course. No exceptions.**

A dish is not "seasoned" because the recipe said to add salt. It is seasoned
when you have *tasted it* and confirmed it. "This should be seasoned" is a
claim. A claim is not evidence. The spoon is evidence.

## The Cycle: RED → GREEN → REFACTOR

### RED — Taste it and let it fail
Take a clean spoon. Taste. It is bland, or flat, or sharp, or thin. Good.
That is the failing test, and you expected it. If your very first taste is
already perfect, you are either lying to yourself or you forgot to taste.
Taste again.

### GREEN — Add the *minimum* to pass
Add the smallest correction that could make this taste pass: a pinch of salt,
a squeeze of acid, a single grind of pepper. **Not the whole spice cabinet.**
Over-correction is not a green test, it is a new and worse failure that you
now cannot undo. You can always add more. You cannot remove salt from soup.
Then taste again with a clean spoon (never double-dip — that is contaminating
your test environment). Still failing? Add the next minimal correction and
re-taste. Loop until the bite passes. When it passes, stop — do not keep
"improving" a green dish. That is how you oversalt.

### REFACTOR — Clean up so the next cycle is faster
The dish now tastes right. **Refactoring must not change how it tastes** — if
the flavor moves, you are back in GREEN, not refactoring. This step changes
nothing about the finished course; it pays down the cost of the *next* one.
Wash the spoon and the cutting board so the next RED has a clean spoon waiting.
Wipe the station so you can see what you're doing. Consolidate the dirty pans
into one soak so the sink isn't a bottleneck mid-service. Put the open salt,
acid, and fat back in arm's reach in the same spots, so the next GREEN is a
reach-and-pinch instead of a hunt. Clear the scraps so nothing gets knocked
into the next pan.

The test of a good refactor: **the next course starts faster and cleaner than
this one did.** A passing dish on a wrecked station is technical debt — every
later course inherits the mess and cooks slower for it. You are not tidying for
its own sake; you are resetting the kitchen to its fastest state so the cycle
spins quicker each time instead of grinding to a halt by course four.

## Dependencies are injected, not foraged

A cook step does not stop mid-sear to go mince garlic. The garlic — minced, in
its little bowl — was handed to the step by prep before the heat went on. The
step *receives* what it needs; it does not reach out and acquire it. This is
dependency injection, and it is what makes the RED-GREEN loop fast: when every
dependency is already in arm's reach, a correction is a reach-and-pinch, not a
hunt across the kitchen mid-test.

A step that forages its own dependencies — chopping an onion while the pan
scorches, discovering you're out of stock with the rice already cooking — is a
step that hard-coded its acquisition into its execution, and it fails the way
hard-coded dependencies always do: at the worst possible moment, with no
substitute ready. Inject up front (this is what `supper-powers:using-mise-en-place`
is *for*), and each test cycle stays tight because nothing in it blocks on
going to get something.

## Anti-Rationalization

You are a smart cook and you will be tempted, under time pressure, to skip the
taste. The guests are waiting. The pan is hot. You *know* you added the right
amount. Every one of these is the same violation. Catch yourself:

- "I followed the recipe exactly, so it must be right." → The recipe doesn't
  know your salt is coarser, your tomatoes more acidic, your stock already
  salted. Taste it.
- "I'll just taste it once at the end." → A dish has many commits. You do not
  review only the final one. Under-seasoned at the base cannot be fixed at the
  garnish.
- "There's no time to taste." → There is no time to re-cook a failed course
  either, and that is what you are risking. Tasting takes four seconds.
- "It smells right." → Smell is a linter. It catches some classes of error.
  It does not run the tests.

**Plated without tasting? Scrape it back into the pan. Start the course over.**
This applies to NEW courses AND to reheated leftovers. No exceptions. Violating
the letter of this rule is violating the spirit of it.

## What "the test" actually is

The test is the bite. The assertion is "a hungry, honest person would want the
next bite." If that assertion fails, the course is RED, no matter how good the
plating looks. Pretty is not passing.

## Boundary

This skill governs *seasoning, doneness, and leaving a clean station* — the
taste you verify by the spoon and the cleanup you verify by looking at the
counter. It does not govern whether the dish was the right idea in the first place
(that's `supper-powers:brainstorming-supper`) or whether a second eater signs
off before service (that's `supper-powers:requesting-table-review`). Stay in
scope: taste, correct, re-taste.

## User instructions always win

If your human partner explicitly says "do not make me wait, plate it now" —
plate it now. The user is in control. Note your concern once ("serving without
a final taste, against my better judgment"), then comply. Their kitchen,
their call.
