# TaskItem.tsx Documentation

## Overview

`TaskItem.tsx` is a React component that renders a single task item in a task list interface. It provides functionality for displaying task text, marking tasks as complete or incomplete via a checkbox, and deleting tasks. The component uses a client-side rendering approach and incorporates styling with Tailwind CSS classes.

## Class Documentation

### TaskItem

A functional React component that renders an individual task item.

#### Props

| Name | Type | Description |
|------|------|-------------|
| `task` | [Task](../../../types/index.md) | Task object containing id, text, and completion status |
| `onToggleTask` | `(id: string) => void` | Callback function to toggle task completion status |
| `onDeleteTask` | `(id: string) => void` | Callback function to delete a task |

## Method Documentation

### TaskItem Function

```typescript
export function TaskItem({ task, onToggleTask, onDeleteTask }: TaskItemProps) { ... }
```

**Access Modifier:** `export`  
**Parameters:**
- `{ task, onToggleTask, onDeleteTask }`: Destructured `TaskItemProps` object

**Return Type:** JSX.Element

**Functionality:**
1. Generates a unique ID for the checkbox based on the task ID
2. Returns a list item (`<li>`) containing:
   - A checkbox for toggling task completion
   - A label displaying the task text
   - A delete button with trash icon

**Example Usage:**
```jsx
<TaskItem 
  task={{ id: "task-1", text: "Complete documentation", completed: false }}
  onToggleTask={(id) => handleTaskToggle(id)}
  onDeleteTask={(id) => handleTaskDelete(id)}
/>
```

## Component Details

### Visual Representation
The component displays as a list item with:
- A checkbox on the left for toggling completion status
- The task text in the center
- A delete button (trash icon) on the right

### Behavior
- When the checkbox is clicked, the `onToggleTask` function is called with the task ID
- When the delete button is clicked, the `onDeleteTask` function is called with the task ID
- Completed tasks show with a line-through text style and muted color
- The component has hover states for better user interaction feedback

### Accessibility Features
- Proper aria-labels for the checkbox and delete button
- Associated label with checkbox using htmlFor/id pairing
- Semantic HTML structure with list item

## Dependencies

The component depends on:
- Task type from [types/index.ts](../../../types/index.md)
- [Button](../../ui/button.md) component from UI library
- [Checkbox](../../ui/checkbox.md) component from UI library
- Trash2 icon from [lucide-react](https://lucide.dev/icons/trash-2) library
- cn utility function from [lib/utils.ts](../../../lib/utils.md) for conditional class name composition

## Related Components

This component is typically used within:
- [TaskList.tsx](./TaskList.md) - Which renders a collection of TaskItem components