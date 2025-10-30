# Switch Component Documentation

## Overview

The `switch.tsx` file defines a reusable Switch component, which is a toggle control that allows users to choose between two states. This component is built using Radix UI's React Switch primitive and styled with Tailwind CSS utility classes. The component supports all the props of the underlying Radix UI Switch component while adding custom styling that integrates with the application's design system.

## Class Documentation

### `Switch`

A React functional component that renders a toggle switch control.

**Type:**
```typescript
React.ForwardRefExoticComponent<
  React.ComponentPropsWithoutRef<typeof SwitchPrimitives.Root> & 
  React.RefAttributes<React.ElementRef<typeof SwitchPrimitives.Root>>
>
```

**Attributes:**
- Inherits all props from `SwitchPrimitives.Root` 
- `className`: Optional string for additional CSS classes

## Component Implementation Details

The `Switch` component is implemented using React's `forwardRef` to allow passing of refs to the underlying DOM element. It wraps Radix UI's `SwitchPrimitives.Root` and `SwitchPrimitives.Thumb` components to create a styled toggle switch.

The component uses the `cn` utility function from [utils.ts](../../lib/utils.md) to combine class names for styling the switch.

### Styling

The switch has the following styling features:
- A rounded, pill-shaped toggle (11px × 6px)
- Different background colors for checked and unchecked states
- A moving thumb element that slides from left to right
- Focus state indicators for accessibility
- Disabled state styling
- Smooth transitions for state changes

## Usage Example

```tsx
import { Switch } from "@/components/ui/switch";

// Basic usage
<Switch />

// With controlled state
const [checked, setChecked] = React.useState(false);
<Switch checked={checked} onCheckedChange={setChecked} />

// With additional props
<Switch 
  checked={enabled}
  onCheckedChange={setEnabled}
  aria-label="Toggle feature"
  disabled={isLoading}
  className="my-custom-class"
/>
```

## Accessibility

The component ensures accessibility by:
- Using Radix UI primitives that manage ARIA attributes and keyboard interactions
- Supporting focus states with visible outlines
- Maintaining proper contrast between states
- Supporting disabled states with visual indicators

## Dependencies

- React: Used for component definition and rendering
- `@radix-ui/react-switch`: Provides the underlying unstyled switch functionality
- [utils.ts](../../lib/utils.md): Provides the `cn` utility for class name management

## Notes

This component is part of the UI component library and can be used across the application wherever a toggle control is needed. The styling follows the application's design system, using the `primary` color for the checked state and appropriate visual feedback for user interactions.