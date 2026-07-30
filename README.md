# SmartSpender AI

Intelligent personal finance app built with **Next.js 15**, Clerk auth, Prisma + PostgreSQL, Gemini AI, Inngest, and Arcjet.

## Features

- Track income & expenses across accounts
- Budgets with progress alerts
- AI receipt scanning (Gemini)
- Recurring transactions (Inngest)
- Charts and dashboard insights

## Prerequisites

- Node.js 18+
- PostgreSQL 14+ (local or [Neon](https://neon.tech) / Supabase)
- Free accounts:
  - [Clerk](https://dashboard.clerk.com) (auth)
  - [Google AI Studio](https://aistudio.google.com/apikey) (Gemini)
  - [Arcjet](https://app.arcjet.com) (optional locally)
  - [Resend](https://resend.com) (optional; email alerts)

## Setup

```bash
# 1. Install dependencies
npm install

# 2. Copy env template and fill in keys
cp .env.example .env

# 3. Create DB tables
npx prisma migrate deploy
# or during development:
npx prisma db push

# 4. Run the app
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Required `.env` values

```
DATABASE_URL=
DIRECT_URL=

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/dashboard
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/dashboard

GEMINI_API_KEY=
RESEND_API_KEY=
ARCJET_KEY=
```

For local Postgres without a password:

```
DATABASE_URL="postgresql://YOUR_USER@localhost:5432/smart_spender?schema=public"
DIRECT_URL="postgresql://YOUR_USER@localhost:5432/smart_spender?schema=public"
```

In Clerk, add `http://localhost:3000` as an allowed origin and set sign-in/sign-up paths to `/sign-in` and `/sign-up`.

## Scripts

| Command        | Description              |
|----------------|--------------------------|
| `npm run dev`  | Dev server (Turbopack)   |
| `npm run build`| Production build         |
| `npm start`    | Run production server    |
| `npm run lint` | ESLint                   |

## Deploy (GitHub → Vercel)

1. Push this repo to GitHub
2. Import the project in [Vercel](https://vercel.com)
3. Add the same env vars in Vercel project settings
4. Use a hosted Postgres URL (Neon/Supabase) for `DATABASE_URL` / `DIRECT_URL`
5. Add your Vercel URL in Clerk allowed origins

## Tech stack

Next.js · React · Tailwind · shadcn/ui · Prisma · PostgreSQL · Clerk · Gemini · Inngest · Arcjet · Resend
