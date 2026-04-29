# Lumixy Project Overview

## About the Application
Lumixy is a full-stack platform for managing service providers and administrative operations. The app allows admins to manage categories and providers, while providers can register, edit their profiles, and track their approval status. The platform features a public directory for users to search and discover providers.

### Main Features
- Admin dashboard for managing categories and providers
- Provider registration and profile management
- Approval workflow for new providers
- Public directory with search and filtering
- Full backend integration for all features

## Tech Stack
- **Frontend:** React Native (Expo), TypeScript, NativeWind, React Query
- **Backend:** Custom API (integrated via services layer)
- **State Management:** React Query, Context API
- **Styling:** NativeWind, Tailwind CSS

## Folder Structure
- `app/` — Main application pages (admin, provider, auth, tabs)
- `components/` — Reusable UI and feature components
- `services/` — API clients and business logic
- `hooks/` — Custom React hooks
- `contexts/` — Context providers for global state
- `store/` — State stores (e.g., provider registration)
- `theme/` — Theme and style definitions
- `utils/` — Utility functions

## How to Run the Project

### 1. Install Dependencies
Make sure you have Node.js and npm installed. Then run:

```bash
npm install
```

### 2. Start the Expo Development Server

```bash
npm start
```

Or, to run directly on a device or emulator:

```bash
npm run android   # For Android
yarn ios         # For iOS (requires Mac)
```

### 3. Environment Variables
- The project may require API URLs or keys. Check `app.json` or `.env` files if available.
- For backend integration, ensure the API server is running and accessible.

### 4. Linting and Formatting

```bash
npm run lint
```

### 5. Reset Project (if needed)

```bash
node scripts/reset-project.js
```

## Notes
- All main features are fully integrated with the backend.
- For any issues, check the `services/` folder for API logic.
- The UI is responsive and supports both Arabic and English.

## Contact
For more details or technical questions, please contact the main developer.

---

This file is ready to be used as a complete README or project overview for your repository.
