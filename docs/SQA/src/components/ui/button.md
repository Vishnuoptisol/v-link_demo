# Button Component Documentation

## Overview

The Button component is a reusable UI element that implements a customizable button with various styling options. It provides multiple variants and sizes, allowing for consistent button styling throughout the application. This component is built using React and leverages the class-variance-authority library for handling style variations.

## Dependencies

- React core functionality from React library
- Slot component from Radix UI for component composition
- Class variance authority (cva) for style variant management
- Utility function `cn` from [utils.ts](../../lib/utils.md) for merging class names

## Class Documentation

### `Button`

A flexible button component that can be customized with different variants and sizes.

#### Props

The `ButtonProps` interface extends:
- `React.ButtonHTMLAttributes<HTMLButtonElement>`: All standard HTML button attributes
- `VariantProps<typeof buttonVariants>`: Variant props generated from buttonVariants

Additional props:
- `asChild?: boolean`: When true, the component renders its children as the root element (defaults to false)

## Style Variants

The `buttonVariants` constant defines the styling options available for the Button component:

### Variants

- `default`: Primary button with brand color background
- `destructive`: Red/warning button for dangerous actions
- `outline`: Button with a border and transparent background
- `secondary`: Alternative button style with secondary colors
- `ghost`: Transparent button that shows background only on hover
- `link`: Button that appears as a text link with underline on hover

### Sizes

- `default`: Standard button size (h-10, px-4, py-2)
- `sm`: Small button (h-9, rounded-md, px-3)
- `lg`: Large button (h-11, rounded-md, px-8)
- `icon`: Square button for icons (h-10, w-10)

## Implementation Details

The Button component uses React's `forwardRef` to properly handle ref forwarding to the DOM button element. It conditionally renders either a standard HTML button or a Radix UI Slot component based on the `asChild` prop.

The component applies class names using the `cn` utility function from [utils.ts](../../lib/utils.md), which combines the variant styles with any additional className passed to the component.

## Example Usage

Basic usage:

```tsx
import { Button } from "@/components/ui/button"

// Default button
<Button>Click me</Button>

// Destructive variant with small size
<Button variant="destructive" size="sm">Delete</Button>

// Outline variant with large size
<Button variant="outline" size="lg">Cancel</Button>

// Icon button
<Button size="icon">
  <svg>...</svg>
</Button>

// As child (wrapping another component)
<Button asChild>
  <a href="/dashboard">Go to Dashboard</a>
</Button>
```

## Related Components

The Button component is a fundamental UI element that is likely used by many other components in the project, such as forms, dialogs, and interactive elements throughout the application.

## Notes

- The component includes special styling for SVG icons with the class rule `[&_svg]:size-4`
- Focus states are managed with the `focus-visible` class variants for accessibility
- Disabled state styling is handled automatically when the disabled attribute is applied