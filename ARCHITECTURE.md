# HabitQuest Architecture

> Technical overview for developers and AI systems.

## System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Client Layer                           │
├──────────────────┬──────────────────┬───────────────────────┤
│   Next.js App    │   Capacitor      │   Service Worker      │
│   (React 19)     │   (Android APK)  │   (PWA/Offline)       │
└──────────────────┴──────────────────┴───────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                     API Layer                               │
├─────────────────────────────────────────────────────────────┤
│           Next.js Server Actions (app/actions.ts)           │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   Supabase Backend                          │
├──────────────────┬──────────────────┬───────────────────────┤
│   PostgreSQL     │   Auth           │   Realtime            │
│   (Database)     │   (Users)        │   (Subscriptions)     │
└──────────────────┴──────────────────┴───────────────────────┘
```

## Directory Structure

```
habitquest/
├── app/                    # Next.js app router
│   ├── actions.ts          # Server actions
│   ├── page.tsx            # Main app entry
│   └── api/                # API routes
├── components/
│   ├── habit-tracker/      # Core habit tracking UI
│   ├── social/             # Squad and chat components
│   ├── reading-tracker/    # EPUB reader
│   └── ui/                 # shadcn/ui primitives
├── lib/
│   ├── services/           # Supabase service functions
│   ├── hooks/              # React custom hooks
│   └── utils/              # Utility functions
├── android/                # Capacitor Android project
└── docs/                   # Documentation
```

## Database Schema (Supabase PostgreSQL)

### Core Tables

| Table | Purpose |
|-------|---------|
| `users` | User profiles, XP, level, settings |
| `habits` | Habit definitions per user |
| `habit_history` | Daily completion records |
| `journal_entries` | User journal content |
| `achievements` | Unlocked badges |

### Social Tables

| Table | Purpose |
|-------|---------|
| `squads` | Squad metadata (name, code, level) |
| `squad_members` | User-squad relationships |
| `squad_chat` | Squad message history |
| `world_chat` | Global chat messages |
| `boss_raids` | Daily boss battle state |

## Key Technologies

- **Next.js 16** — React framework with App Router
- **React 19** — UI library with latest features
- **TypeScript** — Type-safe development
- **Supabase** — Backend-as-a-service (Auth, DB, Realtime)
- **Capacitor** — Native mobile bridge (Android)
- **Tailwind CSS 4** — Utility-first styling
- **Framer Motion** — Animation library
- **Radix UI** — Accessible component primitives

## Deployment

- **Web**: Vercel (automatic from GitHub)
- **Android**: Capacitor → Android Studio → APK/AAB
- **Database**: Supabase Cloud

---

*See [FEATURES.md](FEATURES.md) for user-facing documentation.*
