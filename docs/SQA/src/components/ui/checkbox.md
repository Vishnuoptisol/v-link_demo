# Checkbox Component Documentation

## Overview
The `checkbox.tsx` file defines a reusable Checkbox component for the Testing application. This component is built using Radix UI's Checkbox primitive and styled with Tailwind CSS classes. The Checkbox component provides a customizable, accessible checkbox input that can be used throughout the application.

## Component Documentation

### Checkbox

#### Purpose
A customizable checkbox component that follows modern accessibility practices and provides consistent styling throughout the application.

#### Dependencies
- React from "react"
- Checkbox primitives from "@radix-ui/react-checkbox"
- Check icon from "lucide-react"
- Utility function `cn` from [utils.ts](../../lib/utils.md) for managing CSS class names

#### Props
The component accepts all standard React Checkbox props from Radix UI's CheckboxPrimitive.Root component:
- `className`: Optional string for additional CSS classes
- All other props are passed through to the underlying Radix UI Checkbox component

#### Implementation Details

The Checkbox component is implemented as a forwarded ref component that wraps the Radix UI CheckboxPrimitive.Root:

```tsx
const Checkbox = React.forwardRef<
  React.ElementRef<typeof CheckboxPrimitive.Root>,
  React.ComponentPropsWithoutRef<typeof CheckboxPrimitive.Root>
>(({ className, ...props }, ref) => (
  <CheckboxPrimitive.Root
    ref={ref}
    className={cn(
      "peer h-4 w-4 shrink-0 rounded-sm border border-primary ring-offset-background focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 data-[state=checked]:bg-primary data-[state=checked]:text-primary-foreground",
      className
    )}
    {...props}
  >
    <CheckboxPrimitive.Indicator
      className={cn("flex items-center justify-center text-current")}
    >
      <Check className="h-4 w-4" />
    </CheckboxPrimitive.Indicator>
  </CheckboxPrimitive.Root>
))
```

The component includes:
- A root element that renders the checkbox container with styling for different states (focus, disabled, checked)
- An indicator element that displays a check icon when the checkbox is checked
- Proper accessibility attributes via Radix UI primitives

#### Styling
The component uses Tailwind CSS classes for styling through the `cn` utility function from [utils.ts](../../lib/utils.md):
- Base sizing: `h-4 w-4` (height and width of 1rem)
- Visual styling: `rounded-sm border border-primary`
- Focus states: `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2`
- Disabled states: `disabled:cursor-not-allowed disabled:opacity-50`
- Checked states: `data-[state=checked]:bg-primary data-[state=checked]:text-primary-foreground`

#### Usage Example
```tsx
import { Checkbox } from "@/components/ui/checkbox"

// Basic usage
<Checkbox />

// With a label
<div className="flex items-center space-x-2">
  <Checkbox id="terms" />
  <label htmlFor="terms">Accept terms and conditions</label>
</div>

// Controlled component
const [checked, setChecked] = React.useState(false)
<Checkbox 
  checked={checked} 
  onCheckedChange={(value) => setChecked(value === true)} 
/>
```

## Related Components
The Checkbox component may be used in various forms throughout the application, including:
- [TaskForm.tsx](../tasks/TaskForm.md) for task creation/editing
- [FilterDrawer.tsx](../projects/FilterDrawer.md) for filtering options

## Notes
- The component uses the "use client" directive at the top, indicating it's designed to be used in Next.js client components.
- The checkbox includes a visual check icon from the Lucide icon library that appears when the checkbox is in a checked state.