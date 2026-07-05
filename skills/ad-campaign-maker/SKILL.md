---
name: ad-campaign-maker
description: Guided advertising creation workflow for making ads, campaign concepts, promotional copy, social media ads, video ad scripts, storyboards, ecommerce ads, landing page copy, slogans, UGC/influencer scripts, A/B variants, and media-specific ad deliverables. Use when the user asks to create, plan, rewrite, localize, adapt, or evaluate advertising or marketing creative; this skill forces a requirement-clarification step before producing ads and then creates deliverables matched to the user's objective, audience, channel, offer, brand voice, and constraints.
---

# Ad Campaign Maker

## Core rule

Clarify first, then create. Do not produce the final advertisement until the user's requirements are sufficiently clear. If required information is missing, ask focused questions and stop. If the user explicitly says to proceed without answers, create using labeled assumptions.

## Workflow

### 1. Classify the request

Identify the requested advertising output:

- Strategy: campaign concept, positioning, angle, offer, messaging framework.
- Copy: headlines, primary text, slogans, CTAs, email/SMS/push ads, search ads.
- Visual ad: static poster/banner/social image layout, image-generation prompt, design direction.
- Video/audio: short video script, TVC, storyboard, shot list, voiceover, UGC/influencer script.
- Funnel asset: landing page hero, ecommerce product detail ad copy, lead-gen ad, retargeting ad.
- Optimization: critique, rewrite, localization, A/B variants, platform adaptation.

Read `references/deliverable-templates.md` when producing final deliverables or when the user requests a specific format. Read `references/channel-playbooks.md` when the channel/platform has special constraints or best practices.

### 2. Gather the ad brief

Ask only for missing information. Prefer 5-8 concise questions. Combine related fields in one question when possible.

Required brief fields:

1. Product/service: what is being advertised, key features, price or offer if relevant.
2. Audience: who should respond, their pain point, desire, objections, awareness level.
3. Goal: awareness, clicks, leads, purchases, app installs, event registration, retention, etc.
4. Channel and format: platform, placement, length/size, paid/organic, video/static/audio/text.
5. Message and offer: main promise, proof, promotion, CTA, landing destination.
6. Brand voice: tone, language, style, examples to imitate or avoid.
7. Constraints: legal/compliance limits, claims that must/must not appear, required words, assets, deadline.
8. Success metric: KPI and any testing requirements.

If the user provided enough information, summarize the brief in 3-6 bullets and proceed. If not, ask questions such as:

```text
为了按固定流程制作广告，我需要先确认这些信息：
1. 广告卖的是什么？核心卖点/价格/优惠是什么？
2. 目标用户是谁？他们最在意的痛点或欲望是什么？
3. 投放目标是什么：曝光、点击、留资、下单、下载，还是其他？
4. 用在哪个渠道和格式：小红书/抖音/视频号/Meta/Google/海报/短视频等？时长或尺寸要求？
5. 希望的品牌语气是什么：专业、年轻、奢华、强促销、温暖、搞笑等？
6. 有哪些必须包含或不能出现的内容、素材、合规限制？
```

Stop after asking if answers are required. Do not fill the rest of the turn with speculative ads unless the user asked for assumptions.

### 3. Confirm assumptions

When proceeding with incomplete data, add an `Assumptions` section before the ad output. Keep assumptions practical and easy for the user to correct.

### 4. Create the advertisement

Match the deliverable to the brief. Use this default output structure unless a format is specified:

1. `Brief recap`: product, audience, goal, channel, tone, CTA.
2. `Creative strategy`: core insight, value proposition, hook, reason-to-believe, objection handling.
3. `Ad deliverables`: the actual copy/script/layout/storyboard/variants.
4. `A/B variants`: 2-5 variations with different hooks or angles when useful.
5. `Production notes`: visual direction, pacing, asset list, localization notes, compliance caveats.
6. `Quality checklist`: confirm the ad has a clear audience, single promise, CTA, proof, channel fit, and avoids unsupported claims.

## Creation standards

- Lead with a concrete user benefit, not generic adjectives.
- Use one main promise per ad unless the format allows multiple sections.
- Make the CTA specific and aligned to the funnel stage.
- Prefer specific proof: numbers, demo, testimonial, mechanism, guarantee, before/after context. Do not invent proof; ask for it or label as placeholder.
- Write in the user's language by default. If the target market differs from the conversation language, ask or provide localized variants.
- Avoid unverifiable superlatives like “best”, “guaranteed”, “No.1”, medical/financial promises, or competitor claims unless the user provides proof and asks to include them.
- For regulated topics, request the user's compliance requirements before finalizing.
- For image/video prompts, specify subject, scene, composition, style, text overlay, aspect ratio, lighting, camera movement, and negative constraints.
- For short-form video, include hook in the first 1-3 seconds, scene-by-scene script, on-screen text, VO, visuals, CTA, and duration.

## Response behavior

- If the user only says “帮我做个广告” or equivalent, ask the ad brief questions first.
- If the user provides a partial brief, ask only for the missing fields that materially change the output.
- If the user says “你先假设/直接做/随便定”, proceed with assumptions and make a complete first draft.
- If the user asks for multiple channels, create a master idea first, then adapt by channel.
- If the user asks to revise, preserve confirmed brief fields and ask only about the changed requirement.
