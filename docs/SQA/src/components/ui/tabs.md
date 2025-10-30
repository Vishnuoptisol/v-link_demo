# Tabs Component Documentation

## Overview

This file provides a set of customizable tab components built on top of Radix UI's tabs primitives. The components offer accessible tab functionality with custom styling using Tailwind CSS. The tabs allow for organizing content into multiple sections that can be shown one at a time, improving UI organization and user experience.

## Component Documentation

### Tabs

A wrapper component that manages the state and functionality of the tabs interface.

**Type**: `React.FC<TabsPrimitive.TabsProps>`

**Usage**: Serves as the root container for all tab-related components.

### TabsList

A component that contains and displays the tab triggers in a horizontal layout.

**Type**: `React.ForwardRefExoticComponent<TabsPrimitive.TabsListProps & React.RefAttributes<HTMLDivElement>>`

**Props**:
- `className`: Optional string for additional CSS classes
- All other props from `TabsPrimitive.List`

**Styling**: 
- Displays as an inline flex container with rounded corners and muted background
- Has consistent height and padding
- Inherits text colors from the muted foreground theme

### TabsTrigger

A component representing an individual tab button that users can click to switch between tab contents.

**Type**: `React.ForwardRefExoticComponent<TabsPrimitive.TabsTriggerProps & React.RefAttributes<HTMLButtonElement>>`

**Props**:
- `className`: Optional string for additional CSS classes
- All other props from `TabsPrimitive.Trigger`

**Styling**:
- Displays as an inline flex item with centered content
- Has padding and rounded corners
- Shows visual feedback when active, focused, or disabled
- Uses transition effects for smooth state changes

### TabsContent

A component that contains the content associated with a specific tab trigger.

**Type**: `React.ForwardRefExoticComponent<TabsPrimitive.TabsContentProps & React.RefAttributes<HTMLDivElement>>`

**Props**:
- `className`: Optional string for additional CSS classes
- All other props from `TabsPrimitive.Content`

**Styling**:
- Has margin at the top to separate from triggers
- Includes focus styles with outline and ring effects

## Dependencies

- **React**: Core library for building the component UI
- **@radix-ui/react-tabs**: Provides accessible tab primitives
- **[utils.ts](../../lib/utils.md)**: Imports the `cn` utility function for handling class name composition

## Example Usage

```tsx
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";

export default function TabsExample() {
  return (
    <Tabs defaultValue="account">
      <TabsList>
        <TabsTrigger value="account">Account</TabsTrigger>
        <TabsTrigger value="password">Password</TabsTrigger>
        <TabsTrigger value="settings" disabled>Settings</TabsTrigger>
      </TabsList>
      <TabsContent value="account">
        <p>Account content goes here.</p>
      </TabsContent>
      <TabsContent value="password">
        <p>Password content goes here.</p>
      </TabsContent>
      <TabsContent value="settings">
        <p>Settings content goes here.</p>
      </TabsContent>
    </Tabs>
  );
}
```

## Accessibility Features

- Keyboard navigation between tabs
- Proper ARIA attributes through Radix UI primitives
- Focus management
- State indicators for active tabs

## Notes

- All components use the `forwardRef` pattern to properly handle refs
- The components leverage Tailwind CSS for styling through the `cn` utility
- The tabs are fully responsive and can be customized with additional classes