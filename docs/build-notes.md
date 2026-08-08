BUILD NOTES

What's complete:
- Dev store on stock Dawn (15.5.0), clean git history from vanilla install
- 8 products seeded, including sold-out, no-image, and long-title edge cases
- Metaobject data model planned for reviews, combos, and bundle tiers
  (see docs/metaobjects.md) — Review definition created and populated
  with 3 real entries; combo_component and bundle_tier definitions
  designed but not yet created in admin
- Hero section (sections/hero.liquid) built to spec: schema-driven
  blocks for trust badges and product-stage slides, real Shopify
  product data throughout, no hardcoded content

What I flagged in the original file:
- The rotating hero product stage used hardcoded placeholder SVG art
  with no connection to real product data — rebuilt to pull real
  products via a product_list block setting instead.
- The full-page animated background used data-scene="1/2/3/4" numbers
  hardcoded across multiple sections. That breaks the moment a
  merchant reorders or removes a section in the theme editor, so I
  gave Hero its own self-contained background instead of depending on
  page-wide section order. Rebuilding the full cinematic multi-scene
  system is scoped as a follow-up, not required for the five sections.
- Combos, bundles, and reviews have no native Shopify field — solved
  via metaobjects rather than hardcoding or misusing product types.
- The CSS shipped ~10 base64-encoded placeholder SVGs in :root,
  loaded on every page regardless of use — a real performance cost
  that real product photography removes entirely.

What I changed in the code and why:
- CSS background-image + hardcoded aspect-ratio swapped for real
  <img> tags with width/height attributes sized from the actual
  product image, for correct CLS behavior with varying real photos.
- Section-scoped styles via {% style %} to avoid collision with
  Dawn's existing CSS.
- Rotator JS respects prefers-reduced-motion, pauses off-screen via
  IntersectionObserver, pauses on hover/focus, and cleans up on
  shopify:section:unload for theme-editor safety.
- Products with no image get a placeholder_svg_tag fallback instead
  of breaking layout.

What's not built yet, and why:
- Shop/product grid, combos, bundles, and reviews rail sections are
  not code-complete. Given the time available, I prioritized getting
  the data model right and one section (Hero) fully correct over
  producing five partially-broken sections. The metaobject schema for
  all four remaining sections is designed and documented.

With more time, I would:
- Finish creating combo_component and bundle_tier metaobject
  definitions and populate real entries
- Build the remaining four sections against that schema
- Extract shared design tokens (currently inline in hero.liquid) into
  a single assets/purelane-base.css used by every section
- Fix a contrast issue on the hero price tag when real product photos
  (light backgrounds) sit behind text styled for the original's dark
  gradient backdrop
- Add shopify theme check to CI so schema/Liquid errors are caught
  automatically, not manually