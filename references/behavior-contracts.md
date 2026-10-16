# Behavior Contracts for AI Coding PRDs

Use this reference when specifying a feature for Lovable or another coding agent. It complements the complete PRD blueprint rather than replacing it.

## Why the structure matters

Prose such as “users can generate an invoice” leaves the event, validation, storage, permission check and visible success undefined. A well-specified feature defines all these and supplies a directly verifiable test. Apply this level of detail to **essential or risky** interactions, not to every decorative UI element.

## Required behavior contract

**F04 — Create invoice**
- **User story:** As a freelancer, I want to issue an invoice to a client so I can track the payment.
- **Trigger:** Signed-in owner presses **Create Invoice** from an invoice draft.
- **Action:** Validate required fields; calculate totals from line-item amounts; authorize owner; insert invoice and items atomically; assign an owner-scoped invoice number; return the new invoice ID.
- **Result:** User lands on the invoice detail view; the saved invoice survives reload; a new row appears in their invoice list. No email is sent unless separately requested and connected.
- **Failure handling:** Invalid fields show inline errors without any write; duplicate request cannot create two invoices; database errors retain the draft and show a retry option.
- **Permissions:** Only the invoice owner can read or edit it; a second user cannot access it through URLs or API calls.
- **Dependencies:** Authentication and persistent data store must be connected and tested. Label draft-only behavior if not.

## Numbered user flow

**Happy path**
1. User opens invoice editor and sees an editable draft.
2. User enters a client, currency, due date and one or more line items.
3. User presses Create Invoice and sees a loading state.
4. System validates, computes totals and saves an owner-scoped invoice.
5. User sees invoice detail; reloading retains it.

**Alternative: invalid line item**
1. User enters a negative quantity and presses Create Invoice.
2. Inline validation explains the correction; no invoice is saved.
3. User corrects the field and can retry.

## Acceptance tests (Given / When / Then)

- **AC-F04-1:** Given a signed-in user and valid invoice draft, when Create Invoice is submitted, then exactly one invoice with correct totals is persisted and displayed after reload.
- **AC-F04-2:** Given an invalid quantity, when Create Invoice is submitted, then inline validation appears and invoice count remains unchanged.
- **AC-F04-3:** Given an invoice owned by User A, when User B requests its ID via the UI or API, then access is denied with no private fields exposed.
- **AC-F04-4:** Given a transient database error, when the user submits, then the draft remains intact, an understandable error appears, and retry is offered without duplicate writes.

## Extend an existing app safely

Add a **Do Not Change** contract alongside regular **Do Not Build** exclusions.

Example:
- Preserve existing email/password auth, roles and account IDs.
- Preserve current invoice table/columns and all existing records; propose additive migrations for required fields.
- Keep existing dashboard navigation and unrelated pages unchanged.
- Do not change payment settings or start sending emails as a side effect.
- Run the existing create/edit/export flows before and after the change; document regressions.

This is a protection contract, **not** a blanket ban on necessary schema changes: if the new behavior requires migration, list the exact proposed migration, data safety/rollback approach, tests and approval needed.

## Feature traceability

For each Must-have requirement, link all four items:

| Feature | Behavior contract | Tests | Implementation phase |
|---|---|---|---|
| F04 Create invoice | Trigger/Action/Result F04 | AC-F04-1…AC-F04-4 | Phase 2 |

Avoid:
- Abstract “AI handles it” without input/output contracts.
- “Works perfectly” as acceptance criteria.
- Claims that an integration is active without a real test.
- Relying on frontend-only access checks for private data.
- Massive one-shot build prompts or building features explicitly out of scope.
