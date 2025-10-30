# Accordion Component Documentation

## Overview
This file defines a customized accordion component for the Testing application. It's built using Radix UI's accordion primitive and is enhanced with styling and animation. The accordion component provides collapsible sections that can expand and collapse, ideal for presenting information in a space-efficient manner.

## Dependencies
- React components from Radix UI
- Styling utility function from [utils.ts](../../lib/utils.md)
- Icon components from Lucide React

## Component Documentation

### Accordion
The root component of the accordion system that wraps all accordion items.

**Type**: Direct export of `AccordionPrimitive.Root`  
**Usage**: Container for accordion items

### AccordionItem
A single item within the accordion that can be expanded or collapsed.

**Props**:
- All props from `AccordionPrimitive.Item`
- `className`: Optional string for additional CSS classes

**Styling**:
- Default styling includes a bottom border
- Custom classes can be provided via the className prop

**Example Usage**:
```tsx
<AccordionItem className="custom-class">
  {/* Trigger and content components */}
</AccordionItem>
```

### AccordionTrigger
The clickable element that toggles the expansion state of an accordion item.

**Props**:
- All props from `AccordionPrimitive.Trigger`
- `className`: Optional string for additional CSS classes
- `children`: React nodes to be displayed in the trigger

**Styling**:
- Displays as a flex container with space-between alignment
- Includes a chevron icon that rotates 180° when the accordion is open
- Adds a hover underline effect
- Custom classes can be provided via the className prop

**Example Usage**:
```tsx
<AccordionTrigger className="custom-trigger">
  Section Title
</AccordionTrigger>
```

### AccordionContent
The content area that expands and collapses when the trigger is clicked.

**Props**:
- All props from `AccordionPrimitive.Content`
- `className`: Optional string for additional CSS classes
- `children`: React nodes to be displayed in the content area

**Styling**:
- Includes animations for smooth expanding and collapsing
- Content is wrapped in a div with padding
- Custom classes can be provided via the className prop

**Example Usage**:
```tsx
<AccordionContent className="custom-content">
  <p>This is the content that will be shown or hidden.</p>
</AccordionContent>
```

## Implementation Details

### Styling Approach
The component uses the `cn` utility function from [utils.ts](../../lib/utils.md) to merge default styles with custom classNames. This allows for consistent base styling while enabling customization where needed.

### Animation
The component uses CSS animations defined elsewhere in the project:
- `data-[state=closed]:animate-accordion-up`: Animation when closing the accordion
- `data-[state=open]:animate-accordion-down`: Animation when opening the accordion

### Accessibility
Built on Radix UI primitives, which provide robust accessibility features:
- Proper ARIA attributes
- Keyboard navigation support
- Focus management

## Complete Example

```tsx
<Accordion type="single" collapsible>
  <AccordionItem value="item-1">
    <AccordionTrigger>Section 1</AccordionTrigger>
    <AccordionContent>
      This is the content for section 1.
    </AccordionContent>
  </AccordionItem>
  <AccordionItem value="item-2">
    <AccordionTrigger>Section 2</AccordionTrigger>
    <AccordionContent>
      This is the content for section 2.
    </AccordionContent>
  </AccordionItem>
</Accordion>
```

This accordion component is designed to integrate seamlessly with other UI components in the project and maintains consistency with the overall design system.