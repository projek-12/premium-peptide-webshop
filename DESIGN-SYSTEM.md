# Design system specification

- **Status:** Draft v0.1 — awaiting owner review. Nothing in this document is final until the owner approves it.
- **Date:** 2026-11-24
- **Phase:** 3 (Design system)
- **Builds on:** `docs/design/DESIGN-SYSTEM-BRIEF.md` (kept unchanged as the original direction). Where the two differ, this document takes precedence once approved. Differences are listed in section 2.5.
- **Architecture context:** ADR-001 (approved): Next.js App Router, strict TypeScript, CSS Modules, CSS custom properties, no UI or animation framework.

This is documentation only. It contains no application code. Token names and CSS in this file are illustrative specification, not source files to be copied unreviewed.

## 1. Direction and principles

Premium editorial commerce: calm, precise, credible, tactile, and product-led. The storefront is a product catalogue, not an agency portfolio. The visual reference studio is broad inspiration only; no wording, assets, or layouts are copied.

1. **Light theme only.** No dark theme, no theme switcher. Declare `color-scheme: light` on the root and add `<meta name="color-scheme" content="light">`. No `prefers-color-scheme: dark` rules. System dark mode must not invert the design.
2. **Restraint.** Generous whitespace, a strong grid, few colours, hairline rules. Avoid gradients, drop-shadow stacks, heavy rounding, decorative clutter, and dark sections.
3. **Honest information design.** Verification state is always visible and always text, never colour alone. Unknown is shown as unknown.
4. **Catalogue first.** Navigation, product cards, and documentation status are the primary patterns.
5. **No commerce UI.** While commerce is disabled there is no cart, checkout, account, price, "add to cart", or "buy" control anywhere in the design.
6. **No unverified claims.** The design system supplies containers for facts; it never supplies the facts (see section 11).

## 2. Colour

### 2.1 Palette

| Token | Value | Role |
|---|---|---|
| `--color-ivory` | `#F6F5F1` | Page background (the "ivory" of the approved direction) |
| `--color-white` | `#FFFFFF` | Raised surfaces: cards, form fields, menus |
| `--color-stone` | `#ECEAE3` | Subtle panels, image placeholders, table stripes |
| `--color-charcoal` | `#171916` | Primary text, primary button, focus ring |
| `--color-charcoal-soft` | `#5A5D56` | Secondary text, metadata |
| `--color-olive` | `#737A60` | Accent for large text, rules, icons, and graphics only. Not for normal-size text. |
| `--color-olive-strong` | `#565D45` | Olive for text links, button hover, verified-state text |
| `--color-hairline` | `#E4E2DA` | Decorative dividers only |
| `--color-border-strong` | `#7C7F76` | Borders of interactive controls |
| `--color-error` | `#9B2C2C` | Form error text and error borders |

The palette is ivory, charcoal, muted olive, and white, as directed. `--color-stone`, `--color-hairline`, `--color-border-strong`, `--color-charcoal-soft`, `--color-olive-strong`, and `--color-error` are supporting tokens that exist to meet contrast and state requirements.

### 2.2 Contrast ratios

Ratios were calculated with the WCAG 2.x relative-luminance formula. Targets: 4.5:1 for normal text, 3:1 for large text (at least 24 px, or 18.66 px bold) and for user-interface boundaries and graphics.

| Foreground on background | Ratio | Permitted use |
|---|---|---|
| Charcoal on ivory | 16.22:1 | All text |
| Charcoal on white | 17.69:1 | All text |
| Charcoal on stone | 14.70:1 | All text |
| Ivory on charcoal | 16.22:1 | Primary button label |
| Charcoal-soft on ivory | 6.14:1 | Secondary text, metadata |
| Charcoal-soft on white | 6.70:1 | Secondary text, metadata |
| Charcoal-soft on stone | 5.56:1 | Secondary text, metadata |
| Olive-strong on ivory | 6.32:1 | Text, links, badge text |
| Olive-strong on white | 6.89:1 | Text, links, badge text |
| Olive-strong on stone | 5.72:1 | Text, links, badge text |
| Ivory on olive-strong | 6.32:1 | Button hover label |
| Error on ivory | 6.90:1 | Error text |
| Error on white | 7.53:1 | Error text |
| Border-strong on ivory | 3.73:1 | Control borders (meets 3:1) |
| Border-strong on white | 4.07:1 | Control borders (meets 3:1) |
| Border-strong on stone | 3.38:1 | Control borders (meets 3:1) |
| Olive on ivory | 4.11:1 | Large text, icons, rules only |
| Olive on white | 4.49:1 | Large text, icons, rules only (just under 4.5) |
| Olive on stone | 3.73:1 | Large text, icons, rules only |
| Hairline on ivory | 1.19:1 | Decoration only; never the sole indicator of a boundary |

