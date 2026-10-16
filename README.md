# Lovable PRD Generator

An open-format **Agent Skill** (v1.1) for turning an app idea into a product requirements document (PRD) and practical, phased implementation prompts for [Lovable](https://lovable.dev/).

It focuses on real user problems, restrained scope, **numbered end-to-end flows, Trigger → Action → Result feature contracts, Given → When → Then tests**, information architecture, security, data design, AI integration where needed, and avoiding mock features that masquerade as completed software. When improving an existing project, it requires a **Do Not Change** safety contract.

> Independent community-authored skill; not an official Lovable product, integration, or endorsement.

## What's inside

```text
lovable-prd-generator/
├── SKILL.md                     # Agent instructions and trigger metadata
├── README.md                    # Download and usage instructions
├── references/
│   ├── prd-blueprint.md         # Detailed PRD authoring reference
│   └── behavior-contracts.md   # Trigger/Action/Result and test examples
├── assets/
│   └── prd-template.md          # Fillable full PRD template
└── examples/
    └── example-brief.md         # Example request and expected behaviors
```

## Quick start

You do not need to write code to try the instructions. This skill helps an AI assistant create a PRD; you then use that PRD to guide a build in Lovable.

### 1. Download the files

1. At the top of this repository, click the green **Code** button.
2. Choose **Download ZIP**.
3. Extract/unzip the download. Open the extracted folder: you should see `SKILL.md`, `README.md`, `assets/`, `references/` and `examples/`.
4. Keep the supporting folders and files together when installing the skill.

### 2. Choose how to use it

#### Option A — Try it with file attachments

Use an AI assistant that supports Markdown (`.md`) attachments and can read all the attached files in the same conversation. This is a manual way to supply the instructions for that conversation.

1. Start a new conversation.
2. Attach these five files from the extracted folder:
   - `SKILL.md`
   - `assets/prd-template.md`
   - `references/prd-blueprint.md`
   - `references/behavior-contracts.md`
   - `examples/example-brief.md`
3. Paste the prompt below and replace the bracketed details:

> Read all five attached Markdown files. Use SKILL.md as the instructions, the two reference files as guidance, and prd-template.md as the output structure. The example brief illustrates expected behavior; my actual idea is below. If you cannot read an attachment, tell me which one before continuing.
>
> Create a detailed, Lovable-ready PRD for [describe your app idea]. The primary users are [audience], their main problem is [problem], and the first release should let them [core task]. Launch scope: [private pilot / MVP / V2]. Include numbered user flows, Trigger → Action → Result feature contracts, acceptance tests, and phased Lovable build prompts. Ask only material unanswered questions; label any assumptions. Deliver a self-contained Markdown PRD.

Attaching files supplies context to that conversation. It does not install a persistent skill. If your assistant cannot accept or read all five files, use a host with native Agent Skills support instead.

#### Option B — Install in Claude Code

**Prerequisite:** Claude Code is already installed and working. These steps use its project-level skills folder for a local project.

1. In a project folder where you use Claude Code, create `.claude/skills/`.
2. Copy the extracted skill folder into it and name that folder `lovable-prd-generator`. Copy the whole folder, including its supporting files.
3. Check that the resulting path is `.claude/skills/lovable-prd-generator/SKILL.md`. The files should not be inside an extra `lovable-prd-generator-main` subfolder.
4. Start a new Claude Code session in that project folder.
5. Enter:

```text
/lovable-prd-generator Create a Lovable-ready MVP PRD for [your app idea]. Include phased implementation prompts.
```

Claude Code documents project skills under `.claude/skills/<skill-name>/SKILL.md` and direct invocation with `/skill-name`. See the [official Claude Code skills guide](https://code.claude.com/docs/en/skills) for setup and troubleshooting. These instructions concern local Claude Code sessions; other Claude products have separate setup steps.

For another Agent Skills host, follow that product's installation instructions and include the supporting files.

### 3. Use your PRD in Lovable

1. Review the generated PRD's confirmed decisions, assumptions, release scope and open questions.
2. Save/download the PRD as a Markdown (`.md`) file.
3. Attach it to your Lovable project and paste the kickoff prompt included in the PRD.
4. Ask Lovable to implement the first phase, verify the acceptance checks, and continue one phase at a time.

This skill produces requirements and build prompts. It does not automatically build, connect services, or deploy your application.

## Example prompts

- "Create a Lovable-ready MVP PRD for an AI invoice generator for freelancers. English and Indonesian, private pilot first."
- "Turn this messy feature list into a phased Lovable V2 PRD. Challenge the MVP scope and include tests and RLS."
- "Update this PRD after switching the pilot audience to teachers. Keep confirmed requirements and give me revised build prompts."


## Compatibility

The structure follows the [Agent Skills specification](https://agentskills.io/specification) (YAML frontmatter in `SKILL.md`, supporting `references/`, `assets/` and `examples/`). Different agent products have their own install paths and limitations. Setup instructions were checked against the linked Claude Code documentation on 16 October 2026; this is not a claim of end-to-end testing in every host. Lovable features and integrations should be verified against current [Lovable documentation](https://docs.lovable.dev/).

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
