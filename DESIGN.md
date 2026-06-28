# supper-powers — Design Notes

The rationale behind the skills: why each one exists, what engineering concept
it encodes, what failure it prevents, and the decisions (and rejections) that
shaped the set. The `README.md` is the entry point; this is the *why* behind it.

## What this is

`supper-powers` is an agentic skills framework dressed as a home-cookery
methodology. It's a deliberate parody-with-teeth of
[obra/superpowers](https://github.com/obra/superpowers) — the structure is real
(brainstorm → build → review, TDD, debt triage, code review gates), the costume
is a kitchen. Each skill maps a genuine software-engineering discipline onto a
cooking task so cleanly that the file would teach the underlying concept even to
someone who only cares about dinner.

## Origin

It started as a riff: "what would a plugin called *supper-powers* do?" The bit
got serious because the mapping turned out to be unusually tight — the real
superpowers repo's skills (brainstorming, git-worktrees, writing-plans, TDD,
code-review, writing-skills) each have a near-exact culinary counterpart. Once
the parallel held, the goal became a set where **every skill earns its place the
way the original's do**: by stopping a specific failure mode, not by completing a
pun.

## Design philosophy — the rules that govern the set

These are the constraints every skill is held to. They're the reason the set
stays tight instead of sprawling into a pun catalogue.

1. **Each skill must stop a distinct failure mode.** If a candidate only
   *describes* a thing (variation tracking, symmetry) rather than preventing a
   specific way dinner goes wrong, it's ornamentation and doesn't ship. This is
   the test that killed several proposed skills (see *Rejected ideas*).

2. **Titles reinforce the concept; they never fight it.** A good name puns on
   the *idea*, not just the spelling. `bake-or-bakery` *is* the build-vs-buy
   choice; `paying-down-the-pantry` *is* debt. A name that undercuts its own
   content is worse than a plain one. (This is why `soiled-principles` was
   rejected — "soiled" means dirty, fighting a skill about clean structure.)

3. **Straight title, clever content.** The comedy and the rigor live in the
   body — the translated principle, the named anti-rationalizations — not in a
   groan-worthy title. Same trick the real superpowers uses.

4. **Evidence over claims.** The spine of the whole set. "This should be
   seasoned" is not seasoned. The spoon is evidence. Verify before you declare
   done. Every skill bottoms out here.

5. **Don't build the framework no app uses.** The set refuses speculative
   generality *in its own design*. A skill added for structural symmetry (all
   five SOLID letters!) is exactly the anti-pattern the skills warn cooks
   against. When an idea was only two-thirds of a skill, it got folded into an
   existing one instead of padded into a standalone.

6. **User instructions always win.** Skills override default behavior, but the
   human is in control. Every skill ends here: name a concern once, plainly,
   then defer. Their kitchen, their call.

## Skill anatomy — the shared structure

Every full skill carries the same DNA (lifted from the real superpowers format):

- **Frontmatter** — `name` + `description`, the description written so the agent
  can decide relevance from it alone.
- **Activation line** — when this fires, in bold.
- **The Iron Law** — the single non-negotiable rule, stated plainly.
- **Body sections** — the technique, translated.
- **Anti-Rationalization** — named loopholes the agent will reach for under
  pressure, each slammed shut, with the clause: *violating the letter of this
  rule is violating the spirit of it.* (Agents are smart and rationalize; the
  skill has to pre-empt the specific excuses.)
- **Boundary** — what this skill does *not* do, with pointers to the sibling
  skill that owns the adjacent job. Keeps the set from overlapping.
- **User instructions always win** — the deferral clause.

## The engineering → kitchen mapping

