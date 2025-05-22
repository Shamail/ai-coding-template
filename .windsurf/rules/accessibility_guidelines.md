---
trigger: glob
description: Defines accessibility standards and practices for the application
globs: **/*.{ts,tsx,js,jsx}
---

# Accessibility Guidelines

This document outlines concrete accessibility standards that must be followed when generating code to ensure inclusive user experiences.

## HTML Structure and Semantics

1. **Semantic HTML**
   - Always use semantic HTML elements (`<header>`, `<main>`, `<nav>`, `<footer>`, `<section>`, `<article>`) instead of generic `<div>` elements
   - Implement proper heading hierarchy (h1-h6) with only one `<h1>` per page
   - Use appropriate list structures (`<ul>`, `<ol>`, `<dl>`) for list content
   - Use `<button>` for clickable actions and `<a>` for navigation with proper href attributes
   - Use `<table>` with `<th>`, `<caption>`, and appropriate ARIA attributes for tabular data

2. **Form Implementation**
   - Always associate `<label>` with form controls using `for` attribute or wrapping
   - Group related form controls with `<fieldset>` and `<legend>`
   - Include validation feedback that is programmatically associated with inputs
   - Use appropriate input types (`email`, `tel`, `number`, etc.)
   - Add `required` attribute and aria-required for mandatory fields

## ARIA and Keyboard Support

1. **ARIA Usage**
   - Add `aria-label` or `aria-labelledby` for elements without visible text
   - Use `aria-expanded`, `aria-haspopup`, and `aria-controls` for interactive components
   - Implement `aria-live` regions for dynamic content with appropriate politeness levels
   - Add `role` attributes only when HTML semantics need enhancement
   - Use `aria-hidden="true"` for decorative elements

2. **Keyboard Interactions**
   - Ensure all interactive elements can be accessed and activated with keyboard
   - Implement keyboard event handlers (Enter/Space for buttons, arrow keys for navigation)
   - Add visible focus styles with `:focus` and `:focus-visible`
   - Implement focus management for modals, dialogs, and custom widgets
   - Add `tabindex="0"` only for non-interactive elements that need focus

## Media and Content

1. **Images and Icons**
   - Add descriptive `alt` text for all informative images
   - Use empty `alt=""` for decorative images
   - Implement SVG icons with appropriate accessibility attributes
   - Add title and description for complex SVGs using `<title>` and `<desc>`
   - Ensure text overlaid on images has sufficient contrast

2. **Color and Contrast**
   - Maintain minimum contrast ratios: 4.5:1 for normal text, 3:1 for large text
   - Never rely on color alone to convey information (add text, patterns, or icons)
   - Provide visible focus indicators with sufficient contrast
   - Implement high contrast mode support
   - Use relative units (em, rem) for text sizing

## Component-Specific Guidelines

1. **Modal Dialogs**
   - Trap focus within modal when open
   - Add `role="dialog"` and `aria-modal="true"`
   - Provide close mechanism via button and ESC key
   - Return focus to triggering element when closed
   - Add descriptive aria-labelledby pointing to modal title

2. **Navigation Menus**
   - Implement keyboard navigation for dropdown menus
   - Add aria-expanded and aria-haspopup for dropdown triggers
   - Make menu items focusable and selectable by keyboard
   - Provide visual indication of current page/section
   - Add skip links at the beginning of the page

3. **Custom Components**
   - Follow WAI-ARIA Authoring Practices for custom widgets
   - Implement expected keyboard behavior for each component type
   - Test custom components with keyboard-only navigation
   - Provide appropriate ARIA roles, states, and properties
   - Ensure touch targets are at least 44x44 pixels
