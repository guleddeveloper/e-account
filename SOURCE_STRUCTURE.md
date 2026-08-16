# e-Account Full Source Structure

This archive contains the complete current source tree for the e-Account project. It excludes only `node_modules/`, `dist/`, `.git/`, and local development logs because those are regenerated or environment-specific.

## Project layout

```text
 e-account/
 ├── client/
 │   ├── index.html                 Browser document shell and metadata
 │   ├── public/manifest.json       PWA manifest
 │   └── src/
 │       ├── App.tsx                Application routes and shell
 │       ├── index.css               Emerald Ledger design system
 │       ├── main.tsx                React, tRPC, and Query providers
 │       ├── pages/
 │       │   ├── Home.tsx            Local ledger experience
 │       │   ├── OwnerDashboard.tsx  Owner/Super Admin workspace
 │       │   ├── BusinessLogin.tsx   Business username/password login
 │       │   ├── BusinessDashboard.tsx Tenant business workspace
 │       │   └── NotFound.tsx
 │       ├── components/              Reusable UI and shadcn components
 │       ├── contexts/                Theme context
 │       ├── hooks/                   Reusable React hooks
 │       ├── lib/trpc.ts              Typed tRPC client
 │       └── _core/hooks/useAuth.ts   Manus Owner authentication hook
 ├── server/
 │   ├── routers.ts                  tRPC API procedures
 │   ├── db.ts                       Drizzle database helpers
 │   ├── storage.ts                  Storage helpers
 │   ├── security/passwords.ts       Scrypt password hashing/verification
 │   ├── security/businessSession.ts Signed business session cookies
 │   ├── _core/                      Auth, Express, OAuth, env, and runtime plumbing
 │   └── *.test.ts                   Vitest coverage
 ├── drizzle/
 │   ├── schema.ts                   Users, businesses, accounts, customers, transactions, subscriptions
 │   ├── relations.ts                Drizzle relations
 │   ├── 0000_*.sql ... 0004_*.sql  Applied schema migrations
 │   └── meta/                       Drizzle migration snapshots
 ├── shared/
 │   ├── subscription.ts             Subscription access rules
 │   ├── const.ts                    Shared constants
 │   └── types.ts                    Shared types
 ├── package.json                    Scripts and dependencies
 ├── pnpm-lock.yaml                  Locked dependency versions
 ├── vite.config.ts                  Vite configuration
 ├── tsconfig.json                   TypeScript configuration
 ├── drizzle.config.ts              Database migration configuration
 ├── vitest.config.ts                Test configuration
 ├── components.json                 UI component configuration
 ├── manifest.json                   PWA configuration under client/public
 └── ideas.md                        Design direction and implementation notes
```

## Local setup

Use Node.js and pnpm. From the project directory, install dependencies and run the verification commands:

```bash
pnpm install
pnpm check
pnpm test
pnpm build
pnpm dev
```

The app contains server-side environment references for `DATABASE_URL`, `JWT_SECRET`, Manus OAuth values, and built-in storage/API values. Do not commit real secrets or `.env` files. Set the environment variables in your local development environment before using database-backed or authenticated flows.

## Main routes

| Route | Purpose |
|---|---|
| `/` | Existing local ledger workspace |
| `/owner` | Owner/Super Admin business onboarding and access management |
| `/business-login` | Business Admin/Cashier login |
| `/business` | Tenant business dashboard and database-backed customer list |

## Important current limitation

This is the complete source for the current verified milestone, not a claim that every item in the long-term product specification is finished. The archive includes the implemented Owner Dashboard, business authentication foundation, tenant-scoped customer/transaction schema and procedures, and database-backed business dashboard. User management, full transaction UI, full role enforcement, payments, audit logs, offline synchronization, and remaining operational features are still planned for subsequent milestones.
