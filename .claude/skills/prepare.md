# Prepare Operational Reference

Sets up a Technical Scope or Deployment Checklist for a planned infrastructure change, guides the user through filling it in, and tracks completion.

## Process

### 1. Determine Document Type

Ask the user which document they need:

1. **Technical Scope** — for announcing any infrastructure change (on- or offchain) with enough technical detail for external review
2. **Deployment Checklist** — for contract deployments covering deployer hygiene, foundry setup, test deployments, and verification

If unclear, ask about the work: if they're deploying contracts, they likely need both (Technical Scope first, then Deployment Checklist for each deployment within it).

### 2. Create the File

**Technical Scope:**
```bash
cp templates/technical-scope-template.md technical-scope-<descriptive-name>.md
```
Use kebab-case. Include date or spell cycle if applicable (e.g., `technical-scope-grove-may-2026-spell.md`).

**Deployment Checklist:**
```bash
cp checklists/deployment-checklist.md deployment-checklist-<descriptive-name>.md
```

### 3. Walk Through the Document

Read the template or checklist and the relevant examples in `examples/` to understand what good looks like. Then guide the user section by section.

**General rules (Technical Scope):**
- No sections can be skipped or removed. If non-applicable, provide a one-line explanation why.
- All addresses must be in checksummed EIP-55 format.
- All notes and warnings must be removed from the filled-in version before submission.

**General rules (Deployment Checklist):**
- Every checkbox must be checked or explicitly marked as not applicable with an explanation.
- A different deployer EOA must be used across different chains.
- The deployer EOA must not be used for other transactions besides deployments and configuration.

For each section, ask the user for the information, fill it in, and move to the next. Refer to the examples in `examples/technical-scope/` to calibrate the expected level of detail — the examples include `[ADDED]` markers showing what was missing from real submissions and had to be supplemented.

### 4. Completion Checklist

After filling in the document, run through this checklist with the user. Print it and check each item together.

**Technical Scope completion checklist:**
- [ ] Introduction provides enough context for an outsider to review without additional information
- [ ] Every section is filled in or has a one-line explanation of why it is not applicable
- [ ] All `> [!NOTE]` and `> [!WARNING]` blocks removed from the filled-in version
- [ ] All addresses are in checksummed EIP-55 format
- [ ] All audit report links point to the auditor's website (not internal copies)
- [ ] All code links use the audited commit hash
- [ ] Every pre-deployed contract has: chain, address, deployment trace, code verification, constructor args with external sources, ownership/roles, explorer verification, deployer privilege status
- [ ] Every constructor argument and function argument has an external source or explanation of how to verify
- [ ] Security-sensitive sections (Technical Risk Self-Assessment, Emergency Actions, Monitoring) are filled in
- [ ] Security-sensitive sections are clearly separated and will NOT be included in the Forum post

**Deployment Checklist completion checklist:**
- [ ] Foundry version documented
- [ ] Audit commit hash identified and recorded
- [ ] Repository freshly cloned at the audit commit
- [ ] Deployer address verified and has sufficient gas
- [ ] Deployment command documented
- [ ] Test deployment on private Tenderly testnet completed and inspected
- [ ] Production deployment executed with `--slow --verify`
- [ ] All checks from the technical doc performed (constructor args, optimizations, bytecode, ownership)
- [ ] Independent verification by another team member completed

### 5. Submission Reminder

**Technical Scope submission:**

- **Public (Forum post):** All sections EXCEPT Technical Risk Self-Assessment, Emergency Actions, and Monitoring.
- **Private:** The full template including security-sensitive sections. Submit via the dedicated private repository, or via HackMD to the Executive Process Liaison.

**Prime Spell deadlines:**
- Sky Governance path: by **Wednesday, 16:00 UTC of Week 1**
- Independent Governance path: by **end of Friday of Week 1**

**Deployment Checklist submission:** Attach to the deployment script Pull Request, or if no PR exists, document in a GitHub issue within the repository of the deployed code.

Tell the user: "Run `/pre-submission-review` to validate the completed document against the requirements and examples before submitting."
