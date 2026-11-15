---
name: design-taste-lite
description: Condensed anti-template frontend design guide for websites, landing pages, portfolios and blogs. Load before writing HTML/CSS so the page does not look AI-generated.
# Condensed version of the design-taste-frontend skill (see LICENSE).
---

# Design Taste Lite

For landing pages, portfolios, blogs, redesigns. Not dashboards or data tables.
Rules are contextual: read the brief first, apply what fits. "Banned" means banned unless the brief explicitly asks for it.

## 1. Read the Brief First

Check these signals before writing code:
1. Page kind: landing (SaaS / consumer / agency / event), portfolio, blog/editorial, redesign.
2. Vibe words the user used: minimalist, premium, playful, brutalist, editorial, dark tech, trust-first.
3. References: linked sites, screenshots, named brands.
4. Audience: the audience picks the look, not your taste.
5. Existing brand assets (logo, colors, fonts): use them.
6. Quiet constraints (public sector, regulated, kids, accessibility-first) override aesthetics.

Before any code, write ONE line:
"Reading this as: <page kind> for <audience>, with a <vibe> language, leaning toward <aesthetic>."

If the brief is truly ambiguous, ask exactly ONE question. Otherwise do not ask; proceed.

Set three dials (1-10) and let them drive layout, motion and spacing:
- VARIANCE (symmetry 1 to asymmetry 10)
- MOTION (static 1 to cinematic 10)
- DENSITY (airy 1 to packed 10)
Presets (V/M/D): SaaS landing 7/6/4. Agency/creative 9/8/3. Premium consumer 7/6/3. Designer portfolio 8/7/3. Developer portfolio 6/5/4. Blog/editorial 6/4/3. Public sector 3/2/5. Minimalist/calm 5/3/2.

Stack note: plain HTML + CSS + vanilla JS is fine. Use CSS variables for tokens, CSS Grid for layout, no framework required. One icon library only (Phosphor, Tabler, etc.), never hand-draw SVG icon paths.

## 2. Typography

- Headline default: 2.25rem mobile to 3.75rem desktop, letter-spacing -0.02em to -0.04em, line-height 1 to 1.1.
- Hero with 3-5 word headline may go to 4.5rem. Longer headline: stay at 2.25-3.75rem. A 4-line headline is a font-size error.
- Body: 1rem, line-height 1.6-1.7, max-width 65ch, muted (not pure black) text.
- Do not default to Inter. Prefer Geist, Outfit, Satoshi, Cabinet Grotesk, General Sans, PP Neue Montreal. Inter is OK only for neutral/public-sector briefs.
- Good pairs: Geist + Geist Mono, Satoshi + JetBrains Mono, Cabinet Grotesk + Inter Tight.
- Serif is NOT the default for "creative" or "premium". Use serif only if the brand names one or the brand is truly editorial/luxury/heritage. Never default to Fraunces or Instrument Serif.
- Emphasis inside a headline: italic or bold of the SAME font. Never mix in a random serif word.
- Italic display words with descenders (g j p q y): line-height at least 1.1 plus a small bottom padding so they do not clip.
- Control hierarchy with weight and color, not just giant size. No gradient text on big headlines.
- Load fonts with @font-face and font-display: swap (self-host when possible).

## 3. Color

