# Alert Dialog Component Documentation

## Overview

The Alert Dialog component is a client-side React UI element that implements an accessible modal dialog for critical information that requires user acknowledgment or confirmation before proceeding with an action. It's built on top of [Radix UI's Alert Dialog primitives](https://www.radix-ui.com/primitives/docs/components/alert-dialog) with additional styling and composition enhancements for better usability and visual integration with the application design system.

This component is specifically designed for important confirmations where users should be explicitly asked before proceeding with potentially destructive actions, unlike standard dialogs that can be used for more general-purpose modals.

## Dependencies

- The component uses utilities from [`@/lib/utils`](../../lib/utils.md) for class name management
- It leverages button styling from [`@/components/ui/button`](./button.md)
- It's built using Radix UI's Alert Dialog primitives

## Component Documentation

### AlertDialog

**Purpose**: Root component that manages the state of the alert dialog.

```tsx
const AlertDialog = AlertDialogPrimitive.Root
```

### AlertDialogTrigger

**Purpose**: The button that opens the alert dialog when clicked.

```tsx
const AlertDialogTrigger = AlertDialogPrimitive.Trigger
```

### AlertDialogPortal

**Purpose**: Creates a portal for rendering the dialog outside the DOM hierarchy.

```tsx
const AlertDialogPortal = AlertDialogPrimitive.Portal
```

### AlertDialogOverlay

**Purpose**: Creates a semi-transparent overlay that covers the page behind the dialog.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogOverlay = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Overlay>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Overlay>
>(({ className, ...props }, ref) => (
  <AlertDialogPrimitive.Overlay
    className={cn(
      "fixed inset-0 z-50 bg-black/80 data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0",
      className
    )}
    {...props}
    ref={ref}
  />
))
```

### AlertDialogContent

**Purpose**: The container for alert dialog content with positioning and styling.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogContent = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Content>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Content>
>(({ className, ...props }, ref) => (
  <AlertDialogPortal>
    <AlertDialogOverlay />
    <AlertDialogPrimitive.Content
      ref={ref}
      className={cn(
        "fixed left-[50%] top-[50%] z-50 grid w-full max-w-lg translate-x-[-50%] translate-y-[-50%] gap-4 border bg-background p-6 shadow-lg duration-200 data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0 data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-95 data-[state=closed]:slide-out-to-left-1/2 data-[state=closed]:slide-out-to-top-[48%] data-[state=open]:slide-in-from-left-1/2 data-[state=open]:slide-in-from-top-[48%] sm:rounded-lg",
        className
      )}
      {...props}
    />
  </AlertDialogPortal>
))
```

### AlertDialogHeader

**Purpose**: Container for the title and description of the alert dialog.

**Props**:
- `className`: Custom CSS class
- Additional standard HTML div props

```tsx
const AlertDialogHeader = ({
  className,
  ...props
}: React.HTMLAttributes<HTMLDivElement>) => (
  <div
    className={cn(
      "flex flex-col space-y-2 text-center sm:text-left",
      className
    )}
    {...props}
  />
)
```

### AlertDialogFooter

**Purpose**: Container for the action buttons of the alert dialog.

**Props**:
- `className`: Custom CSS class
- Additional standard HTML div props

```tsx
const AlertDialogFooter = ({
  className,
  ...props
}: React.HTMLAttributes<HTMLDivElement>) => (
  <div
    className={cn(
      "flex flex-col-reverse sm:flex-row sm:justify-end sm:space-x-2",
      className
    )}
    {...props}
  />
)
```

### AlertDialogTitle

**Purpose**: The title of the alert dialog.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogTitle = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Title>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Title>
>(({ className, ...props }, ref) => (
  <AlertDialogPrimitive.Title
    ref={ref}
    className={cn("text-lg font-semibold", className)}
    {...props}
  />
))
```

### AlertDialogDescription

**Purpose**: The description text of the alert dialog that explains the action.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogDescription = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Description>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Description>
>(({ className, ...props }, ref) => (
  <AlertDialogPrimitive.Description
    ref={ref}
    className={cn("text-sm text-muted-foreground", className)}
    {...props}
  />
))
```

### AlertDialogAction

**Purpose**: The primary action button, typically to confirm the action.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogAction = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Action>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Action>
>(({ className, ...props }, ref) => (
  <AlertDialogPrimitive.Action
    ref={ref}
    className={cn(buttonVariants(), className)}
    {...props}
  />
))
```

### AlertDialogCancel

**Purpose**: The cancel button that dismisses the dialog.

**Props**:
- `className`: Custom CSS class
- Additional props passed through to the underlying component

```tsx
const AlertDialogCancel = React.forwardRef<
  React.ElementRef<typeof AlertDialogPrimitive.Cancel>,
  React.ComponentPropsWithoutRef<typeof AlertDialogPrimitive.Cancel>
>(({ className, ...props }, ref) => (
  <AlertDialogPrimitive.Cancel
    ref={ref}
    className={cn(
      buttonVariants({ variant: "outline" }),
      "mt-2 sm:mt-0",
      className
    )}
    {...props}
  />
))
```

## Usage Example

```tsx
import {
  AlertDialog,
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogFooter,
  AlertDialogHeader,
  AlertDialogTitle,
  AlertDialogTrigger,
} from "@/components/ui/alert-dialog"

export function DeleteConfirmation() {
  return (
    <AlertDialog>
      <AlertDialogTrigger>Delete Project</AlertDialogTrigger>
      <AlertDialogContent>
        <AlertDialogHeader>
          <AlertDialogTitle>Are you absolutely sure?</AlertDialogTitle>
          <AlertDialogDescription>
            This action cannot be undone. This will permanently delete your
            project and remove all associated data from our servers.
          </AlertDialogDescription>
        </AlertDialogHeader>
        <AlertDialogFooter>
          <AlertDialogCancel>Cancel</AlertDialogCancel>
          <AlertDialogAction>Continue</AlertDialogAction>
        </AlertDialogFooter>
      </AlertDialogContent>
    </AlertDialog>
  )
}
```

This example shows how to use the AlertDialog component to create a confirmation dialog for a potentially destructive action like deleting a project.

## Accessibility Features

- Implements the WAI-ARIA Alert Dialog pattern
- Focus is trapped within the dialog when open
- Keyboard navigation support (Escape to close)
- Screen reader announcements for dialog content
- Clear visual distinction between primary and cancel actions