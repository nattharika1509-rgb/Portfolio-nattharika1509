---
description: Comprehensive error checking and debugging before deployment
---

# Debug & Validate Workflow

The final stage of the High-End AI Architect's process to ensure zero errors.

## Steps

### 1. Static Analysis
// turbo
Run: `npm run lint`
Run: `npx tsc --noEmit`

### 2. Performance Check
// turbo
Run: `npx lighthouse http://localhost:3000` (or similar audit tool)
Verify that LCP is under 2.5s.

### 3. Visual Regression
Use the browser subagent to visit the main pages and check for layout shifts (CLS).

### 4. Accessibility Check
Ensure all interactive elements have ARIA labels and pass basic contrast checks.
