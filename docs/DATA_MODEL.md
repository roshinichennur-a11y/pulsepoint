# Data model

See `frontend/types/huddle.ts` for runtime schemas and `docs/API.md` for the proposed backend contract.

Huddle states: `ready` (question and context prepared), `pending` (expert requested), `complete` (response and brief available). Original question text is retained. Evidence, expert metadata, response, and brief are separate fields. Source provenance and demo flags must be preserved across each transition.

The demo only recognizes breast-cancer questions using a simple keyword rule. This is not semantic AI extraction. Topic classification is a scripted demo, with a single generic treatment-sequencing path. Unknown inputs produce no sources and no expert. The 94% expert match is an illustrative fixture, not a computed relevance score.

Demo records are tab-local in session storage, capped at 30, validated on load, and resettable. Live huddles remain in memory only. The Question Graph is a separate fixed aggregate illustration and does not ingest submitted questions or claim to anonymize them.
