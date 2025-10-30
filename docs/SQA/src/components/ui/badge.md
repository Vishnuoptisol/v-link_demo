# Badge Component Documentation

## Overview

The Badge component is a UI element that renders a small, pill-shaped indicator typically used for status updates, notifications, or labels. This component is part of the UI library and provides various visual styles through its variant system.

## Class Documentation

### `Badge` Function Component

A React functional component that renders a stylized badge with customizable appearances.

**Props**:
- `className`: String - Additional CSS classes to apply to the badge
- `variant`: String - Visual style variant for the badge (default, secondary, destructive, outline, success)
- `...props`: Object - Any additional HTML div element props

## Implementation Details

The Badge component uses the class-variance-authority (cva) library to manage style variants and the [utils.ts](../../lib/utils.md) utility for class name composition.

### Style Variants

The component defines several visual styles through the `badgeVariants` configuration:

- `default`: Primary background color with contrasting text
- `secondary`: Secondary background color with contrasting text
- `destructive`: Error/destructive background color with contrasting text
- `outline`: Bordered style with foreground text color
- `success`: Green background color for success states

### Component Structure

The Badge component renders as a `<div>` element with appropriate styling based on the selected variant and any additional className passed to it.

## Usage Examples

```tsx
// Default variant
<Badge>New</Badge>

// Success variant
<Badge variant="success">Completed</Badge>

// Destructive variant
<Badge variant="destructive">Error</Badge>

// Outline variant
<Badge variant="outline">Draft</Badge>

// With additional className
<Badge className="my-2">Custom Badge</Badge>
```

## Dependencies

- React: Core library for component creation
- class-variance-authority: For creating variant-based styling
- [utils.ts](../../lib/utils.md): Utilizes the `cn` utility function for class name composition

## API Reference

### BadgeProps Interface

Extends standard HTML div element attributes with variant options:

```tsx
export interface BadgeProps
  extends React.HTMLAttributes<HTMLDivElement>,
    VariantProps<typeof badgeVariants> {}
```

### Exports

The component exports:
- `Badge`: The main component
- `badgeVariants`: The style variants configuration (useful for composition with other components)

## Related Components

The Badge component is often used with other UI components like:
- Status indicators
- Notification systems
- Category labels
- Tag systems

Being a simple display component, the Badge is typically used within other more complex components to highlight information or status.