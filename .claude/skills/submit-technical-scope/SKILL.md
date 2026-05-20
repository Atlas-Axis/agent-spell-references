---
name: submit-technical-scope
description: >
  End-to-end Technical Scope submission: copies the latest template, opens
  it for editing, reviews the completed document, submits via PR to the
  private submissions repo, and requests Atlas Axis review.
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

# Submit Technical Scope

## Step 1 — Get the Latest Template

Ensure the user is on the latest main:

```bash
git checkout main && git pull
```

Ask the user for a short description of the infrastructure change (e.g., "grove-may-2026-spell", "morpho-vault-deployment").

Copy the template:

```bash
cp templates/technical-scope-template.md <description>.md
```

## Step 2 — Open for Editing

Open the file:

```bash
open <description>.md
```

Tell the user:

> The template is open in your editor. Fill in each section — refer to the examples in `examples/technical-scope/` for the expected level of detail.
>
> **Rules:**
> - No sections can be skipped. If non-applicable, write a one-line explanation.
> - All addresses must be in checksummed EIP-55 format.
> - Remove all `> [!NOTE]` and `> [!WARNING]` blocks before you're done.
>
> When you're ready for review, come back and let me know.

**Stop here and wait for the user to come back.**

## Step 3 — Pre-Submission Review

When the user says they're ready, read the completed file and both examples in `examples/technical-scope/`. Pay attention to `[ADDED]` markers in the examples — these are the most commonly missing items.

Check each category and report findings as **Blocker** (must fix) / **Warning** (should fix) / **Note** (observation):

**Structure and completeness:**
- Every section from the template is present
- No sections empty without explanation
- All `> [!NOTE]` and `> [!WARNING]` instruction blocks removed
- Security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, Monitoring) filled in

**Address hygiene:**
- Every address in checksummed EIP-55 format
- Every address has a block explorer link
- Every address has an external source URL or verification explanation

**Verification and sourcing:**
- Audit report links point to the auditor's website
- Code links use the audited commit hash
- Every constructor argument and function argument has an external source
- Every role/privilege caller has an external source for the address

**Consistency:**
- Addresses match across sections
- Chain names consistent throughout
- Contract names match between Trusted Addresses and Pre-deployed Contracts
- Proposed actions reference contracts listed earlier in the document

**Security-sensitive sections:**
- Technical Risk Self-Assessment lists specific risks with mitigations, not generic statements
- Emergency Actions are actionable (specific calls, staged transactions)
- Monitoring lists specific invariants and which team monitors them

After the report, give a verdict: **Ready to submit** or **Needs fixes**. If blockers exist, the user must fix them and come back. Repeat this step until clean.

## Step 4 — Submit PR

Ask the user for their fork of the submissions repo (`Atlas-Axis/technical-scope-submissions-template`). If they don't have a fork yet, tell them to fork it first.

```bash
git clone https://github.com/<their-org>/technical-scope-submissions-template.git /tmp/submission
cd /tmp/submission
git checkout -b submission/<description>
cp <path-to-completed-file> submissions/<description>.md
git add submissions/<description>.md
git commit -m "Technical Scope: <description>"
git push -u origin submission/<description>
gh pr create --title "Technical Scope: <description>" --body "Submission for review."
gh pr edit <pr-number> --add-reviewer aa-lex,kohla-sky
```

Give the user the PR URL.

## Step 5 — Forum Post

Offer to prepare the public version by stripping the three security-sensitive sections. Show the user the result for confirmation. Remind them: the PR is the private submission, the Forum post is the public one. Both are required.
