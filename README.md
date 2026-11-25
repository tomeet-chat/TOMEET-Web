<div align="center">

# TOMEET Web

**Bilingual Next.js 16 web & PWA client for TOMEET — a conversational social Agent turning dialogue into real-world connections.**

[![Live Preview](https://img.shields.io/badge/Live-rendez--web.vercel.app-111827.svg)](https://rendez-web.vercel.app)
[![Next.js](https://img.shields.io/badge/Next.js-16-000000.svg)](package.json)
[![React](https://img.shields.io/badge/React-19%20%7C%20TypeScript-2563EB.svg)](package.json)
[![Backend](https://img.shields.io/badge/Backend-TOMEET__Backend-10B981.svg)](https://github.com/toMeetADX/TOMEET_Backend)

**English** | [简体中文](README.zh-CN.md)

</div>

---

## Overview

**TOMEET Web** is the responsive web and installable PWA interface for [**TOMEET**](https://github.com/toMeetADX/TOMEET_Backend). It provides the brand landing experience, Supabase-authenticated user onboarding, real-time conversational UI with the TOMEET social Agent (`AgentChat`), profile hub, optional WeChat QR linking (`WechatQrEntry`), and seamless English/Chinese localization.

## Features

- **Conversational Agent Interface (`/[locale]/agent`)**: Interactive dialogue with TOMEET's social Agent backed by server-side API proxying (`/api/tomeet/[...path]`).
- **Bilingual by Default (`next-intl`)**: Full English (`src/messages/en.json`) and Chinese (`src/messages/zh.json`) localized routing (`/[locale]`).
- **Installable PWA**: Web app manifest (`src/app/manifest.ts`), service worker (`public/sw.js`), offline fallback (`public/offline.html`), and mobile install prompt (`InstallAppPrompt`).
- **Supabase SSR Auth**: Email/identifier login & sign-up (`/[locale]/login`, `/[locale]/signup`), OAuth callbacks (`/api/auth/callback`), and SSR session middleware.
- **Feature-Flagged Modules**: Toggle experimental views cleanly via environment variables (`NEXT_PUBLIC_FOODIES_ENABLED`, `NEXT_PUBLIC_QR_SERVICE_ENABLED`).
- **Motion & Craft**: Custom typography, Framer Motion transitions, Tailwind CSS v4, `@base-ui/react`, and `shadcn/ui` primitives.

## Tech Stack

| Layer | Technologies |
| --- | --- |
| Framework | Next.js 16 (App Router), React 19, TypeScript |
| Styling & UI | Tailwind CSS v4, shadcn/ui, `@base-ui/react`, Framer Motion, Lucide Icons |
| State & i18n | Zustand, `next-intl` |
| Auth & Backend | Supabase SSR (`@supabase/ssr`), server-side proxy to [TOMEET_Backend](https://github.com/toMeetADX/TOMEET_Backend) |
| Deployment | Vercel |

## Project Structure

```text
src/
├── app/
│   ├── [locale]/              # Localized routes: landing, agent, profile, foodies, login, signup
│   ├── api/
│   │   ├── auth/              # Supabase auth callback & signout handlers
│   │   └── tomeet/[...path]/  # Server-side proxy forwarding to TOMEET_API_BASE_URL
│   └── manifest.ts            # PWA manifest
├── components/                # AgentChat, Hero, Manifesto, ProfileHub, WechatQrEntry, UI primitives
├── i18n/                      # next-intl routing & request config
├── lib/                       # Supabase client/server/middleware, API helpers, feature flags
└── messages/                  # en.json & zh.json localization bundles
```

## Quick Start

### 1. Install Dependencies

```sh
npm install
```

### 2. Configure Environment Variables

```sh
cp .env.local.example .env.local
```

Fill in `.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key

# Server-side Railway API base URL (no trailing slash)
TOMEET_API_BASE_URL=http://localhost:4000

# Optional feature flags
NEXT_PUBLIC_FOODIES_ENABLED=false
NEXT_PUBLIC_QR_SERVICE_ENABLED=false
```

### 3. Run Locally

```sh
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). Verify lint and production build before opening a PR:

```sh
npm run lint && npm run build
```

## Contributing

UI polish, accessibility improvements, PWA enhancements, and localization fixes are all welcome! Check [CONTRIBUTING.md](CONTRIBUTING.md) and coordinate API contract updates with [TOMEET_Backend](https://github.com/toMeetADX/TOMEET_Backend).