Rules:
- Do not set normal-size text in `--color-olive`, and do not place white or ivory text on `--color-olive`.
- Re-check any new combination before use. Any contrast change must update this table.
- Overlaying text on photographs is not permitted by default. If an exception is approved, it needs a solid or scrim backing that meets 4.5:1.

### 2.3 Colour usage rules
- Body and headings: charcoal. Metadata and captions: charcoal-soft.
- Page background: ivory. Cards and fields: white. Quiet panels and image placeholders: stone.
- Colour is never the only carrier of meaning. Status, error, and selection always have text and, where useful, a shape or icon.
- Olive is an accent and used sparingly: rules, small icons, large numerals, and the hover state of primary actions.

### 2.4 Verification and status colours
Status badges use the palette only (no red/amber/green traffic-light scheme, which would imply safety or approval). See section 6.6.

### 2.5 Differences from `DESIGN-SYSTEM-BRIEF.md`
| Brief | This specification | Reason |
|---|---|---|
| Secondary text `#686B63` | `#5A5D56` | 4.51:1 on stone was marginal; 5.56:1 gives margin |
| Single olive `#737A60` | Olive (accent only) plus olive-strong `#565D45` | Olive fails 4.5:1 for normal text on ivory (4.11:1) and on white (4.49:1) |
| Hairline `#E4E2DA` for borders | Hairline decorative; `#7C7F76` for control borders | Hairline is 1.19:1 on ivory, below the 3:1 needed for controls |
| No error colour | `#9B2C2C` | Form errors need a colour that passes 4.5:1 |
| "Warm paper", "Primary ink" | Named ivory, charcoal | Matches the approved direction wording |

Owner confirmation that near-black `#171916` is acceptable as "charcoal" is requested (open question 12).

## 3. Typography

### 3.1 Roles
- **Display / editorial:** a high-quality serif for page titles, section headings, and product names.
- **Interface / body:** a highly legible sans-serif for body, navigation, buttons, forms, and cards.
- **Metadata:** a restrained mono or tabular-figure sans, used sparingly for labels, status badges, and identifiers.

### 3.2 Font licensing requirements
No typeface is selected yet. Selection is an owner decision and is outstanding (open question 11). Any typeface must satisfy all of the following before use:
1. A licence that explicitly permits web embedding and self-hosting for the intended traffic and any needed languages.
2. The licence text and source are recorded in the repository (for example in `docs/design/FONT-LICENSES.md`) with licence type, version, date, and purchaser or licensor.
3. Self-hosted font files, with no third-party font CDN, so visitor data is not sent to a font host.
4. Subsetting is permitted if subsetting is used.
5. No fonts sourced from unlicensed websites, converted desktop fonts, or font-extraction tools.
6. `font-display: swap` (or `optional`) and a metrics-matched fallback to limit layout shift.
7. Support for the characters needed by the launch language(s). English is assumed in this document until confirmed (open question 9).

Open-licence families (for example, families published under the SIL Open Font License) may be considered. Any candidate must have its licence read and recorded by the project owner or a delegate. This document does not certify any licence.

### 3.3 Fallback stacks
Used until fonts are selected and as the fallback afterwards.

| Token | Stack |
|---|---|
| `--font-display` | `Georgia, "Times New Roman", serif` |
| `--font-sans` | `system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif` |
| `--font-mono` | `ui-monospace, "SFMono-Regular", Menlo, Consolas, monospace` |

