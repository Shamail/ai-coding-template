---
trigger: glob
description: Defines frontend development guidelines for React applications
globs: packages/web/**/*.{ts,tsx,js,jsx}
---

# Frontend Development Guidelines

These guidelines build upon the core coding conventions and are specific to frontend development with React.

## React Component Structure

1. **Component Organization**
   - Use functional components with hooks instead of class components
   - Keep components small and focused on a single responsibility
   - Extract reusable logic into custom hooks
   - Co-locate component files with their test files
   - Use kebab-case for component filenames (e.g., `user-profile.tsx`)

2. **Component Hierarchy**
   - Create a clear component hierarchy with smart/container components and presentational components
   - Use composition over prop drilling
   - Limit component nesting to avoid performance issues

3. **Props and State Management**
   - Define prop types explicitly using TypeScript interfaces
   - Use default props when appropriate
   - Avoid large prop objects; break them down into smaller, more specific props
   - Use React Context for global state that doesn't change often
   - Consider using state management libraries only when necessary

## React Hooks

1. **Hook Usage**
   - Follow the Rules of Hooks strictly
   - Use appropriate dependency arrays for useEffect, useMemo, and useCallback
   - Extract complex hook logic into custom hooks
   - Name custom hooks with the "use" prefix

2. **Common Hooks**
   - `useState`: For local component state
   - `useEffect`: For side effects (API calls, subscriptions)
   - `useContext`: For accessing context
   - `useReducer`: For complex state logic
   - `useMemo`: For expensive calculations
   - `useCallback`: For memoized callbacks
   - `useRef`: For mutable references

## Styling

1. **Tailwind CSS**
   - Use Tailwind CSS for styling components
   - Follow the utility-first approach
   - Extract common patterns into component classes when they repeat
   - Use the @apply directive sparingly
   - Maintain a consistent color scheme using Tailwind's configuration

2. **Shadcn UI Components**
   - Use Shadcn UI components for common UI elements
   - Customize components through Tailwind configuration
   - Follow Shadcn UI's composition patterns
   - Keep component customizations consistent
   - use `bunx shadcn@latest [component a] [component b]` to install components 

## Routing

1. **React Router**
   - Define routes in a centralized location
   - Use dynamic routes for parameterized pages
   - Implement proper route guards for authenticated routes
   - Use lazy loading for route components to improve performance

## Forms

1. **Form Handling**
   - Use controlled components for form inputs
   - Implement proper form validation
   - Provide clear error messages for invalid inputs
   - Use form libraries (like React Hook Form) for complex forms

## Performance Optimization

1. **Rendering Optimization**
   - Use React.memo for components that render often with the same props
   - Use useMemo and useCallback to prevent unnecessary re-renders
   - Implement virtualization for long lists
   - Use code splitting and lazy loading for large components

2. **Asset Optimization**
   - Optimize images and other assets
   - Use appropriate image formats (WebP, SVG)
   - Implement lazy loading for images

## Testing

1. **Component Testing**
   - Test component rendering and interactions
   - Use React Testing Library for component tests
   - Test both success and error states
   - Mock external dependencies

## Accessibility

1. **A11y Requirements**
   - Use semantic HTML elements
   - Implement proper ARIA attributes
   - Ensure keyboard navigation works
   - Test with screen readers
   - Maintain appropriate color contrast

## SEO

1. **SEO Best Practices**
   - Use appropriate meta tags
   - Implement structured data when applicable
   - Ensure proper heading hierarchy
   - Optimize for performance (Core Web Vitals)

## Internationalization

1. **i18n Support**
   - Extract all user-facing strings
   - Use appropriate i18n libraries
   - Support right-to-left languages when necessary

## Error Boundaries

1. **Error Handling**
   - Implement error boundaries to catch rendering errors
   - Provide fallback UI for error states
   - Log errors appropriately

## Package Management

1. **Dependencies**
   - Keep dependencies up to date
   - Avoid unnecessary dependencies
   - Use specific version numbers in package.json
   - Consider bundle size when adding new dependencies