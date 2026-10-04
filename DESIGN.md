---
version: alpha
colors:
  primary: "#E20750"
  heading: "#231A5C"
  text: "#2B2533"
  muted: "#696475"
  canvas: "#F6F6F8"
  surface: "#FFFFFF"
typography:
  ui:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif"
rounded:
  control: "8px"
  panel: "12px"
spacing:
  unit: "8px"
components:
  button:
    padding: "10px 16px"
  panel:
    padding: "24px"
---

# Customer order design

## Overview

This is a Meesho DICE 3.0 customer order prototype. It should feel like a familiar shopping app: the product, the money due, and the next action are easy to find. The visual reference is the supplied DICE presentation's navy and pink identity, applied to a restrained order screen.

The signature is the plain ₹20 now / ₹279 on receipt breakdown beside the actual kurti photo. Preserve the existing ₹299 order, ₹20 token, ₹5 next-order reward, pickup timeline, and IVR outcomes. Prototype navigation stays in a quiet, clearly labelled strip rather than leading the product screen.

## Colors

Runtime token ownership is in `styles.css`. Its foundation is copied from the sibling apps' shared palette. `DESIGN.md` documents those values and does not generate CSS. Change both together when a palette decision changes.

| Role | Runtime token | Value |
| --- | --- | --- |
| Primary action | `--acc` | `#E20750` |
| Headings and focus | `--navy`, `--focus` | `#231A5C` |
| Body text | `--ink` | `#2B2533` |
| Secondary text | `--muted` | `#696475` |
| Page canvas | `--bg` | `#F6F6F8` |
| Panels | `--surface` | `#FFFFFF` |

Pink identifies the main action. Navy carries hierarchy. Success and caution use the foundation's semantic colors with visible text. Customer chat replies use the local `--chat-reply` token; that color never defines payment or delivery status.

## Typography

`--font-ui` owns the system font stack. Use the same family throughout. Headings are navy and moderately sized; amounts use tabular numbers. Secondary copy stays readable and wraps naturally. Avoid remote font requests and decorative display faces.

## Layout

The current task appears before the order summary in DOM order. On desktop, the task and summary sit side by side; below 800px, they stack. Below 640px, prototype step controls use two columns. At 320px, every action and amount remains in the document's natural flow. The kurti image reserves 88 × 112px and uses `object-fit: contain`.

## Elevation & Depth

Use flat white surfaces and fine borders. The payment explanation and delivery call use quiet tinted backgrounds. No shadows, gradients, glass effects, decorative emoji, or floating elements.

## Shapes

`--radius-control` is 8px and `--radius-panel` is 12px. Chat bubble corners distinguish incoming and outgoing messages. Circles only mark the actual delivery timeline.

## Components

The user-supplied Meesho logo is stored unchanged at `assets/meesho-logo.png` and used in the header and favicon. The shared `.brand-logo` rule in `styles.css` reserves a 44px square on desktop and 40px on phones, with `alt="Meesho"` and preserved image proportions. The adjacent descriptor identifies this prototype.

The foundation in `styles.css` owns buttons, panels, tables, focus, semantic notices, responsive shell, and global scrollbars. Customer-specific rules extend that foundation for the payment block, chat, delivery timeline, summary, and IVR options.

Use native buttons for actions. Selected prototype steps expose `aria-current`; IVR options expose `aria-pressed`. Focus uses a visible navy outline. Feedback stays within the relevant screen. The existing state object, amounts, data arrays, and handlers remain the behavior authority in `index.html`.

## Do's and Don'ts

- Keep one primary action per decision, with supporting text immediately beside it.
- Keep the current token, amount due, and next-order credit visible in the summary.
- Preserve the original store, distance, dates, pickup code, and simulated outcomes; add no invented store details.
- Keep all four prototype steps reachable.
- Do not add a payment provider, new state transitions, dependencies, or extra customer workflows.
- Do not present this static prototype as a live transaction.
