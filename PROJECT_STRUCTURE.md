# CareChain Frontend - Project Architecture & Folder Structure

This document outlines the scalable, feature-based architecture for the CareChain frontend client application. The structure follows Clean Architecture principles, ensuring modularity, maintainability, and enterprise-level scalability.

## 📁 Complete Folder Structure

```text
CareChain-Frontend/
├── .github/                           # GitHub Actions CI/CD workflows
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── ci.yml                     # General CI (Lint, Typecheck, Test)
│       ├── lint.yml                   # Code style and formatting checks
│       ├── build.yml                  # Build validation
│       ├── preview-deployment.yml     # Staging/Preview deployments
│       └── production-deployment.yml  # Production release pipeline
├── .husky/                            # Git hooks for pre-commit formatting and linting
├── .vscode/                           # IDE-specific configurations
├── docs/                              # Project documentation
│   ├── architecture/                  # Deep dives into system design
│   ├── api/                           # API integration guidelines
│   └── setup/                         # Local development guides
├── public/                            # Static assets (images, fonts, icons)
│   ├── assets/
│   └── locales/                       # i18n translation files
├── src/                               # Application source code
│   ├── app/                           # Next.js App Router layout and pages
│   │   ├── (auth)/                    # Authentication routes (login, register)
│   │   ├── (dashboard)/               # Protected dashboard routes
│   │   │   ├── admin/
│   │   │   ├── caregiver/
│   │   │   └── user/
│   │   ├── (public)/                  # Public facing routes (landing, about)
│   │   ├── api/                       # Next.js API routes (BFF pattern)
│   │   ├── layout.tsx                 # Root layout
│   │   └── page.tsx                   # Entry page
│   ├── assets/                        # Dynamic assets (SVGs, internal graphics)
│   ├── components/                    # Global shared components
│   │   ├── layouts/                   # Shared layouts (sidebar, navbar)
│   │   ├── forms/                     # Reusable form controls
│   │   ├── ui/                        # Core UI components (buttons, inputs)
│   │   └── shared/                    # Common functional components
│   ├── config/                        # Global configuration files
│   │   ├── constants/                 # Immutable application constants
│   │   └── environments/              # Environment variable validation schemas
│   ├── context/                       # React Context providers (theme, auth state)
│   ├── features/                      # Feature-based modules (Domain-driven design)
│   │   ├── admin/                     # Admin platform oversight
│   │   ├── auth/                      # Authentication logic
│   │   ├── bookings/                  # Booking workflows
│   │   ├── caregivers/                # Caregiver discovery
│   │   ├── dashboard/                 # Dashboard widget logic
│   │   ├── notifications/             # Notification state and UI
│   │   └── reviews/                   # Review and rating system
│   ├── hooks/                         # Global custom React hooks
│   ├── lib/                           # Third-party library initializations
│   │   ├── axios.ts                   # Axios client setup
│   │   ├── blockchain/                # Web3/Stellar SDK wrappers
│   │   ├── websocket/                 # Socket.io/WebSocket clients
│   │   └── validation/                # Zod schemas for validation
│   ├── middleware/                    # Next.js and custom middlewares
│   ├── services/                      # API communication layer
│   │   ├── api/                       # REST endpoint definitions
│   │   └── blockchain/                # Smart contract/Escrow interactions
│   ├── store/                         # Global state management (Zustand/Redux)
│   ├── styles/                        # Global CSS, Tailwind configurations
│   ├── types/                         # Global TypeScript definitions
│   └── utils/                         # Helper functions and utilities
├── tests/                             # Testing infrastructure
│   ├── e2e/                           # Cypress or Playwright end-to-end tests
│   ├── integration/                   # Integration tests
│   └── unit/                          # Jest/Vitest unit tests
├── scripts/                           # Build and automation scripts
├── .env.example                       # Environment variable template
├── .eslintrc.json                     # ESLint configuration
├── .prettierrc                        # Prettier configuration
├── Dockerfile                         # Containerization configuration
├── docker-compose.yml                 # Local development container orchestration
├── jest.config.js                     # Test runner configuration
├── next.config.mjs                    # Next.js framework configuration
├── package.json                       # Dependencies and scripts
├── tailwind.config.ts                 # Tailwind CSS design system configuration
└── tsconfig.json                      # TypeScript compiler configuration
```

## 🏗️ Directory Explanations

- **`.github/workflows`**: Houses CI/CD automation logic. It ensures that every PR is tested, type-checked, and linted before merging. Deployments are handled automatically across environments.
- **`src/app`**: Utilizes Next.js App Router for routing, leveraging server components by default. Grouped folders like `(auth)` help logically organize routes without affecting the URL path.
- **`src/features`**: Implements Domain-Driven Design (DDD). Instead of scattering components, hooks, and services across global folders, they are grouped by domain (e.g., `bookings` contains all booking-related UI, state, and logic).
- **`src/components/ui`**: The foundational design system components (buttons, modals, typography). These should be highly reusable and agnostic to business logic.
- **`src/lib/blockchain`**: Isolates all Web3/Stellar network interactions, ensuring the UI remains decoupled from blockchain complexities.
- **`src/services/api`**: The central communication hub for backend API requests, structured to support robust error handling, retries, and token refresh mechanisms.
- **`tests/`**: Separates tests by scope to ensure clear boundaries. Unit tests evaluate individual functions, integration tests evaluate combined components, and e2e tests validate complete user journeys.

## 🚀 Frontend Scaling Strategy

1. **Feature-Based Modularity**: By organizing code within `src/features`, the codebase can scale indefinitely without global folders becoming bottlenecks. Teams can own specific feature domains.
2. **Server Components First**: Leveraging Next.js App Router allows the platform to shift heavy rendering to the server, resulting in smaller JavaScript bundles and faster Time-To-Interactive (TTI).
3. **Decoupled State Management**: Global state is restricted to truly global data (auth, theme) using tools like Zustand, while complex server state is managed via libraries like React Query, reducing boilerplate and managing cache efficiently.
4. **Web3 Readiness**: The architecture separates conventional Web2 APIs (`src/services/api`) from Web3 transactions (`src/lib/blockchain`), allowing seamless integration of wallets and decentralized escrows as the platform evolves.

## 🔄 CI/CD Structure Planning

The GitHub Actions workflows are designed to maintain enterprise-level code quality:
- **`ci.yml`**: Runs on every push and PR. Executes `npm run lint`, `npm run typecheck`, and `npm run test`.
- **`build.yml`**: Validates that the application can be built successfully for production without memory or dependency errors.
- **`preview-deployment.yml`**: Triggers on PRs to `main`. Creates an ephemeral Vercel preview deployment for QA and stakeholder review.
- **`production-deployment.yml`**: Triggers exclusively on tagged releases or merges to `main`. Manages the deployment to production infrastructure and runs post-deployment E2E sanity checks.
