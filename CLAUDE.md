# Project instructions for Claude Code

## Mission
Build a premium, international-facing, light-theme editorial webshop for research-oriented peptide products. The visual direction is inspired by the restraint, typography, spacing, and editorial confidence of high-end creative studios such as Dapper Agency, but the information architecture and interactions must be those of a real product catalogue—not an agency portfolio.

## First rule: inspect before editing
Before changing files:
1. Read this file, `README.md`, `DEVELOPMENT_ROADMAP.md`, all relevant files in `docs/`, and the active task in `tasks/`.
2. Inspect the repository tree, package manager, framework, scripts, and git status.
3. Do not assume this foundation bundle is the only work in the repository.
4. Do not overwrite or delete existing work without explaining the reason and obtaining approval.
5. Work on a feature branch; do not commit directly to `main`.

## Product and compliance boundaries
- Treat product content as informational and research-oriented only unless a qualified legal review establishes otherwise.
- Do not write or generate human-use dosing, treatment, injection, reconstitution, syringe-conversion, or self-administration instructions.
- Do not make therapeutic, safety, efficacy, disease-treatment, or regulatory-approval claims without substantiated and approved evidence.
- Never invent peptide identity, sequence, blend ratio, concentration, purity, manufacturing origin, certificates, COAs, batch data, approvals, or citations.
- Clearly label placeholders and unverified information. Prefer omitting an unknown claim over filling it with plausible-sounding copy.
- No live checkout, payment capture, order placement, or shipping promises until product classification, destination-market eligibility, payment-provider rules, and legal review have been approved.
- Default all jurisdictions to `unverified`; default sales and shipping eligibility to `false`.
- Do not provide a workaround to sell into a market marked prohibited, restricted, or unverified.

## Design principles
- Light theme only. Do not add a dark-mode toggle.
- Premium editorial layout: restrained palette, generous whitespace, deliberate typography, strong grid, clear hierarchy, precise product photography.
- Product catalogue first: clear category navigation, search/filter affordances, product cards, transparent product facts, documentation status, and useful product detail pages.
- Avoid agency language such as “our services”, “projects”, “clients”, or “case studies” unless contextually appropriate to the brand.
- Responsive from small mobile screens upward.
- Respect `prefers-reduced-motion`; motion must never block content or navigation.
- Accessibility: semantic HTML, keyboard operation, visible focus, sufficient contrast, descriptive labels, and meaningful alt text.

## Engineering principles
- Follow the architecture approved in ADR-001. It is a proposal until explicitly approved.
- Keep presentation, product data, jurisdiction policy, and commerce integration separated.
- Use strict TypeScript and avoid `any` unless justified and documented.
- Keep dependencies minimal. Do not add a UI framework or animation library without a documented reason.
- Keep secrets out of source control. Include `.env.example` only when needed; never include real credentials.
- Add tests for business-critical eligibility and adapter behavior.
- Use clear, small commits on feature branches. Summarize changed files, tests, risks, and unresolved questions.

## Definition of done
A task is done only when its acceptance criteria are met, relevant tests/checks pass, responsive and accessibility implications are considered, documentation is updated, and no unverified product or compliance claim has been introduced.
