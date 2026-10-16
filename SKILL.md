---
name: lovable-prd-generator
description: Turn a product or app idea into a research-aware, build-ready Product Requirements Document (PRD) and staged Lovable implementation prompts. Use when someone asks to plan, scope, refine, or write a Lovable PRD for a web app, SaaS, internal tool, game, community platform, or AI-powered product.
metadata:
  version: "1.1.0"
  category: "product-planning"
---

# Lovable PRD Generator

Produce a decision-ready PRD that a human can review and an AI builder can implement incrementally in Lovable. Prioritize user outcomes and working behavior over impressive but untestable feature lists.

## Inputs and context

Accept an informal idea, existing PRD, screenshots, a competitor, or a conversation as input. Extract decisions already supplied; **never re-ask answered questions**. If needed, ask a few *material* missing decisions (e.g., target user, launch audience, core workflow, required integrations); for larger ambiguous projects, use a short conversational discovery round, never a mandatory questionnaire. Do not stall when sensible defaults permit progress. When the user asks to proceed, state assumptions explicitly and create the draft. Never repeat answered questions.

Inspect provided references first. Do not pretend to have viewed inaccessible screenshots, files, sites, or connected services. If current capabilities, regulations, prices, technical constraints, or competitor claims matter, verify them with available sources and date the verification; otherwise flag them for verification. Research enriches the PRD; it must not replace a clear problem definition.

## Working method

1. **Reconstruct the brief.** Write the product vision, target users, problem, desired outcome, platform, language, launch scope, and known constraints. Mark decisions `Confirmed`, `Assumed`, or `Open`.
2. **Challenge the thesis.** Identify alternatives users have today, differentiators that are concrete and testable, the smallest meaningful adoption loop, major risks, and what would invalidate the idea. Avoid inventing market size, competitor features, willingness to pay, or traction.
3. **Shape the product.** Describe core jobs-to-be-done, specific pages/screens, role permissions, accessibility, content, localization and onboarding. Write **numbered, sequential user flows** for the principal task, repeat usage, and at least one alternative path (e.g., blank state, validation failure, denied permission, offline/API failure). Cover loading/empty/error/success states without implying unimplemented screens work.
4. **Define behavior.** Give each essential feature a stable ID and a **Trigger → Action → Result** behavior contract: what initiates it, the app/server/storage steps it performs, and the observable state after success or failure. Define user story, validation, permissions, dependencies and **Given → When → Then** acceptance tests linked to each ID. Include side effects and error behavior; don't write vague commands such as “make it functional.” Prioritize Must/Should/Later. Separate prototype mocks from live functionality. See [behavior contracts](references/behavior-contracts.md).
5. **Specify data and integrations.** Propose entities/tables with key field names/types, relationships, uniqueness, ownership, state transitions, authentication/authorization, storage, event tracking, integrations and data retention. Make secrets server-side. Require least privilege and row-level security or equivalent for private data. Mark architecture as a proposal, not a claim about the current project. **When extending an existing app, add a Do Not Change contract** that protects confirmed working routes, schema, existing user data, auth/roles, design conventions, integrations and flows unless a migration and regression plan is explicitly agreed. Don't assume a greenfield build.
6. **Design AI deliberately, if applicable.** Specify when AI runs, provider-agnostic inputs/outputs, structured output validation, reference grounding, moderation/safety, fallbacks, retries, latency/cost ceilings, human review where necessary, and evaluation criteria. Never imply a model has guaranteed accuracy or silently fabricates data.
7. **Scope a buildable release.** Divide delivery into phases with demonstrable milestones, dependencies, and explicit exclusions. Do not design a full company platform as the default MVP. If the user explicitly wants V2 or a full spec, produce it while distinguishing V1 essentials and later releases.
8. **Produce a Lovable build plan.** Start with a short kickoff prompt referring to the attached PRD as authoritative, followed by small, sequential phase prompts with completion gates. Tell Lovable to report real completed behaviors and unresolved dependencies, not to mark mocked flows as done.
9. **Check completeness.** Apply the release checklist below before final output. Resolve contradictions between scope, screens, behavior contracts, schema, permissions, implementation phases, and test cases. Ensure each Must-have feature can be traced **feature ID → behavior → acceptance tests → implementation phase**.
10. **Deliver a usable artifact.** For a full PRD, create a Markdown `.md` file when the current environment supports file output and provide its real location/link. If file creation isn't supported, supply the full Markdown in chat; never claim a file has been created when it hasn't. Don't hardcode a machine-specific output directory.

