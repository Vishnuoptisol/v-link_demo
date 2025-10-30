# SuggestedTasks Component Documentation

## Overview

The `SuggestedTasks` component is a React component that displays AI-generated task suggestions to users. It presents a list of suggested tasks that users can add to their task list with a single click. The component handles both loading states and the display of suggestion items, providing a clean interface for AI-assisted task management.

## Class Documentation

### SuggestedTasks Function Component

**Type:** React Functional Component  
**Exported:** Yes  
**Props Type:** `SuggestedTasksProps`

```tsx
export function SuggestedTasks({
  suggestions,
  loading,
  onAddSuggestedTask,
}: SuggestedTasksProps)
```

## Props Documentation

### SuggestedTasksProps

**Type:** TypeScript Interface  
**Properties:**
- `suggestions`: `string[]` - Array of task suggestion texts provided by AI
- `loading`: `boolean` - Flag indicating whether suggestions are currently being loaded
- `onAddSuggestedTask`: `(taskText: string) => void` - Callback function that gets triggered when a user adds a suggested task

## Component Behavior

The component renders differently based on the `loading` prop:

1. **When loading is true:**
   - Displays skeleton UI elements to indicate loading in progress
   
2. **When loading is false and suggestions are available:**
   - Renders a list of suggested tasks with an "Add" button for each suggestion

3. **When no suggestions are available:**
   - Nothing is displayed inside the suggestions container beyond the header

## Dependencies

- UI Components:
  - [`Button`](../ui/button.md) from `@/components/ui/button` - Used for the "Add" action button
  - [`Skeleton`](../ui/skeleton.md) from `@/components/ui/skeleton` - Used for loading states

- Icons (from `lucide-react`):
  - `Lightbulb` - Icon displayed next to the "AI Suggestions" heading
  - `Plus` - Icon for the add button on each suggestion

## Detailed Implementation

The component structure consists of:

1. **Container**: A bordered, slightly translucent container with rounded corners that holds all suggestion content.

2. **Header**: A heading that displays "AI Suggestions" with a lightbulb icon.

3. **Content Area**: Conditionally renders either:
   - Skeleton loaders when `loading` is true
   - A list of suggestions when `loading` is false and `suggestions` has items

4. **Suggestion Items**: Each suggestion is displayed in its own container with:
   - The suggestion text displayed with muted styling
   - An "Add" button that calls the `onAddSuggestedTask` callback when clicked

## Usage Example

```tsx
import { SuggestedTasks } from '@/components/tasks/SuggestedTasks';
import { useState } from 'react';

function TaskContainer() {
  const [tasks, setTasks] = useState<string[]>([]);
  const [isLoading, setIsLoading] = useState(false);
  const suggestions = ["Complete project documentation", "Schedule team meeting"];

  const handleAddSuggestion = (taskText: string) => {
    setTasks(prev => [...prev, taskText]);
  };

  return (
    <div className="p-4">
      <SuggestedTasks
        suggestions={suggestions}
        loading={isLoading}
        onAddSuggestedTask={handleAddSuggestion}
      />
    </div>
  );
}
```

## Accessibility

- The component uses appropriate semantic HTML elements
- The "Add" button includes an `aria-label` that describes the action and includes the suggestion text for screen readers
- Visual states are communicated through both color and icon to support users with visual impairments

## Related Components

The `SuggestedTasks` component would likely be used alongside other task management components in the application, such as:

- [`TaskList`](TaskList.md) - For displaying the user's current tasks
- [`TaskForm`](TaskForm.md) - For manually adding new tasks
- [`TaskItem`](TaskItem.md) - For rendering individual task items