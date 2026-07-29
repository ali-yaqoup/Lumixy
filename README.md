# Lumixy

A React Native mobile application for a service-provider marketplace. Customers can browse and discover local service providers; providers register, manage their profiles, and track their approval status; admins manage categories and provider applications. Backend powered by the companion [Lumixy-backend](https://github.com/ali-yaqoup/Lumixy-backend) Laravel API.

---

## Tech Stack

| Technology | Version |
|---|---|
| React Native | 0.81.5 |
| React | 19.1.0 |
| Expo | ~54.0.33 |
| Expo Router | ~6.0.23 |
| TypeScript | ~5.9.2 |
| React Navigation (bottom tabs) | ^7.4.0 |
| React Native Reanimated | ~4.1.1 |
| Expo Google Fonts (Cairo) | ^0.4.2 |

---

## Features

- **Public directory** — Browse approved service providers on the home screen, with dynamic category listing and featured-provider sections
- **Search** — Filter providers by category; results are shown as scrollable provider cards
- **Provider registration flow** — "Join as Provider" entry point from the About tab; multi-step onboarding screens under `app/provider/`
- **Provider waiting screen** — Dedicated `waiting-approval` screen shown after submission while the application is under review
- **Provider dashboard** — Authenticated provider section with Home, Search, and Profile tabs (`app/provider/tabs/`)
- **Admin dashboard** — Authenticated admin section with Home, Search, and Profile tabs (`app/admin/tabs/`)
- **Authentication** — Login screen at `app/auth/login.tsx` backed by Sanctum token auth
- **About page** — App information and call-to-action for providers to join
- **Arabic and English UI** — Cairo font loaded via `@expo-google-fonts/cairo`

---

## Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/ali-yaqoup/Lumixy.git
cd Lumixy

# 2. Install dependencies
npm install

# 3. Start the Expo development server
npm start

# Run on a specific platform
npm run android   # Android emulator or device
npm run ios       # iOS simulator (macOS only)
npm run web       # Web browser

# Lint
npm run lint
```

Ensure the Lumixy backend API is reachable and the base URL is configured in your environment or `app.json`.

---

## Project Structure

```
Lumixy/
├── app/
│   ├── (tabs)/         # Public tab navigator: Home, Search, About
│   ├── admin/          # Admin-only screens and tab navigator
│   ├── auth/           # Login screen
│   ├── provider/       # Provider screens, tab navigator, and waiting-approval screen
│   ├── providers/      # React context providers
│   ├── entry.tsx       # App entry and authentication routing
│   └── index.tsx       # Root redirect
├── components/         # Reusable UI components
├── assets/             # Images and fonts
├── constants/          # App-wide constants
├── hooks/              # Custom React hooks
├── scripts/            # Developer utility scripts (e.g. reset-project)
└── theme/              # Shared theme definitions
```

---

## Related Repository

This app is backed by **Lumixy-backend** — a Laravel 12 REST API:
[https://github.com/ali-yaqoup/Lumixy-backend](https://github.com/ali-yaqoup/Lumixy-backend)
