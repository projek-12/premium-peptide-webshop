# Jurisdiction policy

This document describes a software safety boundary, not legal advice.

## Fail-closed defaults
Every market starts as:
- classification: `unverified`
- regulatoryStatus: `unverified`
- legalReviewStatus: `not_reviewed`
- salesEligible: `false`
- shippingEligible: `false`
- requiredDocuments: unknown / not satisfied

No market is enabled by default. Do not infer country eligibility from another country's status.

## Suggested typed model
```ts
type VerificationStatus = "unverified" | "pending_review" | "verified" | "rejected";
type Eligibility = "blocked" | "review_required" | "allowed";

interface JurisdictionConfig {
  countryCode: string;
  productClassification: VerificationStatus;
  regulatoryStatus: VerificationStatus;
  legalReviewStatus: VerificationStatus;
  salesEligibility: Eligibility;
  shippingEligibility: Eligibility;
  requiredDocuments: string[];
  evidenceRefs: string[];
  reviewedAt?: string;
  reviewedBy?: string;
}
```

The runtime policy should allow a transaction only when the product and destination are explicitly verified and every required gate passes. Missing, stale, or contradictory data must block the transaction.

## Content
Do not publish legal conclusions as marketing copy. Store source references, reviewer, and review date for each market decision. Escalate ambiguous cases to qualified counsel.