### 3.4 Type scale
Fluid sizes interpolate linearly between a 320 px and a 1440 px viewport. The `clamp()` values below are derived from those anchors. **They must be tested at 320 px width and at 200%/400% zoom before approval**, as required by the brief.

| Token | Min (320 px) | Max (1440 px) | `clamp()` | Line height | Weight / tracking | Font |
|---|---|---|---|---|---|---|
| `--text-display` | 40 px | 80 px | `clamp(2.5rem, 1.786rem + 3.571vw, 5rem)` | 1.05 | 400, -0.02em | display |
| `--text-h1` | 34 px | 56 px | `clamp(2.125rem, 1.732rem + 1.964vw, 3.5rem)` | 1.1 | 400, -0.015em | display |
| `--text-h2` | 28 px | 40 px | `clamp(1.75rem, 1.536rem + 1.071vw, 2.5rem)` | 1.15 | 400, -0.01em | display |
| `--text-h3` | 22 px | 28 px | `clamp(1.375rem, 1.268rem + 0.5357vw, 1.75rem)` | 1.25 | 400, -0.005em | display |
| `--text-h4` | 18 px | 20 px | `clamp(1.125rem, 1.089rem + 0.1786vw, 1.25rem)` | 1.3 | 600, 0 | sans |
| `--text-lead` | 18 px | 20 px | `clamp(1.125rem, 1.089rem + 0.1786vw, 1.25rem)` | 1.5 | 400, 0 | sans |
| `--text-body` | 16 px | 16 px | `1rem` | 1.6 | 400, 0 | sans |
| `--text-small` | 14 px | 14 px | `0.875rem` | 1.5 | 400, 0 | sans |
| `--text-meta` | 12 px | 12 px | `0.75rem` | 1.4 | 500, +0.06em, uppercase | mono |

Rules:
- Body text never below 16 px. Metadata never below 12 px and used for short labels only, never for paragraphs.
- Prose measure: 60–75 characters (`max-width: 68ch` as the default).
- Use `rem` units so user font-size settings are respected. Never disable browser zoom.
- Headings follow document structure, not visual size. One `h1` per page. Visual size is controlled by classes.
- Left-aligned text. No justified text. No all-caps for anything longer than a short label.
- Use tabular figures (`font-variant-numeric: tabular-nums`) for identifiers and tabular data.

## 4. Spacing

4 px base unit.

| Token | Value |
|---|---|
| `--space-0` | 0 |
| `--space-1` | 4 px |
| `--space-2` | 8 px |
| `--space-3` | 12 px |
| `--space-4` | 16 px |
| `--space-5` | 24 px |
| `--space-6` | 32 px |
| `--space-7` | 48 px |
| `--space-8` | 64 px |
| `--space-9` | 96 px |
| `--space-10` | 128 px |

Section vertical rhythm (padding above and below a section): mobile `--space-8`, tablet `--space-9`, desktop `--space-10`. Use component-internal spacing from `--space-2` to `--space-5`.

Other tokens:
- `--radius-sm: 2px` for controls, badges, and cards. No radius above 4 px. No pill shapes.
- `--border-width: 1px`.
- Minimum interactive target: 44 × 44 CSS px for touch-primary controls; never below 24 × 24 CSS px, including spacing.

## 5. Breakpoints and grid

Mobile-first (`min-width` queries). The design is supported from a 320 px viewport upward, with no horizontal scrolling at 320 px.

| Name | Range | Columns | Gutter | Side margin |
|---|---|---|---|---|
| Mobile | 0–639 px | 4 | 16 px | 20 px |
| Tablet | 640–1023 px | 8 | 24 px | 32 px |
| Desktop | 1024–1439 px | 12 | 32 px | 48 px |
| Wide | 1440 px and above | 12 | 32 px | 48 px minimum; content centred |

Tokens: `--bp-tablet: 640px`, `--bp-desktop: 1024px`, `--bp-wide: 1440px`.

Container:
- Content box maximum width: 1280 px, centred, with the side margins above.
- Prose blocks: maximum 68ch regardless of container width.
- Full-bleed imagery is allowed; its text content must still align to the grid.

