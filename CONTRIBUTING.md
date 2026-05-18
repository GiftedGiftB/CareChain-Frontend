Contributing to CareChain Frontend

Thank you for your interest in contributing to the CareChain Frontend! We welcome contributions from the community to help build the user interface for CareChain — a care coordination and support platform designed to connect users, caregivers, and service providers through a seamless digital experience.

Whether you are building new Next.js UI components, fixing bugs, improving accessibility, or proposing new features, your contributions are highly valuable.

Product Reference

Before contributing, please review the Product Requirements Document (PRD) to understand the system design, user flows, and development phases:

📄 CareChain Frontend PRD (add your link here)

Getting Started
1. Fork the repository on GitHub
2. Clone your fork locally:
git clone https://github.com/GiftedGiftB/CareChain-Frontend.git
cd CareChain-Frontend
3. Create a branch for your feature or fix:
git checkout -b feature/my-new-feature

Development Workflow

The CareChain frontend is the primary interface for users to interact with care services, manage requests, and communicate within the platform.

1. Tech Stack: Next.js (App Router), TypeScript, Tailwind CSS, React Hook Form, Zod, Axios, TanStack Query, Zustand, WebSocket client
2. User Roles: Users, Caregivers, and Administrators
3. Prerequisites: Node.js (v18 or higher) and a package manager (npm, yarn, or pnpm)

Installation & Setup

Install dependencies:

pnpm install

Set up environment variables:

cp .env.example .env.local

Then fill in the required values inside .env.local.

Start the development server:

pnpm dev

The app will be available at:
http://localhost:3000

Testing & UI Guidelines

Component Reliability
- Ensure UI components handle API failures gracefully
- Include loading states (skeletons/spinners)
- Follow acceptance criteria defined in the PRD (empty states, error handling, notifications)

Responsive Design

- All features must be mobile-first and fully responsive
- Test on mobile (375px) and desktop breakpoints

Accessibility

- Maintain proper contrast ratios
- Use semantic HTML and ARIA labels where needed
- Ensure keyboard navigation support

Feature Requests & GitHub Issues

We encourage community-driven contributions aligned with CareChain’s roadmap (MVP → Core Care Features → Scaling & Enhancements).

Tackling Existing Issues

Check the GitHub Issues tab and filter by:

- priority (high / medium / low)
- type (frontend / UI / bug)

Requesting a New Feature

Before opening a new issue:

- Search existing issues to avoid duplicates
- Clearly describe the problem or user need
- Explain your proposed solution
- Reference the PRD when applicable

Submitting a Pull Request

Before submitting your PR:

- Ensure all tests and checks pass
- Fix all TypeScript errors (no strict warnings)
- Run linting and formatting tools (ESLint / Prettier)
- Update documentation if you modify architecture or core components

PR Requirements

- Provide a clear description of changes
- Include screenshots or screen recordings for UI changes
- Link related issues using:
Closes #issue_id

License & Copyright

By contributing to this project, you agree that your contributions will be licensed under the MIT License, the same as the project.