---
name: ad-campaign-maker
description: Guided advertising creation workflow for campaign concepts, promotional copy, visual ads, image-generation prompts, social media ads, video scripts, storyboards, ecommerce ads, landing pages, slogans, UGC scripts, A/B variants, and model-specific image prompt adaptation for OpenAI GPT Image, Nano Banana/Gemini Image, Doubao, Midjourney, and Stable Diffusion. Use when the user asks to create, plan, rewrite, localize, adapt, or evaluate advertising or marketing creative.
---

# Ad Campaign Maker

## Core rule

Clarify first, then create. Do not produce final ads until the brief is clear enough. If the user explicitly says to proceed without answers, create with labeled assumptions.

This skill creates advertising strategy, copy, visual direction, scripts, storyboards, and image-generation packs. A skill cannot force an external platform to use a specific image model; it must adapt the deliverable to the generator the user will actually use.

## Workflow

### 1. Classify the request

Identify the requested output:

- Strategy: campaign concept, positioning, angle, offer, messaging framework.
- Copy: headlines, primary text, slogans, CTAs, email/SMS/push, search ads.
- Visual ad: poster, banner, social image, ecommerce image, cover image, design direction, image prompt.
- Video/audio: short video script, TVC, storyboard, shot list, voiceover, UGC/influencer script.
- Funnel asset: landing page hero, product detail ad copy, lead-gen ad, retargeting ad.
- Optimization: critique, rewrite, localization, A/B variants, platform adaptation.

Read references as needed:

- `references/deliverable-templates.md` for final output formats.
- `references/channel-playbooks.md` for platform/channel constraints.
- `references/visual-ad-design-playbook.md` for visual ads, posters, banners, covers, product images, and image-generation planning.
- `references/image-model-adapters.md` when the user wants image generation or names a target generator/model.

### 2. Gather the ad brief

Ask only for missing fields that materially change the output. Prefer 5-8 concise questions.

Required brief fields:

1. Product/service: what is advertised, key features, price or offer if relevant.
2. Audience: who should respond, pain point, desire, objections, awareness level.
3. Goal: awareness, clicks, leads, purchases, app installs, event registration, retention, etc.
4. Channel and format: platform, placement, length/size/aspect ratio, paid/organic, video/static/audio/text.
5. Message and offer: main promise, proof, promotion, CTA, landing destination.
6. Brand voice: tone, language, style, examples to imitate or avoid.
7. Constraints: legal/compliance limits, claims that must/must not appear, required words, assets, deadline.
8. Success metric: KPI and testing requirements.

For visual/image-generation tasks, also ask:

- Target generator: OpenAI GPT Image, Nano Banana/Gemini Image, Doubao/豆包, Midjourney, Stable Diffusion, or model-agnostic prompt.
- Required aspect ratio/size and whether text must be rendered inside the image.
- Available assets: product photos, logo, brand colors, fonts, screenshots, spokesperson/persona references.

If the user only says “帮我做个广告” or equivalent, ask:

```text
为了按固定流程制作广告，我需要先确认这些信息：
1. 广告卖的是什么？核心卖点、价格或优惠是什么？
2. 目标用户是谁？他们最在意的痛点、欲望或顾虑是什么？
3. 投放目标是什么：曝光、点击、留资、下单、下载，还是其他？
4. 用在哪个渠道和格式：小红书、抖音、视频号、Meta、Google、海报、短视频等？尺寸或时长要求？
5. 品牌语气是什么：专业、年轻、奢华、强促销、温暖、搞笑、克制等？
6. 有哪些必须包含或不能出现的内容、素材、合规限制？
7. 如果要生图，准备用哪个生图工具/模型：OpenAI GPT Image、Nano Banana/Gemini、豆包、Midjourney、Stable Diffusion，还是通用 prompt？
```

Stop after asking if answers are required. Do not fill the rest of the turn with speculative ads unless the user asked for assumptions.

### 3. Confirm assumptions

When proceeding with incomplete data, add an `Assumptions` section before the output. Keep assumptions practical and easy to correct.

### 4. Visual Ad Design Workflow

Use this workflow whenever the output includes a visual ad, static social image, poster, banner, product image, cover, thumbnail, or image-generation prompt.

1. Define the visual job: stop-scroll, explain product, build trust, show lifestyle, create urgency, or retarget.
2. Choose a composition template from `visual-ad-design-playbook.md`.
3. Specify layout before prompt: focal point, product placement, text hierarchy, background, color palette, typography direction, CTA zone, safe margins.
4. Decide whether text should be generated in-image or added later. If exact copy matters, recommend leaving clean text zones and adding typography in design software unless the selected model handles text reliably.
5. Select Target generator and adapt the prompt using `image-model-adapters.md`.
6. Provide at least 2 visual variants with different angles or composition, not only different adjectives.
7. Include post-generation edit notes: crop, retouch, text overlay, logo placement, product accuracy checks, and compliance checks.

### 5. Create the advertisement

Use this default structure unless a format is specified:

1. `Brief recap`: product, audience, goal, channel, tone, CTA, target generator if visual.
2. `Creative strategy`: core insight, value proposition, hook, proof, objection handling.
3. `Ad deliverables`: copy/script/layout/storyboard/image-generation pack.
4. `A/B variants`: 2-5 variations with different hooks, audience angles, or visual concepts.
5. `Production notes`: assets, visual direction, pacing, localization, compliance.
6. `Quality checklist`: audience, single promise, CTA, proof, channel fit, visual hierarchy, model fit.

## Creation standards

- Lead with a concrete user benefit, not generic adjectives.
- Use one main promise per ad unless the format allows multiple sections.
- Make the CTA specific and aligned to funnel stage.
- Prefer specific proof: numbers, demo, testimonial, mechanism, guarantee, before/after context. Do not invent proof; ask for it or label as placeholder.
- Write in the user's language by default. If the target market differs from the conversation language, ask or provide localized variants.
- Avoid unverifiable superlatives like “best”, “guaranteed”, “No.1”, medical/financial promises, or competitor claims unless the user provides proof and asks to include them.
- For regulated topics, request compliance requirements before finalizing.
- For visual/image prompts, specify subject, product treatment, scene, composition, lighting, camera, brand palette, text area, aspect ratio, negative constraints, and post-edit steps.
- For short-form video, include a 1-3 second hook, scene-by-scene script, on-screen text, VO, visuals, CTA, and duration.

## Response behavior

- If the user only says “帮我做个广告” or equivalent, ask the ad brief questions first.
- If the user provides a partial brief, ask only for missing fields that materially change output.
- If the user says “你先假设，直接做”, proceed with assumptions and make a complete first draft.
- If the user asks for multiple channels, create a master idea first, then adapt by channel.
- If the user asks for image generation, do not only output a prompt; output visual strategy, layout spec, model-specific prompt, negative prompt/avoid list, and edit notes.
- If the user asks to revise, preserve confirmed fields and ask only about changed requirements.
