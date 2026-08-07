# Metaobject Definitions

## review
- Reviewer name — Single line text
- Rating — Rating (1–5)
- Review title — Single line text
- Review body — Multi-line text
- Product label — Single line text     (e.g. "Laundry detergent" — a caption, not a product ref)

## combo_component
- Product — Reference (Product, single)
- Caption — Single line text            (e.g. "Cuts grease instantly")

## combo
- Title — Single line text
- Badge — Single line text, optional   (e.g. "Most popular")
- Components — Reference list (combo_component, list)
- Price — Number (decimal)
- Compare at price — Number (decimal)
- CTA label — Single line text, default "Shop bundle"
- CTA link — URL

## bundle_tier
- Tag — Single line text               (e.g. "Starter")
- Quantity — Integer
- Price — Number (decimal)
- Compare at price — Number (decimal)
- Per-product note — Single line text  (e.g. "Flat ₹174 per product")
- Features — List of single line text
- Featured — Boolean
- Preview products — Reference list (Product, list)
- CTA label — Single line text
- CTA link — URL

Used by: sections/reviews-rail.liquid, sections/combos.liquid, sections/bundle-tiers.liquid