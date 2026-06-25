# Frontend UI Contribution Guide

This guide is for contributors working on Aiki frontend UI tasks. It focuses on the day-to-day workflow for routes, components, styling, and review-ready pull requests.

## Frontend Structure

Use these folders when planning a UI change:

- `app/`: Next.js application routes, pages, and route-level layouts.
- `components/`: Reusable React UI components shared across routes.
- `hooks/`: Custom React hooks for reusable client-side behavior.
- `lib/`: Shared utilities and Web3 configuration helpers.
- `mocks/`: Mock data used while the frontend is still being prototyped.
- `public/`: Static images and other public assets.
- `types.ts`: Shared TypeScript types used by the frontend.

Prefer updating an existing component before adding a new one. If a new component is needed, keep it focused on one UI responsibility and place it near similar components.

## Run the App Locally

Install dependencies:

```bash
npm install
```

Create a local environment file:

```bash
cp .env.example .env.local
```

Start the development server:

```bash
npm run dev
```

Open the app at:

```text
http://localhost:3000
```

For wallet-related UI work, use `NEXT_PUBLIC_PROJECT_ID` in `.env.local` when testing Reown or WalletConnect behavior. Non-wallet UI tasks should still be reviewable without a live project ID.

## Required Checks

Run these commands before opening a pull request:

```bash
npm run lint
npm run type-check
npm run build
```

What each check covers:

- `npm run lint`: ESLint checks across the project.
- `npm run type-check`: TypeScript validation with `tsc --noEmit`.
- `npm run build`: Next.js production build validation.

If a check fails because of unrelated existing code, include the command output and explain why the failure is outside your change.

## UI Contribution Expectations

Keep UI pull requests small and reviewable:

- Solve one issue or one focused UI improvement.
- Reuse existing components, utilities, and styling conventions where possible.
- Keep layouts responsive for mobile and desktop widths.
- Use clear loading, empty, and error states when the UI depends on data.
- Avoid hard-coded mock values outside the existing mock data patterns.
- Keep text concise and aligned with the education platform tone.
- Include screenshots or short screen recordings for visible UI changes.
- Avoid unrelated formatting churn, dependency changes, or broad rewrites.

## Accessibility Basics

Before submitting UI work, check the basics:

- Interactive elements can be reached with the keyboard.
- Buttons and links have clear accessible names.
- Text remains readable on light and dark backgrounds where applicable.
- Focus states are visible for keyboard users.
- Form validation messages explain what needs to be fixed.
- Animations do not hide important state changes.

## Pre-PR Checklist

Use this checklist before opening a frontend UI pull request:

- [ ] I linked the issue in the PR body with `Closes #<issue-number>`.
- [ ] I kept the PR focused on one UI task.
- [ ] I ran `npm run lint`.
- [ ] I ran `npm run type-check`.
- [ ] I ran `npm run build`.
- [ ] I tested the changed UI in a browser at `http://localhost:3000` when the change is visual.
- [ ] I checked mobile and desktop widths for layout issues.
- [ ] I added screenshots or notes for reviewers when the change affects visuals.
- [ ] I documented any existing blocker that prevents a check from passing.

## Suggested PR Summary Format

```markdown
## Summary
- Briefly describe the UI change.
- Mention the route, component, or flow that changed.

Closes #<issue-number>

## Validation
- npm run lint
- npm run type-check
- npm run build
- Browser check at http://localhost:3000
```