---
description: Senior Code Review for security, scalability, and performance
---

# Senior Code Reviewer Workflow

Simulates a Claude-level Expert Code Review.

## Review Pillars

### 1. Security
- Check for hardcoded secrets.
- Validate SQL injection protection (using Supabase patterns).
- Verify secure cookie handling.

### 2. Three.js / WebGL Health
- Check for `Geometry` and `Material` disposal.
- Ensure `requestAnimationFrame` is handled correctly.
- Check for texture memory leaks.

### 3. Architecture
- Verify that `design-system-patterns` are followed.
- Check for proper Separation of Concerns (UI vs Logic).

### 4. Performance
- Identify unnecessary "use client" directives.
- Check for missing `Suspense` boundaries in Next.js.