| Skill | Engineering concept | Failure it prevents |
|---|---|---|
| `provisioning-your-kitchen` | Dev environment / toolchain setup | Many half-known tools; gadgets where skill would do |
| `brainstorming-supper` | Spec before build; refine reqs, get sign-off | The eager cook who sears before knowing what/for whom |
| `mise-en-container` | Reusable primitives / building a library; batch as a base | Re-cooking from raw every time (no leverage) |
| `staging-for-service` | Separating releases from deployments | Building under pressure at service time |
| `paying-down-the-pantry` | Technical-debt audit & triage | Accumulated mess that taxes every future cook |
| `bake-or-bakery` | Build vs. buy; dependency management | Building the commodity, buying the thing that mattered |
| `test-driven-dinner` | TDD: RED → GREEN → REFACTOR | Plating without tasting; "should be fine" to the table |
| `seasoning-to-taste` | The GREEN technique: small, measured, reversible-by-recovery adjustment toward a target | Timid under-seasoning; un-recoverable overshoot |
| `requesting-table-review` | Code review as a severity-ranked gate | One nervous reveal at the end; shipping the raw center |

## Per-skill rationale

**provisioning-your-kitchen** — Your durable infrastructure. Few good tools over
many cheap ones; resist the unitasker when a skill or existing tool covers it;
"skill is the tool that fits in no drawer." The tool-side cousin of
`bake-or-bakery` (same instinct, applied to equipment instead of ingredients).
*(Originally `setting-up-your-station`; renamed to surface the provisioning /
workstation mapping.)*

**brainstorming-supper** — Always first. No prep starts until there's an agreed
menu, because heat is a commitment and the talking phase is the cheap phase.
Ask who's eating, the time budget, what must get used, the mood; offer genuinely
different directions rather than committing to the first idea; present in chunks
for sign-off. Output is a spec (a recipe).

**mise-en-container** — The asset-building skill. Batch-cook reusable, labeled
bases at the right level of abstraction (raw onion → diced → caramelized →
sofrito) so future meals assemble by composition. The iron law is **prep for
composition, not just preservation** — a container is a building block, not a
place to put leftovers. Failure modes on both ends: no leverage (cook fresh
every time) and speculative generality (prep primitives you never compose). The
positive inverse of `paying-down-the-pantry`: same shelf, opposite sign.

**staging-for-service** — Cooking toward a fixed serve time. Cut the *release*
ahead (the slow, stable, hold-well work — braises, stocks, doughs — built calm
with no audience and set aside) and *deploy* on the day (only the fast, fresh,
irreversible finishing — reheat, sear, dress, plate). "When guests arrive, you
are deploying, not building." Distinct from `mise-en-container`: that's reusable
bases for many meals; this is staging one specific event.

**paying-down-the-pantry** — The tech-debt skill. Audit and triage the debt past
cooks left — the unscrubbed pan, the impulse ingredient, the freezer
archaeology, the smashed chip bag — price each by interest × payoff, pay down the
cheap high-interest items, or route a "use this up" brief into
`brainstorming-supper`. Framed explicitly as *the REFACTOR step skipped one too
many times*, so it and `test-driven-dinner` point at each other.

**bake-or-bakery** — Build vs. buy, with real teeth on both sides: over-building
(four hours of stock for a Tuesday soup) and over-buying (paying convenience tax
on the one component that mattered). Build what's the point, buy the commodity
nobody can taste. Carries several folded-in ideas — see below.

**test-driven-dinner** — The cooking loop, strict. RED (taste, it fails) → GREEN
(smallest correction, re-taste to confirm) → REFACTOR (reset the station so the
next cycle is faster). Iron law: **taste before you plate, every course.** Also
carries the dependency-injection principle (below).

**seasoning-to-taste** — The technique beneath GREEN, given its own file because
the *recovery* knowledge (rescue overshoot with volume, acid, or fat) and
*threshold* knowledge (a dish is oversalted only when you taste salt itself;
under-salting is the more common, fear-driven error) are real domain content
that would bloat TDD if inlined. Deliberately **not** given a forced CS pun — a
contrived label would be the first dishonest mapping in the set.

**requesting-table-review** — The quality gate. A second eater checks the dish
against the agreed menu and ranks issues: critical (raw chicken) blocks service,
major gets fixed, minor gets logged and served. Continuous review between
courses, not one reveal at the end. Minor findings loop back to the pantry's
next-cook list.

## Folded-in principles

Rather than spawn thin standalone skills, several concepts live *inside* an
existing skill as a named principle:

