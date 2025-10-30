# Label Component Documentation

## Overview
The `label.tsx` component provides a customizable and accessible label component for form elements in the Testing application. It's built on top of Radix UI's Label primitive, enhanced with styling through class-variance-authority, and integrated with the application's utility functions.

## Class Documentation

### `Label` Component

#### Purpose
A reusable label component that can be associated with form inputs to provide accessible text descriptions. The component supports all standard HTML label attributes while adding consistent styling and accessibility features.

#### Attributes
- `className`: `string` (optional) - Additional CSS classes to apply to the label
- `...props`: Any valid React props that can be applied to a label element
- Variant props from `labelVariants` - Style variants defined by class-variance-authority

#### Component Structure
The component is implemented as a forwarded ref component that wraps the Radix UI Label primitive, applying consistent styling through the defined `labelVariants`.

## Component Details

### `labelVariants`
A style configuration object created with `cva` (class-variance-authority) that defines the base styling for labels in the application.

```typescript
const labelVariants = cva(
  "text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
)
```

This applies the following styles to labels:
- Small text size (`text-sm`)
- Medium font weight (`font-medium`)
- No line height (`leading-none`)
- When associated with disabled elements:
  - Not-allowed cursor (`peer-disabled:cursor-not-allowed`)
  - Reduced opacity (`peer-disabled:opacity-70`)

### Dependencies
- Relies on the utility function `cn` from [utils.ts](../../lib/utils.md) to merge Tailwind CSS classes
- Uses the `LabelPrimitive` from Radix UI's React Label library
- Implements styling with `cva` from class-variance-authority

## Usage Examples

### Basic Usage
```tsx
import { Label } from "@/components/ui/label"
import { Input } from "@/components/ui/input"

export function InputWithLabel() {
  return (
    <div className="grid gap-2">
      <Label htmlFor="email">Email</Label>
      <Input id="email" type="email" />
    </div>
  )
}
```

### With Custom Styling
```tsx
import { Label } from "@/components/ui/label"
import { Input } from "@/components/ui/input"

export function CustomStyledLabel() {
  return (
    <div className="grid gap-2">
      <Label htmlFor="name" className="text-blue-500">
        Name
      </Label>
      <Input id="name" type="text" />
    </div>
  )
}
```

### With Form Component
The Label component is designed to work seamlessly with other form elements in the UI component library, such as [Input](./input.md), [Checkbox](./checkbox.md), [RadioGroup](./radio-group.md), and [Select](./select.md).

## Accessibility Features
- Properly forwards attributes like `htmlFor` to connect labels with their respective form controls
- Maintains ARIA compliance by using the Radix UI primitives
- Provides visual feedback for disabled states through the peer styling

## Related Components
- [Input](./input.md)
- [Checkbox](./checkbox.md)
- [RadioGroup](./radio-group.md)
- [Form](./form.md)
- [Select](./select.md)