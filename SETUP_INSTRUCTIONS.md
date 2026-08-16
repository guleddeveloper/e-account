# e-Account Setup Instructions

## 1. Requirements

Install Node.js 22+ and pnpm. The project uses React/TypeScript/Vite on the client, an Express/tRPC server, Drizzle ORM, and a MySQL/TiDB-compatible database.

## 2. Install

```bash
cd e-account
pnpm install
```

## 3. Environment variables

Create a local environment configuration from the deployment environment. Required categories include:

```env
DATABASE_URL=mysql://USER:PASSWORD@HOST:3306/DATABASE
JWT_SECRET=generate-a-long-random-secret
VITE_APP_TITLE=e-Account
VITE_APP_ID=your-oauth-app-id
OAUTH_SERVER_URL=your-oauth-server-url
VITE_OAUTH_PORTAL_URL=your-oauth-portal-url
```

Use the actual OAuth, storage, and built-in API values supplied by your hosting/provider environment. Never commit `.env`, database passwords, JWT secrets, or API keys.

## 4. Database

The database schema is in `drizzle/schema.ts`. Applied migrations are in `drizzle/0000_*.sql` through `drizzle/0004_*.sql`.

The current schema includes:

- `users`: Owner/Manus-authenticated users.
- `businesses`: Customer businesses, status, owner profile, and paid-until information.
- `business_accounts`: Business Admin/Cashier credentials and roles.
- `business_members`: Owner membership relationships.
- `customers`: Tenant-scoped customer accounts.
- `transactions`: Tenant-scoped IN/OUT records with rate and calculation metadata.
- `subscriptions`: Business subscription status and expiry data.

For a new database, review the migration files and apply them with the project’s migration workflow. Do not insert demo customer or transaction data into production.

## 5. Verify and run

```bash
pnpm check
pnpm test
pnpm build
pnpm dev
```

The development server serves the application using the configured runtime port. Do not hardcode a production port.

## 6. Routes

- `/` — local ledger experience.
- `/owner` — Owner Dashboard and business onboarding.
- `/business-login` — Business Admin/Cashier login.
- `/business` — authenticated business dashboard.

## 7. First workflow

Sign in as the Owner, open `/owner`, create a business with owner profile details and a business-admin username/password, then use `/business-login` with that account. Business customer and transaction data must remain scoped to the authenticated business.

## 8. Security

The source archive does not contain database credentials, password values, OAuth secrets, JWT secrets, or API keys. Supply those values through secure environment variables or the hosting provider’s secrets manager. Rotate any credential that has been exposed.

## 9. Current milestone limitation

This source archive represents the current verified milestone. It includes the Owner Dashboard foundation, business authentication/session foundation, tenant-scoped customer/transaction schema and procedures, and database-backed business dashboard. Full transaction UI, complete role enforcement, payment collection, audit logs, offline synchronization, and other long-term specification items remain subsequent development milestones.
