# TaskList Component Documentation

## Overview

The `TaskList` component is responsible for rendering a list of tasks in the application. It displays either a list of tasks or an empty state message when no tasks are available. Tasks are sorted to show incomplete tasks before completed ones.

## Component Documentation

### TaskList

A functional React component that renders either a list of tasks or an empty state indicator.

#### Props

- **tasks**: `Task[]` - An array of task objects to be displayed, imported from [`@/types`](../../types/index.md).
- **onToggleTask**: `(id: string) => void` - A callback function to toggle a task's completion status.
- **onDeleteTask**: `(id: string) => void` - A callback function to delete a task.

## Implementation Details

### Conditional Rendering

The component implements conditional rendering based on the presence of tasks:

1. If the `tasks` array is empty, it renders an empty state with an icon and informative message.
2. If tasks exist, it sorts them (incomplete tasks first) and renders each as a `TaskItem` component.

### Task Sorting

The component sorts tasks by their completion status:
```typescript
const sortedTasks = [...tasks].sort((a, b) => Number(a.completed) - Number(b.completed));
```
This ensures incomplete tasks appear before completed ones in the list.

### Empty State

When no tasks are present, the component displays a styled empty state with:
- A `FileCheck2` icon from [Lucide React](https://lucide.dev)
- "All Clear!" heading
- A guidance message encouraging the user to add a new task

### Task List Rendering

When tasks exist, the component:
1. Displays a "Your Tasks" heading
2. Maps through the sorted tasks array
3. Renders each task as a [`TaskItem`](./TaskItem.md) component, passing:
   - The task object
   - Toggle and delete callback functions

## Example Usage

```tsx
import { TaskList } from '@/components/tasks/TaskList';
import { useState } from 'react';
import type { Task } from '@/types';

export function TaskManager() {
  const [tasks, setTasks] = useState<Task[]>([
    { id: '1', title: 'Complete project documentation', completed: false },
    { id: '2', title: 'Review pull requests', completed: true }
  ]);
  
  const handleToggleTask = (id: string) => {
    setTasks(tasks.map(task => 
      task.id === id ? { ...task, completed: !task.completed } : task
    ));
  };
  
  const handleDeleteTask = (id: string) => {
    setTasks(tasks.filter(task => task.id !== id));
  };
  
  return (
    <TaskList 
      tasks={tasks} 
      onToggleTask={handleToggleTask} 
      onDeleteTask={handleDeleteTask} 
    />
  );
}
```

## Dependencies

- [`@/types`](../../types/index.md) - Imports the `Task` type definition
- [`./TaskItem`](./TaskItem.md) - Imports the `TaskItem` component used to render individual tasks
- [`lucide-react`](https://lucide.dev) - Imports the `FileCheck2` icon for the empty state

## Styling

The component uses Tailwind CSS classes for styling:
- Flexbox for layout alignment
- Border styling for the empty state container
- Spacing utilities for consistent padding and margins
- Text styling for proper typography hierarchy