Product grid: 1 column on mobile, 2 on tablet, 3 on desktop, 4 on wide.

Responsive rules:
- Layouts collapse in source order. DOM order equals reading order and tab order.
- Reflow at 320 px width and at 400% zoom without two-dimensional scrolling (tables and code excepted, in their own scroll container).
- Do not rely on hover for any information or action.
- Test at 320, 390, 768, 1024, 1280, and 1920 px.

## 6. Components

Each component below is specified for appearance, states, and accessibility. No component includes pricing, cart, or checkout elements.

### 6.1 Header
- Height: 64 px mobile, 72 px tablet, 80 px desktop. Background ivory (solid, no transparency or blur). A 1 px hairline bottom rule.
- Contents, in DOM order: skip link, brand wordmark, primary navigation. Layout: wordmark at the start, navigation at the end on desktop; wordmark and a "Menu" button on mobile.
- **Brand wordmark:** the brand name is not decided (open question 1). Until it is, use a neutral text placeholder in `--font-display`, easy to replace, linking to `/`. No logo, mark, or tagline is invented.
- **Skip link:** first focusable element, labelled "Skip to main content", visually hidden until focused, then shown at top start with charcoal background and ivory text.
- **Not sticky** in v0.1. Sticky headers can obscure focused elements (WCAG 2.2 criterion 2.4.11). If the owner wants a sticky header, it requires `scroll-padding-top` equal to the header height and a re-test. This is an open item.
- **Excluded while commerce is disabled:** cart, account, wishlist, currency, and region selectors.
- **Reserved:** a catalogue search entry point is anticipated by `CLAUDE.md` but is a Phase 5 decision and is not part of the Phase 4 header.
- Language switcher: not included. English is assumed pending confirmation.

### 6.2 Navigation
- Provisional items, derived from the routes in `docs/architecture/OVERVIEW.md`: Shop, Research, Quality, About, Contact. Labels are provisional and must not carry claims. The "Quality" label and page must follow the documentation rules in `docs/content/PRODUCT-DATA-GUIDE.md`.
- Container: `<nav aria-label="Primary">` containing a list of links.
- Link style: `--text-small` or `--text-body`, charcoal, no underline by default; hover adds a 1 px underline with `text-underline-offset: 0.3em`; current page uses `aria-current="page"` plus a 1 px olive rule below the label (non-colour cue: a visible underline plus the attribute).
- Desktop: horizontal list, links with at least 44 px height and `--space-5` between them.
- Tablet and mobile (below 1024 px): a "Menu" button (visible text label, not icon-only) with `aria-expanded` and `aria-controls`. The panel is a non-modal disclosure below the header, ivory background, links stacked at minimum 48 px height. Escape closes the panel and returns focus to the button. Opening the panel moves no focus unexpectedly. Focus moves naturally through the links in order.
- No-JavaScript baseline: the navigation list is rendered visible and stacked, so every link is reachable without scripting.
- Footer navigation repeats the primary items and adds contact and policy links when those pages exist. Footer content must not be invented (contact details, addresses, and registration numbers are supplied by the owner).

### 6.3 Buttons
| Variant | Default | Hover | Use |
|---|---|---|---|
| Primary | Charcoal background, ivory label | Olive-strong background, ivory label | One primary action per view area |
| Secondary | Transparent, 1 px charcoal border, charcoal label | Stone background, charcoal border | Supporting actions |
| Tertiary (text) | No border, charcoal label, 1 px underline | 2 px underline | Low-emphasis actions |

Specification:
- Sizes: default minimum height 44 px, large 52 px. Horizontal padding `--space-5`. Radius `--radius-sm`.
- Label: `--text-body` size, weight 500, sentence case, no uppercase.
- Focus: see section 8.
- Active (pressed): primary returns to the charcoal background; secondary uses the stone background with a charcoal border. No movement or scaling.
- Disabled: use `aria-disabled="true"` where the control must stay discoverable, with a visible text reason nearby. Disabled controls are exempt from contrast rules but must remain legible (charcoal-soft text on stone).
- Elements: use `<button>` for actions and `<a>` for navigation. Never a `<div>` with a click handler.
- **Permitted labels (examples):** "Browse catalogue", "View details", "View documentation status", "Read the research", "Contact".
- **Prohibited while commerce is disabled:** "Buy now", "Add to cart", "Checkout", "Order", "Pay", "Reserve", and any label that implies a transaction is possible.

