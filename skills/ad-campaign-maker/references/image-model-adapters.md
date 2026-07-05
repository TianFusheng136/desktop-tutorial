# Image model adapters

Use this when the user asks for image generation, poster generation, cover generation, or model-specific prompt output. The skill adapts to the backend implied by the current platform instead of asking the user to choose.

## Selection rule

Infer the image backend from context:

- Doubao / 豆包: use the Doubao adapter.
- ChatGPT / OpenAI / GPT Image: use the OpenAI GPT Image adapter.
- Gemini / Nano Banana: use the Nano Banana / Gemini adapter.
- Midjourney: use the Midjourney adapter.
- Stable Diffusion / SDXL / Flux / ComfyUI / Automatic1111: use the Stable Diffusion adapter.
- Unknown: output a universal prompt and state the assumed backend.

Ask for backend choice only when the user requests prompt export for another model or a cross-model prompt pack.

## OpenAI GPT Image adapter

Best for instruction-following, iterative editing, product/lifestyle scenes, and conversational refinements.

```markdown
### OpenAI GPT Image prompt
Create a [format/aspect ratio] advertising image for [product].
Goal: [awareness/clicks/leads/purchases/etc.]
Audience: [target audience].
Scene: [specific scene].
Composition: [layout, focal point, text-safe area].
Product treatment: [accuracy, size, angle, packaging details].
If reference photo exists: lightly clean the product presentation first while keeping identity unchanged.
Style: [commercial/lifestyle/editorial/etc.].
Lighting/camera: [lighting, lens, perspective].
Brand direction: [colors, mood, typography area].
Text handling: [blank text area OR exact text if requested].
Avoid: [distortions, extra logos, unsupported claims, clutter, misspelled text].
```

Notes:
- Prefer plain natural language over parameter-heavy syntax.
- For exact typography, request clean space and add text later unless the user explicitly wants rendered text.

## Nano Banana / Gemini adapter

Best for conversational image editing, subject consistency, combining reference images, lifestyle scenes, and fast iteration.

```markdown
### Nano Banana / Gemini prompt
Task: Generate/Edit an ad image.
Keep consistent: [product/person/logo/reference elements].
Change/create: [scene, action, background, mood].
Composition: [where subject, product, headline area, CTA area go].
Commercial purpose: [what the image should sell or communicate].
Style: [realistic product photo / UGC / premium poster / app promo].
Text-safe areas: [blank regions for later typography].
Do not change: [identity, packaging, product shape, brand colors].
Avoid: [fake UI, warped hands, wrong labels, clutter, unreadable text].
```

Notes:
- When editing references, emphasize what stays unchanged.
- Use a first pass for 产品轻微美化 / cleanup, then a second pass for poster or video cover composition.

## Doubao / 豆包 adapter

Best for Chinese-language workflows, social media posters, ecommerce images, lifestyle ads, and fast native Chinese iteration.

```markdown
### 豆包图片提示词
画面类型：[海报/小红书封面/电商主图/信息流广告/短视频封面]
广告目标：[曝光/点击/下单/留资]
主体：[产品/人物/场景，必须准确]
画面构图：[主体位置、文字留白、前中后景、视觉焦点]
风格：[真实商业摄影/高级感海报/生活方式/UGC/科技感/强促销]
光线与色彩：[光线、主色、辅助色、氛围]
文字区域：[需要留白的位置；如需文字，写明短文案]
品牌元素：[logo位置、品牌色、包装特征]
比例：[1:1 / 3:4 / 4:5 / 9:16 / 16:9]
不要出现：[错字、乱码、多余logo、畸形手、产品变形、虚假夸张效果]
```

Reference-photo edit wording:

```text
保持产品主体、形状、材质、颜色、logo/标签不变，只清理灰尘、反光、杂乱背景和偏色，提升光线质感；再基于清理后的产品做广告海报/短视频封面构图。
```

Notes:
- Use Chinese prompts by default.
- Keep overlay text short. If exact text matters, ask for blank space and add text later.
- Add “商业广告质感、主体清晰、背景干净、适合投放” when the user wants polished output.

## Midjourney adapter

Best for high-style campaign key visuals, mood boards, premium art direction, cinematic or editorial concepts.

```markdown
### Midjourney prompt
[subject/product], [scene], [composition], [style], [lighting], [camera/lens], [materials/textures], [brand color mood], clean advertising layout, text-safe negative space --ar [ratio] --style raw --v [version]
```

Notes:
- Do not rely on Midjourney for exact text. Recommend adding typography later.
- Use `--ar` for ratio.

## Stable Diffusion adapter

Best for controllable pipelines, negative prompts, LoRA/control images, batch variations, and inpainting.

```markdown
### Stable Diffusion positive prompt
[quality/style tags], [subject/product], [scene], [composition], [lighting], [camera], [advertising design direction], [clean background/text-safe area]

### Stable Diffusion negative prompt
low quality, blurry, distorted product, wrong logo, extra text, misspelled text, watermark, clutter, deformed hands, duplicate objects, bad anatomy, cropped product, fake claims

### Suggested controls
- Aspect ratio / size:
- Seed strategy:
- Reference/control image use:
- Inpainting plan:
- Post-edit typography:
```

## Universal fallback

When the image backend is unknown, output:

1. Visual strategy.
2. Layout spec.
3. Universal prompt.
4. Optional backend-specific adaptations.
5. Post-generation edit checklist.
