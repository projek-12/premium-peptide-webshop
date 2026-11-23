# ADR-001: Initial web architecture

- **Status:** Approved
- **Date proposed:** 2026-11-24
- **Date approved:** 24 November 2026
- **Decision owners:** Project owner

> The file name keeps "proposed" so that existing links and references remain valid. The status above is authoritative.

## Context
The audited repository snapshot contains no application code or established architecture. A framework and implementation boundary must therefore be selected before Phase 3/4.

## Decision
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
- The project adopts the Next.js toolchain.
- Hosting and deployment choices remain open.
- A CMS, database, search service, and payment provider are intentionally deferred.
- Build/deployment complexity is higher than a simple static HTML site.
- All market eligibility remains blocked until verified.

## Alternatives considered
- **Static HTML/CSS/JS:** simpler, but less suitable if the approved roadmap requires structured routing and a growing catalogue.
- **Vite + React:** viable, but Next.js offers integrated routing and metadata conventions.
- **Hosted commerce platform immediately:** deferred because product classification, target markets, and provider eligibility are unresolved.

## Scope of this approval
This approval covers the architecture decisions listed under "Decision" only. It does **not**:
- start Phase 4 or any application code (the roadmap requires Phase 3 review first);
- select hosting, CMS, database, search, analytics, or a payment provider;
- authorize checkout, payment, order, or shipping functionality (`DisabledAdapter` remains the only commerce implementation);
- enable any market, change any jurisdiction default, or verify any product classification;
- approve a brand name, typefaces, or the design tokens in `docs/design/DESIGN-SYSTEM.md`.

The package manager and Node.js version are not yet decided and should be recorded when scaffolding is planned.

## Approval
- [x] Approved
- [ ] Approved with changes
- [ ] Rejected

Owner comments:
Approved as proposed, without changes. Approval date: 24 November 2026. The approval was given by the project owner and recorded in this file on the same date.
