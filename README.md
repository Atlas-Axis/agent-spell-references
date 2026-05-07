# Agent Spell References

Canonical operational reference materials for Agent teams preparing Spells and infrastructure deployments within the Sky Ecosystem.

This repository represents the initial v1 set of canonical reference materials for Agent operational processes. Additional templates, examples, workflows, and guidance may be added over time as Agent onboarding and deployment processes mature.**Note:** The Agent Spell Reviewer Checklist currently remains maintained in its existing canonical location here: https://github.com/sky-ecosystem/pe-checklists/blob/master/spell/star-spell-reviewer-checklist.md. Agents and reviewers should continue using that version until further alignment on repository structure, and migration decisions is completed.

This repository is intended to operationalize the relevant Atlas requirements and processes. Direct Atlas references will be referenced here once the associated Atlas edits are finalized.

## Contents

```
agent-spell-references/
├── technical-scope-template.md
├── deployment-checklist.md
├── examples/
│   ├── star-spell-technical-scope-example.md
│   └── non-spell-technical-scope-example.md
├── .claude/skills/
└── .github/workflows/
```

## Agent Guide

### Technical Scope Template (`technical-scope-template.md`)

**What it is:** A standardized template for announcing any infrastructure changes (on- or offchain) with enough technical detail for an external team to review without additional context.

**Security-sensitive sections:** The template introduces sections for Technical risk self-assessment, Emergency actions, and Monitoring. These sections enforce a rigorous security mindset by requiring teams to consider risks, emergency responses, and monitoring for every infrastructure change. Because these sections may contain information that could be exploited if publicly disclosed, they are handled through a separate private submission process.

**Where to submit:** The filled-in template must be submitted through both public and private channels:

- **Public:** All sections except the security-sensitive sections defined above must be published as a Forum post on the Sky Forum.
- **Private:** The full template, including the security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, and Monitoring), must be submitted internally through a dedicated private repository. Until that repository is established, the full template should be shared via HackMD to Core GovOps and any other relevant parties.

For Technical Scopes associated with a Prime Spell, submissions must be completed by **Wednesday at 16:00 UTC during Week 1 of the Prime Spell Process**.

### Deployment Checklist (`deployment-checklist.md`)

**What it is:** A standardized checklist for contract deployments covering deployer hygiene, foundry setup, test deployments, and verification.

**When to use:** For every contract deployment, whether part of a Spell or not.

**Where to submit:** The completed checklist must be attached to the deployment script Pull Request or, if no Pull Request exists, documented in a GitHub issue within the repository of the deployed code.

## Getting started

Clone this repository:

```bash
git clone https://github.com/Atlas-Axis/agent-spell-references.git
```

## Before you start

> [!IMPORTANT]
> Before using any reference material, you must pull the latest version to ensure your copy is aligned with the source repository:
> ```bash
> cd agent-spell-references
> git pull origin main
> ```

Do not modify the template files directly. When filling out a template, copy it to a new file with a descriptive name (e.g., `technical-scope-may-2026-spell.md`) and work from the copy. This ensures `git pull` always updates the templates cleanly without merge conflicts.

## Maintenance

### Technical Scope Template

The Technical Scope Template is maintained by Core GovOps. All changes must be submitted as a Pull Request in this repository and require two (2) approvals, one (1) from each Core Spell Team, before they can be merged.     

### Deployment Checklist

The Deployment Checklist is maintained by Core GovOps. All changes must be submitted as a Pull Request in this repository and require two (2) approvals, one (1) from each Core Spell Team, before they can be merged.   

