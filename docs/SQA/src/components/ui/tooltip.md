# Tooltip Component Documentation

## Overview

The `tooltip.tsx` file implements a customizable tooltip component for the application, providing contextual information that appears when users hover over or focus on an element. This component is built using Radix UI's tooltip primitives and styled with Tailwind CSS. The tooltip offers a clean, accessible way to display additional information without cluttering the interface.

## Class Documentation

### Component Exports

The file exports four main components:

1. **TooltipProvider** - A context provider that manages tooltip interactions
2. **Tooltip** - The root component that wraps tooltip functionality
3. **TooltipTrigger** - The element that triggers the tooltip display
4. **TooltipContent** - The content displayed inside the tooltip

## Component Documentation

### `TooltipProvider`

A direct re-export of `TooltipPrimitive.Provider` from Radix UI.

- **Purpose**: Provides context for tooltips to function properly within the application
- **Usage**: Should be used at a high level in the component tree, typically wrapping areas where tooltips are needed

### `Tooltip`

A direct re-export of `TooltipPrimitive.Root` from Radix UI.

- **Purpose**: Root component that manages tooltip state and behavior
- **Usage**: Wraps both the trigger and content components

### `TooltipTrigger`

A direct re-export of `TooltipPrimitive.Trigger` from Radix UI.

- **Purpose**: Defines the interactive element that will show the tooltip when hovered or focused
- **Usage**: Wraps the element that should trigger the tooltip display

### `TooltipContent`

A customized version of `TooltipPrimitive.Content` from Radix UI.

- **Purpose**: Defines the appearance and behavior of the tooltip content
- **Type**: React.ForwardRefExoticComponent
- **Props**:
  - `className`: Optional string for additional CSS classes
  - `sideOffset`: Number determining the distance from the trigger (defaults to 4)
  - `...props`: All other props are passed to the underlying TooltipPrimitive.Content component
- **Styling**: Uses the `cn` utility from [`utils.ts`](../../lib/utils.md) to merge the default styles with any custom classes

## Method Documentation

### TooltipContent forwardRef Implementation

```typescript
const TooltipContent = React.forwardRef<
  React.ElementRef<typeof TooltipPrimitive.Content>,
  React.ComponentPropsWithoutRef<typeof TooltipPrimitive.Content>
>(({ className, sideOffset = 4, ...props }, ref) => (
  <TooltipPrimitive.Content
    ref={ref}
    sideOffset={sideOffset}
    className={cn(
      "z-50 overflow-hidden rounded-md border bg-popover px-3 py-1.5 text-sm text-popover-foreground shadow-md animate-in fade-in-0 zoom-in-95 data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=closed]:zoom-out-95 data-[side=bottom]:slide-in-from-top-2 data-[side=left]:slide-in-from-right-2 data-[side=right]:slide-in-from-left-2 data-[side=top]:slide-in-from-bottom-2",
      className
    )}
    {...props}
  />
))
```

- **Purpose**: Creates a styled tooltip content component that forwards refs
- **Parameters**:
  - `{ className, sideOffset = 4, ...props }`: Destructured props with default sideOffset of 4
  - `ref`: React ref passed to the underlying component
- **Returns**: A styled TooltipPrimitive.Content component
- **Styling Details**:
  - Uses `z-50` for high stacking context
  - Applies rounded corners, border and shadow for visual definition
  - Includes animations for entry/exit transitions
  - Has directional animations based on tooltip position (top, bottom, left, right)
  - Uses Tailwind's utility classes for styling

## Example Usage

```tsx
import { Tooltip, TooltipContent, TooltipProvider, TooltipTrigger } from "@/components/ui/tooltip";

export function TooltipExample() {
  return (
    <TooltipProvider>
      <Tooltip>
        <TooltipTrigger asChild>
          <button className="rounded-md bg-primary px-4 py-2 text-white">
            Hover me
          </button>
        </TooltipTrigger>
        <TooltipContent>
          <p>This is a helpful tooltip</p>
        </TooltipContent>
      </Tooltip>
    </TooltipProvider>
  );
}
```

## Dependencies

The tooltip component has the following dependencies:
- React from 'react'
- Radix UI tooltip primitives from '@radix-ui/react-tooltip'
- The `cn` utility function from [`utils.ts`](../../lib/utils.md), which is used for merging class names

## Accessibility

The tooltip component leverages Radix UI's primitives which provide built-in accessibility features including:
- Proper focus management
- Keyboard navigation
- ARIA attributes
- Screen reader compatibility