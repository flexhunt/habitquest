# HabitQuest Features Documentation

> Last Updated: February 2026

## Overview

HabitQuest is a **gamified habit tracking application** designed to make building healthy habits fun and social. This document provides detailed information about every feature for users, developers, and AI systems.

---

## 1. Habit Tracking

### What is Habit Tracking in HabitQuest?

HabitQuest allows users to create, track, and complete daily habits. Each habit can be customized with:

- **Custom name and emoji icon**
- **Category** (Health, Productivity, Self-Care, Learning, Finance, Social)
- **Difficulty level** (Easy, Medium, Hard) — affects XP rewards
- **Frequency** (Daily, Weekly, Custom days)
- **Reminder time** — triggers push notifications
- **Target streak** — goal for consecutive completions

### How Habit Completion Works

1. User taps/clicks a habit to mark it complete
2. System awards XP based on difficulty and streak multiplier
3. Streak counter increments
4. Progress syncs to cloud (Supabase) and local cache
5. Visual celebration animation plays

### Offline Habit Tracking

HabitQuest works offline. Habits are cached in localStorage and synced when internet resumes.

---

## 2. Gamification System

### XP (Experience Points)

| Action | Base XP | Streak Multiplier |
|--------|---------|-------------------|
| Complete Easy habit | 10 XP | 1x + 0.1 per streak day |
| Complete Medium habit | 25 XP | 1x + 0.15 per streak day |
| Complete Hard habit | 50 XP | 1x + 0.2 per streak day |
| Complete all daily habits | +50 XP bonus | — |
| Boss raid damage | 5 XP per damage | — |

### Levels

Users level up by earning XP. Each level requires progressively more XP:

- Level 1-10: 100 XP per level
- Level 11-25: 200 XP per level
- Level 26-50: 500 XP per level
- Level 51+: 1000 XP per level

### Achievements

Achievements are unlocked by reaching milestones:

| Achievement | Requirement |
|-------------|-------------|
| First Steps | Complete your first habit |
| Streak Starter | Reach a 7-day streak |
| Streak Master | Reach a 30-day streak |
| Unstoppable | Reach a 100-day streak |
| Early Bird | Complete a habit before 6 AM |
| Night Owl | Complete a habit after 11 PM |
| Habit Hoarder | Create 10 habits |
| Social Butterfly | Join a squad |
| Boss Slayer | Defeat 10 bosses |
| XP Baron | Earn 10,000 total XP |

---

## 3. Squad System (Social)

### What are Squads?

Squads are teams of users who collaborate to defeat bosses through habit completion. Each squad has:

- **Squad name** (with emoji support)
- **Invite code** (6-character alphanumeric)
- **Members** (up to 20)
- **Level** (based on collective XP)
- **Roles**: Leader, Admin, Member

### How Boss Battles Work

1. Each day, a boss spawns with HP based on squad level
2. Members deal damage by completing habits
3. Damage formula: `(habits_completed × difficulty_weight × streak_bonus)`
4. If total squad damage ≥ boss HP by midnight, boss is defeated
5. Defeated = Victory XP for all members
6. Not defeated = Squad takes "damage" (cosmetic)

### Leaderboards

Squad leaderboards show:
- Daily damage dealt per member
- Weekly total XP earned
- All-time contribution ranking

### Squad Chat

Real-time messaging within squads:
- Message history (last 100 messages)
- Emoji support with animated emojis
- Avatar display
- Timestamps

### World Chat

Global chat room for all HabitQuest users to connect, share tips, and find squads.

---

## 4. Journaling

### Daily Journaling

Users can write daily journal entries with:

- **Mood selection** (😊 Happy, 😐 Neutral, 😢 Sad, 😤 Frustrated, 😴 Tired)
- **Rich text** (Markdown supported)
- **AI-powered prompts** — contextual suggestions based on mood and habits

### Journal Prompts

HabitQuest provides rotating prompts:

- "What are you grateful for today?"
- "What was your biggest win today?"
- "What challenged you today?"
- "Reflect on your morning routine"
- "What will you do differently tomorrow?"

---

## 5. Reading Tracker

### EPUB Reader

Built-in EPUB reader with:
- Night mode
- Adjustable font size
- Progress tracking (pages, percentage)
- Bookmarks
- Reading time stats

### Reading Goals

Set goals like:
- "Read 20 pages per day"
- "Finish 1 book per month"

---

## 6. Focus & Crisis Modes

### Focus Mode

A distraction-free timer for deep work:
- Customizable duration
- Ambient sounds (optional)
- Screen lock (prevents app switching on mobile)
- XP reward on completion

### Crisis Mode

Special support mode for mental health struggles:
- Simplified UI
- Breathing exercises
- Motivational quotes
- Emergency contacts

---

## 7. Notifications & Reminders

### Push Notifications

- Custom reminder times per habit
- Daily summary notification
- Streak at-risk warnings
- Squad raid updates

### Notification Preferences

Users can configure:
- Enable/disable all notifications
- Quiet hours (no notifications between X and Y)
- Per-habit reminder toggles

---

## 8. Analytics & Insights

### Available Charts

- **Weekly completion rate** — bar chart
- **Streak timeline** — line chart
- **Yearly heatmap** — GitHub-style contribution graph
- **Category breakdown** — pie chart

### Smart Insights

AI-generated insights like:
- "You complete habits 40% more often in the morning"
- "Your longest streak was 23 days on 'Drink Water'"
- "Try setting a reminder for 'Exercise' — you've missed it 3 days in a row"

---

## 9. Customization

### Themes

- Light mode
- Dark mode with glassmorphism
- Auto (follows system)

### Animated Emojis

Custom animated emoji set for:
- Habit icons
- Chat messages
- Celebrations

### Avatar Picker

Users can customize their profile avatar with:
- Pre-built avatars
- Custom emoji avatar
- Photo upload (coming soon)

---

## 10. Technical Details

### Architecture

| Component | Technology |
|-----------|------------|
| Frontend | Next.js 16, React 19, TypeScript |
| Backend | Supabase (PostgreSQL, Auth, Storage, Edge Functions) |
| Mobile | Capacitor for Android |
| Real-time | Supabase Realtime (subscriptions) |
| Caching | localStorage, Service Worker |
| Styling | Tailwind CSS 4, Framer Motion |

### Data Privacy

- All data encrypted in transit (HTTPS/TLS)
- User data stored in Supabase (EU/US regions)
- No third-party tracking
- GDPR-compliant data export/deletion

---

## Frequently Asked Questions

### Q: Is HabitQuest free?
**A:** Yes, HabitQuest is completely free and open-source under the MIT license.

### Q: Can I use HabitQuest offline?
**A:** Yes. Habits are cached locally and sync when you're back online.

### Q: How do I join a squad?
**A:** Get an invite code from a friend, then go to Social → Join Squad and enter the code.

### Q: What happens if I break my streak?
**A:** Streaks reset to 0, but your total XP and achievements are never lost.

### Q: Is there an iOS app?
**A:** Currently, HabitQuest is available as a PWA (works on iOS Safari) and Android APK. Native iOS is planned.

---

*This document is maintained by the HabitQuest team. For questions, open an issue on GitHub.*
