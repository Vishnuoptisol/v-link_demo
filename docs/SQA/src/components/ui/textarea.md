# Textarea Component Documentation

## Overview

The `textarea.tsx` file defines a reusable Textarea component that provides a styled `<textarea>` HTML element for use throughout the application. This component is part of the UI component library and follows a consistent design pattern with other form elements. It utilizes React's forwardRef to properly handle ref forwarding and implements customizable styling through className merging.

## Component Documentation

### Textarea

A customized textarea component that applies consistent styling and supports all standard HTML textarea attributes.

#### Props

- **className**: `string` (optional) - Additional CSS classes to apply to the textarea
- **...props**: All standard HTML textarea attributes are supported via React.ComponentProps<'textarea'>
- **ref**: Forwarded React ref to access the underlying HTML textarea element

#### Implementation Details

The component:
1. Uses React's forwardRef to properly handle ref forwarding to the underlying textarea element
2. Applies a set of base styles using the [utils.ts](../../../lib/utils.md) `cn` utility function
3. Merges any additional className passed in props with the base styles
4. Spreads all other props to the underlying textarea element

## Usage Example

```tsx
import { Textarea } from "@/components/ui/textarea";

// Basic usage
<Textarea placeholder="Enter your message here" />

// With additional properties
<Textarea 
  placeholder="Enter your feedback" 
  className="h-32" 
  name="feedback"
  required
/>

// With controlled component pattern
const [value, setValue] = React.useState("");
<Textarea 
  value={value}
  onChange={(e) => setValue(e.target.value)}
  placeholder="Type here..."
/>
```

## Dependencies

- Imports React from the React library
- Uses the `cn` utility function from [utils.ts](../../../lib/utils.md) for class name merging

## Styling

The component uses a set of base Tailwind CSS classes that:

- Set minimum height (`min-h-[80px]`)
- Make the textarea full width (`w-full`)
- Apply rounded corners (`rounded-md`)
- Add a border with the designated input color (`border border-input`)
- Set background color (`bg-background`)
- Apply consistent padding (`px-3 py-2`)
- Set text styling (`text-base` on mobile, `text-sm` on medium screens and up)
- Style the placeholder text (`placeholder:text-muted-foreground`)
- Add focus styles with a ring outline (`focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2`)
- Apply disabled state styling (`disabled:cursor-not-allowed disabled:opacity-50`)

## Related Components

This component is part of the UI component library and follows similar patterns to other form components like:

- [Input](./input.md) - For single-line text input
- [Select](./select.md) - For dropdown selection
- [Checkbox](./checkbox.md) - For boolean input
- [Form](./form.md) - For form composition