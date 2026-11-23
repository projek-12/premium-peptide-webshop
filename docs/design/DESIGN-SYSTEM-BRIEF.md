# Design system brief

## Direction
Premium editorial commerce: calm, precise, credible, tactile, and product-led. Use the reference studio site for broad visual inspiration only; do not copy its wording, assets, layout pixel-for-pixel, or agency information architecture.

## Initial palette proposal
- Warm paper: `#F6F5F1`
- Surface: `#FFFFFF`
- Primary ink: `#171916`
- Secondary text: `#686B63`
- Muted olive accent: `#737A60`
- Hairline border: `#E4E2DA`
- Subtle warm panel: `#ECEAE3`

Check text/background combinations for WCAG contrast before use. Palette values are starting tokens, not final approved brand colors.

## Typography
- Editorial display: a high-quality serif with appropriate web licensing.
- Interface/body: a highly legible sans-serif.
- Metadata: restrained mono or tabular sans, used sparingly.
- Define a fluid type scale with `clamp()` only after testing narrow mobile widths.

## Layout
- Use a consistent max-width container and responsive side gutters.
- Use an intentional 12-column desktop grid where useful; collapse cleanly on tablet/mobile.
- Product cards must prioritize product name, category, verified key facts, and documentation status.
- Avoid decorative clutter, excessive rounded cards, gradients, and dark sections.

## Motion
- Short, purposeful transitions only.
- Respect `prefers-reduced-motion: reduce`.
- No scroll-jacking, forced smooth scrolling, or animation that delays access to content.
- Use IntersectionObserver only where it adds value and provide a no-JS content baseline.

## Light-only rule
Do not implement a theme switcher or dark theme. Ensure system dark-mode preferences do not invert the design unexpectedly.