### 6.4 Links
- Inline links: olive-strong text with a permanent 1 px underline (`text-underline-offset: 0.2em`). Link colour alone is not sufficient to distinguish links from body text (olive-strong against charcoal is below 3:1), so the underline is mandatory.
- Hover: underline thickens to 2 px. Visited links keep the same style.
- External links: a visible indication ("opens in a new tab" in text or an icon with an accessible name) only if a new tab is used; prefer same-tab navigation. Use `rel="noopener"` for any `target="_blank"`.
- Link text must make sense out of context. Avoid "click here" and bare "read more".
- Link target size: for links in running text, the inline exception applies; stand-alone links meet the 44 px target.

### 6.5 Product card
A product card summarises a catalogue item. Content order: image, category, name, verified key facts, documentation status, link.

Structure (white surface, 1 px hairline border, `--radius-sm`, `--space-4`/`--space-5` internal padding):
1. **Image:** 4:5 aspect ratio on a stone background. If no photograph exists, show a stone tile with the text "Image pending". Never use a fabricated or placeholder vial that looks like a real product.
2. **Category:** `--text-meta`, charcoal-soft.
3. **Name:** `--text-h3`, display font, a heading element at the correct level for its context. The name contains the single link (a stretched link covering the card gives one tab stop).
4. **Key facts:** a short description list showing only facts that are verified and sourced (for example identity fields from the product data model). Each fact has a label and value. If no fact is verified, show "Specifications pending verification" in charcoal-soft. No fact is ever filled in to avoid an empty card.
5. **Documentation status badge:** see section 6.6.
6. **Demo marker:** any demo or illustrative product carries a "Demo" badge on the image and the text "Illustrative demo product, not for sale" in the card body, so it is conveyed to assistive technology too.
7. **Link text:** "View details" (the name acts as the accessible link name; avoid duplicate adjacent links to the same destination).

Not allowed on a card: price, discount, stock urgency ("only 3 left"), ratings, reviews, "best seller", "new" ribbons implying demand, add-to-cart, wishlist, comparison tick-boxes that imply purchase intent, and any efficacy, benefit, or safety statement.

Availability: the data model includes `availabilityStatus`. Availability must never imply legal sale eligibility. Until Phase 5 defines the semantics, cards do not display availability.

States:
- Hover: border darkens to charcoal; the name gains a 1 px underline. No scaling, shadows, or movement.
- Focus-visible: the focus ring (section 8) surrounds the whole card.
- Image with `alt`: describes the visible object only (see section 10.5).

Grid: see section 5. Cards in a row share equal height; content never truncates silently (allow wrapping or "show more" on the detail page).

### 6.6 Badges and status labels
- Shape: rectangle, `--radius-sm`, 1 px border, `--text-meta` (mono, uppercase, +0.06em), padding `--space-1` by `--space-2`.
- Always contain a text label. An optional icon is decorative and hidden from assistive technology.

| Badge text | Meaning | Style |
|---|---|---|
| Demo | Illustrative content, not a real product record | Charcoal background, ivory text |
| Documentation verified | A reviewer has verified the supplied document against the record | Olive-strong text and border on white |
| Pending review | Submitted, not yet verified | Charcoal text on stone, 1 px border-strong |
| Not supplied | No document available | Charcoal-soft text, dashed 1 px border-strong |
| Unverified | A fact has no verification | Charcoal-soft text, dashed 1 px border-strong |

Wording rules:
- "Documentation verified" refers only to an internal data and document check. It does not imply that the product is safe, effective, approved, certified, compliant, or legal to sell anywhere. Do not use the words "Approved", "Certified", "Tested", "Safe", "Clinically", or "Guaranteed" in status badges.
- A batch identifier may be shown only if it is real, supplied, and verified.
- A "verified" state may be shown only when the underlying data record carries a verification status of `verified`. The design never decides that.

