---
name: design-system-patterns
description: Build scalable design systems with design tokens, theming infrastructure, and component architecture patterns.
---

# Design System Patterns

## design-system-patterns Logic

### 1. Design Tokens
- **Primitive**: Raw values (e.g., #3b82f6).
- **Semantic**: Meaningful context (e.g., text-primary).
- **Component**: Specific usage (e.g., button-bg).

### 2. Theme Switching
```tsx
const [theme, setTheme] = useState<Theme>("system");
useEffect(() => {
  const root = document.documentElement;
  root.classList.add(isDark ? "dark" : "light");
}, [theme]);
```

### 3. Variant System with CVA
```tsx
const buttonVariants = cva("...", {
  variants: {
    variant: { default: "...", ghost: "..." },
    size: { sm: "...", lg: "..." }
  }
});
```

### Best Practices
- **Semantic Naming**: Use `text-primary`, not `dark-gray`.
- **Token Hierarchy**: Primitives > Semantic > Components.
- **Automation**: CI/CD for Figma-to-code synchronization.
