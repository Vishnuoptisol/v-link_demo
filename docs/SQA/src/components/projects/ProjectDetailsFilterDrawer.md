# ProjectDetailsFilterDrawer Documentation

## Overview
The `ProjectDetailsFilterDrawer` component is a specialized filter interface for project details in the Testing application. It provides a comprehensive set of filtering options including compliant percentage ranges, project manager selection, team size filtering, and date selection capabilities. The component is designed as a card-based sidebar drawer that can be opened and closed, with options to apply or cancel filter selections.

## Component Documentation

### `ProjectDetailsFilterDrawer`

#### Purpose
Renders a filter drawer interface specifically for filtering project details with various criteria.

#### Props
- `onClose`: Function - Callback function triggered when the drawer is closed or cancel is clicked
- `onApply`: Function - Callback function triggered when filter criteria are applied

#### Dependencies
- UI Components:
  - [`Button`](../ui/button.md) from `@/components/ui/button`
  - [`Select`, `SelectContent`, `SelectItem`, `SelectTrigger`, `SelectValue`](../ui/select.md) from `@/components/ui/select`
  - [`Input`](../ui/input.md) from `@/components/ui/input`
  - [`Label`](../ui/label.md) from `@/components/ui/label`
  - [`RadioGroup`, `RadioGroupItem`](../ui/radio-group.md) from `@/components/ui/radio-group`
  - [`Separator`](../ui/separator.md) from `@/components/ui/separator`
  - [`Card`](../ui/card.md) from `@/components/ui/card`
  - [`Popover`, `PopoverContent`, `PopoverTrigger`](../ui/popover.md) from `@/components/ui/popover`
  - [`Calendar`](../ui/calendar.md) from `@/components/ui/calendar`
- Utilities:
  - `cn` utility function from [`@/lib/utils`](../../lib/utils.md) for conditional class name composition
- Icons:
  - `CalendarIcon` and `X` from the Lucide React library

#### Constants
- `compliantPercentageOptions`: Array of objects defining compliant percentage filter options:
  - `value`: String identifier for the option
  - `label`: Display text for the option
  - `color`: CSS background color class (optional, for visual indication)

#### Component Structure
The component is structured as a card with:
1. A header section with a title and close button
2. A scrollable content section containing filter options
3. A footer section with Cancel and Apply buttons

#### Example Usage
```tsx
<ProjectDetailsFilterDrawer 
  onClose={() => console.log('Filter drawer closed')} 
  onApply={() => console.log('Filters applied')}
/>
```

### Filter Sections

#### Compliant Percentage Filter
- Radio button group with predefined ranges (All, 0%-50%, 50%-80%, 80%-100%)
- Color-coded indicators (red, yellow, green) for visual differentiation
- Alternative custom range input option with "From" and "To" numeric fields

#### PM Name Filter
- Dropdown selection for project manager names
- Predefined options: "Kailash Seervi", "Lara Chen", "Odin Greer"

#### Team Size Filter
- Dropdown selection for team size
- Predefined options: 11, 12, 13

#### Date Filter
- Calendar popup interface for selecting a specific date
- Uses the Calendar component with single selection mode

### Implementation Details

The component uses a responsive layout with:
- Flex container for the main card structure
- Grid layouts for certain filter option groups
- Responsive spacing and padding
- Overflow handling for the content area

The filter options are visually separated and labeled clearly, with appropriate input components for different types of data filtering. The component handles both pre-defined options (through radio buttons and select dropdowns) and custom input ranges.

## Related Components
- This component is similar to [`FilterDrawer`](FilterDrawer.md) but is specifically tailored for project details
- Likely used in conjunction with [`ProjectsTable`](ProjectsTable.md) for filtering project data
- May share functionality with [`ComplianceMetricsDrawer`](ComplianceMetricsDrawer.md) for compliance-related filtering

## Technical Considerations
- The component is client-side rendered as indicated by the 'use client' directive
- Uses conditional class name application through the `cn` utility function
- Implements a responsive design pattern with appropriate spacing and layouts
- Uses controlled form elements that would typically be connected to state handlers (not shown in this snippet)