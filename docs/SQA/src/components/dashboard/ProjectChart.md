# ProjectChart.tsx Documentation

## Overview

`ProjectChart.tsx` is a React component that renders interactive area charts for displaying different types of project metrics over time. It allows users to toggle between three different metrics (Project Count, Resource Utilization, and Average Compliance) and select different time ranges (Yearly, Monthly, Weekly). The component utilizes Recharts for visualization and various UI components for the user interface.

## Class Documentation

### ProjectChart Component

**Type**: React Functional Component  
**Exports**: Named export `ProjectChart`  
**Purpose**: Renders an interactive chart dashboard for displaying project-related metrics over time.

## State Management

The component uses React's `useState` hook to track:

- `activeChart`: Determines which metric is currently displayed (project_count, resource_utilization, or avg_compliance)

## Data Structures

The component uses several data structures:

1. **Data Arrays**: Three separate arrays for different metrics:
   - `projectCountData`: Monthly project count data
   - `resourceUtilizationData`: Monthly resource utilization data
   - `avgComplianceData`: Monthly average compliance data

2. **Chart Configuration Object**: `chartConfigs` maps each chart type to its specific configuration:
   ```typescript
   type ChartType = keyof typeof chartConfigs;
   ```

## Method Documentation

### ProjectChart Function

**Access Modifier**: Public  
**Parameters**: None  
**Return Type**: JSX.Element  

**Step-by-step Explanation**:
1. Initializes state with the default chart type of 'project_count'
2. Gets the configuration for the current active chart
3. Renders a card with:
   - A header containing tabs to switch between chart types and a time range selector
   - A chart container with an area chart displaying the selected metric

**Example Usage**:
```jsx
import { ProjectChart } from '@/components/dashboard/ProjectChart';

function Dashboard() {
  return (
    <div className="dashboard-container">
      <ProjectChart />
      {/* Other dashboard components */}
    </div>
  );
}
```

## Component Dependencies

The ProjectChart component depends on the following files:

- React components from [card.tsx](../ui/card.md) for the main container:
  - Card
  - CardContent
  - CardHeader
  - CardTitle

- Chart components from [chart.tsx](../ui/chart.md) for custom chart styling:
  - ChartContainer
  - ChartTooltipContent

- Form components from [select.tsx](../ui/select.md) for the time range selector:
  - Select
  - SelectContent
  - SelectItem
  - SelectTrigger
  - SelectValue

- Tab components from [tabs.tsx](../ui/tabs.md) for switching between metrics:
  - Tabs
  - TabsList
  - TabsTrigger

- Various components from the Recharts library:
  - Area
  - AreaChart
  - CartesianGrid
  - ResponsiveContainer
  - Tooltip
  - XAxis
  - YAxis

## Detailed Component Breakdown

### Visual Chart Configuration

The chart visualization is created using Recharts and includes:

1. **Area Chart**: Displays the data with a filled area below the line
2. **Gradient Fill**: Uses a linear gradient that fades from the chart's color to transparent
3. **Grid Lines**: Horizontal dashed lines for better readability
4. **Interactive Tooltip**: Shows the exact value when hovering over data points
5. **Responsive Container**: Ensures the chart adapts to the parent container's size

### User Interface Elements

1. **Tabs**: Allow switching between different metrics
   - Project Count
   - Resource Utilization
   - Average Compliance

2. **Time Range Selector**: Dropdown for selecting the data time range
   - Yearly (default)
   - Monthly
   - Weekly

### Style and Appearance

The component uses Tailwind CSS classes for styling and includes:
- Shadow effects (`shadow-lg`)
- Responsive sizing (`h-[300px] w-full`)
- Custom color schemes for each chart type
- Dynamic coloring based on the selected chart

## Notes

1. The time range selector functionality is currently UI-only; changing the selection doesn't filter the data.
2. The data is static and defined within the component rather than being fetched from an external source.
3. The component is designed to be part of a dashboard, likely working alongside [Overview.tsx](Overview.md) and [Header.tsx](Header.md) components.