- **Dependency injection → `test-driven-dinner`.** Dependencies are injected by
  prep, not foraged mid-cook. A step that stops to acquire its own garlic
  hard-coded its acquisition and fails the way hard-coded dependencies always
  do — at the worst moment, with no substitute ready.
- **Open/Closed → `mise-en-container`.** Extend your *portion*, don't modify the
  *base*: take a scoop and finish that scoop, never re-season the whole tub. The
  moment you spike the batch for one meal, the reusable primitive collapses into
  a single-purpose ingredient.
- **Liskov → `bake-or-bakery`.** Commodities are substitutable; the dish
  shouldn't care which one. If it only depends on "a neutral oil," it mustn't
  break when you swap one for another — and if it does break, you were lying to
  yourself about that being a commodity (toasted sesame oil is not a commodity).

## Ideas we deliberately rejected (and why)

- **`forking-a-recipe`** — Cut. It *describes* variation tracking but prevents no
  failure: nobody overwrites Grandma's recipe by adding peas, so there's no "if
  you skip this you get burned" core. The good half (offer alternatives) already
  lives in `brainstorming-supper`.
- **`soiled-principles`** (SOLID pun) — Cut. The pun is on the *spelling*, not
  the *idea*, and "soiled" (dirty) actively fights a skill about clean
  structure. Violates "titles reinforce the concept."
- **A standalone SOLID / storage-principles skill** — Cut. Only two of the five
  letters weren't already covered (Open/Closed, Liskov); the rest would be
  padding. Folded those two into existing skills instead — writing the full five
  would have been the exact speculative-generality move the set warns against.
- **`don't-cross-the-forks`** (cross-contamination / hygiene) — Considered as a
  defensible safety skill with a real iron law (the raw-chicken fork never
  touches the salad). Parked, not built.

## Key design decisions

- **REFACTOR is cleanup, not re-tasting.** An early draft put "taste again" in
  REFACTOR — but tasting-and-correcting changes behavior, so it belongs in
  GREEN. REFACTOR is true refactoring: same dish, better kitchen. Its test: *the
  next course starts faster and cleaner than this one did.* "If the flavor moves,
  you're back in GREEN" keeps it honest.
- **Time is a first-class tradeoff in `bake-or-bakery`.** Buy trades money and a
  little control to buy back *time* — the resource cooks most undervalue,
  because the bill comes due all at once on the night you're already behind. A
  cook with three hours and one with thirty minutes should make different calls
  on the same menu and both be right. Name the trade out loud.
- **Know the framework, not just the recipe (`bake-or-bakery`, Liskov).**
  Substitutability is *resilience*, and it lives in the cook. The recipe-only
  cook is brittle — a dependency goes bad or missing mid-cook (it will, at the
  worst moment) and they're stuck. The framework cook knows *why* the oil is
  there and swaps without breaking stride.
- **Dependencies are a security surface — but worth it on purpose
  (`bake-or-bakery`).** A long, unpronounceable ingredient list is a larger
  attack surface (the hidden allergen, the reaction you didn't choose). Minimal
  footprint is the default — *not* a religion. American cheese melts like nothing
  artisanal; Oreos are perfect. **Take the processed dependency deliberately for
  a real payoff; never by default because it's easy.** Same ingredient, opposite
  decision — what separates them is whether you picked it on purpose.
- **`staging-for-service`: build and set aside, don't necessarily freeze.** The
  release is *cut and sealed* (immutable, done), not literally frozen — most prep
  rests in the fridge or marinates; "freeze the artifact" wrongly implies the
  freezer.
- **Labeling lives in `mise-en-container`**, framed as the function signature:
  an unlabeled container is unusable because you don't know its interface.

## Naming conventions

Skill directories and `name` fields are kebab-case, gerund- or
choice-phrased to match the set's voice (`brainstorming-supper`,
`bake-or-bakery`, `paying-down-the-pantry`). The plugin is named `supper-powers`
so cross-references resolve as `supper-powers:<skill>`. Names were chosen
collaboratively — options floated, weighed against the philosophy above, one
picked — which is why the rationale for each rename is recorded here rather than
lost to chat history.

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
