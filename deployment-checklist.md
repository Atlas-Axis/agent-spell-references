# Deployment Checklist

### General rules
- [ ] A different deployer EOA shall be used across different chains (to prevent a situation where the same address on different chains has a different name and source code).
- [ ] A deployer EOA shall not be used for other transactions besides the deployments and configuration of contracts.
- [ ] Avoid storing a private key in the env files or in the bash history. Prefer using a password-protected keystore or a hardware wallet.

### Deployment preparation
- [ ] Update your foundry to the latest stable version, and ensure that the updated version is at least one week old (to avoid a not-yet-detected supply chain attack).
- [ ] Note down your foundry version used for the deployments by documenting `foundryup` logs:
- [ ] Find the latest audits for the contract to be deployed. If there are 2 reports, compare commit hashes between them and inspect the diff. If the diff is safe, note down the latest of the two commit hashes.
  - The commit URL:
- [ ] Freshly clone the repository with the contract at the commit determined above.
- [ ] Init submodules and install npm packages using the appropriate package manager (npm, yarn, pnpm – based on the lockfile type present in the repository).
- [ ] Check the deployer address (e.g., using `cast wallet address`) to match the expected value and expected transaction history.
- [ ] Ensure the deployer has enough gas tokens.
- [ ] Document the command planned to be used to perform the deployment. Prefer writing a foundry script for anything that requires more than one transaction.

```bash
# Paste the exact deployment command here
```

- [ ] Perform a test deployment using a fresh *private* Tenderly testnet. Then, inspect submitted transactions to match the desired outcome.

### Deployment
- [ ] Set production RPC URL (only trusted RPC provider shall be used to avoid poisoning attacks).
- [ ] Set API key for the verification provider (e.g., Etherscan) compatible with the target chain.
- [ ] Execute the same command used for testnet deployment, but with `--slow --verify`.
- [ ] Inspect the transaction history of the deployer.
- [ ] Perform all relevant checks documented in the technical doc (constructor arguments, optimizations, bytecode verify, ownership transfer).
- [ ] Independently verify the deployment by another member of the team.
