# Caddi

A modern web application built with Vue 3, TypeScript, Vite, Tailwind CSS, and Firebase. The project appears intended to be a productivity/project-shipping platform (SaaS-style product) with features like deployment management, SSL certificates, database backups, and collaboration tools.

## Project Status

### ✅ Completed

- **Project scaffolding**: Vue 3 + TypeScript + Vite application initialized
- **Tailwind CSS integration**: Configured with `@tailwindcss/forms`, `@tailwindcss/typography`, and `@tailwindcss/aspect-ratio` plugins
- **Landing page**: Full marketing landing page built with Tailwind UI components, including:
  - Responsive header with mobile menu (Headless UI `Dialog`)
  - Hero section with app screenshot mockup
  - Logo cloud section
  - Primary feature showcase (dark background section)
  - Secondary feature grid
  - Newsletter / email signup section
  - Testimonials grid with featured testimonial
  - Full footer with navigation, social links, and newsletter subscribe form
- **Firebase project**: Firebase app initialized (`caddi-app` project)
- **UI component library**: Headless UI and Heroicons integrated
- **Security hardening**: Firebase credentials moved to environment variables, all npm dependencies updated to resolve known CVEs

### 🚧 Not Yet Implemented

- **Authentication**: No login/signup flows — the "Log in" link in the header is a placeholder (`#`)
- **Routing**: No Vue Router — the app only renders a single landing page
- **State management**: No Pinia/Vuex store
- **Firebase services**: Firebase is initialized but no services (Auth, Firestore, Storage, Functions, Hosting) are actually used
- **Real content**: All landing page copy is placeholder (lorem ipsum); images point to external Tailwind UI assets
- **Dashboard / App UI**: No authenticated app experience after the landing page
- **API layer**: No backend API, Cloud Functions, or data models
- **Testing**: No test framework or tests
- **CI/CD**: No GitHub Actions, Firebase Hosting deployment, or build pipeline
- **Environment configuration**: `.env.example` created but no deployment/staging/production env management
- **Linting & formatting**: No ESLint or Prettier configuration
- **PWA / SEO**: No meta tags, Open Graph, sitemap, or service worker

## Tech Stack

| Layer        | Technology                          |
| ------------ | ----------------------------------- |
| Framework    | Vue 3 (Composition API, `<script setup>`) |
| Language     | TypeScript                          |
| Build Tool   | Vite 8                              |
| Styling      | Tailwind CSS 3 + Headless UI        |
| Icons        | Heroicons                           |
| Backend      | Firebase (planned)                  |
| Type Checker | vue-tsc                             |

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Setup

```bash
# Install dependencies
npm install

# Copy environment template and fill in your Firebase config
cp .env.example .env

# Start development server
npm run dev

# Type-check and build for production
npm run build

# Preview production build
npm run preview
```

### Environment Variables

Copy `.env.example` to `.env` and fill in your Firebase project credentials:

```
VITE_FIREBASE_API_KEY=your-api-key
VITE_FIREBASE_AUTH_DOMAIN=your-project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project-id
VITE_FIREBASE_STORAGE_BUCKET=your-project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your-sender-id
VITE_FIREBASE_APP_ID=your-app-id
```

## Project Structure

```
caddi/
├── public/               # Static assets
├── src/
│   ├── assets/           # Asset files
│   ├── components/       # Vue components
│   │   ├── Landing.vue   # Marketing landing page
│   │   └── HelloWorld.vue# Starter component (unused)
│   ├── firebase/
│   │   └── index.js      # Firebase initialization
│   ├── App.vue           # Root component
│   ├── main.ts           # Application entry point
│   └── style.css         # Global styles + Tailwind directives
├── .env.example          # Environment variable template
├── index.html            # HTML entry point
├── package.json          # Dependencies and scripts
├── tailwind.config.js    # Tailwind CSS configuration
├── tsconfig.json         # TypeScript configuration
├── postcss.config.js     # PostCSS configuration
└── vite.config.ts        # Vite configuration
```

## Prompts

See the [`/prompts`](./prompts/) directory for a series of development prompts that can be undertaken in sequence to build out the full application functionality.
