# [Template test] Technical scope for a Star spell (April 23 Grove's spell)

> [!IMPORTANT]
> Source technical scope: https://forum.skyeco.com/t/april-23-2026-proposed-changes-to-grove-for-upcoming-spell/27829

> [!NOTE]
> ### Notes on the test of the template
> - The orange text is used to highlight parts that are missing in the original doc and were written by us.
> - The skipped/missing is used to avoid populating a lot of missing information, since the structure will follow the same format as already illustrated.

## Introduction

### Goal of this update

This update proposes eight changes across Ethereum, Avalanche, and Sky Core to expand Grove's Liquidity Layer capacity and cross-chain reach:

1. [Sky Core] Increase ALLOCATOR-BLOOM-A Autoline Gap to 500M
2. [Ethereum] Increase USDS Mint Rate Limits
3. [Ethereum] Onboard USDS to Centrifuge JTRSY
4. [Ethereum] Onboard USDS SkyLink Transfers to Avalanche
5. [Avalanche] Upgrade ForeignController to v1.8.0
6. [Avalanche] Onboard USDS SkyLink Transfers to Ethereum
7. [Avalanche] Increase CCTP USDC Transfer to Ethereum Rate Limit
8. [Avalanche] Onboard USDS/USDC Curve Stableswap Swaps & LP

### Required context

- SkyLink bridge to Avalanche was launched in the `2026-04-09` core spell https://forum.skyeco.com/t/skylink-bridge-to-avalanche/27825

### The reason(s) behind this update

1. **ALLOCATOR-BLOOM-A Autoline Gap**: Increases the DC-IAM gap from 250M to 500M to match Grove's internal rate limit of 500M per day.
2. **USDS Mint Rate Limits**: Increased to 500M USDS max/slope to support higher JTRSY deposit rate limits and growing allocation needs without bottlenecking at the mint step.
3. **JTRSY USDS Vault**: Allows Grove to deposit USDS directly into JTRSY without first converting to USDC via the PSM.
4. **USDS SkyLink (ETH → AVAX)**: Enables USDS bridging to Avalanche for deployment into the Curve USDS/USDC pool and other Avalanche-based opportunities.
5. **ForeignController Upgrade**: Aligns the Avalanche controller with Mainnet v1.8.0 for feature parity; covered by the same audit cycle.
6. **USDS SkyLink (AVAX → ETH)**: Enables USDS to be bridged back from Avalanche to Ethereum.
7. **CCTP USDC Rate Limit**: Removes the bottleneck on repatriating USDC from Avalanche to Ethereum.
8. **Curve USDS/USDC Stableswap**: Provides liquidity and swap capability on Avalanche for bridged USDS.

### Timing of this update (in stages, if needed)

- Star Spell crafted by April 13, 2026
- Star Spell reviewed and handed over by April 16, 2026
- Core spell handed over by April 23, 2026
- Executed on April 27, 2026 (due to enabled office hours)

## Relevant audits

