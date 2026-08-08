AI WORKFLOW NOTES

What I delegated:
- Liquid/schema scaffolding for the Hero section, CSS extraction and
  scoping from the prototype file, the rotator JS, and step-by-step
  guidance through Shopify Partner/CLI/admin setup.

Where it failed or needed correction:
- The AI's first draft of the metaobject schema was too thin — it
  modeled Review and Combo with only basic fields and missed
  compare-at pricing, per-product captions inside a combo, and didn't
  account for the Bundles section needing its own metaobject at all.
  Caught this by checking the schema against every visual data point
  in the design (strike-through prices, per-item captions, badges)
  before creating anything in admin — fixing it after entering real
  data would have meant redoing entries, not just definitions.
- Early in product seeding, AI-suggested product entries pulled in
  real branded product names instead of a fictional Purelane catalog
  — caught on review, deleted, and reseeded manually with explicit
  copy-paste text instead of open-ended suggestions.

What I'd systematize for 20 more of these:
- Always validate a proposed metaobject/data schema against the full
  design (every price format, caption, badge) before touching admin —
  schema mistakes are cheap to fix before data exists, expensive after.
- Keep a running library of exact copy-paste Shopify CLI commands
  (auth, theme dev, remote setup) since the interactive flows are
  slow to redo from memory each time.
- Ask for explicit, literal text/values rather than open-ended
  "generate realistic products" prompts, to avoid real brand names
  or data leaking into a fictional store.