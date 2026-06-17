# Krath Veil Design System (Web)

How the Krath Veil website looks and behaves. Hand this to a designer or an AI and they should reproduce the feel exactly.

## Essence
Combat-credible defence-tech. Dark, tactical, premium, restrained. It should read like classified hardware, not a SaaS landing page. Confidence comes from what is withheld. Reference peers: **himeratech.com** (tone, product-forward), **beijan.com** (minimal, bracketed sections).

## Palette (gold on black, gold is the only accent)
| Token | Hex | Use |
| --- | --- | --- |
| `--bg` | `#000000` | Canvas (true OLED black) |
| `--bg-2` | `#0C0C0E` | Cards, raised surfaces |
| `--gold` | `#C9B06B` | The accent: logo, numbers, highlights, buttons, links |
| `--gold-bright` | `#E6D29A` | Hover / active gold |
| `--gold-dark` | `#8A7440` | Muted gold, small labels, index numbers |
| `--text` | `#F3F0E9` | Warm off-white, headings + strong text |
| `--muted` | `#9D998E` | Body, captions |
| `--dim` | `rgba(243,240,233,0.60)` | Secondary body |
| `--line` | `rgba(255,255,255,0.10)` | Borders |
| `--line-2` | `rgba(255,255,255,0.06)` | Hairline dividers |
| `--line-gold` | `rgba(201,176,107,0.28)` | Gold hairlines, tag borders |

Gold is the **only** accent. No second colour. No red/blue/green (a tactical-green idea was explicitly rejected).

## Type
- **Display / UI:** `Space Grotesk` (700 for headings, 500 for labels). Headings are UPPERCASE, tight tracking.
- **Body:** `Inter` (400/500/600).
- **Hero wordmark:** the geometric **KRATH VEIL logo** (transparent gold PNG), not text.
- **Section headings:** big `clamp()` sizes, all-caps, `font-weight: 700`.
- **Kickers / labels / HUD:** Space Grotesk, ~11px, `letter-spacing: 0.18-0.24em`, uppercase, gold or muted.

## Layout and shape
- **Sharp 90-degree corners everywhere.** No rounded corners.
- Single centred column, `max-width ~940px` (home) / `760px` (founder page), generous padding via `clamp()`.
- **Hairline dividers** between sections; lots of negative space.
- **Bracketed section system:** kicker `[1] THE FABRIC` + big H2 + right-aligned index `[ 01 ]`. Products and tiles use slash numbers `/01`.
- **Mobile-first.** Most traffic is phones (QR + bio links). Grids collapse to 1 column; tap targets are large; primary buttons go full-width on small screens.

## Signature motifs
- **HUD micro-labels:** small tracked caps scattered as instrument readouts, e.g. `17.54455 N  78.57554 E / AES-256 / MESH ONLINE`.
- **Radar hero:** giant gold logo over concentric scope rings with a rotating sweep, expanding signal-ripples, and a periodic **glitch burst** (channel-split slices). The logo is transparent so the animation shows *through* it. Never box the logo on an opaque panel.
- **Animated mesh diagrams:** gold nodes + dashed animated links + range rings (the product showpiece).
- **Advantage grid:** 2-up, hairline-divided, each with a distinct line icon (lock, mesh, reticle, broadcast, shield, waveform, flag, phone) + bold title + one line.
- **Stat band:** big gold numbers + tiny caps labels.
- **Interactive tiles** (Products, Looking for): bordered cards on `--bg-2` that on hover lift, gain a gold border, wipe a 2px gold bar across the top, and slide a `→`. Clickable tiles open pre-filled emails.
- **Gold CTA band:** a full-bleed `--gold` section with ink text and ink buttons. The one place the page inverts.
- **Mission footer:** giant outline (`-webkit-text-stroke`) "DOMINATE. CONNECT. DISAPPEAR."

## Motion and interaction
- Scroll-reveal (fade + 16px rise) on sections via IntersectionObserver.
- Hover micro-interactions: lifts, gold borders, arrow slides, a quick gold **glitch** on the name/wordmark.
- **Hover effects are gated behind `@media (hover: hover) and (pointer: fine)`** so touch devices never get stuck-hover jank.
- Always honour `prefers-reduced-motion` (kill glitch, sweep, ripples, transforms).
- Motion is referential (radar sweep, OLED dot-matrix, signal ripples, signal glitch), never decorative.

## Voice and copy
- Declarative, confident, short. Tagline: **Dominate. Connect. Disappear.**
- Pitched at investors and military/procurement, not the general public (assume the reader knows EW, iDEX/ADITI, ATAK).
- No marketing fluff (no "revolutionary", "cutting-edge", "next-generation", "world-class").

## Hard rules
- **Never use em dashes (—) or en dashes (–). Anywhere.** Use commas, colons, or "to". Hyphens are fine.
- Gold is the only accent colour.
- Sharp corners only.
- Mobile-first; gate hover behind `@media (hover: hover)`.
- Logo floats transparent on black, never inside an opaque box.
- It is a public site: no "Confidential" / classification labels in the live UI.
- Self-contained static HTML: inline CSS + JS, no build step. Fonts via Google Fonts (Space Grotesk + Inter); otherwise no dependencies.

## Stack
Single-page `index.html` + `samarth.html` (founder page), deployed on GitHub Pages (`CNAME` = krathveil.com). Product imagery is cinematic gold-on-black node photography on a pure-black backdrop.
