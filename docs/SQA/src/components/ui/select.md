# Select Component Documentation

## Overview
The `select.tsx` file implements a customizable select component based on Radix UI's select primitive. This component provides a fully accessible dropdown selection interface with keyboard navigation, custom styling, and animated transitions. It's designed to be used within the Testing application UI framework and follows modern React patterns including the use of forward refs and composition.

## Component Documentation

### Dependencies
- React from React library
- Select components from Radix UI
- Icons (`Check`, `ChevronDown`, `ChevronUp`) from Lucide React
- Utility function `cn` from [utils.ts](../../lib/utils.md) for conditional class name merging

### Components

#### `Select`
A direct re-export of the base `SelectPrimitive.Root` component that serves as the container for the entire select component.

#### `SelectGroup`
A re-export of `SelectPrimitive.Group` that allows grouping select items together.

#### `SelectValue`
A re-export of `SelectPrimitive.Value` that displays the currently selected value.

#### `SelectTrigger`
The button that toggles the select dropdown.

**Props:**
- `className`: Optional custom CSS class name
- `children`: React node(s) to be rendered inside the trigger
- All other props are passed to the underlying Radix UI trigger component

**Implementation:**
```tsx
const SelectTrigger = React.forwardRef<
  React.ElementRef<typeof SelectPrimitive.Trigger>,
  React.ComponentPropsWithoutRef<typeof SelectPrimitive.Trigger>
>(({ className, children, ...props }, ref) => (
  <SelectPrimitive.Trigger
    ref={ref}
    className={cn(
      "flex h-10 w-full items-center justify-between rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 [&>span]:line-clamp-1",
      className
    )}
    {...props}
  >
    {children}
    <SelectPrimitive.Icon asChild>
      <ChevronDown className="h-4 w-4 opacity-50" />
    </SelectPrimitive.Icon>
  </SelectPrimitive.Trigger>
))
```

#### `SelectScrollUpButton`
A button that appears at the top of the select content when there are items to scroll up to.

**Props:**
- `className`: Optional custom CSS class name
- All other props are forwarded to the underlying Radix UI scroll up button

#### `SelectScrollDownButton`
A button that appears at the bottom of the select content when there are more items to scroll down to.

**Props:**
- `className`: Optional custom CSS class name
- All other props are forwarded to the underlying Radix UI scroll down button

#### `SelectContent`
The dropdown content that contains the select options.

**Props:**
- `className`: Optional custom CSS class name
- `children`: React node(s) to be rendered inside the content
- `position`: Positioning strategy, defaults to "popper"
- All other props are passed to the underlying Radix UI content component

**Implementation:**
```tsx
const SelectContent = React.forwardRef<
  React.ElementRef<typeof SelectPrimitive.Content>,
  React.ComponentPropsWithoutRef<typeof SelectPrimitive.Content>
>(({ className, children, position = "popper", ...props }, ref) => (
  <SelectPrimitive.Portal>
    <SelectPrimitive.Content
      ref={ref}
      className={cn(
        "relative z-50 max-h-96 min-w-[8rem] overflow-hidden rounded-md border bg-popover text-popover-foreground shadow-md data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0 data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-95 data-[side=bottom]:slide-in-from-top-2 data-[side=left]:slide-in-from-right-2 data-[side=right]:slide-in-from-left-2 data-[side=top]:slide-in-from-bottom-2",
        position === "popper" &&
          "data-[side=bottom]:translate-y-1 data-[side=left]:-translate-x-1 data-[side=right]:translate-x-1 data-[side=top]:-translate-y-1",
        className
      )}
      position={position}
      {...props}
    >
      <SelectScrollUpButton />
      <SelectPrimitive.Viewport
        className={cn(
          "p-1",
          position === "popper" &&
            "h-[var(--radix-select-trigger-height)] w-full min-w-[var(--radix-select-trigger-width)]"
        )}
      >
        {children}
      </SelectPrimitive.Viewport>
      <SelectScrollDownButton />
    </SelectPrimitive.Content>
  </SelectPrimitive.Portal>
))
```

#### `SelectLabel`
A label component for select items or groups.

**Props:**
- `className`: Optional custom CSS class name
- All other props are forwarded to the underlying Radix UI label component

#### `SelectItem`
An individual selectable option within the select dropdown.

**Props:**
- `className`: Optional custom CSS class name
- `children`: React node(s) to be rendered as the item content
- All other props are forwarded to the underlying Radix UI item component

**Implementation:**
```tsx
const SelectItem = React.forwardRef<
  React.ElementRef<typeof SelectPrimitive.Item>,
  React.ComponentPropsWithoutRef<typeof SelectPrimitive.Item>
>(({ className, children, ...props }, ref) => (
  <SelectPrimitive.Item
    ref={ref}
    className={cn(
      "relative flex w-full cursor-default select-none items-center rounded-sm py-1.5 pl-8 pr-2 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[disabled]:pointer-events-none data-[disabled]:opacity-50",
      className
    )}
    {...props}
  >
    <span className="absolute left-2 flex h-3.5 w-3.5 items-center justify-center">
      <SelectPrimitive.ItemIndicator>
        <Check className="h-4 w-4" />
      </SelectPrimitive.ItemIndicator>
    </span>

    <SelectPrimitive.ItemText>{children}</SelectPrimitive.ItemText>
  </SelectPrimitive.Item>
))
```

#### `SelectSeparator`
A visual separator between select items or groups.

**Props:**
- `className`: Optional custom CSS class name
- All other props are forwarded to the underlying Radix UI separator component

## Usage Example

```tsx
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"

export function ProjectStatusSelect() {
  return (
    <Select defaultValue="active">
      <SelectTrigger className="w-[180px]">
        <SelectValue placeholder="Select status" />
      </SelectTrigger>
      <SelectContent>
        <SelectItem value="active">Active</SelectItem>
        <SelectItem value="completed">Completed</SelectItem>
        <SelectItem value="on-hold">On Hold</SelectItem>
        <SelectItem value="cancelled">Cancelled</SelectItem>
      </SelectContent>
    </Select>
  )
}
```

## Notes
- The component uses Tailwind CSS for styling via the `cn` utility from [utils.ts](../../lib/utils.md)
- All components implement the forwardRef pattern to allow parent components to access the underlying DOM nodes
- The component provides proper accessibility features through the Radix UI primitives
- Animation and transition effects are included for opening/closing the dropdown