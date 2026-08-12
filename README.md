# Invoice & Report Generation System — Frontend

React (Vite) + TypeScript frontend for the automated invoice and report generation system: admin dashboard, technician job-completion flow, and the public client-facing invoice page.

See [`../PRD.md`](../PRD.md) for full product scope.

## Tech Stack

- React + Vite + TypeScript
- JWT auth against the NestJS backend (`admin` / `technician` roles)

## Project Setup

```bash
npm install
cp .env.example .env
```

`VITE_API_URL` points at the backend API (defaults to `/api/v1`, proxied to `http://localhost:3000` in dev — see `vite.config.ts`).

## Running

```bash
npm run dev       # dev server with HMR
npm run build     # production build
npm run preview   # preview production build
```

## App Areas

- **Auth** (`features/auth`) — login for Admin and Technician.
- **Dashboard** (`features/dashboard`) — revenue, outstanding/overdue totals, invoice status breakdown, top clients.
- **Jobs** (`features/jobs`) — client/job management (admin).
- **Invoices** (`features/invoices`) — list/filter/search, detail view, download/regenerate/resend, bulk actions.
- **Technician** (`features/technician`) — mobile-friendly job-completion form (notes, photos, checklist).
- **Notifications** (`features/notifications`) — in-app read/unread notifications.
- **Public Invoice** (`features/public-invoice`) — no-login invoice view with a Stripe "Pay Now" link, accessed via unguessable token URL.

## Backend Connection

The dev server proxies `/api/v1/*` requests to the backend (`http://localhost:3000`), so the backend must be running separately (`npm run start:dev` in `../backend`). API calls go through `src/api/client.ts`.
