# Calendar Component Documentation

## Overview
The Calendar component is a customizable date picker UI element implemented using the react-day-picker library. It provides a visually appealing and functional calendar interface with support for date selection, range selection, and custom styling. The component is part of the UI component library in the Testing application.

## Class Documentation

### Calendar Component
A function component that wraps and extends the DayPicker component from the react-day-picker library.

**Props**:
- `className`: `string` (optional) - Additional CSS classes to apply to the calendar component
- `classNames`: `object` (optional) - Custom class names for various parts of the calendar
- `showOutsideDays`: `boolean` (optional, default: true) - Whether to show days from previous/next months
- `...props`: Additional props passed through to the DayPicker component

## Component Structure

The Calendar component is a client-side component (indicated by "use client" directive) that renders a DayPicker with predefined styling and behavior. The component utilizes:

- [utils.ts](../../lib/utils.md) for the `cn` utility function to compose class names
- [button.tsx](./button.md) for the `buttonVariants` styling function to maintain consistent button styling

## Implementation Details

The Calendar component is implemented as a function that:

1. Takes in props including className, classNames, and showOutsideDays
2. Returns a DayPicker component with:
   - Custom styling via Tailwind CSS classes
   - Custom navigation icons using Lucide React icons (ChevronLeft and ChevronRight)
   - Styling for different states like selected days, today, disabled days, etc.

The component is highly customizable through the `classNames` prop, which allows overriding any of the default styles. It maintains consistent styling with the rest of the UI by leveraging the `buttonVariants` function from the button component.

### Navigation Icons
The component provides custom navigation icons using:
- `ChevronLeft` for previous month navigation
- `ChevronRight` for next month navigation

### Style Customization
The calendar has detailed styling for different states:
- Day selection states (selected, range, today, outside days)
- Layout structuring for responsive design (mobile and desktop)
- Accessibility considerations with proper aria attributes

## Usage Example

```tsx
import { Calendar } from "@/components/ui/calendar";
import { useState } from "react";

export function DatePickerDemo() {
  const [date, setDate] = useState<Date | undefined>(new Date());
  
  return (
    <Calendar
      mode="single"
      selected={date}
      onSelect={setDate}
      className="rounded-md border"
    />
  );
}
```

## Export Information

The component exports:
- The `Calendar` component as a named export
- The `CalendarProps` type which extends React.ComponentProps<typeof DayPicker>

The component also has a displayName of "Calendar" set for better debugging experience.

## Related Components

The Calendar component integrates with:
- [button.tsx](./button.md) - Uses button styling for consistent appearance
- Utility functions from [utils.ts](../../lib/utils.md) for className management

This component would typically be used in date selection interfaces, forms requiring date input, or any feature requiring date picking functionality.