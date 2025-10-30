# ProjectsTable.tsx Documentation

## Overview

`ProjectsTable.tsx` is a React component that displays project and compliance information in tabular format with filtering and viewing capabilities. The component implements a tabbed interface that allows users to switch between "Project Details" and "Compliance Details" views. Each tab presents data in a sortable, filterable table with interactive elements for viewing additional information.

## Class Documentation

### ProjectsTable

This is a functional React component that displays project and compliance data in tabular format with filtering and navigation capabilities.

#### Props
- `isFilterOpen: boolean` - Indicates whether the filter panel is open
- `filtersApplied: boolean` - Indicates whether filters are currently applied to the data
- `onFilterToggle: () => void` - Handler function for toggling the filter panel
- `onViewTeam: (project: Project) => void` - Handler function for viewing team details
- `selectedProjectId?: number | null` - ID of the currently selected project (optional)
- `onViewCompliance: (complianceDetail: ComplianceDetail) => void` - Handler function for viewing compliance details
- `selectedComplianceId?: number | null` - ID of the currently selected compliance detail (optional)
- `onTabChange: (tab: string) => void` - Handler function for tab changes
- `activeTab: string` - The currently active tab
- `complianceRange?: string` - Range for compliance filtering (optional)

## Method Documentation

### ProjectsTable Component Function

**Access Modifier**: Export
**Parameters**: 
- Props object containing all properties listed above

**Return Type**: JSX.Element

**Step-by-step Explanation**:
1. Defines a handler function `handleFilterClick` that calls the passed `onFilterToggle` function
2. Uses `useMemo` to filter compliance details based on the selected compliance range
3. Renders a tabbed interface with two tabs: "Compliance Details" and "Project Details"
4. Provides a search input, filter button, and optional date selector
5. Renders tables with appropriate data for each tab
6. Implements pagination controls at the bottom of the component

**Example Usage**:
```tsx
<ProjectsTable
  isFilterOpen={false}
  filtersApplied={true}
  onFilterToggle={() => setIsFilterOpen(!isFilterOpen)}
  onViewTeam={(project) => handleViewTeam(project)}
  selectedProjectId={3}
  onViewCompliance={(complianceDetail) => handleViewCompliance(complianceDetail)}
  selectedComplianceId={null}
  onTabChange={(tab) => setActiveTab(tab)}
  activeTab="project_details"
  complianceRange="80-100"
/>
```

### getComplianceColor Function

**Access Modifier**: Private (within module)
**Parameters**:
- `compliance: number` - The compliance percentage value

**Return Type**: string (CSS class name)

**Step-by-step Explanation**:
1. Takes a compliance percentage value
2. Returns a CSS class based on the value:
   - 'text-green-600' if compliance is >= 90
   - 'text-yellow-600' if compliance is >= 80
   - 'text-red-600' otherwise

**Example Usage**:
```tsx
<span className={getComplianceColor(85)}>85%</span>
```

### getStatusBadgeVariant Function

**Access Modifier**: Private (within module)
**Parameters**:
- `status: string` - The status text

**Return Type**: string (badge variant name)

**Step-by-step Explanation**:
1. Takes a status string
2. Converts it to lowercase and matches it against known statuses
3. Returns the appropriate badge variant name:
   - 'success' for 'good' or 'excellent'
   - 'destructive' for 'critical'
   - 'default' for any other status

**Example Usage**:
```tsx
<Badge variant={getStatusBadgeVariant('Good')}>Good</Badge>
```

### getPercentageBadgeClass Function

**Access Modifier**: Private (within module)
**Parameters**:
- `percentage: number` - The percentage value

**Return Type**: string (CSS class name)

**Step-by-step Explanation**:
1. Takes a percentage value
2. Returns a CSS class based on the value:
   - 'bg-red-100 text-red-700' if percentage is < 40
   - 'bg-yellow-100 text-yellow-700' if percentage is < 80
   - 'bg-green-100 text-green-700' otherwise

**Example Usage**:
```tsx
<Badge className={getPercentageBadgeClass(75)}>75%</Badge>
```

## Dependencies

This component uses several UI components and utility functions from other project files:

- Table components from [`table.tsx`](../ui/table.md)
- Tabs components from [`tabs.tsx`](../ui/tabs.md)
- Input component from [`input.tsx`](../ui/input.md)
- Select components from [`select.tsx`](../ui/select.md)
- Button component from [`button.tsx`](../ui/button.md)
- Badge component from [`badge.tsx`](../ui/badge.md)
- The `cn` utility function from [`utils.ts`](../../lib/utils.md)
- Type definitions (`Project`, `ComplianceDetail`, `ComplianceMetricDetail`) from [`index.ts`](../../types/index.md)

It also imports React and Lucide icons including `Search`, `ChevronRight`, `ChevronLeft`, `ListFilter`, `X`, and `Eye`.

## Data Models

The component uses two main data models:

1. `Project` type (imported from `@/types`) with the following properties:
   - `id: number`
   - `projectName: string`
   - `client: string`
   - `pm: string` (Project Manager)
   - `techLead: string`
   - `teamSize: number`
   - `started: string`
   - `compliance: number`
   - `issues?: number` (optional)

2. `ComplianceDetail` type (imported from `@/types`) with the following properties:
   - `id: number`
   - `projectName: string`
   - `categoryScore: number`
   - `development: number`
   - `devops: number`
   - `qualityMetrics: number`
   - `compliancePercentage: number`
   - `status: string`
   - `metricDetails: ComplianceMetricDetail`

The component also contains mock data arrays for `projects` and `complianceDetails` for demonstration purposes.

## Key Features

1. **Tabbed Interface**: Toggles between "Compliance Details" and "Project Details" views
2. **Filtering**: Supports filtering projects by compliance range
3. **Search**: Provides a search input field (functionality not fully implemented in the code)
4. **Team View**: Allows viewing team details for a project
5. **Compliance View**: Provides detailed compliance metrics for projects
6. **Visual Status Indicators**: Uses color-coded badges to indicate status and compliance levels
7. **Pagination**: Displays pagination controls (functionality not fully implemented in the code)