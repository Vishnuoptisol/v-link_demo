# RadioGroup Component Documentation

## Overview
The `radio-group.tsx` file defines a reusable radio group component built on top of Radix UI's radio group primitive. It provides styled radio group functionality for the Testing application, allowing users to select a single option from a set of choices. The component consists of two main parts: a container (`RadioGroup`) and individual radio items (`RadioGroupItem`).

## Class Documentation

### RadioGroup
A wrapper component around the Radix UI RadioGroup.Root component that creates a container for radio options.

**Attributes:**
- `className`: string (optional) - Additional CSS classes to apply to the component
- All other props inherited from RadioGroupPrimitive.Root

**Access Modifier:** Public component exported from the module

### RadioGroupItem
A component representing an individual radio button option within a RadioGroup.

**Attributes:**
- `className`: string (optional) - Additional CSS classes to apply to the component
- All other props inherited from RadioGroupPrimitive.Item

**Access Modifier:** Public component exported from the module

## Method Documentation

### RadioGroup
```tsx
const RadioGroup = React.forwardRef<
  React.ElementRef<typeof RadioGroupPrimitive.Root>,
  React.ComponentPropsWithoutRef<typeof RadioGroupPrimitive.Root>
>(({ className, ...props }, ref) => {
  return (
    <RadioGroupPrimitive.Root
      className={cn("grid gap-2", className)}
      {...props}
      ref={ref}
    />
  )
})
```

**Description:**
1. Accepts a className and other props for customization
2. Uses forwardRef to allow ref forwarding to the underlying DOM element
3. Renders a RadioGroupPrimitive.Root component with a default grid layout and spacing
4. Applies utility class merging using the `cn` function from [utils.ts](../../lib/utils.md)

**Parameters:**
- `className`: string (optional) - CSS classes to be merged with default styles
- `props`: React.ComponentPropsWithoutRef<typeof RadioGroupPrimitive.Root> - All other props to be passed to the RadioGroupPrimitive.Root component
- `ref`: React.Ref - Reference to be forwarded to the underlying element

**Return Type:** JSX.Element

**Example Usage:**
```tsx
<RadioGroup defaultValue="option1" onValueChange={(value) => console.log(value)}>
  <div className="flex items-center space-x-2">
    <RadioGroupItem value="option1" id="option1" />
    <Label htmlFor="option1">Option 1</Label>
  </div>
  <div className="flex items-center space-x-2">
    <RadioGroupItem value="option2" id="option2" />
    <Label htmlFor="option2">Option 2</Label>
  </div>
</RadioGroup>
```

### RadioGroupItem
```tsx
const RadioGroupItem = React.forwardRef<
  React.ElementRef<typeof RadioGroupPrimitive.Item>,
  React.ComponentPropsWithoutRef<typeof RadioGroupPrimitive.Item>
>(({ className, ...props }, ref) => {
  return (
    <RadioGroupPrimitive.Item
      ref={ref}
      className={cn(
        "aspect-square h-4 w-4 rounded-full border border-primary text-primary ring-offset-background focus:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50",
        className
      )}
      {...props}
    >
      <RadioGroupPrimitive.Indicator className="flex items-center justify-center">
        <Circle className="h-2.5 w-2.5 fill-current text-current" />
      </RadioGroupPrimitive.Indicator>
    </RadioGroupPrimitive.Item>
  )
})
```

**Description:**
1. Accepts a className and other props for customization
2. Uses forwardRef to allow ref forwarding to the underlying DOM element
3. Renders a RadioGroupPrimitive.Item component with styled appearance
4. Includes a RadioGroupPrimitive.Indicator that displays a Circle icon when the item is selected
5. Applies accessibility-friendly focus and disabled states
6. Utilizes the `cn` function from [utils.ts](../../lib/utils.md) for class name composition

**Parameters:**
- `className`: string (optional) - CSS classes to be merged with default styles
- `props`: React.ComponentPropsWithoutRef<typeof RadioGroupPrimitive.Item> - All other props to be passed to the RadioGroupPrimitive.Item component
- `ref`: React.Ref - Reference to be forwarded to the underlying element

**Return Type:** JSX.Element

**Example Usage:**
```tsx
<div className="flex items-center space-x-2">
  <RadioGroupItem value="default" id="default" />
  <Label htmlFor="default">Default</Label>
</div>
```

## Dependencies
- React: Used for component definition and hooks
- @radix-ui/react-radio-group: Provides unstyled, accessible radio group primitives
- lucide-react: Provides the Circle icon for the selected indicator
- [utils.ts](../../lib/utils.md): Provides the `cn` utility function for composing class names

This component is a UI building block that can be used in forms across the application, particularly in the [TaskForm.tsx](../tasks/TaskForm.md) component or other form components requiring radio selection functionality.