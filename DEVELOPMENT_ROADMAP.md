# Development roadmap

## Guiding sequence
Do not build all phases in one pass. Each phase should be reviewed before the next begins.

| Phase | Scope | Exit criteria |
|---|---|---|
| 1. Repository audit | Inspect existing repository, stack, git state, and assets | Audit recorded; existing work identified |
| 2. Foundation | Approve architecture, design principles, compliance boundaries, task plan | ADR-001 reviewed; docs and tasks accepted |
| 3. Design system | Tokens, typography, grid, components, motion and responsive rules | Design system documented and reviewed |
| 4. Homepage | Responsive editorial storefront landing page | Homepage approved on mobile and desktop |
| 5. Shop and product detail | Catalogue, filters, product details, evidence/documentation states | Product data is sourced or clearly marked placeholder |
| 6. Commerce foundation | Disabled adapter, eligibility gates, provider integration seam | No transaction can occur while disabled or unverified |
| 7. QA and launch readiness | Accessibility, SEO, performance, security, content and legal review checklist | QA report complete; launch blockers explicit |

## Phase 1 audit result
The repository snapshot supplied for audit contained a single `README.md` with the heading `# webshop`. No application source, package manifest, architecture documents, tasks, ADRs, or prototype were present in that snapshot. Git branches and pull requests were not visible in the ZIP snapshot and must be checked in the actual Git repository.

## Phase 2 status
This bundle proposes an initial stack and boundaries. ADR-001 is not approved merely because it is included. Review it before implementation.

## Release gates
A visually complete storefront is not equivalent to a legally launchable webshop. Launch requires documented product classification, destination-specific review, payment-provider approval, fulfilment/shipping review, privacy and consumer-law review, and verified product documentation.
