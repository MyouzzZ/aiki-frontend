<p align="center">
  <img src="./public/logo2.png" alt="Aiki Logo" width="160" />
</p>

<h1 align="center">Aiki Frontend</h1>

<p align="center">
  Open-source Web3 education infrastructure for courses, learner dashboards, blockchain certificates, and learning rewards.
</p>

<p align="center">
  <strong>Built for Web3 learning today, with a roadmap toward Stellar payments and Soroban-powered certificate verification.</strong>
</p>

---

## Overview

Aiki is an open-source Web3 education platform designed to help instructors create courses, learners track progress, and communities issue verifiable blockchain-based certificates.

This repository contains the frontend application for the Aiki platform.

## Problem

Online learning platforms often make it difficult for learners to prove course completion, for instructors to manage transparent learning records, and for communities to reward meaningful learning activity.

## Solution

Aiki provides a modern, wallet-ready learning interface that can support:

- Course discovery
- Learner enrollment
- Instructor dashboards
- Learner dashboards
- Progress tracking
- Certificate verification
- Future Stellar/Soroban payment and reward flows

## Features

- Responsive landing page and dashboard UI
- Course and project discovery sections
- Wallet connection interface
- Reusable UI components
- Type-safe frontend development
- Mock data structure for rapid prototyping
- Planned Stellar/Soroban integration path

## Tech Stack

- Next.js
- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- wagmi
- viem
- TanStack Query

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Aiki-INC/aiki-frontend.git
cd aiki-frontend
```

### 2. Install dependencies

```bash
npm install
```

### 3. Create an environment file

Copy the example environment file:

```bash
cp .env.example .env.local
```

The current example file contains one public browser variable:

```env
NEXT_PUBLIC_PROJECT_ID=
```

`NEXT_PUBLIC_PROJECT_ID` is used by `lib/wagmi-provider.tsx` to enable the WalletConnect/Reown connector. Add your WalletConnect or Reown project ID when you need to test QR-code wallet connection flows:

```env
NEXT_PUBLIC_PROJECT_ID=your_walletconnect_or_reown_project_id
```

For non-wallet UI work, the app can still run without this value. When `NEXT_PUBLIC_PROJECT_ID` is empty, the wallet provider falls back to the MetaMask connector only.

Restart `npm run dev` after changing `.env.local`, because Next.js reads public environment variables when the dev server starts.

### 4. Run the development server

```bash
npm run dev
```

Open the app in your browser:

```text
http://localhost:3000
```

If port `3000` is already in use, follow the Next.js terminal prompt or stop the process using that port before retrying.

## Available Scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the local Next.js development server. |
| `npm run build` | Build the production version and catch build-time issues. |
| `npm run start` | Start the production server after a successful build. |
| `npm run lint` | Run ESLint across the project. |
| `npm run type-check` | Run TypeScript validation with `tsc --noEmit`. |

Before opening a pull request, run:

```bash
npm run lint
npm run type-check
npm run build
```

## Local Setup Troubleshooting

- If dependencies fail to install, delete `node_modules`, keep `package-lock.json`, and run `npm install` again with the current Node.js LTS release.
- If wallet QR-code connection is unavailable, confirm `NEXT_PUBLIC_PROJECT_ID` exists in `.env.local` and restart the dev server.
- If you do not have a WalletConnect/Reown project ID, continue with MetaMask-only testing for non-wallet UI tasks.
- If TypeScript path aliases fail, make sure imports use the configured `@/*` alias from `tsconfig.json` or valid relative paths.
- If a check fails after a fresh clone, include the failing command and output in your pull request notes.

## Project Structure

```text
aiki-frontend/
  app/              Application routes and pages
  components/       Reusable UI components
  hooks/            Custom React hooks
  lib/              Utilities and Web3 configuration
  mocks/            Mock data for development
  public/           Static assets and images
  types.ts          Shared TypeScript types
  README.md         Project documentation
  package.json      Project scripts and dependencies
```

## Stellar/Soroban Roadmap

Aiki is preparing support for the Stellar ecosystem. Planned work includes:

- Researching Stellar wallet connection options
- Designing course payment flows using Stellar assets
- Creating Soroban-based certificate verification documentation
- Exploring learning rewards and achievement verification on Stellar
- Creating contributor-friendly issues for GrantFox and Drips Wave

## Contributing

We welcome contributors. Please read [`CONTRIBUTING.md`](./CONTRIBUTING.md) before starting.

A good first step is to check the Issues tab, comment on the issue you want to work on, and wait for maintainer confirmation before opening a pull request.

## Contribution Areas

Good areas for contributors include:

- UI improvements
- Documentation
- Dashboard components
- Wallet connection improvements
- Stellar/Soroban research
- Frontend testing
- Accessibility improvements

## License

MIT
