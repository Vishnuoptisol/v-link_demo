# Form Component Documentation

## Overview

The `form.tsx` component provides a comprehensive form management system that integrates [React Hook Form](https://react-hook-form.com/) with accessible UI components. This file exports various form-related components such as `Form`, `FormField`, `FormItem`, `FormLabel`, `FormControl`, `FormDescription`, and `FormMessage`, which together create an accessible, type-safe form system with built-in error handling capabilities.

The implementation uses React context to manage form field state and accessibility attributes, ensuring proper ARIA relationships between form elements. This component depends on the [utils.ts](../../../lib/utils.md) utility module and the [label.tsx](./label.md) component.

## Class Documentation

### Context Providers

#### FormFieldContext
- **Purpose**: Manages the context for individual form fields
- **Type**: React Context
- **Value Type**: `FormFieldContextValue` - Contains the field name

#### FormItemContext
- **Purpose**: Manages the context for form items (containers for fields)
- **Type**: React Context
- **Value Type**: `FormItemContextValue` - Contains the unique ID for the form item

## Component Documentation

### Form
- **Purpose**: Main form container component
- **Type**: Alias for `FormProvider` from react-hook-form
- **Usage**: Used as the root component for forms to provide form context

### FormField
- **Purpose**: Connects form controls to React Hook Form
- **Type**: Generic React function component
- **Generic Types**:
  - `TFieldValues`: Type of form values
  - `TName`: Type of field name paths
- **Props**: Accepts all `ControllerProps` from react-hook-form
- **Implementation**: Wraps the react-hook-form `Controller` with context

### FormItem
- **Purpose**: Container for form field components
- **Type**: React forwardRef component
- **Props**: HTML div attributes
- **Implementation**: Provides item context with a unique ID and renders a styled container

### FormLabel
- **Purpose**: Label for form inputs with error styling
- **Type**: React forwardRef component
- **Props**: Extends LabelPrimitive.Root props
- **Implementation**: Uses [Label](./label.md) component with error styling when field has errors

### FormControl
- **Purpose**: Connects inputs to the form field
- **Type**: React forwardRef component
- **Props**: Extends Slot props
- **Implementation**: Adds appropriate ARIA attributes based on field state

### FormDescription
- **Purpose**: Provides descriptive text for form fields
- **Type**: React forwardRef component
- **Props**: HTML paragraph attributes
- **Implementation**: Renders helper text with appropriate styling and ARIA connections

### FormMessage
- **Purpose**: Displays form validation error messages
- **Type**: React forwardRef component
- **Props**: HTML paragraph attributes
- **Implementation**: Shows field error messages with appropriate styling and ARIA connections

## Method Documentation

### useFormField
- **Purpose**: Custom hook to access form field context values
- **Access Modifier**: Public
- **Return Type**: Object containing:
  - `id`: Field ID
  - `name`: Field name
  - `formItemId`: ID for the form item
  - `formDescriptionId`: ID for form description element
  - `formMessageId`: ID for error message element
  - Field state properties from react-hook-form
- **Implementation**:
  ```typescript
  const useFormField = () => {
    const fieldContext = React.useContext(FormFieldContext)
    const itemContext = React.useContext(FormItemContext)
    const { getFieldState, formState } = useFormContext()

    const fieldState = getFieldState(fieldContext.name, formState)

    if (!fieldContext) {
      throw new Error("useFormField should be used within <FormField>")
    }

    const { id } = itemContext

    return {
      id,
      name: fieldContext.name,
      formItemId: `${id}-form-item`,
      formDescriptionId: `${id}-form-item-description`,
      formMessageId: `${id}-form-item-message`,
      ...fieldState,
    }
  }
  ```
- **Example Usage**:
  ```tsx
  const CustomInput = () => {
    const { error, formItemId } = useFormField();
    return <input id={formItemId} className={error ? "error" : ""} />;
  }
  ```

## Usage Example

```tsx
import { useForm } from "react-hook-form";
import { z } from "zod";
import { zodResolver } from "@hookform/resolvers/zod";
import {
  Form,
  FormField,
  FormItem,
  FormLabel,
  FormControl,
  FormDescription,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

// Define form schema
const formSchema = z.object({
  username: z.string().min(2, {
    message: "Username must be at least 2 characters.",
  }),
});

export function ProfileForm() {
  const form = useForm({
    resolver: zodResolver(formSchema),
    defaultValues: {
      username: "",
    },
  });

  function onSubmit(values) {
    console.log(values);
  }

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
        <FormField
          control={form.control}
          name="username"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Username</FormLabel>
              <FormControl>
                <Input placeholder="johndoe" {...field} />
              </FormControl>
              <FormDescription>
                This is your public display name.
              </FormDescription>
              <FormMessage />
            </FormItem>
          )}
        />
        <button type="submit">Submit</button>
      </form>
    </Form>
  );
}
```

## Dependencies

- [utils.ts](../../../lib/utils.md): Provides utility functions like `cn()` for class name management
- [label.tsx](./label.md): Provides the Label component used by FormLabel
- External libraries:
  - `@radix-ui/react-label`: Provides accessible label primitives
  - `@radix-ui/react-slot`: Provides the Slot component for passing refs through components
  - `react-hook-form`: Provides form state management and validation

## Accessibility Features

- Proper ARIA attributes for form fields
- Error state handling with appropriate ARIA attributes
- Connected form labels and descriptions
- Unique IDs for form elements