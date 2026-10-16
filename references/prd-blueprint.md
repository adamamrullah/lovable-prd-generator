# PRD Blueprint: level of detail by section

Use this when the product is complex or a full PRD is requested. Do not copy it mechanically; adapt to actual needs.

## 1. Framing and validation
- **Summary:** who, problem, outcome, core mechanism, launch scope, major boundary in five sentences or fewer.
- **Problem and alternatives:** show the old process and friction; include a specific why-now only when evidence exists.
- **Personas/JTBD:** one primary audience, possibly one secondary audience; map top tasks and triggers.
- **Value proposition:** concrete new capability, not "AI-powered" alone.
- **Hypotheses/metrics:** label numeric goals as pilot targets, not forecasts. Define denominators, event names and time windows.
- **Risks:** technical, adoption, operating costs, compliance, content quality. Propose cheap tests to reduce uncertainty.

## 2. Product experience
- **Architecture:** public/private pages, navigation and guest-to-user transition.
- **Journeys:** first-time setup, core task completion, return use, recover from failure, export/share, deletion when applicable.
- **Per-screen detail:** goal, sections, user actions, inputs, validation, skeleton/empty/error/success state, responsive changes, permission gates and links.
- **Accessibility:** keyboard and focus, semantic labels, readable contrast, touch targets, reduced motion, alt text, audio captions/transcripts where relevant.
- **Visual direction:** articulate brand references, layout density, tokens, illustration rules and originality requirements; distinguish provided references from inferred style.

## 3. Functional specification
Use a table with columns: ID, priority, requirement, trigger/behavior, failure/edge case, acceptance evidence. Example:

| ID | Priority | Requirement | Acceptance evidence |
|---|---|---|---|
| F01 | Must | User can create a project with validated title | Saves and survives reload; error on invalid title |
| F02 | Must | Projects are scoped to their owner | Account B cannot read/update A's project, UI or API |

For each complicated feature, include a stable ID, Trigger → Action → Result behavior contract, state model, deterministic rules, expected latency, retries and failure handling. Write numbered happy and alternative flows, Given → When → Then tests, and a feature-to-phase traceability link. See [behavior contracts](behavior-contracts.md). Explicitly list non-goals and external dependencies.

## 4. Architecture and data
- **Architecture diagram in text:** frontend → server/edge logic → persistence → external APIs. State stack choices as conditional proposals; for Lovable greenfield web, verify before assuming React/TypeScript/Vite/Tailwind/shadcn and backend setup. For existing apps, add explicit Do Not Change protections and a safe migration/regression plan.
- **Data dictionary:** each table/collection's purpose, main columns, relations, ownership and constraints. Don't invent a migration as if executed.
- **Authorization:** roles, RLS/equivalent, server-only secrets and private asset rules; cross-account isolation tests.
- **Integrations:** system, purpose, needed access, authentication, rate limits, cost/quotas, fallback when disconnected.
- **AI (when used):** input schema, output JSON example or schema, validation, hallucination/error strategy, safety constraints, logging/redaction, evaluation and review workflow. Prefer deterministic app logic for rules that need consistency.
- **Ops:** environment configuration, retention/deletion, logging, failure alerts, migrations and backup implications according to actual platform capabilities.

## 5. Delivery and measurement
- **Phases:** Phase 0 technical proof when risk warrants; Phase 1 credible vertical slice; later phases with explicit working tests.
- **Build prompts:** self-contained enough for Lovable, refer back to authoritative PRD, state exact scope and what not to build. End every phase with a verification report.
- **QA:** happy path, empty/error states, offline/network issues where relevant, invalid input, permission separation, browser/mobile coverage, edge cases and provider failures.
- **Release criteria:** explicit pass/fail checks; no placeholders quietly shipped as integrations.
- **Evidence ledger:** sources verified and date, assumptions, open questions, technical spikes, owner decision needed.

## Optional domain modules
- **Children/family:** age-appropriate interaction, parental consent/controls, minimized data, accessible audio, content review, attention considerations; avoid unreviewed open-ended chat.
- **Education:** learning objectives, adaptive rules, content quality, practice vs official assessment, calibrated feedback and clear uncertainty.
- **Marketing/growth:** acquisition and onboarding instrumentation, activation, referral loops, attribution and privacy-consistent funnel tracking. Don't fake outcomes.
- **Marketplace:** buyer/seller roles, trust, dispute flow, moderation, payments and supply-side launch assumptions.
- **Fintech:** security, compliance scope, data provenance and boundaries against regulated advice.
- **Media generation:** rights management, generation pipeline, prompts/structured output, asset persistence, revision, budget caps and export fidelity.