- Neutral base (zinc, slate, stone or similar) plus ONE accent. Saturation under 80%.
- Lock the accent: same accent on the whole page. No blue CTA on a rose site, no teal badge in the footer.
- One gray family: do not mix warm and cool grays.
- No "AI purple/blue glow": no purple gradients, neon glows, random neon gradients. Purple only if the brand is purple, then use it with restraint.
- No pure #000000 or #ffffff. Use off-black and off-white.
- Shadows: tinted toward the background hue, never pure black on light backgrounds.
- Premium-consumer ban: do not default to beige/cream background + brass/clay/oxblood accent + espresso text (e.g. #f5f1ea, #b08947, #1a1714). Alternatives: cold luxury (silver, chrome, smoke), forest green + bone + amber, black + tan, cobalt + one neutral, terracotta + slate, olive + brick, monochrome + one bright pop.
- Theme lock: the whole page is light, dark, or auto. Sections do not flip theme mid-page. Small tint shifts within the same theme are fine.
- Support dark mode via CSS variables and prefers-color-scheme for consumer pages. Keep hierarchy and contrast in both modes.

## 4. Layout and Spacing

- Container: max-width about 1280-1400px, centered, side padding 1rem on mobile.
- Section padding by DENSITY: airy (1-3) 8-12rem; normal (4-7) 4-6rem; dense (8-10) tight, 1px lines instead of cards.
- Use CSS Grid, not flexbox percentage math like calc(33% - 1rem).
- Full-height hero: min-height: 100dvh, never height: 100vh.
- Breakpoints: 640, 768, 1024, 1280px. Every multi-column layout collapses to one column under 768px, written explicitly.
- VARIANCE > 4: avoid the centered hero. Use split (50/50), text-left + image-right, or asymmetric whitespace. Centered is OK for manifesto/announcement pages.
- VARIANCE 8-10: uneven grids (2fr 1fr 1fr), varied image ratios (4:3 next to 16:9), large empty zones.
- No three equal feature cards in a row. Use asymmetric grid, 2-column, or bento.
- Each layout family (3-col cards, split text+image, full-width quote, etc.) appears at most ONCE per page. 8 sections = at least 4 different layouts.
- Max 2 consecutive image+text zigzag sections. Break with a full-width, stacked, or grid section.
- Bento: exactly as many cells as items, no empty cells. At least 2-3 cells with real visual variation (image, tinted bg, pattern), not all plain white text cards.
- Section header: headline stacked above body. No "big headline left + tiny paragraph floating right".
- Content per section: headline <= 8 words, sub-paragraph <= 25 words, plus one visual or one CTA.
- More than 5 list items: use grouped columns, card grid, tabs/accordion, or scroll-snap pills, not a long bulleted list. No hairline under every row of a spec table.

## 5. Hero Rules

- Must fit the first viewport: headline max 2 lines, subtext max 20 words and 4 lines, CTA visible without scrolling.
- Top padding max 6rem on desktop. Do not let content float halfway down.
- Max 4 text elements: optional eyebrow, headline, subtext, CTAs (1 primary + max 1 secondary).
- Not in the hero: tagline under CTAs, "trusted by" strip, pricing teaser, bullet list, avatar row. Put the logo wall in its own section directly below.
- Hero needs a real visual (photo or real screenshot). Text + gradient blob is a placeholder.

## 6. Components and States

Buttons:
- Text contrast at least 4.5:1 (3:1 for 18px+ text). No white text on white/transparent buttons. Ghost buttons on photos need a scrim or border.
- CTA label on one line at desktop. Max 3 words, ideally 1-2.
- One label per intent: pick "Contact" OR "Let's talk", not both. Same for signup and "view work" labels.
- Hover: subtle color/shadow shift. Active: translateY(1px) or scale(0.98).
- Focus: visible :focus-visible outline/ring, never removed.

Cards and shape:
- Use cards only when elevation shows real hierarchy. Otherwise group with spacing or a single divider.
- One corner-radius system: all sharp (0), all soft (12-16px), or pill for interactive. If mixed, a written rule followed everywhere.

Navigation:
- One line at desktop (1024px+). Shorten labels, drop items, or use a menu button.
- Height 64-72px, max 80px.

Forms:
- Label above input, helper text, error text below input. Never placeholder as label.
- Inputs, placeholders, labels, focus rings all pass WCAG AA contrast.

States: provide loading (skeleton shaped like the content, not a spinner), empty and error states where data or forms exist.

Quotes: max 3 lines, attribution = name + role (+ company). Curly quotes or none.

Logo walls: real SVG logos (e.g. cdn.simpleicons.org/{slug}) or a simple made-up monogram SVG for invented brands. Logos only, no category labels under them. Works in both themes.

## 7. Images

- Use an image tool if available. Otherwise https://picsum.photos/seed/{descriptive-seed}/{w}/{h} or real brand images.
- If none possible, leave labeled placeholder comments and tell the user which images are needed.
- Even minimal sites need 2-3 real images.
- Banned: fake product UI built from divs (fake dashboard, fake terminal, fake task list), hand-drawn decorative SVG illustrations, tag pills on top of photos, fake photo-credit captions.

## 8. Motion

- Every animation needs a reason: hierarchy, storytelling, feedback, or state change. "It looks cool" is not a reason.
- MOTION 1-3: hover/active only. 4-7: CSS transitions about 0.3s cubic-bezier(0.16, 1, 0.3, 1), staggered entry. 8-10: scroll-driven reveals, parallax.
- If MOTION > 4, the page must actually move (hero entry, scroll reveal, button hover). Can't build it well? Lower the dial and ship static.
- Animate only transform and opacity. Never top/left/width/height.
- No scroll event listeners. Use IntersectionObserver or CSS animation-timeline.
- Max one marquee per page. Not every card needs an infinite loop.
- Respect prefers-reduced-motion: disable loops, parallax and scroll effects under reduce.
- Grain/noise only on a fixed, pointer-events: none overlay. No custom cursors.

## 9. Copy and Content

- ZERO em-dashes (—) or en-dashes (–) anywhere visible. Use a period, comma, colon, parentheses, or a plain hyphen (-). Ranges: 2018-2026.
- No filler words: elevate, seamless, unleash, next-gen, revolutionize. Use concrete verbs.
- No generic names (John Doe, Acme, Nexus, SmartFlow). Invent realistic, locale-fitting names.
- No fake-precise or fake-perfect numbers (99.99%, 4.1x) unless from the brief or marked as sample.
- One copy tone per page. Re-read every visible string; rewrite anything broken, vague, or "cute AI". Boring and clear beats clever and wrong.
- Emojis: none unless the brief is playful/social.

## 10. AI-Slop Clichés (Banned)

- Eyebrows (small uppercase tracked labels above headings): max 1 per 3 sections, hero counts. Usually just drop them.
- Section numbers as labels: "01 / INDEX", "002 · Capabilities", "Step 1 / Stage 2". Use the real step name.
- Version labels in hero (v2.0, BETA, EARLY ACCESS) unless it is a launch. Version/build strings in footers.
- Scroll cues ("Scroll to explore", mouse-wheel icons).
- Decorative colored status dots before nav items, badges, list rows.
- Middle dot (·) chains: max one per line.
- Hero bottom text strips like "DESIGN · BUILD · SHIP".
- Locale/time/weather strips ("Lisbon 14:23 · 18°C") unless place matters.
- Poetic section labels: "Field notes", "Quietly trusted by", "On our desks". Use plain labels.
- Rotated vertical text, decorative crosshair/grid lines, <br>-split italic headlines.
- Progress bars with gray filled tracks as comparison visuals.
- Glassmorphism on everything. If used: 1px light inner border, subtle inset highlight, solid fallback.
- Arbitrary z-index spam: use a small defined layer scale.

## 11. Redesigns

- Decide mode: preserve (evolve the brand) or overhaul (new visuals, same content). Ask once if unclear.
- Audit first: brand colors, fonts, nav, page structure, what works.
- Never silently change URLs, nav labels, form field names, logo, legal text. Keep existing a11y wins.
- Lever order: typography, spacing, color cleanup, motion, hero rework, full section replacement.

## 12. Accessibility and Performance Musts

- Semantic HTML: header, nav, main, section, footer; one h1; logical heading order.
- Alt text on meaningful images; empty alt on decorative ones.
- WCAG AA contrast everywhere (4.5:1 body, 3:1 large text), in both themes.
- Full keyboard use with visible focus.
- Reserve image space (width/height or aspect-ratio) to avoid layout shift. Preload the hero image, lazy-load the rest.
- Targets: LCP < 2.5s, INP < 200ms, CLS < 0.1.

## 13. Pre-Flight Checklist

Do not finish until every item passes:
- [ ] Design read line written; dials chosen from the brief.
- [ ] Zero em/en dashes in visible text.
- [ ] One theme, one accent, one gray family, one radius system.
- [ ] No Inter/serif/purple/beige-brass default without a brief reason.
- [ ] Hero: fits viewport, headline <= 2 lines, subtext <= 20 words, max 4 text elements, top padding <= 6rem, real visual.
- [ ] Eyebrows <= ceil(sections / 3).
- [ ] No three equal cards; no layout family repeated; max 2 zigzags in a row.
- [ ] Bento: exact cell count, visual variety.
- [ ] Nav one line, <= 80px tall.
- [ ] Buttons: contrast OK, one line, one label per intent, hover/active/focus states.
- [ ] Forms: labels above, AA contrast, no placeholder-labels.
- [ ] Logo wall below hero, real logos, no labels.
- [ ] Real images; no div-made fake screenshots.
- [ ] Every animation motivated; max one marquee; reduced-motion honored; only transform/opacity animated.
- [ ] Every multi-column layout collapses under 768px; min-height 100dvh for full hero.
- [ ] Copy re-read: no filler verbs, generic names, fake stats, or slop labels from section 10.
- [ ] Semantic HTML, alt text, keyboard focus visible, dark mode checked.
