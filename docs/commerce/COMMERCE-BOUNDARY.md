# Commerce boundary

## Current state
Commerce is intentionally disabled. This project may prepare a clean integration seam, but must not accept orders or payments.

## Adapter proposal
A `CommerceAdapter` interface may define operations such as:
- `getAvailability(productId, destination)`
- `createCheckoutSession(request)` (must reject while disabled)
- `getCapabilities()`

The initial `DisabledAdapter` must fail closed and return a clear non-transactional status. Do not create a fake checkout flow that looks operational.

## Activation requirements
Do not implement or enable a live provider until all of the following have been reviewed:
1. Product identity and classification are documented by qualified sources.
2. Legal review covers each intended destination market.
3. Payment provider has explicitly confirmed product/business eligibility.
4. Fulfilment, import/export, customs, and shipping constraints are reviewed.
5. Consumer disclosures, privacy, returns/refunds, age or access restrictions (if applicable), and terms are reviewed.
6. Product data and any displayed certificates/COAs are authentic and traceable.

A developer must not infer approval from a provider API being technically available.
