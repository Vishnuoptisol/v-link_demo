# Input Component Documentation

## Overview

The `Input` component is a customizable and reusable form input element for the Testing application. It extends the native HTML input element with consistent styling while maintaining all standard input functionality. This component is part of the UI component library and is designed to work seamlessly with other UI components in the application.

## Component Documentation

### Input

A styled input component that uses React's forwardRef to allow ref forwarding to the underlying HTML input element.

#### Props

The component accepts all standard HTML input attributes from React.ComponentProps<"input">, including:

- `className`: Optional string for additional CSS classes
- `type`: Optional string defining the input type (text, email, password, etc.)
- `...props`: All other standard HTML input attributes (placeholder, value, onChange, etc.)

#### Implementation

The Input component wraps the native HTML `<input>` element and applies consistent styling through the [utility function `cn`](../../../lib/utils.md), which combines Tailwind CSS classes with any custom classes passed to the component.

## Usage Examples

### Basic Usage

```tsx
import { Input } from "@/components/ui/input"

function MyForm() {
  return <Input placeholder="Enter your name" />
}
```

### With Type

```tsx
import { Input } from "@/components/ui/input"

function PasswordField() {
  return <Input type="password" placeholder="Enter your password" />
}
```

### With Custom Styling

```tsx
import { Input } from "@/components/ui/input"

function CustomInput() {
  return <Input className="border-red-500" placeholder="Error state" />
}
```

### As Form Element

```tsx
import { Input } from "@/components/ui/input"
import { Label } from "@/components/ui/label"

function FormField() {
  return (
    <div className="space-y-2">
      <Label htmlFor="email">Email</Label>
      <Input id="email" type="email" placeholder="example@mail.com" required />
    </div>
  )
}
```

## Dependencies

- [utils.ts](../../../lib/utils.md): Provides the `cn` utility function for combining class names with Tailwind's conditional classes

## Styling Details

The component applies a comprehensive set of styles that handle:

- Base dimensions (height, width, padding)
- Border styling and rounding
- Background and text colors
- Focus states with ring outlines
- Disabled state styling
- File input special styling
- Responsive text sizing (base on mobile, sm on desktop)

The component also inherits the application's theme colors through Tailwind's semantic color variables like `border-input`, `bg-background`, and `ring-ring`.

## Related Components

The Input component is often used with other form components like:

- [Label](./label.md)
- [Form](./form.md)
- [Textarea](./textarea.md)