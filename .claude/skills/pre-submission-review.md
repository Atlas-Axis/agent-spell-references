# Pre-Submission Review

Reviews a completed Technical Scope or Deployment Checklist against the submission requirements and examples before the user submits it.

## Process

### 1. Identify the Document

Ask the user which file to review, or detect it from the working directory (any file matching `technical-scope-*.md` or `deployment-checklist-*.md`).

### 2. Read the Source Materials

Before reviewing, read:
- The original template (`templates/technical-scope-template.md` or `checklists/deployment-checklist.md`) to know what is required
- Both examples in `examples/technical-scope/` to calibrate expectations — pay attention to `[ADDED]` markers (information that was missing from real submissions) and `[MISSING]` markers (gaps the examples flagged but did not fill)
- The submission instructions in the root `README.md`

### 3. Run the Review

Check the document against each of the following categories. Report findings grouped by severity: **Blocker** (must fix before submission), **Warning** (should fix), **Note** (observation).

**Structure and completeness:**
- Every section from the template is present
- No sections are empty without an explanation of why they are not applicable
- All `> [!NOTE]` and `> [!WARNING]` instruction blocks have been removed
- Security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, Monitoring) are present and filled in

**Address hygiene:**
- Every address is in checksummed EIP-55 format
- Every address includes a block explorer link
- Every address has an external source URL or explanation of how it can be verified
- No address appears without context (contract name, role, or purpose)

**Verification and sourcing:**
- Every audit report links to the auditor's website (not internal documents or Google Drive)
- Every code reference uses the audited commit hash, not `main` or `latest`
- Every constructor argument has an external source for its value
- Every function argument has an external source for its value
- Every role/privilege caller has an external source for the address

**Consistency:**
- Addresses referenced in multiple sections are consistent (same checksummed format, same contract name)
- Chain names are consistent throughout
- Contract names match between the Trusted Addresses table and Pre-deployed Contracts list
- Proposed actions reference contracts that were listed in Pre-deployed Contracts or Trusted Addresses

**Compared to examples:**
- Level of detail is comparable to the examples in `examples/technical-scope/`
- Areas where the examples had `[ADDED]` markers are filled in (these are the most commonly missing items)
- Areas where the examples had `[MISSING]` markers are either filled in or explicitly acknowledged as pending

**Security-sensitive sections:**
- Technical Risk Self-Assessment lists specific risks with mitigations, not generic statements
- Emergency Actions are actionable (specific contract calls, staged transactions, not just "freeze the protocol")
- Monitoring lists specific invariants and which team monitors them

**Deployment Checklist specific (if applicable):**
- Foundry version is documented
- Audit commit hash is recorded
- Test deployment on Tenderly is confirmed
- Independent verification by another team member is confirmed
- Every checkbox is checked or marked not applicable with an explanation

### 4. Report Findings

Present findings as a numbered list grouped by severity. For each finding, quote the specific text or section and explain what needs to change.

After the report, give a clear verdict:
- **Ready to submit** — no blockers, warnings are minor
- **Needs fixes** — blockers present, list what must be addressed

### 5. Forum Post Preparation

If the document is a Technical Scope and the user is ready to submit, offer to prepare the Forum post version:
- Strip the three security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, Monitoring)
- Confirm the remaining content is suitable for public posting
- Remind the user to submit the full version (including security-sensitive sections) privately
