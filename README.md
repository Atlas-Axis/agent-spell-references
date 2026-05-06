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

### Technical Scope Template

**What it is:** A standardized template for announcing any infrastructure changes (on- or offchain) with enough technical detail for an external team to review without additional context.

**Mandatory:** Yes — for any infrastructure change, including Spells, vault deployments, and other on- or offchain changes.

**When to submit:** By Wednesday, 16:00 UTC of week 1 of the Prime Spell Process.

**Security-sensitive sections:** The template introduces sections for Technical risk self-assessment, Emergency actions, and Monitoring. These sections enforce a rigorous security mindset by requiring teams to consider risks, emergency responses, and monitoring for every infrastructure change. Because these sections may contain information that could be exploited if publicly disclosed, they are handled through a separate private submission process.

**Where to submit:** The completed template must be submitted to both:

- **Public:** All sections except the security-sensitive sections must be posted as a Forum post on the Sky Forum.
- **Private:** The full template including the security-sensitive sections (Technical risk self-assessment, Emergency actions, Monitoring) must be submitted internally in a private repo that will be specified later. In the interim, the full template should be published as a HackMD and circulated with the relevant parties.

### Deployment Checklist

**What it is:** A standardized checklist for contract deployments covering deployer hygiene, foundry setup, test deployments, and verification.

**Mandatory:** Yes — for all contract deployments.

**When to use:** For every contract deployment, whether part of a Spell or not.

**Where to submit:** The completed checklist must be attached to the deployment script Pull Request or, if no Pull Request exists, documented in a GitHub issue within the repository of the deployed code.

### Agent Spell Reviewer Checklist

**What it is:** A standardized checklist defining the steps for Agent Spell Reviewers.

**Mandatory:** Yes — for all Agent Spells, effective with the June 18, 2026 Executive Vote.

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

> [!TIP]
> Remember to remove all notes and warnings from the templates before posting or submitting.

## Maintenance

### Technical Scope Template

The Technical Scope Template is maintained by Core GovOps. Any changes to the content of the template require two (2) approvals, one (1) from Core GovOps and one (1) from a Core Spell Team.

### Deployment Checklist

The Deployment Checklist is maintained by Core GovOps. Any changes to the content of the checklist require two (2) approvals, one (1) from Core GovOps and one (1) from a Core Spell Team.

### Agent Spell Reviewer Checklist

The Agent Spell Reviewer Checklist is maintained by the Core Spell Teams. Agent Spell Crafters and Reviewers, including external auditors, are encouraged to extend and improve the checklist as improvements are identified during Spell crafting. Any changes to the content of the checklist are submitted as Pull Requests to this repository and require two (2) approvals, one (1) from each Core Spell Team, before they can be merged.
