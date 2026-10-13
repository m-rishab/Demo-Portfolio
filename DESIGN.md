# Nishita Chauhan — Portfolio Design System

Single self-contained `index.html`. No build step. CDN libs pinned:
GSAP 3.12.5 + ScrollTrigger 3.12.5 (cdnjs), Lenis 1.1.13 (jsDelivr).
Google Fonts: Fraunces (variable, wght + SOFT + WONK), Inter (400/500/600/700),
JetBrains Mono (400/500). `no localStorage`.

## 1. Palette — 5 named colours

| Token | Dark (default) | Light | Role |
|---|---|---|---|
| **Ink** | `#0B0E17` | `#0B0E17` | Dark canvas / primary text on light |
| **Fog** | `#E9EBE6` | `#E9EBE6` | Light canvas / primary text on dark |
| **Ultramarine** | `#3B54F0` | `#2A3FD6` | Primary accent: links, active state, series A, focus ring |
| **Signal** | `#CDFF34` | `#9FD800` (text-safe) | Live/highlight: metric ticks, hover, "current", series B |
| **Mist** | `#7C87A0` | `#5B657A` | Muted text, gridlines, borders, series C |

Derived surfaces (not "new colours", alpha/tints of the above):
- `--surface-1` = Ink lightened → `#141A28` (dark) / `#DFE2DC` (light) — raised cards
- `--surface-2` = Ink lightened more → `#1D2436` (dark) / `#D3D7CF` (light) — insets
- Chart series D/E: `#E4572E` (vermilion), `#2FB7A6` (teal) — data-viz only, never UI chrome.

Rule: **no purple, no cream/terracotta.** Dark is the default; a `data-theme="light"` toggle
swaps canvas, surface and text tokens only — accents stay constant so charts read the same.

Banned-word check: all five names are distinctive and ownable (not "primary/secondary").

## 2. Typography — two faces + one utility

- **Display: Fraunces** (variable; WONK axis engaged for headlines, optical size large).
  Editorial, high-character — instantly separates from SaaS grotesque. Tracking -0.02em,
  tight leading (0.95–1.05). Used for H1/H2, big numbers' labels, section eyebrows.
- **Text: Inter** — neutral, legible UI/body face. `font-variant-numeric: tabular-nums` for all data.
- **Utility: JetBrains Mono** — metric values, units, tags, timeline dates, chart labels only.
  This is the "technical" bridge that makes the editorial serif read as a data desk, not a magazine.

Scale (clamp, fluid): display `clamp(2.75rem, 9vw, 7rem)` / h2 `clamp(2rem,4.5vw,3.5rem)` /
body `1.0625rem` / mono-label `0.75rem` uppercase `0.08em`.

## 3. Section rhythm — alternating surfaces

Sections alternate **Ink ⇄ Fog** so boundaries are always obvious; each also gets its own
layout *shape*, not just a colour swap.

| # | Section | Surface | Layout shape | Signature move |
|---|---|---|---|---|
| 0 | Loader | Ink | full-screen | counter 0→100, masked wipe reveal |
| 1 | Hero | Ink | 12-col, text left / interaction right→full | self-organising data cloud |
| 2 | About | Fog | asymmetric 5/7, portrait col | 4 mini-chart metrics count up |
| 3 | What I do | Ink-1 | 4-col capability rails | each block a tiny live SVG |
| 4 | Selected work | Ink | **pinned horizontal filmstrip** (desktop) / native swipe (mobile) | filter + case-study drawer |
| 5 | Experience | Fog | vertical spine, alternating cards | scroll-scrubbed progress spine |
| 6 | Toolkit | Ink-1 | grouped bars + radial skill map | bars grow on enter |
| 7 | Education & certs | Fog | 2-col: degrees / cert cards | cert chips lift |
| 8 | Contact | Ink | centred, huge headline | magnetic buttons + mailto form |

## 4. Hero interaction — the one place we spend boldness

~140 SVG points that idle as a loose cloud, then **spring-settle onto a rising trend line**
(spring easing, staggered by x). Cursor = a soft radial repulsion field; the ~6 nearest points
light up Signal and draw faint k-NN connecting lines (a live "signal detect"). On
`prefers-reduced-motion`, points settle instantly with no repulsion.

## 5. Motion inventory (GSAP + ScrollTrigger + Lenis on one ticker)

- Lenis drives ScrollTrigger via `lenis.on('scroll', ScrollTrigger.update)`; single rAF ticker.
- Loader count → hero split-text (word/char clip-up) → cloud settle (orchestrated timeline).
- Pinned horizontal scroll for Selected work (desktop only, `matchMedia`).
- Count-ups, SVG line `stroke-dashoffset` draw, bars `scaleY`, donut `stroke-dasharray`.
- Section transitions via clip-path wipe; card parallax (y 8–12%); custom cursor (ring → label).
- Everything gated behind `gsap.matchMedia()` + reduced-motion off-switch.

## 6. Why this isn't a generic portfolio

1. Hero is an ownable interactive idea (self-organising data), not a gradient blob.
2. Editorial serif × mono data labels = a "data journalism desk" voice, not a template.
3. Every metric is a real mini-chart, not a number in a rounded card.
4. The site is *usable*: sticky nav + active-section indicator + filterable work + case drawers
   → a hiring manager gets proof in 30 seconds.
5. Work is a pinned filmstrip, not a 3-col SaaS card grid.
6. Disciplined 5-colour ink/fog/ultramarine/signal/mist system; boldness confined to the hero.

## 7. Stage plan

- Stage 1: loader, nav (+active indicator, progress bar), hero, about, 4 metrics.
- Stage 2: What I do, Selected work (filter All/BI/AI/ML/Automation), 6 case studies.
- Stage 3: experience timeline, toolkit, education & certifications.
- Stage 4: contact, footer, a11y/responsive/perf polish, back-to-top.

## 8. Open [EDIT ME] items (Stage 0)

- Confirm/adjust the five hexes and the Fraunces + Inter + JetBrains Mono pairing.
- Portrait image for About (real asset or refined placeholder).
- Project 6 content ("One more project I will describe later").
- GitHub username (profile link says `github.com/nishitachauhan`; DataSentinal repo is `m-rishab/DataSentinal` — confirm both).
- LinkedIn confirm: `linkedin.com/in/nishitachauhan`.
