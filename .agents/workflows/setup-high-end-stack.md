---
description: Setup a high-end web stack (Next.js, Better Auth, Supabase, Shadcn UI)
---

# High-End Stack Setup Workflow

This workflow automates the initialization of a premium web application stack.

## Steps

### 1. Initialize Next.js Project
// turbo
Run: `npx create-next-app@latest ./ --typescript --tailwind --eslint --app`

### 2. Install Expert Skills
// turbo
Run: `npx skills add https://github.com/google-labs-code/stitch-skills --skill shadcn-ui`
Run: `npx skills add better-auth-best-practices`

### 3. Initialize Shared Components
// turbo
Run: `npx shadcn@latest init`
Run: `npx shadcn@latest add button card dialog`

### 4. Configure Design Tokens
Apply the `design-system-patterns` defaults to `tailwind.config.ts`.

### 5. Setup Database & Auth
Initialize Supabase client and Better Auth server configuration using the provided skills.