### 6.7 Form controls
Forms in scope for the design system: contact form and catalogue filters (Phase 5). There are no payment, address, account, or age-gate fields. Newsletter or consent patterns require privacy review and are not specified here; no consent wording is invented.

Field anatomy, top to bottom: visible label, optional hint, control, optional error.
- **Label:** always visible, above the control, `--text-small` weight 500, linked with `for`/`id`. A placeholder is never a substitute for a label.
- **Required marking:** the text "(required)" in the label. An asterisk alone is not used.
- **Control:** white background, 1 px `--color-border-strong` border, `--radius-sm`, minimum height 48 px, text at least 16 px (also prevents mobile zoom on focus), padding `--space-3` to `--space-4`.
- **Hint:** `--text-small`, charcoal-soft, associated with `aria-describedby`.
- **Error:** appears below the control; error-coloured text with a leading icon (decorative) and a message that says what is wrong and how to fix it. The control gets `aria-invalid="true"` and a 2 px error border. The message is associated by `aria-describedby`.
- **Error summary:** for forms with more than one field, a summary at the top lists errors as links to each field. It receives focus after a failed submit.
- **Focus:** see section 8.
- **Disabled:** stone background, charcoal-soft text, and a visible reason where the context needs one.
- **Select, checkbox, radio:** use native elements. Checkbox and radio visuals are at least 24 px with a 44 px clickable label area; checked state uses a charcoal fill plus a visible mark (not colour alone).
- **Autocomplete:** use correct `autocomplete` attributes (name, email) for contact fields.
- **Validation:** validate on submit and on blur after first interaction. Never clear user input on error. Server-side validation is required regardless of client validation.
- **Filters (Phase 5):** native inputs (checkboxes, radios, selects), grouped with `<fieldset>` and `<legend>`; the applied-filter state is announced through a polite live region; all filtering works by keyboard.
- **Contact form submission:** the contact form needs a defined destination, privacy notice, and retention approach before it is built. These are not yet decided and are not invented here.

## 7. Motion

Motion is minimal and never required to access content.

| Token | Value | Use |
|---|---|---|
| `--motion-fast` | 120 ms | Colour, border, underline changes |
| `--motion-base` | 200 ms | Menu panel open and close, disclosure |
| `--motion-slow` | 320 ms | Maximum duration for any transition |
| `--ease-standard` | `cubic-bezier(0.2, 0, 0, 1)` | Default easing |

Rules:
- Animate only `opacity`, `transform` (translation of 8 px or less), `color`, `background-color`, and `border-color`. Do not animate layout properties.
- No scroll-jacking, parallax, forced smooth scrolling, auto-advancing carousels, auto-playing video or audio, or looping decorative animation.
- No animation delays access to content or navigation. All content is present and readable without any animation.
- **Reduced motion:** under `@media (prefers-reduced-motion: reduce)`, remove transforms, set transitions and animations to effectively instant (`0.01ms`), and show end states immediately. Colour and underline changes may remain because they are not motion.
- `IntersectionObserver` may be used only for progressive reveals that add value. The no-JavaScript baseline shows everything fully visible, and reduced-motion users see everything immediately.
- Anything that moves for more than 5 seconds needs a pause control. The default is not to have any such motion.

## 8. Keyboard navigation and focus

- **Tab order** equals DOM order equals visual order. Do not use positive `tabindex` values.
- **Skip link** is the first focusable element and moves focus to `<main id="main">`, which uses `tabindex="-1"` to receive focus.
- **Focus-visible style (all interactive elements):** `outline: 2px solid var(--color-charcoal); outline-offset: 3px;`. The offset gap shows the page colour between the element and the ring, so the indicator stays visible on charcoal, olive-strong, white, stone, and ivory elements. Charcoal against ivory is 16.22:1 (minimum required 3:1).
- Never remove the outline without an equal or stronger replacement. Use `:focus-visible` so mouse clicks do not trigger rings, while keyboard users always see them.
- **Forced colours mode:** do not suppress outlines; keep borders on controls and badges so they remain visible with system colours.
- **Focus must not be obscured** by sticky or overlaid content. No sticky header in v0.1.
- **Menu disclosure:** Enter and Space toggle; Escape closes and returns focus to the toggle button.
- **No keyboard traps.** Any overlay that is introduced later must be dismissible by keyboard and return focus to its trigger.
- **Cards:** one tab stop per card (the stretched link). Interactive elements are not nested inside the link.
- **Touch and pointer:** hover is never the only way to reach content; drag gestures have a single-pointer alternative.

