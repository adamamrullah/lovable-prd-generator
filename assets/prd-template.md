# [Product Name] — Lovable Product Requirements Document

**Version:** 1.0  
**Status:** Draft for review / Ready for build (choose accurately)  
**Date:** [date]  
**Release type:** Prototype / Pilot / MVP / V2  
**Target:** [platform, audience, geography, languages]  

## 1. Executive summary
[5 sentences: problem, user, outcome, solution, scope, primary constraint.]

## 2. Decision ledger
| Topic | Decision | Status (Confirmed/Assumed/Open) | Implication |
|---|---|---|---|
| Primary user | [ ] | [ ] | [ ] |
| Launch scope | [ ] | [ ] | [ ] |

## 3. Problem and opportunity
### Existing alternatives and pain points
[Describe current workflow and credible alternatives.]
### Hypotheses and differentiation
[Explicitly separate facts from hypotheses.]

## 4. Audience and jobs-to-be-done
[Primary persona; optional secondary.]

## 5. Goals and measurement
| Metric | Definition | Pilot target (hypothesis) | Event/source |
|---|---|---|---|
| Activation | [ ] | [ ] | [ ] |

## 6. Scope and non-goals
| Must have in current release | Should have | Later/out of scope |
|---|---|---|
| [ ] | [ ] | [ ] |

## 7. Navigation, screens and numbered journeys
[Information architecture, end-to-end first-run and repeat journeys. For each screen: purpose, content, actions, loading/empty/error/success, mobile differences.]

**Flow A — [primary user task]**
1. [User enters screen and sees specific content.]
2. [User provides input; validation and next action.]
3. [App persists/processes information and updates UI.]

**Alternative flow A1 — [invalid data / denied access / provider outage]**
1. [What fails and what the user sees.]
2. [Retry/recovery path; whether data is saved, rolled back or not changed.]

## 8. Functional requirements and behavior contracts
| ID | Priority | User need / requirement | Trigger | Action (system/data) | Result (visible/persisted) | Failure / permissions | Acceptance test ID |
|---|---|---|---|---|---|---|---|
| F01 | Must | [ ] | [ ] | [ ] | [ ] | [ ] | AC-F01-1 |

For complex interactions, expand an ID into a separate contract:

**F01 — [feature]**
- **Trigger:** [exact click/event/schedule]
- **Action:** [validation → authorized server call → DB/API changes, or intentionally no persistence]
- **Result:** [success UI, persisted state, side effects]
- **On failure:** [what stays unchanged, user feedback, retry path]
- **Permissions/dependencies:** [role, connection, rate/usage limits]

## 9. Design system and accessibility
[Visual references, tokens, components, original assets, mobile UX, keyboard/accessibility and localization.]

## 10. Technical architecture and data model
[Proposed frontend/backend/storage/auth; typed table columns, relationships, uniqueness, state transitions, authorization, RLS and secrets. Greenfield Lovable web default can be React/TypeScript/Vite/Tailwind/shadcn if verified; use Lovable Cloud or compatible Supabase only when justified.]

### Existing-project protection (omit if greenfield)
**Do Not Change without explicit approval:** [existing routes, auth, schema, user data, integrations, working components, visual conventions]
**Migration / regression checks if change is unavoidable:** [backup, review, feature flag/rollback, tests]

## 11. Integrations and AI (if relevant)
[External systems, inputs/outputs, validation, permissions, quotas, costs, retry/fallback, moderation and review.]

## 12. Privacy, security and compliance boundaries
[Data minimization, retention/deletion, account isolation, audit and risks relevant to jurisdiction.]

## 13. Analytics and operating plan
[Events, funnels, logs/alerts, estimated run costs and ongoing owner responsibilities.]

## 14. Milestone delivery plan
| Phase | Deliverable | Depends on | Demonstrable completion gate |
|---|---|---|---|
| 1 | [ ] | [ ] | [ ] |

## 15. QA and acceptance tests
[Numbered verifiable scenarios mapped to feature IDs, covering working user flows, edge cases, access control, accessibility, external failures.]

**AC-F01-1**
- **Given:** [starting data and permissions]
- **When:** [precise user action]
- **Then:** [observable UI, API or persisted outcome]

**AC-F01-2 (failure)**
- **Given:** [invalid input, unauthorized actor or provider failure]
- **When:** [same action]
- **Then:** [no illicit write, clear explanation, recoverable UI]

## 16. Lovable kickoff prompt
> Build [product] according to this PRD. Implement Phase 1 only first. [Specific stack/scope/user-visible action]. Follow the numbered flows, Trigger → Action → Result behavior contracts and acceptance tests for the relevant feature IDs. Respect Do Not Build and (if applicable) Do Not Change. Report tested behavior, what remains mocked, blockers, and next-stage dependencies. Do not invent integrations, data or success states.

## 17. Lovable follow-up prompts
**Phase 2:** [Scope, exact tables/screens/behavior, test gate.]  
**Phase 3:** [Scope, integration/AI, test gate.]  
**Final QA:** [Security, mobile, performance, feature acceptance test gate.]

## 18. Risks, open questions and sources
[Label evidence and verification dates; unresolved decisions; what needs human review.]
