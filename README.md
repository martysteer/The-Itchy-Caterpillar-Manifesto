# The Itchy Caterpillar Manifesto

A 2025 experiment in **progressive-complexity prompting** — using deliberately silly
subject matter (revolutionary manifestos for itchy caterpillars) as a safe sandbox for
exploring how to scaffold an LLM from a one-shot request up to a reusable, self-guiding
generation framework.

This was done with an earlier version of Claude, **before skills or reusable agent
instructions were a thing**. The final artifact —
[`rubric-document-generation/manifesto-generation-guide.md`](rubric-document-generation/manifesto-generation-guide.md)
— is essentially a hand-rolled proto-skill: a distilled process document that a fresh
conversation could pick up and execute with zero prior context.

A fun detail: **each git commit message in this repo is the actual prompt** that produced
that commit's changes. `git log --reverse` replays the whole experiment.

## The experiment, phase by phase

The session (preserved verbatim in [`chat-history.md`](chat-history.md)) escalated
through ten moves. Each one adds exactly one new element of complexity — which is the
whole point.

| Phase | Prompting move | Cognitive load principle |
|---|---|---|
| 1. One-shot baseline | "Write a 5 point manifesto for itchy caterpillars" | Establish low **intrinsic load** baseline before adding anything |
| 2. Diverge on subjects | "Suggest 5 more animals" (with defense mechanisms) | Vary **one variable at a time** — subject only |
| 3. Add a modifier axis | "Add a radical adjective" → *Anarchist Porcupines*, *Insurgent Skunks*... | Introduce one new element; keep interactivity between elements low |
| 4. Iterate the modifier | Regenerate adjectives: radical → non-radical → **equitable technology** | Cheap iteration on the isolated variable until it fits |
| 5. Tighten constraints | "Only 2 manifesto points — only the most hilarious parallel principles" | Prune **extraneous load**: cut everything that isn't the signal |
| 6. Shift sampling | "Lower your temperature so we get really novel conceptual allegories" | Separate *generation* from *selection*; ask for candidates, not commitments |
| 7. Co-design the rubric | "Let's explore rubric options **before** implementing" → 5 rubrics proposed, #4 chosen | **Germane load**: effort spent building the schema, not just outputs |
| 8. Apply + extend rubric | Implement Conceptual Depth Progression; later add a 4th section from rubric #5 | Rubric as **worked example** — structure carries the load, content varies |
| 9. Distill the process | "Analyse this method and distil it into concise project instructions" | **Schema externalization** — the proto-skill. Knowledge moves from chat context into an artifact |
| 10. Test transfer | Fresh "hi" → guide takes over with Q&A → tardigrade and centipede manifestos | **Scaffolded transfer**: the artifact now guides the human, load is offloaded to the document |

The end state is the inversion worth noticing: in phase 1 the human supplies all the
structure; by phase 10 the *document* interviews the human ("what animal? what domain?
what themes?") and the human just answers multiple-choice questions. The scaffolding was
built collaboratively, then baked in, then faded.

## Why cognitive load theory?

Cognitive load theory (Sweller) splits mental effort into three kinds. All three map
directly onto prompting an LLM — where the "working memory" being managed is both yours
and the model's context:

- **Intrinsic load** — complexity inherent to the task itself. You can't remove it, but
  you can sequence it. Phases 1–4 never combine two new ideas in one prompt: first
  subjects, *then* adjectives, *then* the domain. Element interactivity stays low, so
  each turn's output is easy to evaluate and easy to steer.

- **Extraneous load** — effort wasted on things that don't serve the goal. Phase 5's
  "only the 2 most hilarious points" is extraneous-load surgery: less output, higher
  density, easier review. Bad prompts bury the model (and you) in irrelevant structure.

- **Germane load** — effort invested in building durable schemas. Phase 7 is the pivot
  of the whole experiment: instead of asking for more content, the prompt asks the model
  to propose *five competing rubrics* for structuring content, and a human picks one.
  That rubric (Conceptual Depth Progression: concrete → functional → metaphysical →
  dialectical) then generates every subsequent manifesto. One schema, unlimited
  instances.

Phase 9 is what makes this a precursor to skills: once the schema exists in
conversation, it gets **distilled into a standalone document** so the germane load never
has to be paid again. That's what a `SKILL.md` is — pre-paid schema construction.

## Principles distilled

1. **Start with the naive one-shot.** It's your baseline and it surfaces what the model
   does unprompted.
2. **Add one variable per turn.** Subject, then modifier, then domain, then constraints.
   Never two at once — you can't attribute the change.
3. **Iterate on the isolated variable cheaply.** Regenerating five adjectives costs
   nothing; regenerating five manifestos costs a lot.
4. **Constrain for density, not length.** "Only the funniest 2" beats "write 5" — forced
   selection is a quality filter.
5. **Co-design the rubric before applying it.** Ask for competing structural options,
   choose deliberately, *then* generate. Structure decided under low stakes beats
   structure improvised mid-generation.
6. **Distill the working process into an artifact.** If the conversation found a method,
   make the model write the method down.
7. **Test the artifact on novel input, cold.** The tardigrade and centipede runs prove
   the guide works without the original conversation in context. If it only works warm,
   it's not done.

## Try it yourself

Run the process on any creature. You need one LLM chat and the guide file.

1. **Point the model at the guide.** Give it
   [`rubric-document-generation/manifesto-generation-guide.md`](rubric-document-generation/manifesto-generation-guide.md)
   and say hello. It should start interviewing you.
2. **Pick a creature** with a distinctive defense mechanism or survival trait
   (pistol shrimp, horned lizard, slime mold — the weirder the mechanism, the better the
   metaphors).
3. **Pick a conceptual domain** to collide it with: technology, economics, philosophy,
   art. Combining two domains works (see the Network-Protocol Avant-Garde Centipedes).
4. **Name your themes** — the guide will thread them through all four sections (this
   repo foregrounded equitable technology and climate urgency).
5. **Demand the full progression:** concrete implementation → functional analysis →
   metaphysical extension → dialectical resolution. The last section must resolve a
   genuine contradiction, not restate one.

Or run the *meta*-experiment instead: take any task you do repeatedly with an LLM, walk
it through phases 1–9 above, and end up with your own proto-skill document.

## Repo map

```
caterpillar-manifesto.md          Phase 1: the one-shot original (5 points, no rubric)

anarchist-porcupines.md           Phase 3: the "radical adjective" generation
insurgent-skunks.md
subversive-hagfish.md
militant-eels.md
insurrectionist-beetles.md

open-source-porcupines.md         Phases 4–8: equitable-technology set, built with the
peer-to-peer-skunks.md            Conceptual Depth Progression rubric (4 sections each)
cloud-based-hagfish.md
renewable-eels.md
blockchain-beetles.md

tardigrade-manifesto.md           Phase 10: cold-start runs driven by the guide alone
centipede-manifesto.md

chat-history.md                   The full original session, verbatim
rubric-document-generation/
  manifesto-generation-guide.md   The distilled proto-skill
  Generating Structured Manifesto Documents.md   The distillation conversation
```

*Written in defensive hairs and sealed with urticating bristles.*