## Output contract

Default output is a single self-contained Markdown PRD using [the detailed blueprint](references/prd-blueprint.md) and [the ready-to-fill template](assets/prd-template.md). Adapt headings to the product, but include the following in substance:

- Executive summary and one-sentence value proposition
- Problem, current alternatives, audience and jobs-to-be-done
- Goals, non-goals, hypotheses and measurable pilot success criteria
- Scope matrix (MVP / Later / Out of scope), dependencies and key decisions
- Information architecture, screens and **numbered** user journeys, including unhappy paths
- Feature requirements with stable IDs (e.g., `F01`), **Trigger → Action → Result** contracts, and **Given → When → Then** acceptance criteria
- Design principles, accessibility, mobile behavior and localization
- Proposed technology architecture, typed data entities, auth, permissions and privacy; **Do Not Change** list when extending an app
- Integrations, AI/data flows (when relevant), failure handling and cost controls
- Analytics events, quality bar, test fixtures, release gates and risks
- Phased Lovable implementation prompts and a small kickoff prompt
- Assumptions, open questions and sources/verification notes when applicable

If the user requests only a short brief, an update, or a targeted feature, scale the output accordingly; don't force a full PRD onto a small task. When editing an existing PRD, preserve confirmed decisions, identify changed sections, and keep the document consistent.

## Lovable-specific rules

- Treat Lovable as an implementation environment, not the source of truth on user needs. For a **new** Lovable web project, a common starting point is React + TypeScript + Vite + Tailwind CSS + shadcn/ui; confirm the actual project setup before mandating package changes. Prefer accessible UI patterns and verify current Lovable platform features against official docs when material. Do not assume an existing project uses this exact stack.
- Select Lovable Cloud or a compatible Supabase backend only when needed and document the choice; do not gratuitously introduce a backend into static prototypes. Never claim a database, auth provider, external API, payment flow, or email integration is connected until tested.
- Distinguish **visual demo**, **interactive prototype**, **pilot**, and **production-ready** releases. State what actually needs persistence, identity, privacy and real integrations.
- When extending a project, include explicit **Do Not Build** and **Do Not Change** lists in build prompts. Do not silently rewrite live schemas, reset user data, swap auth, modify unrelated routes, or break existing integrations. Specify preservation tests and propose migrations for necessary changes.
- Do not ask Lovable to build everything in one giant prompt. Use phases: skeleton/design → data/auth → core workflow → integrations/AI → QA/security → launch. Reorder for critical technical proofs (e.g., audio, export, real-time behavior).
- Provide testable acceptance checks for permissions, mobile UX, validation, retries, empty states and real end-to-end user flows. Explicitly prohibit dead-end buttons and fabricated success states.
- Favor reusable components, narrow data contracts, migrations, graceful fallbacks and straightforward maintenance. Do not over-engineer future features.
- Be mindful of Lovable credits and third-party usage costs. Request a working vertical slice before expensive expansion.

## Safety and truthful claims

- Avoid collecting sensitive or children's data without an explicit rationale, controls and applicable legal review. For health, education assessment, money and other consequential domains, articulate limitations and human-review requirements.
- Don't copy protected competitor designs or exams verbatim, fabricate testimonials/metrics, or promise that AI output is exact, official, or human-equivalent.
- If referencing legal/compliance standards, identify the relevant jurisdiction and state what must be reviewed by qualified experts.

## Pre-delivery checklist

- [ ] Confirmed decisions retained; unknowns labeled, no contradictions
- [ ] Clear user problem, differentiated core workflow and restrained MVP
- [ ] Every MVP screen connected to a real action or a candid placeholder
- [ ] Feature IDs map to Trigger → Action → Result contracts, Given → When → Then acceptance tests, and implementation phases
- [ ] If extending existing work, protected routes/data/auth and Do Not Change guardrails explicit
- [ ] Auth/data ownership and secrets/integration boundaries explicit
- [ ] AI outputs validated, limitations and failure states defined if relevant
- [ ] Accessibility, responsive UX, empty/error/loading states accounted for
- [ ] Test cases include unauthorized access and bad inputs
- [ ] Kickoff prompt and next-phase prompts are actually executable in Lovable
- [ ] Sourced facts separated from assumptions; no invented verification

## Files

- [PRD section-by-section guidance](references/prd-blueprint.md)
- [AI coding feature behavior contracts](references/behavior-contracts.md)
- [Markdown PRD template](assets/prd-template.md)
- [Example seed brief](examples/example-brief.md)
