# Image model adapters

Use this when the user asks for image generation or names a target generator. The skill does not force a platform to use a model; it outputs the right prompt format for the tool the user will use.

## Selection rule

Ask for Target generator if missing. If the user says “随便/通用”, provide a model-agnostic prompt plus one recommended adapter based on the platform they will use.

## OpenAI GPT Image adapter

Use for OpenAI GPT Image models such as `gpt-image-2` or compatible ChatGPT image generation.

Best for: instruction-following, ad layouts with natural-language constraints, iterative editing, product/lifestyle scenes, and conversational refinements.

Output format:

```markdown
### OpenAI GPT Image prompt
Create a [format/aspect ratio] advertising image for [product].
Goal: [conversion/awareness/etc.]
Audience: [target audience].
Scene: [specific scene].
Composition: [layout, focal point, text-safe area].
Product treatment: [accuracy, size, angle, packaging details].
Style: [commercial/lifestyle/editorial/etc.].
Lighting/camera: [lighting, lens, perspective].
Brand direction: [colors, mood, typography area].
Text handling: [blank text area OR exact text if requested].
Avoid: [distortions, extra logos, unsupported claims, clutter, misspelled text].
```

Notes:
- Prefer plain natural language over parameter-heavy syntax.
- For exact typography, request clean space and add text later unless the user explicitly wants rendered text.
- For edits, describe what must remain unchanged and what should change.

## Nano Banana / Gemini Image adapter

Use for Nano Banana, Gemini Image, Gemini Flash Image, or Google AI Studio image workflows.

Best for: conversational image editing, subject consistency, combining reference images, lifestyle scenes, and fast visual iteration.

Output format:

```markdown
### Nano Banana / Gemini Image prompt
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
- Emphasize what to keep unchanged when editing references.
- Use iterative follow-up prompts: first composition, then lighting, then cleanup.
- For brand/product accuracy, provide reference images when possible.

## Doubao / 豆包 adapter

Use when the user will paste the prompt into 豆包网页端 or Doubao image tools.

Best for: Chinese-language workflows, social media posters, ecommerce images, lifestyle ads, fast native Chinese prompt iteration.

Output format:

```markdown
### 豆包生图提示词
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

Notes:
- Use Chinese prompts by default.
- Keep overlay text short. If exact text matters, ask for blank space and add text later.
- Add “商业广告质感、主体清晰、背景干净、适合投放” when the user wants polished output.

## Midjourney adapter

Use when the target is Midjourney.

Best for: high-style campaign key visuals, mood boards, premium art direction, cinematic or editorial concepts.

Output format:

```markdown
### Midjourney prompt
[subject/product], [scene], [composition], [style], [lighting], [camera/lens], [materials/textures], [brand color mood], clean advertising layout, text-safe negative space --ar [ratio] --style raw --v [version]
```

Notes:
- Do not rely on Midjourney for exact text. Recommend adding typography later.
- Use `--ar` for ratio. Keep parameter suggestions separate from the descriptive prompt.
- For product accuracy, use image references if available.

## Stable Diffusion adapter

Use for SDXL, Flux-style SD workflows, ComfyUI, Automatic1111, or other local pipelines.

Best for: controllable pipelines, negative prompts, LoRA/control images, batch variations, inpainting.

Output format:

```markdown
### Stable Diffusion positive prompt
[quality/style tags], [subject/product], [scene], [composition], [lighting], [camera], [advertising design direction], [clean background/text-safe area]

### Stable Diffusion negative prompt
low quality, blurry, distorted product, wrong logo, extra text, misspelled text, watermark, clutter, deformed hands, duplicate objects, bad anatomy, cropped product, fake claims

### Suggested controls
- Aspect ratio / size:
- Seed strategy:
- ControlNet / reference use:
- Inpainting plan:
- Post-edit typography:
```

Notes:
- Separate positive and negative prompts.
- Recommend inpainting for product/logo correction.
- Use references/control images for layout or product fidelity.

## Model-agnostic fallback

When the generator is unknown, output:

1. Visual strategy.
2. Layout spec.
3. Universal prompt.
4. Generator-specific adapter choices the user can copy from.
5. Post-generation edit checklist.
