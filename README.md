# Motion Prompt Library

29 copy-paste prompts for vibe-coding websites with motion — each one tested by actually generating a page from it.

Give a prompt to Lovable, Bolt, Cursor, Claude, or any AI coding tool, replace the placeholder content with your product, and get a page whose motion is deliberate instead of decorative.

## Why this exists

Most prompt libraries collect other people's prompts in whatever format they happened to be written. This one is built from a single motion-design method:

- **4 personas** — Playful, Premium, Corporate, Energetic. One per prompt, never mixed.
- **Emotion first** — pick the emotion, then the easing, duration, and overshoot follow from it.
- **7-part format** — every prompt has the same structure (see [FORMAT.md](FORMAT.md)): role & goal, page type & structure, content boundaries, visual rules, interaction & states, technical constraints, acceptance checklist.
- **Tested, not just written** — every prompt was used to generate a real single-file page, then checked: structure (13 items each), headless-browser render with screenshots, interaction verification, and a 390px responsive check. 377 structure checks, 0 failures. Test pages and screenshots are in `tests/`.

## The 29 prompts

| Category | Prompts |
|---|---|
| `prompts/hero/` | Playful, Premium, Corporate, Energetic hero sections |
| `prompts/3d/` | Glass depth, rotating cube, card flip, collectible parallax |
| `prompts/scroll/` | Container reveal, fade-in-up, parallax, snap scroll |
| `prompts/sections/` | Features, pricing, FAQ, footer, header nav |
| `prompts/components/` | Buttons, cards, loaders, forms |
| `prompts/advanced/` | Choreographed sequence, scroll timeline, physics motion, combined 3D + scroll, staggered grid — composite effects a single basic prompt can't produce |
| `prompts/full-page/` | SaaS landing, brand landing, event landing — one prompt, one complete landing page |

Prompts are written in Chinese; the structure, personas, and acceptance criteria work the same in any language. Each prompt file names its persona and emotion at the top.

## Principles

The thinking behind the prompts, not the instructions: [PRINCIPLES.md](PRINCIPLES.md). Why emotion comes before easing, why one persona per page, why three layers, why the 1/3 rule, why transform + opacity only, why no linear easing for spatial motion, why every prompt is tested, and where the persona system comes from.

## How to use

1. Pick a prompt from `prompts/`.
2. Replace the placeholder content (product name, copy, numbers) with your own. Never let the AI invent customers, awards, or statistics — the prompt says so too.
3. Paste it into your AI coding tool.
4. Run the acceptance checklist at the end of the prompt against the result.

## Motion rules baked into every prompt

- One persona per page. No mixing.
- Emotion picked before any motion parameter.
- One motion travels at most 1/3 of the screen; when 3+ elements move, still at most 1/3.
- One hero element at a time; everything else dims to 40–60%.
- Primary layer + secondary layer (30–50% amplitude) + ambient layer (10–20%). All three, every time.
- Never opacity alone for an important state change — always pair it with position or scale.
- Never linear easing for spatial motion (linear is only for spinners, progress bars, timers).
- Animate `transform` + `opacity` only (GPU-accelerated).

Full format standard, persona table, and emotion table: [FORMAT.md](FORMAT.md).

## Tested

Every prompt in this repo has a generated test page and a screenshot under `tests/<category>/`, verified 2026-11-25:

- **Structure**: 13 checks per prompt (single file, easing, duration, overshoot, delay, secondary layer, ambient layer, 1/3 rule, transform+opacity only, no linear easing, core mechanism, responsive) — 377/377 passed (29 prompts: 21 basic + 5 advanced + 3 full-page).
- **Rendering**: headless-browser render, screenshots verified by eye, 0 JS errors on all 29 pages. Full-page prompts get 4 screenshots each (hero / mid / footer / full page).
- **Interaction**: real actions verified per page (tilt angles, cube drag-and-snap, card flip 180°, scroll reveal counts, parallax speed ratios, snap navigation, accordion, pricing toggle, hamburger menu, button states, form validation and success states; advanced pages add spring return-to-origin, momentum scrolling, scroll-driven progress bars, and flip-after-reveal gating; full pages add whole-page reveal counts and per-section handoffs).
- **Responsive**: 390px, no horizontal scroll, body text 16px+.

## License

MIT. Use the prompts however you like.
