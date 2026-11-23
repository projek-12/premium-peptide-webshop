# ADR-001: Proposed initial web architecture

- **Status:** Proposed — approval required
- **Date:** 2026-11-24
- **Decision owners:** Project owner

## Context
The audited repository snapshot contains no application code or established architecture. A framework and implementation boundary must therefore be selected before Phase 3/4.

## Proposal
1. Next.js App Router with TypeScript and strict type checking.
2. CSS Modules and CSS custom properties for styling and design tokens.
3. Static generation for catalogue and editorial pages when content permits.
4. A separated catalogue/domain layer and jurisdiction policy layer.
5. A `CommerceAdapter` boundary with only a fail-closed `DisabledAdapter` initially.
6. No UI framework or animation library at the start.

## Rationale
- Next.js supports structured routing, metadata, and static rendering for an editorial catalogue.
- TypeScript supports explicit product and jurisdiction data models.
- CSS Modules keep styling local and avoid premature framework lock-in.
- Separating commerce and jurisdiction rules reduces the risk of accidentally enabling transactions in unreviewed markets.

## Consequences
- The project adopts the Next.js toolchain if approved.
- Hosting and deployment choices remain open.
- A CMS, database, search service, and payment provider are intentionally deferred.
- Build/deployment complexity is higher than a simple static HTML site.
- All market eligibility remains blocked until verified.

## Alternatives considered
- **Static HTML/CSS/JS:** simpler, but less suitable if the approved roadmap requires structured routing and a growing catalogue.
- **Vite + React:** viable, but Next.js offers integrated routing and metadata conventions.
- **Hosted commerce platform immediately:** deferred because product classification, target markets, and provider eligibility are unresolved.

## Approval
- [ ] Approved
- [ ] Approved with changes
- [ ] Rejected

Owner comments:
_Add decision and any required changes here._
