# Architecture overview

The stack and boundaries below were approved in ADR-001 on 24 November 2026. The directory shape further down remains indicative. The architecture must keep these concerns separate:

- **Presentation:** pages, layout, accessible components, responsive behavior.
- **Catalogue domain:** product identity and factual attributes, with explicit source/provenance and verification status.
- **Jurisdiction policy:** destination-specific product classification and eligibility. Unknown means blocked.
- **Commerce boundary:** an adapter interface that is disabled by default. UI must not call a provider directly.
- **Content:** editorial/research material with source references and review dates.

## Approved stack (ADR-001)
- Next.js App Router
- TypeScript with strict mode
- CSS Modules and CSS custom properties for design tokens
- Static generation for public catalogue/editorial content where appropriate
- No UI framework or animation library initially

## Proposed directory shape
```text
app/
  (store)/
    page.tsx
    shop/
    products/[slug]/
    research/
    quality/
    about/
    contact/
  layout.tsx
components/
  layout/
  navigation/
  product/
  editorial/
  ui/
lib/
  catalogue/
  commerce/
  jurisdiction/
  content/
styles/
  tokens.css
docs/
tasks/
```

The directory shape is indicative, not an instruction to create every directory immediately. Adjust during implementation planning.
