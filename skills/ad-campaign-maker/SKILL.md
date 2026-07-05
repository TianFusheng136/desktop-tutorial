---
name: ad-campaign-maker
description: "Use when creating, planning, rewriting, localizing, adapting, or evaluating ads, campaign concepts, promotional copy, visual ads, image prompts, social media ads, video scripts, ecommerce ads, landing pages, slogans, UGC scripts, A/B variants, or model-specific image prompts. Default to a low-friction brief: ask only user-known facts, infer marketing strategy, and offer choices for unclear goals or channels."
---

# Ad Campaign Maker

## Core rule

Clarify first, then create, but keep clarification easy. Do not produce final ads until the brief is clear enough. If the user explicitly says to proceed without answers, create with labeled assumptions.

**Brief friction rule:** never dump a full marketing brief questionnaire. Ask only user-known facts. Never ask the user to supply pain points, desires, objections, awareness level, KPI, or creative angles unless they volunteer marketing strategy. 禁止让普通用户填写“痛点/需求欲望/决策顾虑”这类专家问题；由 AI 根据产品、人群、渠道和优惠推断，并作为可修改假设呈现。

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


#### Low-friction Brief Mode

Default to low-friction brief collection. Ask only for user-known facts; do not make the user think like a marketing strategist. Never ask the user to supply pain points; infer pain points and decision concerns from the simple audience label. The model should infer pain points, desires, objections, awareness level, likely KPI, and message angles from the product, audience label, channel, and offer. Present these as editable assumptions instead of asking the user to invent them.

Use multiple-choice options for unclear marketing fields. For example, if the goal is missing, ask the user to choose from: awareness / clicks / leads / purchases / app installs / event registration / retargeting / retention, and include one recommended option with a short reason. If the audience is vague, ask for a simple audience label only, then infer likely pain and decision concerns.

Do not ask questions like “what are their core pain points, desires, and objections?” unless the user is clearly a marketer or has already provided strategic context. Ask “who is this mainly for?” and then infer the rest. If the model is tempted to ask a strategic question, convert it into 2-6 multiple-choice options plus “不确定让我推荐”.

Prefer this quick brief format when starting from little context:

```text
我先问几个好回答的问题，其余营销判断我来推断：
1. 你卖的是什么？有没有价格、优惠或核心卖点？
2. 主要想卖给谁？只说人群名称即可，比如宝妈、大学生、健身新手、SaaS 创业者。
3. 准备用在哪个平台/形式？如果不确定，我可以给你选项：小红书封面、抖音信息流、朋友圈海报、电商主图、落地页头图。
4. 你更想要什么结果？A 曝光  B 点击  C 留资  D 下单  E 下载  F 不确定让我推荐。
5. 如果要生图，准备用哪个工具？A 豆包  B OpenAI GPT Image  C Nano Banana/Gemini  D Midjourney  E Stable Diffusion  F 不确定。
6. 有 logo、产品图、品牌色、禁用词或必须出现的信息吗？
```

After the user answers, output `AI-inferred assumptions` with pain points, desires, objections, likely goal, and creative angle. Make the assumptions easy to correct.

Ask only for missing fields that materially change the output. Prefer 3-6 concise questions. Use Low-friction Brief Mode by default.

Internal brief fields to resolve. Do not show this list to the user. Infer what the model can infer and ask only user-known facts:

1. Product/service: what is advertised, key features, price or offer if relevant.
2. Audience: ask who should respond; infer pain point, desire, objections, and awareness level.
3. Goal: offer multiple-choice options such as awareness, clicks, leads, purchases, app installs, event registration, retargeting, or retention; recommend one if unclear.
4. Channel and format: platform, placement, length/size/aspect ratio, paid/organic, video/static/audio/text.
5. Message and offer: main promise, proof, promotion, CTA, landing destination.
6. Brand voice: tone, language, style, examples to imitate or avoid.
7. Constraints: legal/compliance limits, claims that must/must not appear, required words, assets, deadline.
8. Success metric: KPI and testing requirements.

For visual/image-generation tasks, also ask:

- Target generator: OpenAI GPT Image, Nano Banana/Gemini Image, Doubao/豆包, Midjourney, Stable Diffusion, or model-agnostic prompt.
- Required aspect ratio/size and whether text must be rendered inside the image.
- Available assets: product photos, logo, brand colors, fonts, screenshots, spokesperson/persona references.

If the user only says “帮我做个广告” or equivalent, ask the low-friction starter only:

```text
我先问几个好回答的问题，其余营销判断我来推断：
1. 你卖的是什么？一句话说产品/服务即可；有价格、优惠或核心卖点也可以补充。
2. 主要想卖给谁？只说人群名称即可，比如宝妈、大学生、健身新手、企业老板。
3. 准备用在哪个平台/形式？A 小红书封面  B 抖音/视频号短视频  C 朋友圈海报  D 电商主图  E 落地页头图  F 不确定让我推荐。
4. 你更想要什么结果？A 曝光  B 点击  C 留资  D 下单  E 下载  F 不确定让我推荐。
5. 如果要生图，准备用哪个工具？A 豆包  B OpenAI GPT Image  C Nano Banana/Gemini  D Midjourney  E Stable Diffusion  F 不确定。
6. 有 logo、产品图、品牌色、禁用词或必须出现的信息吗？没有也可以说“没有”。
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
