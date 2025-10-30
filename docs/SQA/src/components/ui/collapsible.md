# Collapsible Component Documentation

## Overview
The `collapsible.tsx` file provides a set of React components for creating expandable and collapsible sections in a user interface. These components are built upon Radix UI's Collapsible primitives, offering an accessible and customizable way to implement collapsible content areas in the application. This is a client-side component as indicated by the `"use client"` directive at the top of the file.

## Component Documentation

### Collapsible Components
The file exports three main components that work together to create collapsible UI elements:

#### 1. Collapsible
- **Purpose**: Serves as the root container component for the collapsible functionality
- **Type**: Direct re-export of `CollapsiblePrimitive.Root`
- **Access**: Public export
- **Usage**: Wraps the trigger and content components to create a collapsible section

#### 2. CollapsibleTrigger
- **Purpose**: The interactive element that toggles the visibility of the collapsible content
- **Type**: Direct re-export of `CollapsiblePrimitive.CollapsibleTrigger`
- **Access**: Public export
- **Usage**: Placed within the `Collapsible` component to serve as the clickable trigger element

#### 3. CollapsibleContent
- **Purpose**: Contains the content that will be shown or hidden based on the collapsible state
- **Type**: Direct re-export of `CollapsiblePrimitive.CollapsibleContent`
- **Access**: Public export
- **Usage**: Placed within the `Collapsible` component to wrap the content that should be collapsible

## Dependencies
- **@radix-ui/react-collapsible**: The component relies on Radix UI's Collapsible primitive, which provides the core accessibility and state management functionality.

## Example Usage
```tsx
import { Collapsible, CollapsibleTrigger, CollapsibleContent } from "src/components/ui/collapsible";

export function CollapsibleExample() {
  return (
    <Collapsible className="w-full">
      <CollapsibleTrigger className="flex w-full justify-between p-4 font-medium">
        Click to expand
        <span>▼</span>
      </CollapsibleTrigger>
      <CollapsibleContent className="p-4">
        This is the collapsible content that can be shown or hidden.
      </CollapsibleContent>
    </Collapsible>
  );
}
```

## Integration
This component is part of the UI component library and can be used across the application where collapsible sections are needed, such as in:

- FAQ sections
- Sidebar navigation groups
- Details/summary patterns
- Advanced filtering options in [FilterDrawer.tsx](../../projects/FilterDrawer.md) or [ProjectDetailsFilterDrawer.tsx](../../projects/ProjectDetailsFilterDrawer.md)

The `Collapsible` component is designed to be flexible and can be styled with CSS or Tailwind classes to match the application's design system.