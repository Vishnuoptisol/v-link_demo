# Toast Component Documentation

## Overview

This file implements a comprehensive toast notification system for the application using Radix UI's toast primitives. The toast component provides non-intrusive feedback to users through notifications that appear and disappear automatically. The implementation offers customizable toast notifications with various variants, positions, and interactive elements.

## Component Documentation

### ToastProvider

**Purpose**: Provides context for all toast components.

**Usage**: Should wrap the application or section where toasts are used.

### ToastViewport

**Purpose**: Defines the container where toasts are rendered.

**Properties**:
- `className`: Optional string to add custom CSS classes
- All other props passed to the underlying Radix UI Viewport component

**Implementation**: A forwarded ref component that renders toasts in a fixed position on the screen, with responsive behavior for different screen sizes.

### Toast

**Purpose**: The main toast component that displays notifications.

**Properties**:
- `variant`: Determines the visual style of the toast ("default" or "destructive")
- `className`: Optional string to add custom CSS classes
- All other props from Radix UI's Toast.Root component

**Variants**:
- `default`: Standard notification with neutral styling
- `destructive`: Error/warning notification with emphasis styling

### ToastAction

**Purpose**: An action button that can be included in toasts.

**Properties**:
- `className`: Optional string to add custom CSS classes
- All other props passed to the underlying Radix UI Action component

**Styling**: Adapts its styling based on the parent toast's variant.

### ToastClose

**Purpose**: A close button for dismissing toasts manually.

**Properties**:
- `className`: Optional string to add custom CSS classes
- All other props passed to the underlying Radix UI Close component

**Visual**: Renders an 'X' icon from Lucide React library.

### ToastTitle

**Purpose**: The title section of a toast notification.

**Properties**:
- `className`: Optional string to add custom CSS classes
- All other props passed to the underlying Radix UI Title component

### ToastDescription

**Purpose**: The descriptive content section of a toast notification.

**Properties**:
- `className`: Optional string to add custom CSS classes
- All other props passed to the underlying Radix UI Description component

## Type Definitions

### ToastProps

**Purpose**: Type definition for the Toast component props.

**Definition**: Extends React's ComponentPropsWithoutRef for the Toast component.

### ToastActionElement

**Purpose**: Type definition for action elements within toasts.

**Definition**: React.ReactElement specialized for the ToastAction component.

## Usage Examples

### Basic Toast

```tsx
import { ToastProvider, ToastViewport, Toast, ToastTitle, ToastDescription } from "@/components/ui/toast";

// Inside your component
<ToastProvider>
  <Toast>
    <ToastTitle>Notification</ToastTitle>
    <ToastDescription>Your action was completed successfully.</ToastDescription>
  </Toast>
  <ToastViewport />
</ToastProvider>
```

### Toast with Action and Close Button

```tsx
<Toast>
  <div>
    <ToastTitle>Error occurred</ToastTitle>
    <ToastDescription>Could not save your changes.</ToastDescription>
  </div>
  <ToastAction altText="Try again">Retry</ToastAction>
  <ToastClose />
</Toast>
```

### Destructive Toast

```tsx
<Toast variant="destructive">
  <ToastTitle>Error</ToastTitle>
  <ToastDescription>There was a problem with your request.</ToastDescription>
  <ToastClose />
</Toast>
```

## Dependencies

This component depends on:
- React from [React](https://reactjs.org/)
- Radix UI React Toast primitives from [@radix-ui/react-toast](https://www.radix-ui.com/docs/primitives/components/toast)
- class-variance-authority for variant styling
- Lucide React for the close icon
- The utility function `cn` from [utils.ts](../../lib/utils.md) for class name merging

## Related Components

The toast system is typically used alongside the [toaster.tsx](./toaster.md) component, which implements the toast management system and provides hooks for creating and managing toasts throughout the application.