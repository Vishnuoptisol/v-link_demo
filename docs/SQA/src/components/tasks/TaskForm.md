# TaskForm Component Documentation

## Overview

The `TaskForm.tsx` component provides a form interface for adding new tasks to a task list. It implements form validation using Zod schema, handles form submission, and renders a responsive form with an input field and a submission button.

## Component Documentation

### TaskForm Component

A client-side React component for creating new tasks.

#### Props

- **onAddTask**: `(taskText: string) => void` - A callback function that is invoked when a new task is submitted. It receives the task text as an argument.

#### Dependencies

- React Hook Form for form state management
- Zod for schema validation
- UI components from the project's component library
- Lucide React for icons

## Schema Documentation

### formSchema

A Zod schema that validates task input:

- **taskText**: A string that must be:
  - At least 1 character long (cannot be empty)
  - Maximum 100 characters

## Method Documentation

### onSubmit

A form submission handler that processes validated form data.

- **Access Modifier**: Private function within component scope
- **Parameters**:
  - `values`: `z.infer<typeof formSchema>` - An object containing the validated form values, specifically the `taskText` field
- **Functionality**:
  1. Calls the `onAddTask` callback with the task text
  2. Resets the form to its default state
- **Example Usage**:
  ```tsx
  function onSubmit(values: z.infer<typeof formSchema>) {
    onAddTask(values.taskText);
    form.reset();
  }
  ```

## Component Implementation

The component:

1. Sets up a form using React Hook Form with Zod validation
2. Defines default values for the form fields
3. Renders a responsive form layout that:
   - Displays vertically on small screens and horizontally on larger screens
   - Includes an input field for the task text
   - Shows validation errors when applicable
   - Provides a submit button with a plus icon

## UI Components Used

The component utilizes several UI components from the project's UI library:

- [`Button`](../ui/button.md) - For form submission
- [`Input`](../ui/input.md) - For text entry
- [`Form`](../ui/form.md) components - For form structure and validation display
  - `Form`
  - `FormControl`
  - `FormField`
  - `FormItem`
  - `FormMessage`

## Accessibility Features

- The "Add task" button includes an `aria-label` for screen readers
- Form validation provides error messages for invalid inputs
- The component maintains a logical tab order

## Related Components

This component is likely used within the task management system along with:

- [`TaskList.tsx`](./TaskList.md) - For displaying tasks
- [`TaskItem.tsx`](./TaskItem.md) - For rendering individual tasks
- [`SuggestedTasks.tsx`](./SuggestedTasks.md) - For task recommendations