# Wallet Network Assumptions

This document records the current wallet setup in Aiki and the assumptions that should be resolved before Stellar/Soroban wallet work begins.

## Current frontend wallet setup

The current frontend uses wagmi for an EVM-style wallet connection flow:

| Area | Current behavior |
|------|------------------|
| Provider wrapper | `lib/providers.tsx` wraps the app with `CustomWagmiProvider`. |
| Wallet library | `lib/wagmi-provider.tsx` uses `wagmi`, `@tanstack/react-query`, and wagmi connectors. |
| Active chain | `arbitrum` from `wagmi/chains`. |
| Wallet connectors | MetaMask is always enabled; WalletConnect is enabled when `NEXT_PUBLIC_PROJECT_ID` is configured. |
| Transport | Default `http()` transport for the Arbitrum chain id. |
| Onboarding UI | `components/wallet/CustomWalletModal.tsx` connects a wallet, collects email/password, stores a role, and redirects to a role dashboard. |
| Local persistence | `lib/user-storage.ts` stores wallet onboarding state locally in the browser. |

The current wallet flow should be treated as a prototype for Web3 onboarding. It is not yet a Stellar wallet integration.

## Current network assumptions

- The app currently assumes an EVM-compatible wallet address from wagmi.
- The configured chain is Arbitrum, not Stellar testnet, Stellar mainnet, or a Soroban RPC network.
- `NEXT_PUBLIC_PROJECT_ID` is a WalletConnect/Reown project id, not a Stellar network setting.
- There is no current Soroban RPC URL, Horizon URL, Stellar network passphrase, or Stellar contract id in the frontend wallet configuration.
- Dashboard routing is role-based (`student`, `instructor`, or `admin`) and is not currently tied to Stellar account roles.

## Future Stellar/Soroban assumptions

Before adding Stellar wallet behavior, the project should decide and document:

| Topic | Assumption to validate |
|-------|------------------------|
| Network | Whether the first Stellar target is testnet, futurenet, or mainnet. |
| Wallets | Which wallet providers should be supported for learners and instructors. |
| Account model | Whether Aiki stores Stellar public keys, federated addresses, contract ids, or linked EVM and Stellar identities. |
| Soroban RPC | Which RPC URL and network passphrase should be used in local development and production. |
| Certificates | Whether certificates are verified by Soroban contracts, off-chain metadata, or both. |
| Payments | Whether course payments use Stellar assets directly, a custodial flow, or a later payment abstraction. |
| Rewards | Whether learner rewards are tracked as off-chain progress first, then settled on-chain later. |

## Suggested environment variables

Future Stellar/Soroban work may need explicit variables rather than reusing EVM wallet settings:

```env
NEXT_PUBLIC_STELLAR_NETWORK=testnet
NEXT_PUBLIC_STELLAR_HORIZON_URL=https://horizon-testnet.stellar.org
NEXT_PUBLIC_SOROBAN_RPC_URL=https://soroban-testnet.stellar.org
NEXT_PUBLIC_STELLAR_NETWORK_PASSPHRASE=Test SDF Network ; September 2015
NEXT_PUBLIC_CERTIFICATE_CONTRACT_ID=PLACEHOLDER_CONTRACT_ID
```

These are placeholders only. Do not add production keys, secrets, or private signing material to frontend environment files.

## Open questions

1. Should Aiki keep the current EVM wallet prototype while Stellar wallet support is designed, or replace it once Stellar support is ready?
2. Which Stellar wallet should be the first supported wallet for learners?
3. Do instructors and learners need different wallet requirements?
4. Should course certificate verification happen on Soroban before payment and reward flows are introduced?
5. Where should wallet-to-role onboarding state live once the app moves beyond browser local storage?
6. What network should documentation use for examples: Stellar testnet, futurenet, or mainnet?
7. Should the frontend support multiple networks, or should the network be fixed by deployment environment?

## Contributor guidance

Wallet changes should stay explicit about which network they target. Avoid describing the current wagmi/Arbitrum connector as Stellar support until a Stellar wallet provider, network passphrase, and Soroban RPC configuration are implemented.