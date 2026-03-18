---
name: nextjs-performance
description: Expert Next.js performance optimization skill covering Core Web Vitals, image/font optimization, caching strategies, streaming, bundle optimization, and Server Components best practices.
---

# Next.js Performance Optimization

## Core Web Vitals Optimization
- **LCP (Largest Contentful Paint)**: Optimize images and fonts.
- **INP (Interaction to Next Paint)**: Reduce JS, use Server Components.
- **CLS (Cumulative Layout Shift)**: Add dimensions to images, use `next/font`.

## Core Principles
1. **Prefer Server Components**: Only use 'use client' when necessary.
2. **Load components low**: Keep Client Components at leaf nodes.
3. **Use Suspense boundaries**: Enable streaming and progressive loading.
4. **Cache appropriately**: Use tags for granular revalidation.

## Examples

### Image Optimization
```tsx
import Image from 'next/image'

export function Hero() {
  return (
    <Image src="/hero.jpg" alt="Hero" fill priority sizes="100vw" />
  )
}
```

### Caching Strategy
```tsx
const getProducts = unstable_cache(
  async () => db.product.findMany(),
  ['products'],
  { revalidate: 3600, tags: ['products'] }
)
```

### Next.js 16 + React 19: useOptimistic
```tsx
'use client'
import { useOptimistic } from 'react'

export function TodoList({ todos }) {
  const [optimisticTodos, addOptimisticTodo] = useOptimistic(
    todos,
    (state, newTodo) => [...state, newTodo]
  )
  // ...
}
```
