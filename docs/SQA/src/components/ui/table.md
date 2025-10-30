# Table Component Documentation

## Overview

The `table.tsx` file provides a comprehensive set of React components for creating accessible, styled tables in the application. These components are built using React's forwardRef pattern to allow passing refs to the underlying HTML elements, making them highly composable and ensuring proper accessibility. The table components use utility classes from [utils.ts](../../lib/utils.md) for consistent styling while allowing customization through class name props.

## Component Documentation

### Table

A container component that wraps an HTML `<table>` element with responsive styling.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the table
- All other standard HTML table attributes are supported via `...props`

#### Example Usage
```tsx
<Table className="my-custom-class">
  {/* Table content goes here */}
</Table>
```

### TableHeader

A styled wrapper for the HTML `<thead>` element that contains header rows.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the header
- All other standard HTML thead attributes are supported via `...props`

#### Example Usage
```tsx
<TableHeader>
  <TableRow>
    <TableHead>Name</TableHead>
    <TableHead>Status</TableHead>
  </TableRow>
</TableHeader>
```

### TableBody

A wrapper component for the HTML `<tbody>` element that contains the main content rows.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the body
- All other standard HTML tbody attributes are supported via `...props`

#### Example Usage
```tsx
<TableBody>
  <TableRow>
    <TableCell>Project Alpha</TableCell>
    <TableCell>Active</TableCell>
  </TableRow>
</TableBody>
```

### TableFooter

A styled wrapper for the HTML `<tfoot>` element with distinctive background styling.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the footer
- All other standard HTML tfoot attributes are supported via `...props`

#### Example Usage
```tsx
<TableFooter>
  <TableRow>
    <TableCell colSpan={2}>Total Projects: 10</TableCell>
  </TableRow>
</TableFooter>
```

### TableRow

A component representing a table row (`<tr>`), styled with hover effects and selection states.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the row
- All other standard HTML tr attributes are supported via `...props`

#### Example Usage
```tsx
<TableRow data-state="selected">
  <TableCell>Content</TableCell>
</TableRow>
```

### TableHead

A component for table header cells (`<th>`), styled for headers with consistent padding and text alignment.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the header cell
- All other standard HTML th attributes are supported via `...props`

#### Example Usage
```tsx
<TableHead className="w-[100px]">Column Title</TableHead>
```

### TableCell

A component for standard table cells (`<td>`), with consistent padding and alignment.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the cell
- All other standard HTML td attributes are supported via `...props`

#### Example Usage
```tsx
<TableCell>Cell content goes here</TableCell>
```

### TableCaption

A component for table captions (`<caption>`), styled with muted text and proper spacing.

#### Props
- **className**: `string` (optional) - Additional CSS classes to apply to the caption
- All other standard HTML caption attributes are supported via `...props`

#### Example Usage
```tsx
<TableCaption>Table 1: Project Overview</TableCaption>
```

## Dependencies

- This component uses the `cn` utility function from [utils.ts](../../lib/utils.md) for class name composition.
- The table components are used in [ProjectsTable.tsx](../../components/projects/ProjectsTable.md) for displaying project data.

## Implementation Notes

- All components utilize React's `forwardRef` to properly pass refs to the underlying HTML elements.
- Each component has a proper `displayName` set for better debugging in React DevTools.
- The styling uses Tailwind CSS classes for responsive design and consistent appearance.
- The table components support hover states, selection states, and special styling for rows containing checkboxes.
- The table is wrapped in a container with `overflow-auto` to handle horizontal scrolling on small screens.