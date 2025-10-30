# TeamMembersDrawer.tsx Documentation

## Overview

`TeamMembersDrawer.tsx` is a React component that displays team members associated with a specific project in a card-based drawer layout. It provides a searchable table view of team members with their roles and names. The component is designed to be used as a slide-in drawer or panel in the project management application.

## Class Documentation

### TeamMembersDrawer

A functional React component that renders a card containing project team member information in a table format.

#### Props

| Name | Type | Description |
|------|------|-------------|
| project | Project | The project object containing details of the current project |
| onClose | () => void | Callback function to close the drawer |

## Constants

### teamMembers

An array of objects containing mock team member data with the following structure:

```typescript
{
  sNo: number;      // Serial number
  role: string;     // Role in the project
  empName: string;  // Employee name
}
```

This is a static array of 9 team members with predefined roles and names.

## Type Definitions

### TeamMembersDrawerProps

```typescript
type TeamMembersDrawerProps = {
  project: Project;   // Project object from the application types
  onClose: () => void; // Function to handle drawer close event
};
```

The `Project` type is imported from the project's type definitions in [`@/types`](../types/index.md).

## Component Structure

The component renders a card with the following structure:

1. Header section with:
   - Project name and "Team Members" title
   - Search input with a search icon
   - Close button with an X icon

2. Content section with:
   - A table displaying team members with columns for serial number, role, and employee name

## Method Documentation

### TeamMembersDrawer Function

**Access Modifier:** Public  
**Parameters:**
- `props: TeamMembersDrawerProps` - Object containing the project and onClose function
  
**Returns:** JSX.Element - The rendered component

**Implementation Details:**
1. Receives a project object and onClose callback as props
2. Renders a card containing a header with project name and controls
3. Displays a table of team members with their roles and names
4. Provides a search input (functionality not implemented in this version)
5. Includes a close button that calls the onClose callback when clicked

**Example Usage:**
```tsx
<TeamMembersDrawer 
  project={{ 
    id: "1", 
    projectName: "Website Redesign", 
    // ...other Project properties 
  }} 
  onClose={() => setDrawerOpen(false)} 
/>
```

## Dependencies

The component depends on the following internal components:

- [`Button`](../components/ui/button.md) - Used for the close button
- [`Card`](../components/ui/card.md) - Main container for the drawer
- [`Input`](../components/ui/input.md) - Search input field
- [`Table` components](../components/ui/table.md) - Used for displaying the team members list
- [`Project` type](../types/index.md) - Type definition for project objects

It also uses the following external dependencies:
- `lucide-react` - For the Search and X icons
- React's 'use client' directive - Indicates this is a client component in Next.js

## Styling

The component uses a combination of Tailwind CSS classes for styling:
- Flexbox layout for the overall structure and header alignment
- Border styling for section separation
- Spacing utilities for padding and gaps
- Overflow handling for scrollable content
- Typography styling for the header text

## Notes

1. The search functionality is currently only visually implemented - no actual filtering logic is present in this version.
2. Team members are hardcoded in the component rather than being passed as props or fetched from an API.