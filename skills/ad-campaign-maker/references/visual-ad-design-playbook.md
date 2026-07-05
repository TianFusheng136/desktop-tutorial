# Visual ad design playbook

Use this when the user asks for posters, banners, product ads, social covers, thumbnails, ecommerce images, or image-generation prompts.

## Product photo intake and light beautification

When the user has a physical product, ask lightly:

```text
有产品照片/参考图/logo 吗？可以直接拍照上传；没有也可以继续。
```

This is optional and must not block progress.

If a product photo/reference exists, use a two-stage visual workflow:

1. Product cleanup / 产品轻微美化 pass:
   - Preserve product identity, shape, material, logo, label, color, and key details.
   - Improve only presentation: remove dust, fingerprints, glare, wrinkles, color cast, messy background, bad crop, and weak lighting.
   - Do not redesign the product, invent packaging, add fake logos, change claims, or make the product look like another item.
   - Keep realistic texture and scale.
2. Advertising key visual pass:
   - Place the cleaned product into the chosen composition template.
   - Add scene, background, brand color, text-safe area, CTA zone, and platform ratio.
   - For video poster / short-video cover, create a clean hero frame first, then design the poster around that frame.

Suggested output wording:

```markdown
## Product image prep
- Reference/photo needed: optional; user can upload a quick phone shot.
- Cleanup pass: remove dust/glare/background clutter; preserve product identity.
- Ad pass: use cleaned product as hero object in [composition].
```

## Visual input checklist

- Visual job: stop-scroll, explain, build trust, lifestyle desire, price urgency, retarget, or launch announcement.
- Asset reality: product photo, logo, packaging, screenshots, spokesperson, brand colors, fonts.
- Output constraints: platform, aspect ratio, safe margins, text amount, whether exact text must appear in-image.
- Action cue: discount, demo, testimonial, before/after, comparison, guarantee, limited-time cue, QR/link/CTA.

## Composition templates

| Template | Best for | Layout rule |
|---|---|---|
| Center hero product | ecommerce, launch, premium goods | Product large in center, short headline above/left, proof badge near product, CTA bottom. |
| Left text / right product | banners, app ads, B2B | Left 40% text stack, right 60% product/screenshot, CTA under body copy. |
| Product in use | lifestyle, beauty, food, fitness | Human/context leads emotion; product visible in hand/scene; benefit text in clean negative space. |
| Problem → solution → result | problem-solution ads, lead gen | Three zones or panels; keep labels short; product appears in solution/result zone. |
| Before / after split | transformation proof | Clear divider; same camera angle; label both sides; avoid exaggerated unsupported claims. |
| Screenshot stack | apps/SaaS/tools | Main UI screenshot plus 2-3 floating feature cards; use depth/shadow; CTA at bottom. |
| Testimonial card | trust/retargeting | Portrait or avatar, quote card, star/proof cue, product or offer secondary. |
| UGC native frame | Douyin/TikTok/Xiaohongshu | Looks like phone capture; casual overlay; imperfect but readable composition. |
| Offer burst | sales/promotion | Price/discount badge dominates; product secondary; urgency cue and CTA obvious. |

## Visual hierarchy rules

1. One focal point only: product, face, result, or offer.
2. Text hierarchy: 3-7 word headline, 1 proof/support line, 1 CTA. Avoid paragraph overlays.
3. Keep text-safe area clean; do not place text over busy details.
4. Show the product doing the promised job, not just floating decoratively.
5. Use proof visually: demo, result, testimonial, rating, press, guarantee, or mechanism diagram. Mark placeholders clearly if proof is not provided.
6. Design for thumbnail first: if it does not read at small size, simplify.

## Style formulas

- Premium/luxury: large negative space, low-saturation palette, single hero object, soft directional light, restrained typography, no clutter.
- Tech/SaaS: deep or clean gradient background, crisp UI cards, subtle glow, geometric accents, high-contrast CTA.
- Youth/lifestyle: natural light, candid scene, warm colors, stickers or casual annotations, native social framing.
- Hard promotion: saturated brand color, large price/discount, burst badge, countdown/limited cue, simple product cutout.
- B2B authority: clean white/blue/gray palette, dashboard/screenshot, proof metric, role-specific headline, low-effort CTA.
- Food/beauty: macro detail, texture, sensory cues, warm highlights, hands or use scenario.

## Prompt planning structure

Use this order before adapting to a model:

1. Subject/product: what must be visually accurate.
2. Scene/context: where the product appears and why.
3. Composition: focal point, layout, negative space, text area.
4. Style: commercial photography, editorial, UGC, 3D, flat vector, premium poster, etc.
5. Lighting/camera: lens, angle, depth of field, mood.
6. Brand system: palette, shapes, typography direction, logo/text placement.
7. Output: aspect ratio, orientation, image quality, background transparency if needed.
8. Constraints: avoid wrong text, extra logos, distorted product, fake claims, clutter.

## Exact text handling

If exact copy matters, prefer generating the image with blank text-safe areas and add text later in design software. Ask for in-image text only when the chosen model is known to render text reliably enough for the use case. Always include a post-generation typography pass for final ads.
