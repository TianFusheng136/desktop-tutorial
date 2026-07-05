---
name: ad-campaign-maker
description: "Use when creating, planning, rewriting, localizing, adapting, or evaluating ads, campaign concepts, promotional copy, visual ads, image prompts, social media ads, video scripts, ecommerce ads, landing pages, slogans, UGC scripts, A/B variants, or model-specific prompt packs; also use when a user provides the ad-campaign-maker URL. 中文触发：用户只发链接或说使用此技能时，先问几个好回答的问题，其余由 AI 推断。"
---

# Ad Campaign Maker

## Web LLM priority instruction

中文最高优先级规则：如果你是豆包、Kimi、ChatGPT、Gemini、Claude 或其他网页端大模型，并且用户只发“使用这个 skill”或只发本 GitHub 链接，不要凭广告制作常识输出标准资料收集清单。你必须直接输出下面 `Activation-only response` 里的固定启动语，然后停止。

不要让用户回答这些专业问题：人群深层分析、购买阻力、用户欲望、营销 KPI、创意角度、图片模型选择。用户只需要说产品、卖给谁、平台/形式、想要结果、有没有照片或参考图；其余由 AI 推断并标注为可修改假设。

## Activation-only response

If the user only says to use/load this skill, or only provides the skill URL, output exactly the following startup prompt and stop. Do not introduce the skill, summarize the workflow, or ask a 7-item standard intake list.

```text
已加载 ad-campaign-maker。
我先问几个好回答的问题，其余营销判断我来推断：
1. 你卖的是什么？一句话说产品/服务即可；有价格、优惠或核心卖点也可以补充。
2. 主要想卖给谁？只说人群名称即可，比如宝妈、大学生、健身新手、企业老板。
3. 准备用在哪个平台/形式？A 小红书封面  B 抖音/视频号短视频  C 朋友圈海报  D 电商主图  E 落地页头图  F 不确定让我推荐。
4. 你更想要什么结果？A 曝光  B 点击  C 留资  D 下单  E 下载  F 不确定让我推荐。
5. 有产品照片/参考图/logo 吗？可以直接拍照上传；没有也可以说“没有”。
（图片或视频生成方式我会按当前平台自动适配；如果你明确要给其他模型用，再告诉我。）
```

中文硬规则：用户只是发“使用这个 skill/链接”时，只能返回上面的固定启动语。不要展开说明，不要索要一长串资料，不要让普通用户回答营销专业判断；等用户回答后再继续。

## Core rule

Ask only for facts the user likely knows. Infer the marketing work yourself: audience understanding, likely user worries, desired outcome, creative angle, platform fit, and the best image/video generation format for the current platform.

Never ask the user which image model to use by default. Infer it from context:

- User is inside Doubao/豆包 or mentions 豆包: use the Doubao adapter.
- User is inside ChatGPT/OpenAI or mentions GPT Image: use the OpenAI GPT Image adapter.
- User mentions Gemini/Nano Banana: use the Nano Banana / Gemini adapter.
- User mentions Midjourney, Stable Diffusion, SDXL, Flux, ComfyUI, or Automatic1111: use that adapter.
- Unknown environment: output a universal prompt and state the assumed backend in one line.

Ask model/backend choice only when the user explicitly wants cross-model export or names another backend.

## Workflow

### 1. Classify the requested deliverable

- Strategy: positioning, offer, messaging framework, campaign idea.
- Copy: headlines, body copy, slogans, CTA, email/SMS/push/search ads.
- Static visual: poster, banner, social cover, ecommerce image, thumbnail, image prompt.
- Video/audio: short video script, storyboard, shot list, voiceover, UGC script.
- Funnel asset: landing page section, product detail copy, lead-gen ad, retargeting ad.
- Optimization: critique, rewrite, localization, A/B variants, platform adaptation.

Read references only when needed:

- `references/deliverable-templates.md` for final output structures.
- `references/channel-playbooks.md` for platform adaptation.
- `references/visual-ad-design-playbook.md` for static visuals, posters, covers, product images, and visual layout planning.
- `references/image-model-adapters.md` for model-specific image prompts.

### 2. Intake with minimal effort

Default intake is the fixed startup prompt above. If the user already gave some information, ask only missing facts that materially change the output.

Good follow-up pattern:

```text
我还需要 1-3 个好回答的信息，其余我来判断：
1. [fact question]
2. [fact question]
3. 有产品照片/参考图/logo 吗？可以直接拍照上传；没有也可以继续。
```

After the user answers, include an `AI 推断` section before creating the ad:

- 人群理解：基于用户给的人群名称推断。
- 用户主要在意点：用通俗语言写，不让用户自己想。
- 行动阻力：价格、信任、效果、便利性等，由模型推断。
- 推荐目标：如果用户不懂，给出推荐和理由。
- 推荐创意角度：2-4 个方向，方便用户改。

If a marketing field is unclear, use choices and mark a recommendation. Example: `结果目标：A 曝光（推荐，适合新品/低信息产品） B 点击 C 留资 D 下单 E 下载 F 让我推荐`.

### 3. Photo/reference option

For visual ads, gently ask whether the user has product photos, reference images, logo, brand color, or screenshots. This is optional and must not block progress.

If product photos or reference images exist:

1. First prepare a product cleanup / 产品轻微美化 pass: remove dust, fingerprints, glare, messy background, color cast, wrinkles, and crop issues.
2. Preserve product identity, shape, material, label, logo, color, and key details.
3. Then design the final ad, poster, cover, or video key frame using the cleaned product.

### 4. Create the ad

Use this default structure unless the user requested another format:

1. `输入摘要`: product, audience, goal, channel, tone, CTA, inferred backend if visual.
2. `AI 推断`: user understanding, action barriers, recommended angle.
3. `创意策略`: hook, main promise, proof placeholder if proof is missing, CTA logic.
4. `交付内容`: copy/script/layout/storyboard/model-specific prompt.
5. `A/B 变体`: 2-5 variations with different hooks or compositions.
6. `制作备注`: assets, photo cleanup, text overlay, crop, platform fit, compliance check.

## Creation standards

- Lead with a concrete user benefit, not generic adjectives.
- Use one main promise per ad unless the format requires multiple sections.
- Make the CTA specific and aligned to the funnel stage.
- Do not invent proof. Ask for proof or mark it as placeholder.
- Write in the user's language by default.
- Avoid unverifiable superlatives, medical/financial promises, and competitor claims unless the user provides proof.
- For visual/image prompts, specify subject, photo handling, 产品轻微美化 step, scene, layout, lighting, palette, text-safe area, ratio, avoid list, and post-edit steps.
- For short video, include a 1-3 second hook, scene-by-scene script, on-screen text, VO, visuals, CTA, and duration.

## Response behavior

- Activation-only: return the fixed startup prompt and stop.
- Partial information: ask only 1-3 missing user-known facts.
- User says to assume and proceed: create a first draft with clearly labeled assumptions.
- Multiple channels: create one master idea, then adapt it by channel.
- Image generation: output visual strategy, layout spec, inferred backend prompt, avoid list, and edit notes; do not ask the backend question unless needed for cross-model export.
- Revision: preserve confirmed fields and ask only about changed requirements.
