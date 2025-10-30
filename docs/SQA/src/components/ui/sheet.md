# Sheet Component Documentation

## Overview

The `sheet.tsx` file implements a customizable sliding panel (or drawer) UI component that appears from any edge of the screen. This component is built upon Radix UI's Dialog primitives and provides a structured, accessible way to display secondary content without navigating away from the current view. The implementation includes animations for entry and exit, various positioning options (top, bottom, left, right), and standard UI elements like headers, footers, titles, and descriptions.

## Dependencies

- Uses [utils.ts](../../lib/utils.md) for className merging functionality
- Built on Radix UI's Dialog primitives
- Utilizes `class-variance-authority` for variant styling
- Uses Lucide React for icons

## Component Documentation

### Sheet Components

#### Sheet
```typescript
const Sheet = SheetPrimitive.Root
```
**Purpose**: The root component that wraps the entire Sheet functionality.

#### SheetTrigger
```typescript
const SheetTrigger = SheetPrimitive.Trigger
```
**Purpose**: The element that toggles the Sheet's open/closed state.

#### SheetClose
```typescript
const SheetClose = SheetPrimitive.Close
```
**Purpose**: A component that closes the Sheet when triggered.

#### SheetPortal
```typescript
const SheetPortal = SheetPrimitive.Portal
```
**Purpose**: Portals the Sheet content into a different part of the DOM hierarchy.

#### SheetOverlay
```typescript
const SheetOverlay = React.forwardRef<
  React.ElementRef<typeof SheetPrimitive.Overlay>,
  React.ComponentPropsWithoutRef<typeof SheetPrimitive.Overlay>
>(({ className, ...props }, ref) => (
  <SheetPrimitive.Overlay
    className={cn(
      "fixed inset-0 z-50 bg-black/80 data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=open]:fade-in-0",
      className
    )}
    {...props}
    ref={ref}
  />
))
```
**Purpose**: Provides a semi-transparent overlay behind the Sheet content.
**Props**:
- `className`: Additional CSS classes
- `ref`: Forwarded ref
- Other standard React props

#### SheetContent
```typescript
interface SheetContentProps
  extends React.ComponentPropsWithoutRef<typeof SheetPrimitive.Content>,
    VariantProps<typeof sheetVariants> {}

const SheetContent = React.forwardRef<
  React.ElementRef<typeof SheetPrimitive.Content>,
  SheetContentProps
>(({ side = "right", className, children, ...props }, ref) => (
  <SheetPortal>
    <SheetOverlay />
    <SheetPrimitive.Content
      ref={ref}
      className={cn(sheetVariants({ side }), className)}
      {...props}
    >
      {children}
      <SheetPrimitive.Close className="absolute right-4 top-4 rounded-sm opacity-70 ring-offset-background transition-opacity hover:opacity-100 focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 disabled:pointer-events-none data-[state=open]:bg-secondary">
        <X className="h-4 w-4" />
        <span className="sr-only">Close</span>
      </SheetPrimitive.Close>
    </SheetPrimitive.Content>
  </SheetPortal>
))
```
**Purpose**: The main content container for the Sheet.
**Props**:
- `side`: Position of the Sheet (`right` by default, can be `top`, `bottom`, `left`, `right`)
- `className`: Additional CSS classes
- `children`: React nodes to render within the Sheet
- `ref`: Forwarded ref
- Other standard React props

#### SheetHeader
```typescript
const SheetHeader = ({
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
**Purpose**: A container for the Sheet's header content with appropriate styling.
**Props**:
- `className`: Additional CSS classes
- Other standard HTMLDivElement props

#### SheetFooter
```typescript
const SheetFooter = ({
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
**Purpose**: A container for the Sheet's footer content with appropriate styling.
**Props**:
- `className`: Additional CSS classes
- Other standard HTMLDivElement props

#### SheetTitle
```typescript
const SheetTitle = React.forwardRef<
  React.ElementRef<typeof SheetPrimitive.Title>,
  React.ComponentPropsWithoutRef<typeof SheetPrimitive.Title>
>(({ className, ...props }, ref) => (
  <SheetPrimitive.Title
    ref={ref}
    className={cn("text-lg font-semibold text-foreground", className)}
    {...props}
  />
))
```
**Purpose**: Displays the title of the Sheet with appropriate styling.
**Props**:
- `className`: Additional CSS classes
- `ref`: Forwarded ref
- Other standard React props

#### SheetDescription
```typescript
const SheetDescription = React.forwardRef<
  React.ElementRef<typeof SheetPrimitive.Description>,
  React.ComponentPropsWithoutRef<typeof SheetPrimitive.Description>
>(({ className, ...props }, ref) => (
  <SheetPrimitive.Description
    ref={ref}
    className={cn("text-sm text-muted-foreground", className)}
    {...props}
  />
))
```
**Purpose**: Displays descriptive text within the Sheet with appropriate styling.
**Props**:
- `className`: Additional CSS classes
- `ref`: Forwarded ref
- Other standard React props

## Usage Examples

### Basic Sheet Example

```tsx
import { Button } from "@/components/ui/button";
import {
  Sheet,
  SheetContent,
  SheetDescription,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";

export function SheetDemo() {
  return (
    <Sheet>
      <SheetTrigger asChild>
        <Button variant="outline">Open Sheet</Button>
      </SheetTrigger>
      <SheetContent>
        <SheetHeader>
          <SheetTitle>Sheet Title</SheetTitle>
          <SheetDescription>
            This is a description of the sheet content.
          </SheetDescription>
        </SheetHeader>
        <div className="py-4">Sheet content goes here</div>
      </SheetContent>
    </Sheet>
  );
}
```

### Sheet with Custom Side Position

```tsx
import {
  Sheet,
  SheetContent,
  SheetTrigger,
} from "@/components/ui/sheet";
import { Button } from "@/components/ui/button";

export function BottomSheetDemo() {
  return (
    <Sheet>
      <SheetTrigger asChild>
        <Button>Open Bottom Sheet</Button>
      </SheetTrigger>
      <SheetContent side="bottom">
        <div className="p-4">This sheet slides up from the bottom</div>
      </SheetContent>
    </Sheet>
  );
}
```

### Sheet with Footer

```tsx
import {
  Sheet,
  SheetContent,
  SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";
import { Button } from "@/components/ui/button";

export function SheetWithFooterDemo() {
  return (
    <Sheet>
      <SheetTrigger asChild>
        <Button>Open Sheet</Button>
      </SheetTrigger>
      <SheetContent>
        <SheetHeader>
          <SheetTitle>Edit Profile</SheetTitle>
        </SheetHeader>
        <div className="py-4">Form fields would go here</div>
        <SheetFooter>
          <Button type="submit">Save changes</Button>
        </SheetFooter>
      </SheetContent>
    </Sheet>
  );
}
```

## Related Components

This component is often used in the following project components:
- [FilterDrawer.tsx](../../components/projects/FilterDrawer.md)
- [ProjectDetailsFilterDrawer.tsx](../../components/projects/ProjectDetailsFilterDrawer.md)
- [ComplianceMetricsDrawer.tsx](../../components/projects/ComplianceMetricsDrawer.md)
- [TeamMembersDrawer.tsx](../../components/projects/TeamMembersDrawer.md)