1. Grove ALM Controller v1.8.0
    - External URL to the audit report: [Certora Audit](https://www.certora.com/reports/grove-alm) & [ChainSecurity Audit](https://www.chainsecurity.com/security-audit/grove-alm-controller-2)
    - Exact commit at which the audit is concluded: [2c6e3d4](https://github.com/grove-labs/grove-alm-controller/tree/2c6e3d4297d5f244894d05f3dbbe47bcada34712)
    - Relevant scope of the audit:
        - ForeignController.sol (item 5)
    - Diff with another independent audit, if any: No diffs

## Trusted addresses

| Contract name | Address with URL | Source URL |
|---|---|---|
| USDS OFT Adapter on Ethereum | [`eth:0x1e1D42781FC170EF9da004Fb735f56F0276d01B8`](https://etherscan.io/address/0x1e1D42781FC170EF9da004Fb735f56F0276d01B8) | USDS_OFT from [chainlog](https://chainlog.skyeco.com/) |
| USDS OFT Adapter on Avalanche | [`avax:0x4fec40719fD9a8AE3F8E20531669DEC5962D2619`](https://snowtrace.io/address/0x4fec40719fD9a8AE3F8E20531669DEC5962D2619) | [SkyLink Bridge to Avalanche forum post](https://forum.skyeco.com/t/skylink-bridge-to-avalanche/27825) |
| Grove's current ForeignController v1.6.0 on Avalanche | [`avax:0x734266cE1E49b148eF633f2E0358382488064999`](https://snowtrace.io/address/0x734266cE1E49b148eF633f2E0358382488064999) | [Original forum post](https://forum.skyeco.com/t/august-21-2025-proposed-changes-to-grove-for-upcoming-spell/26993/7) |
| Grove's ALM Proxy on Avalanche | [`avax:0x7107DD8F56642327945294a18A4280C78e153644`](https://snowscan.xyz/address/0x7107DD8F56642327945294a18A4280C78e153644) | [Original forum post](https://forum.skyeco.com/t/august-7-2025-proposed-changes-to-grove-for-upcoming-spell/26883) |
| Grove's RateLimits on Avalanche | [`avax:0x6ba2e6bCCe3d2A31F1e3e1d3e11CDffBaA002A21`](https://snowscan.xyz/address/0x6ba2e6bCCe3d2A31F1e3e1d3e11CDffBaA002A21) | [Original forum post](https://forum.skyeco.com/t/august-7-2025-proposed-changes-to-grove-for-upcoming-spell/26883) |
| Grove's Executor on Avalanche | [`avax:0x4b803781828b76EaBF21AaF02e5ce23596b4d60c`](https://snowscan.xyz/address/0x4b803781828b76EaBF21AaF02e5ce23596b4d60c#code) | [Original forum post](https://forum.skyeco.com/t/august-7-2025-proposed-changes-to-grove-for-upcoming-spell/26883) |
| DssAutoLine (Sky Core) | [`eth:0xC7Bdd1F2B16447dcf3dE045C4a039A60EC2f0ba3`](https://etherscan.io/address/0xC7Bdd1F2B16447dcf3dE045C4a039A60EC2f0ba3) | MCD_IAM_AUTO_LINE from [chainlog](https://chainlog.skyeco.com/) |
| Centrifuge Hub | [`eth:0xA4A7Bb3831958463b3FE3E27A6a160F764341953`](https://etherscan.io/address/0xA4A7Bb3831958463b3FE3E27A6a160F764341953#code) | [Centrifuge docs](https://docs.centrifuge.io/developer/protocol/deployments/) |
| CurveStableswapFactoryNG on Avalanche | [`avax:0x1764ee18e8B3ccA4787249Ceb249356192594585`](https://snowscan.xyz/address/0x1764ee18e8B3ccA4787249Ceb249356192594585#code) | Factory on Avalanche from [the Curve docs](https://dev.curve.finance/deployments/amm/#stableswap-ng) |
| Uniswap Swap Router on Avalanche | [`avax:0xbb00FF08d01D300023C629E8fFfFcb65A5a578cE`](https://snowscan.xyz/address/0xbb00FF08d01D300023C629E8fFfFcb65A5a578cE#code) | SwapRouter02 from [the Uniswap gov portal](https://gov.uniswap.org/t/official-uniswap-v3-deployments-list/24323/3) |
| Uniswap Nonfungible Position Manager on Avalanche | [`avax:0x655C406EBFa14EE2006250925e54ec43AD184f8B`](https://snowscan.xyz/address/0x655C406EBFa14EE2006250925e54ec43AD184f8B#code) | NonfungiblePositionManager from [the Uniswap gov portal](https://gov.uniswap.org/t/official-uniswap-v3-deployments-list/24323/3) |

## Pre-deployed contracts

1. **JTRSY USDS Vault (Centrifuge V3)**
    - Chain name: Ethereum
    - Contract address (linked to the explorer): [eth:0x381f4f3b43c30b78c1f7777553236e57bb8ae9ff](https://etherscan.io/address/0x381f4f3b43c30b78c1f7777553236e57bb8ae9ff)
    - Deployment transaction trace: [tx](https://dashboard.tenderly.co/tx/0x13fe777b10a2d3404d94314a0fe11db7b32b4ddf6fcdec1ccf5b66f70131e070)
    - Code verification
        - If deployed by a factory
            - Contract being called: Centrifuge Hub
            - External docs page with this address: [Centrifuge docs](https://docs.centrifuge.io/developer/protocol/deployments/)
            - Function being called: [`updateVault(PoolId poolId, ShareClassId scId, AssetId assetId, bytes32 vaultOrFactory, VaultUpdateKind kind, uint128 extraGasLimit, address refund)`](https://etherscan.io/address/0xA4A7Bb3831958463b3FE3E27A6a160F764341953#code#F1#L284)
            - Function arguments
                1. `PoolId poolId`
                    - Argument value: `281474976710662`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: …skipped
                2. `ShareClassId scId`
                    - Argument value: `0x00010000000000060000000000000001`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: …skipped
                3. `AssetId assetId`
                    - Argument value: `5192296858534827628530496329220102`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: …skipped
                4. `bytes32 vaultOrFactory`
                    - Argument value: `0x55cde53b7dbc24336e34ffe233af8df10f72f0be000000000000000000000000`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: …skipped
                5. `VaultUpdateKind kind`
                    - Argument value: `0`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: [DeployAndLink](https://etherscan.io/address/0xd9531AC47928c3386346f82d9A2478960bf2CA7B#code#F9#L46)
                6. `uint128 extraGasLimit`
                    - Argument value: `0`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: …skipped
                7. `address refund`
                    - Argument value: `0x742d100011ffbc6e509e39dbcb0334159e86be1e`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: The deployer
    - Additional parameters configured on the contract by a privileged actor:
        …skipped
    - Ownership, roles, privilege callers:
        …skipped
    - Source code is verified on the block explorer: Yes
    - The deployer no longer has a privileged role: …skipped

2. **New Avalanche ForeignController v1.8.0**
    - Chain name: Avalanche
    - Contract address (linked to the explorer): [`avax:0x4236B772BEeEAFF57550Aa392A0f227C0b908Ce7`](https://snowscan.xyz/address/0x4236b772beeeaff57550aa392a0f227c0b908ce7#code)
    - Deployment transaction trace: [tx](https://snowscan.xyz/tx/0x698184883922cfc84f1935c686f1f989bf89077da51a4132b51ef415880b9050)
    - If deployed by EOA
        - Source code URL (at the audited commit hash): [https://github.com/grove-labs/grove-alm-controller/blob/2c6e3d4297d5f244894d05f3dbbe47bcada34712/src/ForeignController.sol](https://github.com/grove-labs/grove-alm-controller/blob/2c6e3d4297d5f244894d05f3dbbe47bcada34712/src/ForeignController.sol)
        - External URLs to the audit reports: [Certora Audit](https://www.certora.com/reports/grove-alm) & [ChainSecurity Audit](https://www.chainsecurity.com/security-audit/grove-alm-controller-2)
        - Deployed bytecode is verifiable using `forge verify-bytecode` at the audited commit: Yes
        - Constructor arguments:
            1. `address admin_`
                - Argument value: [`avax:0x4b803781828b76EaBF21AaF02e5ce23596b4d60c`](https://snowscan.xyz/address/0x4b803781828b76EaBF21AaF02e5ce23596b4d60c#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: `GROVE_EXECUTOR` on Avalanche
            2. `address proxy_`
                - Argument value: [`avax:0x7107DD8F56642327945294a18A4280C78e153644`](https://snowscan.xyz/address/0x7107DD8F56642327945294a18A4280C78e153644#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Grove's `ALM_PROXY` on Avalanche
            3. `address rateLimits_`
                - Argument value: [`avax:0x6ba2e6bCCe3d2A31F1e3e1d3e11CDffBaA002A21`](https://snowscan.xyz/address/0x6ba2e6bCCe3d2A31F1e3e1d3e11CDffBaA002A21#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Grove's `ALM_RATE_LIMITS` on Avalanche
            4. `address psm_`
                - Argument value: [`avax:0x00000000000000000000000000000000DeaDBeef`](https://snowscan.xyz/address/0x00000000000000000000000000000000DeaDBeef#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Dead address, no PSM deployment on Avalanche
            5. `address usdc_`
                - Argument value: [`avax:0xB97EF9Ef8734C71904D8002F8b6Bc66Dd9c48a6E`](https://snowscan.xyz/address/0xB97EF9Ef8734C71904D8002F8b6Bc66Dd9c48a6E#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: USDC on Avalanche from the [Circle docs](https://developers.circle.com/stablecoins/usdc-contract-addresses)
            6. `address cctp_`
                - Argument value: [`avax:0x28b5a0e9C621a5BadaA536219b3a228C8168cf5d`](https://snowscan.xyz/address/0x28b5a0e9C621a5BadaA536219b3a228C8168cf5d#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: CCTP TokenMessengerV2 address on Avalanche from the [Circle docs](https://developers.circle.com/cctp/references/contract-addresses#tokenmessengerv2)
            7. `address pendleRouter_`
                - Argument value: [`avax:0x00000000000000000000000000000000DeaDBeef`](https://snowscan.xyz/address/0x00000000000000000000000000000000DeaDBeef#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Dead address, no Pendle on Avalanche
            8. `address uniswapV3Router_`
                - Argument value: [`avax:0xbb00FF08d01D300023C629E8fFfFcb65A5a578cE`](https://snowscan.xyz/address/0xbb00FF08d01D300023C629E8fFfFcb65A5a578cE#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Uniswap `SwapRouter02` from [the Uniswap gov portal](https://gov.uniswap.org/t/official-uniswap-v3-deployments-list/24323/3)
            9. `address uniswapV3PositionManager_`
                - Argument value: [`avax:0x655C406EBFa14EE2006250925e54ec43AD184f8B`](https://snowscan.xyz/address/0x655C406EBFa14EE2006250925e54ec43AD184f8B#code)
                - External source of the value or an explanation of how this value can be verified, and who has to confirm it: `NonfungiblePositionManager` from [the Uniswap gov portal](https://gov.uniswap.org/t/official-uniswap-v3-deployments-list/24323/3)
    - Additional parameters configured on the contract by a privileged actor:
        None
    - Ownership, roles, privilege callers:
        - DEFAULT_ADMIN_ROLE
            - What actions can this role perform: [All admin actions](https://github.com/grove-labs/grove-alm-controller/blob/2c6e3d4297d5f244894d05f3dbbe47bcada34712/src/ForeignController.sol#L179-L268)
            - Address: [avax:0x4b803781828b76EaBF21AaF02e5ce23596b4d60c](https://snowscan.xyz/address/0x4b803781828b76EaBF21AaF02e5ce23596b4d60c#code)
            - External source of the address or an explanation of how this address can be verified, and who has to confirm it: Grove's Executor on Avalanche from the [original forum post](https://forum.skyeco.com/t/august-7-2025-proposed-changes-to-grove-for-upcoming-spell/26883)
    - Source code is verified on the block explorer: Yes
    - The deployer no longer has a privileged role: Yes

3. **USDS/USDC Curve Stableswap (Avalanche)**
    - Chain name: Avalanche
    - Contract address (linked to the explorer): [`avax:0xA9d7d3D7e68a0cae89FB33c736199172f405C8D3`](https://snowscan.xyz/address/0xa9d7d3d7e68a0cae89fb33c736199172f405c8d3#code)
    - Deployment transaction trace: [tx](https://dashboard.tenderly.co/tx/0x1597baa75da49d95a83818201ecad2aaf77b4f08db694d5f9fa24193bab67710)
    - Code verification
        - If deployed by a factory
            - Contract being called: [CurveStableswapFactoryNG](https://snowscan.xyz/address/0x1764ee18e8B3ccA4787249Ceb249356192594585#code)
            - External docs page with this address: [safe_proxy_factory v1.4.1 from the docs](https://docs.safe.global/advanced/smart-account-supported-networks?version=v1.4.1&page=26&expand=43114)
            - Function being called: `deploy_plain_pool(_name: String[32], _symbol: String[10], _coins: DynArray[address, MAX_COINS], _A: uint256, _fee: uint256, _offpeg_fee_multiplier: uint256, _ma_exp_time: uint256, _implementation_idx: uint256, _asset_types: DynArray[uint8, MAX_COINS], _method_ids: DynArray[bytes4, MAX_COINS], _oracles: DynArray[address, MAX_COINS])`
            - Function arguments:
                1. `_name`: `USDC/USDS` — …skipped
                2. `_symbol`: `USDCUSDS` — …skipped
                3. `_coins`: `["0xB97EF9Ef8734C71904D8002F8b6Bc66Dd9c48a6E","0x86Ff09db814ac346a7C6FE2Cd648F27706D1D470"]` — …skipped
                4. `_A`: `5969` — …skipped
                5. `_fee`: `268000` — …skipped
                6. `_offpeg_fee_multiplier`: `150000000000` — …skipped
                7. `_ma_exp_time`: `866` — …skipped
                8. `_implementation_idx`: `0` — …skipped
                9. `_asset_types`: `["0","0"]` — …skipped
                10. `_method_ids`: `["0x00000000","0x00000000"]` — …skipped
                11. `_oracles`: `["0x0000000000000000000000000000000000000000","0x0000000000000000000000000000000000000000"]` — …skipped
    - Additional parameters configured on the contract by a privileged actor: …skipped
    - Ownership, roles, privilege callers: …skipped
    - Source code is verified on the block explorer: Yes
    - The deployer no longer has a privileged role: …skipped

4. **ALM Relayer 2 (New SafeProxy msig wallet controlled by Grove)**
    - Chain name: Avalanche
    - Contract address: [`avax:0x9187807e07112359C481870feB58f0c117a29179`](https://snowscan.xyz/address/0x9187807e07112359C481870feB58f0c117a29179#code)
    - Deployment transaction trace: [tx](https://dashboard.tenderly.co/tx/0xd72a10c83613b3a4753b71e649857d26b6e18ef920714ca1a021f43ce815d8cc?trace=0.1.1.7.0.1.0.0.2.0)
    - Code verification
        - If deployed by a factory
            - Contract being called: [`avax:0x4e1DCf7AD4e460CfD30791CCC4F9c8a4f820ec67`](https://snowscan.xyz/address/0x4e1dcf7ad4e460cfd30791ccc4f9c8a4f820ec67#code) (SafeProxyFactory on Avalanche)
            - External docs page with this address: [safe_proxy_factory v1.4.1 from the docs](https://docs.safe.global/advanced/smart-account-supported-networks?version=v1.4.1&page=26&expand=43114)
            - Function being called: [`createProxyWithNonce(address _singleton, bytes memory initializer, uint256 saltNonce)`](https://snowscan.xyz/address/0x4e1dcf7ad4e460cfd30791ccc4f9c8a4f820ec67#code#F1#L52)
            - Function arguments:
                1. `address _singleton`
                    - Argument value: `0x41675C099F32341bf84BFc5382aF534df5C7461a`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: `safe.sol` from [the docs](https://docs.safe.global/advanced/smart-account-supported-networks?version=v1.4.1&page=26&expand=43114)
                2. `bytes initializer`
                    - Argument value: `0xb63e800d00000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000000000000000000000000000000000001000000000000000000000000bd89a1ce4dde368ffab0ec35506eece0b1ffdc540000000000000000000000000000000000000000000000000000000000000140000000000000000000000000fd0732dc9e303f09fcef3a7388ad10a83459ec99000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000005afe7a11e70000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001000000000000000000000000dc3baed945ce9c2fc4f4f2f24a02539bcaa7c8650000000000000000000000000000000000000000000000000000000000000024fe51f64300000000000000000000000029fcb43b46531bca003ddc8fcb67ffe91900c76200000000000000000000000000000000000000000000000000000000`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it: [decoded view](https://calldata.swiss-knife.xyz/decoder?calldata=0xb63e800d00000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000000000000000000000000000000000001000000000000000000000000bd89a1ce4dde368ffab0ec35506eece0b1ffdc540000000000000000000000000000000000000000000000000000000000000140000000000000000000000000fd0732dc9e303f09fcef3a7388ad10a83459ec99000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000005afe7a11e70000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001000000000000000000000000dc3baed945ce9c2fc4f4f2f24a02539bcaa7c8650000000000000000000000000000000000000000000000000000000000000024fe51f64300000000000000000000000029fcb43b46531bca003ddc8fcb67ffe91900c76200000000000000000000000000000000000000000000000000000000)
                3. `uint256 saltNonce`
                    - Argument value: `0`
                    - External source of the value or an explanation of how this value can be verified, and who has to confirm it:
    - Additional parameters configured on the contract by a privileged actor: …skipped
    - Ownership, roles, privilege callers:
        1. Owner
            - What actions can this role perform: Any
            - Address: [`avax:0x95a97815bC8DE7F2C7E4e2eFAF576a638c4d3e9F`](https://snowscan.xyz/address/0x95a97815bC8DE7F2C7E4e2eFAF576a638c4d3e9F)
            - External source of the address or an explanation of how this address can be verified, and who has to confirm it: None
        2. Owner
            - What actions can this role perform: Any
            - Address: [`avax:0x0eEC86649E756a23CBc68d9EFEd756f16aD5F85f`](https://snowscan.xyz/address/0x0eEC86649E756a23CBc68d9EFEd756f16aD5F85f)
            - External source of the address or an explanation of how this address can be verified, and who has to confirm it: None
        3. Owner
            - What actions can this role perform: Any
            - Address: [`avax:0xDC3baED945ce9C2fc4f4F2F24a02539BCaa7C865`](https://snowscan.xyz/address/0xDC3baED945ce9C2fc4f4F2F24a02539BCaa7C865)
            - External source of the address or an explanation of how this address can be verified, and who has to confirm it: None
    - Source code is verified on the block explorer: Yes
    - The deployer no longer has a privileged role: Still has, as expected

## Pre-configurations

These actions were part of the [same multisig transaction that deployed the new vault](https://dashboard.tenderly.co/tx/0x1597baa75da49d95a83818201ecad2aaf77b4f08db694d5f9fa24193bab67710).

1. **Update share price for the pool** `281474976710659` to `1.026620520499990000`

    …skipped

2. **Notify share price for the pool** `281474976710659` **centrifugeId `3`**

    …skipped

3. **Notify share price for the pool** `281474976710659` **centrifugeId `1`**

    …skipped

4. **Notify share price for the pool** `281474976710659` **centrifugeId `5`**

    …skipped

5. **Notify share price for the pool** `281474976710659` **centrifugeId `2`**

    …skipped

6. **Notify share price for the pool** `281474976710659` **centrifugeId `6`**

    …skipped

7. **Notify share price for the pool** `281474976710659` **centrifugeId `1`**

    …skipped

8. **Update share price for the pool** `281474976710660` to `1.020342178518390000`

    …skipped

9. **Notify share price for the pool** `281474976710660` **centrifugeId `5`**

    …skipped

10. **Notify share price for the pool** `281474976710660` **centrifugeId `1`**

    …skipped

11. **Notify share price for the pool** `281474976710660` **centrifugeId `2`**

    …skipped

12. **Notify share price for the pool** `281474976710660` **centrifugeId `3`**

    …skipped

13. **Notify share price for the pool** `281474976710660` **centrifugeId `6`**

    …skipped

14. **Notify asset price for the pool** `281474976710662`
    - Transaction trace URL: [Same tx as the deployment, done via multicall](https://dashboard.tenderly.co/tx/0x13fe777b10a2d3404d94314a0fe11db7b32b4ddf6fcdec1ccf5b66f70131e070?trace=0.3.1.7.0.1.0.0.2.0)
    - Contract being called: Centrifuge Hub
    - Function being called: [`notifyAssetPrice(PoolId poolId, ShareClassId scId, AssetId assetId, address refund)`](https://etherscan.io/address/0xA4A7Bb3831958463b3FE3E27A6a160F764341953#code#F1#L156)
    - Function arguments:
        1. `PoolId poolId`
            - Argument value: `281474976710662`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        2. `ShareClassId scId`
            - Argument value: `0x00010000000000060000000000000001`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        3. `AssetId assetId`
            - Argument value: `5192296858534827628530496329220102`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        4. `address refund`
            - Argument value: `0x742d100011ffbc6e509e39dbcb0334159e86be1e`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing

15. **Update share price for the pool** `281474976710667`
    - Transaction trace URL: [Same tx as the deployment, done via multicall](https://dashboard.tenderly.co/tx/0x13fe777b10a2d3404d94314a0fe11db7b32b4ddf6fcdec1ccf5b66f70131e070?trace=0.3.1.7.0.1.0.0.2.0)
    - Contract being called: Centrifuge Hub
    - Function being called: [`updateSharePrice(PoolId poolId, ShareClassId scId, D18 pricePoolPerShare, uint64 computedAt)`](https://etherscan.io/address/0xA4A7Bb3831958463b3FE3E27A6a160F764341953#code#F1#L315)
    - Function arguments:
        1. `PoolId poolId`
            - Argument value: `281474976710667`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        2. `ShareClassId scId`
            - Argument value: `0x000100000000000b0000000000000001`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        3. `D18 pricePoolPerShare`
            - Argument value: `993047025654000000`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing
        4. `uint64 computedAt`
            - Argument value: `1774440000`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: Missing

16. **Notify share price for the pool** `281474976710667` **centrifugeId `1`**

    …skipped

17. **Notify share price for the pool** `281474976710667` **centrifugeId `10`**

    …skipped

## Pre-requirements

1. Sky Core must increase the `gap` parameter in `MCD_IAM_AUTO_LINE` for `ALLOCATOR-BLOOM-A` from 250M to 500M.
    - Intended end goal: Allow Grove to draw up to 500M USDS per day without being bottlenecked by the autoline refresh cycle.
    - Why is it required to be done in advance: Grove's internal USDS mint rate limit is being set to 500M/day, but the DC-IAM gap currently caps draws at 250M per cycle — the two limits must be aligned.
    - Proof that it was done or planned to be done: We've requested this change from BA labs on XX.XX.XXXX

## Proposed actions

1. **Set LIMIT_USDS_MINT max to 500M USDS and slope to 500M USDS per day**
    - Business reason behind this action: Support higher JTRSY deposit rate limits and growing allocation throughput without bottlenecking at the mint step.
    - Who will perform this action: Grove spell
    - Important arguments:
        1. `uint256 maxAmount`
            - Argument value: `500M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        2. `uint256 slope`
            - Argument value: `500M USDS per day`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

2. **Register the JTRSY USDS Vault and configure deposit/withdrawal rate limits**
    - Business reason behind this action: …skipped
    - Who will perform this action: Grove spell
    - Important arguments:
        1. Vault
            - Argument value: [`eth:0x381f4F3B43C30B78C1f7777553236e57bB8AE9ff`](https://etherscan.io/address/0x381f4f3b43c30b78c1f7777553236e57bb8ae9ff)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: JTRSY USDS Vault deployed above.
        2. Underlying asset
            - Argument value: `USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: USDS from chainlog
        3. Deposit max amount
            - Argument value: `500M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        4. Deposit slope
            - Argument value: `500M USDS per day`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        5. Withdrawal amount
            - Argument value: `Unlimited`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

3. **Set USDS SkyLink (LayerZero V2) transfer rate limits from Ethereum to Avalanche, using the USDS OFT Adapter address to derive the rate limit key**
    - Business reason behind this action: …skipped
    - Who will perform this action: Grove spell
    - Important arguments:
        1. Asset
            - Argument value: [`eth:0x1e1D42781FC170EF9da004Fb735f56F0276d01B8`](https://etherscan.io/address/0x1e1D42781FC170EF9da004Fb735f56F0276d01B8)
            - External source of the value: USDS_OFT from chainlog
        2. USDS SkyLink (ETH → AVAX) max amount
            - Argument value: `50M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        3. USDS SkyLink (ETH → AVAX) slope
            - Argument value: `50M USDS per day`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

4. **Replace the existing Avalanche ForeignController v1.6.0 with the pre-deployed v1.8.0 controller, migrate existing rate limits and integrations, and configure ALM Relayer 2 as a relayer on the new controller**
    - Business reason behind this action: …skipped
    - Who will perform this action: Grove spell
    - Important arguments:
        1. Existing ForeignController (to be replaced)
            - Argument value: [`avax:0x734266cE1E49b148eF633f2E0358382488064999`](https://snowtrace.io/address/0x734266cE1E49b148eF633f2E0358382488064999)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it:
        2. New ForeignController
            - Argument value: [`avax:0x4236B772BEeEAFF57550Aa392A0f227C0b908Ce7`](https://snowscan.xyz/address/0x4236b772beeeaff57550aa392a0f227c0b908ce7)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: ForeignController deployed above
        3. An additional ALM relayer
            - Argument value: [`avax:0x9187807e07112359C481870feB58f0c117a29179`](https://snowtrace.io/address/0x9187807e07112359C481870feB58f0c117a29179)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: SafeProxy from the trusted addresses above

5. **Set USDS SkyLink (LayerZero V2) transfer rate limits from Avalanche to Ethereum using the USDS OFT Adapter (SkyOFTAdapterMintBurn) on Avalanche**
    - Business reason behind this action: Enable USDS to be bridged back from Avalanche to Ethereum
    - Who will perform this action: Grove spell
    - Important arguments:
        1. OFT Adapter
            - Argument value: [`avax:0x4fec40719fD9a8AE3F8E20531669DEC5962D2619`](https://snowtrace.io/address/0x4fec40719fD9a8AE3F8E20531669DEC5962D2619)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: USDS OFT Adapter on Avalanche from the [SkyLink Bridge to Avalanche forum post](https://forum.skyeco.com/t/skylink-bridge-to-avalanche/27825)
        2. USDS SkyLink (AVAX → ETH) max amount
            - Argument value: `20M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        3. USDS SkyLink (AVAX → ETH) slope
            - Argument value: `20M USDS per day`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

6. **Set the CCTP USDC transfer rate limit from Avalanche to Ethereum to unlimited (max and slope)**
    - Business reason behind this action: Remove the bottleneck on repatriating USDC from Avalanche back to Ethereum Mainnet
    - Who will perform this action: Grove spell
    - Important arguments:
        1. CCTP USDC (AVAX → ETH) max amount
            - Argument value: `Unlimited`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        2. CCTP USDC (AVAX → ETH) slope
            - Argument value: `Unlimited`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

7. **Configure swap and LP rate limits for the USDS/USDC Curve Stableswap pool on Avalanche.**
    - Business reason behind this action: Provide liquidity and stablecoin swap capability on Avalanche for bridged USDS; key component for distributing bridged USDS liquidity
    - Who will perform this action: Grove spell
    - Important arguments:
        1. Pool
            - Argument value: [`avax:0xA9d7d3D7e68a0cae89FB33c736199172f405C8D3`](https://snowscan.xyz/address/0xa9d7d3d7e68a0cae89fb33c736199172f405c8d3)
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: New Curve Stableswap pool deployed above
        2. Swap max amount
            - Argument value: `5M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        3. Swap slope
            - Argument value: `100M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        4. Swap maxSlippage
            - Argument value: `0.1%`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        5. LP deposit max amount
            - Argument value: `50M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        6. LP deposit slope
            - Argument value: `50M USDS`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs
        7. LP withdrawal amount
            - Argument value: `Unlimited`
            - External source of the value or an explanation of how this value can be verified, and who has to confirm it: To be confirmed by BA labs

## Post-checks

…skipped

## Technical risk self-assessment

…skipped

## Emergency actions

…skipped

## Monitoring

…skipped

## Research and additional notes

- Item 1 (USDS Mint Rate Limits) follows the same pattern as the PSM USDS/USDC swap rate limit increase in the [April 9, 2026 spell](https://forum.skyeco.com/t/april-9th-2026-proposed-changes-to-grove-for-upcoming-spell/27801).
- Item 2 (JTRSY USDS Vault): Centrifuge V3 supports multiple investment currencies per share class via ERC-7575. The JTRSY vault mirrors the existing USDC Centrifuge vault infrastructure and uses ERC-7540 for deposits/withdrawals. Risk assessment for JTRSY is available [here](https://forum.skyeco.com/t/risk-assessment-spark-tokenization-grand-prix-winners/26170). Centrifuge protocol deployments and addresses can be verified [here](https://docs.centrifuge.io/developer/protocol/deployments/).
- Item 3 (USDS SkyLink ETH → AVAX): The USDS OFT Adapter on Ethereum ([eth:0x1e1D42781FC170EF9da004Fb735f56F0276d01B8](https://etherscan.io/address/0x1e1D42781FC170EF9da004Fb735f56F0276d01B8)) is a SkyOFTAdapter sourced from the Chainlog; it is used to derive the LayerZero transfer rate limit key.
- Item 4 (ForeignController Upgrade): The ForeignController and MainnetController are part of the same v1.8.0 release cycle and covered by the same audit reports. The ALM Relayer 2 ([avax:0x9187807e07112359C481870feB58f0c117a29179](https://snowtrace.io/address/0x9187807e07112359C481870feB58f0c117a29179)) is a Gnosis Safe sharing the same address as mainnet ALM_RELAYER_2 in the registry.
- Item 5 (USDS SkyLink AVAX → ETH): The USDS OFT Adapter on Avalanche ([avax:0x4fec40719fD9a8AE3F8E20531669DEC5962D2619](https://snowtrace.io/address/0x4fec40719fD9a8AE3F8E20531669DEC5962D2619)) is a SkyOFTAdapterMintBurn sourced from the [SkyLink Bridge to Avalanche forum post](https://forum.skyeco.com/t/skylink-bridge-to-avalanche/27825).
- Item 7 (Curve USDS/USDC Stableswap): This onboarding follows a similar pattern to the [Curve AUSD/USDC Swap & LP onboarding on Mainnet](https://forum.skyeco.com/t/january-29-2026-proposed-changes-to-grove-for-upcoming-spell/27608) from the January 29, 2026 spell.
