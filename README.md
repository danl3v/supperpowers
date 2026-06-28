# supper-powers

**An agentic skills framework & home-cookery methodology that works.**

You have supper-powers. They give your cooking structure: defined, repeatable
ways of approaching a meal so you stop improvising the same decisions from
scratch every night and burning the garlic while you think.

It starts the moment someone's hungry. supper-powers doesn't jump to the stove.
It steps back and asks what you're *really* trying to eat, teases a menu out of
the conversation, builds from reusable bases, cooks each course test-first, and
gates every plate at review before it reaches the table.

---

## Install

This repo is a Claude Code plugin marketplace. From inside Claude Code:

```
/plugin marketplace add danl3v/supperpowers
/plugin install supper-powers@supperpowers
```

Then the nine skills activate automatically, and you can invoke any of them
explicitly with `/supper-powers:<skill-name>` (e.g.
`/supper-powers:brainstorming-supper`).

---

## RIGHT NOW, go read the skills

When a relevant skill applies — even a 1% chance it applies — invoke it before
you act. If it turns out wrong for the situation, drop it. But check first.
Announce which skill you're using and why ("Using test-driven-dinner to season
this sauce"), then follow it exactly.

## The nine skills

**provisioning-your-kitchen** — Activates when provisioning or organizing the
kitchen — the durable toolchain, not the meal. Few good tools over many cheap
ones; resist single-purpose gadgets a skill or existing tool already handles.
Your infrastructure — keep it lean, sharp, and in reach. (The tool-side cousin
of bake-or-bakery.)

**brainstorming-supper** — Activates before any burner is lit. Refines a vague
craving into an agreed menu through questions, explores alternatives, gets
sign-off. No prep starts until there's a yes. *This is always the first skill.*

**mise-en-container** — Activates when you have prep time to invest. Batch-cooks
reusable, labeled bases at the right level of abstraction (caramelized onions,
garlic confit, cooked grains) so future meals assemble by composition in
minutes. Builds assets you draw down all week.

**staging-for-service** — Activates when cooking toward a fixed serve time
(dinner party, holiday). Separates the build-ahead from the day-of finish like
releases from deployments: cut the slow, stable, hold-well work as a release the
night before; deploy only the fast, fresh, irreversible finishing on the day, so
you're assembling at service, not building under pressure.

**paying-down-the-pantry** — Activates when planning a cook. Audits and triages
the debt past cooks left — the unscrubbed pan, the impulse ingredient, the
freezer archaeology, the smashed chip bag — and pays down the cheap,
high-interest items first or routes a "use this up" brief into brainstorming.
The negative inverse of mise-en-container: same shelf, opposite sign.

**bake-or-bakery** — Activates when a component could be built or bought. Decides
by whether it's the point of the dish or a commodity nobody can taste — build
what matters, buy the rest — and when buying, prefers the shortest, most legible
ingredient list to keep unknown dependencies (and their hidden risks) out of the
dish. But takes on a processed dependency gladly when it's genuinely the right
tool: use it because it's right, not because it's easy. It's all tradeoffs —
buying trades money and a little control to buy back time, the resource cooks
most undervalue. And know the framework, not just the recipe: understanding each
ingredient's *role* is what lets you swap a bad or missing dependency in real
time instead of being stuck.

**test-driven-dinner** — Activates the moment heat hits food. RED (taste, it
fails) → GREEN (smallest correction, re-taste) → REFACTOR (reset the station so
the next cycle is faster). Iron law: taste before you plate, every course. Also
carries the rule that dependencies are injected by prep, not foraged mid-cook.

**seasoning-to-taste** — The technique beneath GREEN. Season up toward the edge
in small steps (a dish is oversalted only when you taste salt itself; under-
salting is the more common error), and rescue an overshoot with volume, acid, or
fat instead of starting over.

**requesting-table-review** — Activates between courses, before a plate goes out.
A second eater checks the dish against the agreed menu and ranks issues by
severity: critical (raw chicken) blocks service, major gets fixed, minor gets
logged and served.

---

## The loop

```
provisioning-your-kitchen  → (durable) lean, sharp station to cook on
brainstorming-supper       → agree the menu
  ├─ mise-en-container      → (ahead of time) stock composable bases
  ├─ staging-for-service    → (for an event) release stable work ahead, deploy fresh
  ├─ paying-down-the-pantry → clear/triage existing kitchen debt
  └─ bake-or-bakery         → per component: build the point, buy the commodity
test-driven-dinner          → cook each course RED → GREEN → REFACTOR
  └─ seasoning-to-taste     → the salting/balancing technique inside GREEN
requesting-table-review     → gate the pass; critical blocks, minor logs
                              ↑ minor findings & write-offs loop back to
                                paying-down-the-pantry's next-cook list
```

## The philosophy baked in

- **Evidence over claims.** "This should be seasoned" is not seasoned. The spoon
  is evidence. Verify before you declare done.
- **Mise en place is not optional.** The cook who preps before the heat finishes
  calm. The one who chops as they go burns the garlic.
- **Build what's the point, buy the commodity.** Pride is not a flavor. Labor
  goes where the eater can taste it.
- **Prep for composition, not just preservation.** A container is a reusable
  building block, not a place to put leftovers.
- **Few good tools, skill over gadgets.** Capability comes from a few tools
  you've mastered, not many you half-know. The best tool fits in no drawer.
- **Season to the edge, not past it.** A dish is oversalted only when you taste
  salt itself — and under-salting is the more common fear-driven error. Overshot?
  Dilute, brighten, or round; don't start over.
- **Use it because it's right, not because it's easy.** Take on a processed
  dependency deliberately for a real payoff (American cheese melts; Oreos are
  perfect) — never by default out of laziness.
- **It's all tradeoffs; know the framework, not just the recipe.** Buying trades
  money and control to buy back time. And understanding each ingredient's role —
  not just the recipe's steps — is what lets you swap a failed dependency in real
  time instead of being stuck.
- **Separate the release from the deploy.** Cut the slow, stable, hold-well work
  ahead of time; leave only fast, fresh finishing for the serve window. At
  service you should be deploying a tested artifact, not building under pressure.
- **A little payment every cook.** Reset the station each course, use the aging
  thing, clear the clutter — or you borrow speed from future-you at a brutal
  rate and end up with a fridge full of food and no counter to cook on.
- **The best supper is the one that actually gets eaten.** An ambitious meal at
  11pm that nobody's awake for has negative value. Ship while there's appetite.

## User instructions always win

These skills override your default behavior where they conflict — but the user
is always in control. If your human partner says "skip the review, just plate
it" or "don't batch-prep, I only want tonight's dinner," follow them. Name any
real concern once, plainly, then defer. Their kitchen, their call.

---

## Design notes

The *why* behind every skill — the engineering→kitchen mapping, the failure each
one prevents, the principles folded in, and the ideas deliberately rejected —
lives in [`DESIGN.md`](DESIGN.md).
