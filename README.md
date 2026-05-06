# Agent Spell References

Canonical reference materials for Agent teams preparing and reviewing Spells and infrastructure deployments within the Sky Ecosystem.

## Contents

```
agent-spell-references/
├── technical-scope-template.md
├── checklists/
│   ├── agent-spell-reviewer-checklist.md
│   └── deployment-checklist.md
├── examples/
│   ├── star-spell-technical-scope-example.md
│   └── non-spell-technical-scope-example.md
├── .claude/skills/
└── .github/workflows/
```

## Agent Guide

### Technical Scope Template (`technical-scope-template.md`)

**What it is:** A standardized template for announcing any infrastructure changes (on- or offchain) with enough technical detail for an external team to review without additional context. The filled-in Technical Scope must be submitted 

**Security-sensitive sections:** The template introduces sections for Technical risk self-assessment, Emergency actions, and Monitoring. These sections enforce a rigorous security mindset by requiring teams to consider risks, emergency responses, and monitoring for every infrastructure change. Because these sections may contain information that could be exploited if publicly disclosed, they are handled through a separate private submission process.

**Where to submit:** The filled-in template must be submitted through both public and private channels:

- **Public:** All non-security-sensitive sections must be published as a Forum post on the Sky Forum. Please ensure that all security-sensitive sections are omitted. 
- **Private:** The full template, including the security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, and Monitoring), must be submitted internally through a private repository to be designated at a later stage. Until that repository is established, the full template should be shared via HackMD and circulated only with the relevant parties.

### Deployment Checklist (`checklists/deployment-checklist.md`)

**What it is:** A standardized checklist for contract deployments covering deployer hygiene, foundry setup, test deployments, and verification.

**When to use:** For every contract deployment, whether part of a Spell or not.

**Where to submit:** The completed checklist must be attached to the deployment script Pull Request or, if no Pull Request exists, documented in a GitHub issue within the repository of the deployed code.

### Agent Spell Reviewer Checklist (`checklists/agent-spell-reviewer-checklist.md`)

**What it is:** A standardized checklist defining the steps for Agent Spell Reviewers. 

**When to use:** For every Agent Spell.

**Where to submit:** The completed checklist must be included in the Spell review Pull Request prior to Spell handover.

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

The Technical Scope Template is maintained by Core GovOps. All changes must be submitted as a Pull Request in this repository. Core Spell Teams may also propose changes. Every Pull Request requires approval from Core GovOps and at least one Core Spell Team that is not the proposer.

### Deployment Checklist

The Deployment Checklist is maintained by Core GovOps. All changes must be submitted as a Pull Request in this repository. Core Spell Teams may also propose changes. Every Pull Request requires approval from Core GovOps and at least one Core Spell Team that is not the proposer.

### Agent Spell Reviewer Checklist

The Agent Spell Reviewer Checklist is maintained by the Core Spell Teams. Agent Spell Crafters and Reviewers, including external auditors, are encouraged to extend and improve the checklist as improvements are identified during Spell crafting. Any changes to the content of the checklist are submitted as Pull Requests to this repository and require two (2) approvals, one (1) from each Core Spell Team, before they can be merged.