## 9. Accessibility requirements

Target: **WCAG 2.2 Level AA**. This target is a proposal in this draft and is subject to owner confirmation; it is also the standard against which Phase 7 will test.

Requirements:
1. **Structure:** landmarks (`header`, `nav`, `main`, `footer`), one `h1` per page, logical heading order without skipped levels, `lang` set on `<html>`, unique and descriptive `<title>`.
2. **Colour:** contrast per section 2.2; no information by colour alone.
3. **Text and zoom:** text resizes to 200% without loss of content or function; content reflows at 320 CSS px (400% zoom) without two-dimensional scrolling; do not set `maximum-scale` or `user-scalable=no`; respect user text-spacing overrides.
4. **Keyboard and focus:** sections 8 and 6.2, plus visible focus on every interactive element.
5. **Target size:** at least 24 × 24 CSS px everywhere, and 44 × 44 for primary touch controls.
6. **Images:** meaningful images have `alt` text that describes what is visible; decorative images use `alt=""`. Alt text never includes unverified identity, purity, or benefit claims.
7. **Forms:** visible labels, programmatic associations, error identification and suggestion, an error summary, and no reliance on placeholders.
8. **Motion:** section 7, with reduced motion honoured.
9. **Status messages:** dynamic updates (filter results, form submission) are announced via polite live regions.
10. **Consistent navigation:** the header and footer are consistent across pages; help or contact access appears in the same place.
11. **Light only:** `color-scheme: light`; verify the design in a system-dark-mode environment.
12. **Testing (carried into Phase 7):** automated checks, keyboard-only walkthrough, screen reader spot checks, zoom and reflow at 320 px, reduced-motion check, forced-colours check, and contrast re-verification of every token pair used.

## 10. Product photography direction

The photography supports a calm, credible, product-led catalogue. **It never creates, implies, or fabricates product facts.**

### 10.1 Style
- Single product per frame on a seamless warm ivory to neutral background that sits within the page palette.
- Soft, diffused daylight-style lighting from one side, with a gentle, consistent contact shadow. No harsh flash, glossy hotspots, coloured gels, or heavy post-processing.
- Consistent camera height, framing, and scale across all products in a catalogue, so cards align.
- Straight-on or slight three-quarter angle. Packaging and labels are in sharp focus.
- Colour is neutral and accurate. Colour-managed in sRGB. No filters, vignettes, or colour grading that changes how the product looks.

### 10.2 Authenticity of labels and packaging
- Photograph the real product, packaging, and label. The text on the label must be the real label.
- Do not retouch, composite, or render label text, concentrations, amounts, batch numbers, certificates, logos, or seals that are not on the real item.
- Do not use computer-generated or AI-generated product imagery as if it were the product. Any illustrative image must be labelled "Illustrative" in the visible UI and in alt text.
- If a label is not final or the product is not yet photographed, use the "Image pending" tile. Do not show a placeholder bottle that resembles a real product.

### 10.3 Subject matter to avoid
- No needles, syringes, injection, application to skin, or any depiction of using or administering a product.
- No people consuming, holding to the body, or demonstrating use of a product.
- No bodies, physiques, fitness or "transformation" imagery, before-and-after content, or medical settings that imply treatment, endorsement, or clinical outcomes.
- No lab-coat, clinic, or hospital imagery used to imply that a specific product or the business is medically endorsed or clinically tested, unless that is true, documented, and approved.
- No celebrities, testimonials, or trademarked third-party products.
- Editorial photography (research and about pages) may show materials, environments, or abstract textures. It must not imply facilities, equipment, or processes that the business has not documented as its own.

