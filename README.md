# CareChain Frontend 🌐🛡️

**A decentralized, blockchain-powered caregiving platform designed for trust, transparency, and global accessibility.**

![CareChain Banner](https://via.placeholder.com/1200x300?text=CareChain+Frontend+-+Decentralized+Caregiving)

## 📖 Project Overview

**CareChain** is a revolutionary blockchain-powered caregiving platform that bridges the gap between families seeking reliable care and verified caregivers seeking fair, transparent opportunities. 

This repository contains the **Frontend Client Application** of the CareChain ecosystem. It is the primary user-facing interface, built with modern web technologies, ensuring a seamless, responsive, and secure experience while abstracting the complexities of the underlying blockchain infrastructure.

### Why CareChain?
The caregiving industry suffers from structural inefficiencies. CareChain exists to restore trust, automate fair compensation, and provide a secure digital ecosystem where care services can be booked and managed with complete peace of mind.

---

## 🚨 Problem Statement

The traditional caregiving ecosystem is plagued by critical pain points:
- **Lack of Trust:** Families struggle to verify the credentials, history, and reliability of caregivers.
- **Payment Disputes:** Ambiguity in service delivery often leads to delayed payments or wage theft.
- **Accessibility Barriers:** High agency fees limit access to quality care for many families.
- **Cross-Border Payment Challenges:** Migrant or international caregivers face exorbitant remittance fees.

---

## 💡 Proposed Solution

CareChain solves these problems by combining a modern, intuitive frontend UX with robust decentralized infrastructure:
- **Decentralized Infrastructure:** Utilizing the Stellar blockchain for fast, low-cost, and immutable transaction records.
- **Escrow Workflows:** Funds are securely locked in smart contracts and only released upon verifiable completion of care services.
- **Blockchain Transparency:** Every transaction and review is immutably recorded, preventing fraud and manipulation.
- **Modern UX:** A consumer-grade application that feels familiar and easy to use, masking the complexity of Web3.

---

## 📈 Business Value

- **Financial Inclusion:** Enables unbanked caregivers to receive payments globally via crypto wallets.
- **Economic Opportunities:** Removes the "middleman" agencies, allowing caregivers to earn more while families pay less.
- **Trust Infrastructure:** Built-in reputation systems guarantee the highest quality of care.
- **Community Empowerment:** Localized caregiver networks can form seamlessly through the platform.

---

## 👥 Target Users

1. **Families/Care Seekers:** Looking for verified, trusted care for their loved ones.
2. **Caregivers/Nurses:** Professionals seeking fair wages, flexible hours, and transparent payment mechanisms.
3. **Healthcare Communities:** Local organizations needing a trusted ledger of verified workers.
4. **Underserved Populations:** Individuals lacking access to traditional banking infrastructure.
5. **Admins/Moderators:** Platform operators ensuring quality control, dispute resolution, and verification.

---

## 🏗️ Frontend Architecture

The frontend is architected for **enterprise scalability** and **Web3 readiness**:

- **Application Architecture:** Next.js (App Router) for Server-Side Rendering (SSR) and optimized SEO.
- **Component Architecture:** Atomic design principles using Tailwind CSS and Radix UI / Shadcn.
- **State Management:** Zustand for lightweight global UI state; React Query for server/API state caching.
- **API Integration:** Axios instances with centralized error handling and JWT interceptors (BFF pattern).
- **Security:** Strict HTTP-only cookie handling for sessions, XSS/CSRF protections, and robust RBAC (Role-Based Access Control) enforced at the middleware layer.

---

## ✨ Frontend Features

- **Authentication & Authorization:** Secure JWT login, wallet connection (e.g., Freighter/Albedo), and role-based routing (User, Caregiver, Admin).
- **Caregiver Discovery:** Advanced filtering algorithms, geospatial search, and rich caregiver profiles displaying verified skills, availability, and immutable reviews.
- **Booking Workflows:** Intuitive calendar interfaces for scheduling, booking modifications, and real-time status tracking (Pending -> Confirmed -> Completed).
- **Role-Based Dashboards:** Dedicated views for earnings, upcoming jobs, platform analytics, and user management.
- **Decentralized Payments:** Seamless integration with Stellar for escrow funding and release, visualized through human-readable transaction histories.

---

## 🛣️ Development Phases

### Phase 1 — MVP Foundation
- Focus on robust Authentication (Email/Password & JWT).
- Basic caregiver discovery and profile viewing.
- Simple booking flow (creation and status updates).
- MVP Dashboards for Users and Caregivers.
- Core API integration and Demo-ready UX.

### Phase 2 — Core Platform Expansion
- Implementation of distinct Role Dashboards.
- Comprehensive Reviews and Ratings system.
- Advanced filtering, sorting, and search capabilities.
- Real-time updates (WebSocket) for booking status changes.
- Automated caregiver verification workflows.

### Phase 3 — Decentralized Payment & Trust Layer
- Non-custodial Wallet integration (Stellar).
- Blockchain transaction visibility and block explorers.
- Smart contract escrow tracking and visualization.
- Trust indicators and decentralized reputation systems.

### Phase 4 — Production & Scale
- Performance optimization (Lighthouse 90+ across all metrics).
- Security hardening and external audits.
- Telemetry, logging, and advanced analytics integration.
- Global CDN distribution and edge computing readiness.

---

## 📂 Folder Structure Documentation

*(For a comprehensive breakdown, see `PROJECT_STRUCTURE.md`)*

- `src/app`: Next.js App Router definitions and page layouts.
- `src/features`: Domain-driven feature modules (e.g., `bookings`, `auth`).
- `src/components`: Highly reusable, business-agnostic UI elements.
- `src/lib`: Core integrations (Blockchain SDKs, Axios, WebSockets).
- `src/services`: Centralized API and smart contract communication layer.

---

## 🛠️ Installation & Setup

### Prerequisites
- Node.js (v18.x or later)
- npm or yarn
- Git

### Local Development Setup
1. **Clone the repository:**
   ```bash
   git clone https://github.com/CareChain/CareChain-Frontend.git
   cd CareChain-Frontend
   ```
2. **Install dependencies:**
   ```bash
   npm install
   ```
3. **Configure Environment Variables:**
   Copy the example environment file and update the values.
   ```bash
   cp .env.example .env.local
   ```
4. **Run the development server:**
   ```bash
   npm run dev
   ```

### Build Process
```bash
npm run build
npm run start
```

---

## 🔐 Environment Variables

The application requires several environment variables to function correctly. These must be defined in your `.env.local` or deployment provider.

| Variable | Description |
|----------|-------------|
| `NEXT_PUBLIC_API_BASE_URL` | Base URL for the CareChain Backend API |
| `NEXT_PUBLIC_WS_URL` | WebSocket URL for real-time notifications |
| `NEXT_PUBLIC_STELLAR_NETWORK` | Stellar network selection (`TESTNET` or `PUBLIC`) |
| `NEXT_PUBLIC_HORIZON_URL` | Stellar Horizon RPC endpoint |
| `NEXT_PUBLIC_ANALYTICS_ID` | Identifier for platform analytics (e.g., PostHog/GA) |

---

## 🔌 API Integration Layer

The frontend communicates with the backend via a highly structured Service Layer (`src/services/api`):
- **Organization:** APIs are segmented by domain (e.g., `UserService.ts`, `BookingService.ts`).
- **Error Handling:** Centralized Axios interceptors catch 4xx/5xx errors, triggering global toast notifications and localized error states.
- **Retry Mechanisms:** Idempotent requests (e.g., GET) are configured with exponential backoff retries.
- **Token Strategy:** Silent token refresh workflows occur in the background prior to JWT expiration.

---

## 🛡️ Security Overview

- **JWT Handling:** Tokens are stored in secure, `HttpOnly` cookies; access tokens are maintained in memory.
- **Route Protection:** Next.js Middleware intercepts requests to protected routes, validating roles before rendering pages.
- **Frontend Security:** Strict Content Security Policy (CSP), sanitization of user inputs (DOMPurify), and standard CSRF protections.

---

## ♿ Accessibility & UX

- **Responsive Design:** Mobile-first approach ensuring full functionality on devices of all sizes.
- **Accessibility (a11y):** ARIA labels, keyboard navigation support, and WCAG 2.1 AA compliance focus.
- **Feedback States:** Comprehensive loading skeletons, empty state illustrations, and robust error boundaries to prevent app crashes.
- **Notifications:** Non-intrusive toast notifications and a dedicated notification center for critical alerts.

---

## 🧪 Testing Strategy

Quality is ensured through a multi-tiered testing strategy:
- **Unit Testing:** Jest/Vitest for individual utility functions and complex React hooks.
- **Integration Testing:** React Testing Library for verifying component interactions and state changes.
- **E2E Testing:** Cypress/Playwright for critical user journeys (e.g., Wallet Connection -> Booking -> Escrow Release).

---

## 🚀 Deployment Strategy

The application is optimized for containerized and serverless environments:
- **CI/CD Pipelines:** GitHub Actions validate PRs (linting, type-checking, tests).
- **Preview Deployments:** Vercel automatically generates preview URLs for every pull request.
- **Production:** Automated deployments trigger upon merging to the `main` branch, coupled with automated cache invalidation.
- **Docker:** A production-ready `Dockerfile` is included for self-hosted or Kubernetes-based deployments.

---

## 🤝 Contribution Guidelines

1. **Branch Naming:** `feature/<ticket>-<description>`, `bugfix/<ticket>-<description>`
2. **Commit Standards:** Follow Conventional Commits (`feat:`, `fix:`, `chore:`).
3. **Pull Requests:** Must pass all CI checks and require at least one approving review from a core maintainer.
4. **Code Review:** Focus on accessibility, performance, and adherence to the defined architecture.

---

## 🔮 Future Roadmap

- Native mobile application using React Native (sharing core logic).
- Integration of decentralized identity (DID) for advanced caregiver verification.
- AI-powered caregiver-to-family matchmaking algorithms.
- Multilingual and regional localization expansion.

---

## 📄 License

[MIT License](./LICENSE) - Copyright (c) 2024 CareChain

---

## 👥 Team & Author Information

- **Frontend Architect:** [Name/Role]
- **Blockchain Engineer:** [Name/Role]
- **Product Manager:** [Name/Role]
- **Design Lead:** [Name/Role]

*CareChain - Empowering Care, Securing Trust.*
