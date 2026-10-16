# Lovable PRD Generator

An open-format **Agent Skill** (v1.1) for turning an app idea into a product requirements document (PRD) and practical, phased implementation prompts for [Lovable](https://lovable.dev/).

It focuses on real user problems, restrained scope, **numbered end-to-end flows, Trigger → Action → Result feature contracts, Given → When → Then tests**, information architecture, security, data design, AI integration where needed, and avoiding mock features that masquerade as completed software. When improving an existing project, it requires a **Do Not Change** safety contract.

> Independent community-authored skill; not an official Lovable product, integration, or endorsement.

## What's inside

```text
lovable-prd-generator/
├── SKILL.md                     # Agent instructions and trigger metadata
├── README.md                    # Usage and publishing guidance
├── references/
│   ├── prd-blueprint.md         # Detailed PRD authoring reference
│   └── behavior-contracts.md   # Trigger/Action/Result and test examples
├── assets/
│   └── prd-template.md          # Fillable full PRD template
└── examples/
    └── example-brief.md         # Example request and expected behaviors
```

## How to use

1. Use an AI agent that supports the [Agent Skills format](https://agentskills.io/specification). Install or reference the `lovable-prd-generator` folder using that agent's skill-loading instructions.
2. Ask: **"Use the lovable-prd-generator skill to create a detailed PRD for [your idea]. Make it ready to upload into Lovable, and include phased build prompts."**
3. Review the PRD's confirmed decisions, assumptions, MVP scope and technical choices.
4. Attach the PRD to your Lovable project and paste the kickoff prompt. Build and verify one phase at a time.

The skill produces instructions and specs; it does not automatically build or deploy an application, and GitHub hosting alone does not install the skill in an AI agent.

## Example prompts

- "Create a Lovable-ready MVP PRD for an AI invoice generator for freelancers. English and Indonesian, private pilot first."
- "Turn this messy feature list into a phased Lovable V2 PRD. Challenge the MVP scope and include tests and RLS."
- "Update this PRD after switching the pilot audience to teachers. Keep confirmed requirements and give me revised build prompts."

## GitHub publishing

Create a repository named `lovable-prd-generator`, then upload the **contents** of this folder so `SKILL.md` is at the repo root. Add a license after choosing how others may reuse it (for example, MIT for permissive reuse); no license choice has been made for you in this starter package.

## Compatibility

The structure follows the [Agent Skills specification](https://agentskills.io/specification) (YAML frontmatter in `SKILL.md`, supporting `references/`, `assets/` and `examples/`). Different agent products may have their own install paths and limitations. Lovable features and integrations should be verified against current [Lovable documentation](https://docs.lovable.dev/).

## Limits

- Uses sources only when the host agent has access to them.
- Does not guarantee feasibility, legal compliance, security, product-market fit, or AI evaluation accuracy.
- Does not connect external services or test an app unless the agent actually has the necessary tools.

## v1.1 changes

- Added copy-pasteable Trigger → Action → Result contracts for important behaviors.
- Added numbered happy/unhappy journeys and explicit Given → When → Then acceptance tests.
- Added Do Not Change guardrails and regression/migration guidance for existing Lovable projects.
- Made greenfield technology defaults conditional on the actual project setup.
- Made actual Markdown file delivery part of the workflow, without relying on machine-specific paths.

This version incorporates useful patterns from a separately supplied vibe-coding PRD skill while keeping the broader Lovable product strategy, security, AI/operations and phased build approach. The unrelated Claude plugin manifest is not included; this repository is a portable Agent Skill rather than a Claude plugin package.