### 10.4 Technical specification
| Use | Aspect ratio | Notes |
|---|---|---|
| Product card | 4:5 | Subject centred with generous margin |
| Product detail gallery | 1:1 and 4:5 | Includes label close-up when available |
| Editorial / hero | 3:2 and 16:9 | Must remain meaningful when cropped on mobile |

- Masters: at least 3000 px on the long edge, retained by the owner.
- Delivery: responsive sizes via the framework image component, modern formats (AVIF/WebP) with a JPEG fallback, explicit width and height to prevent layout shift, lazy loading below the fold, and the first screen's image prioritised.
- Weight targets are to be set during Phase 7 performance work. This document does not invent a budget.

### 10.5 Alt text and captions
- Describe what is visible, in plain language, without claims. Illustrative pattern: "Glass vial with a white cap on a plain ivory background." Use the real description of the real object; do not copy this example text for products that do not match it.
- Do not include purity, identity, benefit, or batch information in alt text unless it is a verified fact shown in the image and the record.

### 10.6 Rights and provenance
For every image, record: source (owned, licensed, or commissioned), photographer or licensor, licence terms, date, and permitted uses. Do not use images without recorded rights. Stock images must be licensed for commercial web use. Avoid identifiable people; if any are included, obtain and store written releases. Photography sourcing is an open question (open question 7).

## 11. Content and claims guardrails

These apply to every component and template:
- The design system provides placeholders and states, never product facts. Do not invent identity, sequence, blend ratio, concentration, purity, origin, certificates, batch data, approvals, or citations.
- No dosing, injection, reconstitution, syringe-conversion, treatment, or self-administration content or imagery.
- No therapeutic, safety, efficacy, disease-treatment, or regulatory-approval claims without substantiated, approved evidence.
- No fake testimonials, reviews, invented metrics, trust seals, or "as seen in" claims.
- Avoid agency language ("our services", "projects", "clients", "case studies") unless it truly fits the brand.
- Demo content is marked as demo in visible text.
- Jurisdiction defaults remain `unverified`, and sales and shipping eligibility remains `false` (see `docs/compliance/JURISDICTION-POLICY.md`).

## 12. Illustrative token reference

Documentation of intended CSS custom properties. It is not a source file. Final tokens live in `styles/tokens.css` (path per `docs/architecture/OVERVIEW.md`) when implementation is approved.

```css
:root {
  color-scheme: light;

  /* colour */
  --color-ivory: #F6F5F1;
  --color-white: #FFFFFF;
  --color-stone: #ECEAE3;
  --color-charcoal: #171916;
  --color-charcoal-soft: #5A5D56;
  --color-olive: #737A60;          /* accent only: large text, rules, icons */
  --color-olive-strong: #565D45;   /* text, links, hover */
  --color-hairline: #E4E2DA;       /* decorative only */
  --color-border-strong: #7C7F76;  /* control borders */
  --color-error: #9B2C2C;

  /* shape and spacing */
  --radius-sm: 2px;
  --border-width: 1px;
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px; --space-4: 16px;
  --space-5: 24px; --space-6: 32px; --space-7: 48px; --space-8: 64px;
  --space-9: 96px; --space-10: 128px;

  /* motion */
  --motion-fast: 120ms; --motion-base: 200ms; --motion-slow: 320ms;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
}
```

## 13. Open items and approval

Open items that block approval or later phases:
1. Owner review and approval of this specification (palette, contrast changes, scale).
2. Typeface selection and licence record (open question 11).
3. Brand name and wordmark (open question 1). A neutral placeholder is used until then.
4. Initial language confirmation (open question 9).
5. Owner confirmation that near-black `#171916` is acceptable as charcoal (open question 12).
6. Confirmation of WCAG 2.2 AA as the accessibility target.
7. Sticky versus non-sticky header decision.
8. Test of fluid type at 320 px and at 200%/400% zoom.
9. Decide the form of the visual reference sheet or component preview (Phase 3 task).
10. Photography sourcing and ownership (open question 7).

Approval record:
- [ ] Approved
- [ ] Approved with changes
- [ ] Rejected

Owner comments:
_Add decision and any required changes here._
