# Separator Component Documentation

## Overview

The `separator.tsx` file defines a reusable UI component called `Separator`. This component provides a visual divider that can be used to separate content in the user interface. Built on top of Radix UI's primitive separator component, it supports both horizontal and vertical orientations with customizable styling through Tailwind CSS classes.

## Component Documentation

### Separator

A customizable separator component that creates a visual dividing line between UI elements.

#### Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `orientation` | `"horizontal" \| "vertical"` | `"horizontal"` | Determines the direction of the separator |
| `decorative` | `boolean` | `true` | When true, indicates the separator is for visual purposes only and should be ignored by screen readers |
| `className` | `string` | - | Additional CSS classes to apply to the separator |
| `...props` | `React.ComponentPropsWithoutRef<typeof SeparatorPrimitive.Root>` | - | Any other props passed to the underlying Radix UI Separator component |

#### Implementation Details

The component is implemented as a React forwardRef component that wraps the Radix UI Separator primitive. It uses the `cn` utility function from [`utils.ts`](../../lib/utils.md) to merge default and custom class names.

Default styling includes:
- `shrink-0` to prevent the separator from shrinking
- `bg-border` for the separator's color
- Conditional styling based on orientation:
  - Horizontal: `h-[1px] w-full` (1px height, full width)
  - Vertical: `h-full w-[1px]` (full height, 1px width)

## Usage Examples

### Horizontal Separator (Default)

```tsx
import { Separator } from "@/components/ui/separator"

export function HorizontalSeparatorExample() {
  return (
    <div>
      <div>Content above</div>
      <Separator />
      <div>Content below</div>
    </div>
  )
}
```

### Vertical Separator

```tsx
import { Separator } from "@/components/ui/separator"

export function VerticalSeparatorExample() {
  return (
    <div className="flex h-5">
      <div>Left content</div>
      <Separator orientation="vertical" className="mx-2" />
      <div>Right content</div>
    </div>
  )
}
```

### Custom Styling

```tsx
import { Separator } from "@/components/ui/separator"

export function CustomSeparatorExample() {
  return (
    <div>
      <div>Section one</div>
      <Separator className="my-4 bg-red-500" />
      <div>Section two</div>
    </div>
  )
}
```

## Dependencies

- React: Used for component creation and rendering
- `@radix-ui/react-separator`: Provides the underlying primitive separator functionality
- [`utils.ts`](../../lib/utils.md): Imports the `cn` utility function used for class name merging

## Notes

- The component is marked with `"use client"` directive, indicating it's designed to work in Next.js client components.
- The separator is set as decorative by default, making it semantically invisible to screen readers for better accessibility.
- The component properly forwards the React ref to the underlying DOM element.