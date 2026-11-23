# Phase 6 — Commerce foundation

## Goal
Prepare a safe integration seam without activating transactions.

## Tasks
- [ ] Implement the adapter interface from the approved ADR.
- [ ] Implement `DisabledAdapter` as the only active adapter.
- [ ] Implement typed jurisdiction configuration with fail-closed defaults.
- [ ] Add unit tests proving disabled and unverified states cannot create checkout sessions.
- [ ] Document future provider evaluation criteria.

## Acceptance criteria
- Checkout and payment are disabled.
- Missing or unverified jurisdiction data blocks all transaction attempts.
- No API keys or provider credentials are committed.
- No provider is selected until product/business eligibility is confirmed.
