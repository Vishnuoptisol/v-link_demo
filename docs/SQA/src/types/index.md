# `index.ts` Type Definitions Documentation

## Overview

This file defines the core TypeScript interfaces used throughout the application. It contains the type definitions for tasks, projects, and compliance metrics that are essential for type safety across components that deal with tasks, project management, and compliance tracking.

## Interface Documentation

### Task

Defines the structure for task items used in the task management features of the application.

**Properties:**
- `id`: `string` - Unique identifier for the task
- `text`: `string` - Description or content of the task
- `completed`: `boolean` - Flag indicating whether the task has been completed

**Used by:** 
- [TaskItem.tsx](../components/tasks/TaskItem.md)
- [TaskList.tsx](../components/tasks/TaskList.md)
- [TaskForm.tsx](../components/tasks/TaskForm.md)
- [SuggestedTasks.tsx](../components/tasks/SuggestedTasks.md)

### Project

Defines the structure for project data displayed in project listings and tables.

**Properties:**
- `id`: `number` - Unique identifier for the project
- `projectName`: `string` - Name of the project
- `client`: `string` - Client name associated with the project
- `pm`: `string` - Project manager's name
- `techLead`: `string` - Technical lead's name
- `teamSize`: `number` - Number of team members on the project
- `started`: `string` - Project start date
- `compliance`: `number` - Compliance score as a percentage
- `issues?`: `number` - Optional count of issues associated with the project

**Used by:**
- [ProjectsTable.tsx](../components/projects/ProjectsTable.md)
- [Overview.tsx](../components/dashboard/Overview.md)
- [ProjectChart.tsx](../components/dashboard/ProjectChart.md)

### ComplianceMetric

Represents an individual compliance metric with its name and value.

**Properties:**
- `name`: `string` - Name of the compliance metric
- `value`: `number` - Score or value of the metric

**Used by:**
- [ComplianceMetricsDrawer.tsx](../components/projects/ComplianceMetricsDrawer.md)

### ComplianceMetricDetail

Groups related compliance metrics by category for detailed reporting.

**Properties:**
- `compliance`: `number` - Overall compliance score
- `development`: `ComplianceMetric[]` - Array of development-related compliance metrics
- `devops`: `ComplianceMetric[]` - Array of DevOps-related compliance metrics
- `qualityMetrics`: `ComplianceMetric[]` - Array of quality-related compliance metrics

**Used by:**
- [ComplianceMetricsDrawer.tsx](../components/projects/ComplianceMetricsDrawer.md)

### ComplianceDetail

Provides comprehensive compliance information for a project, including categorical breakdowns.

**Properties:**
- `id`: `number` - Unique identifier matching the project id
- `projectName`: `string` - Name of the project
- `categoryScore`: `number` - Overall category score
- `development`: `number` - Development compliance score
- `devops`: `number` - DevOps compliance score
- `qualityMetrics`: `number` - Quality metrics compliance score
- `compliancePercentage`: `number` - Overall compliance as a percentage
- `status`: `string` - Current compliance status (e.g., "Compliant", "At Risk")
- `metricDetails`: `ComplianceMetricDetail` - Detailed breakdown of all compliance metrics

**Used by:**
- [ComplianceMetricsDrawer.tsx](../components/projects/ComplianceMetricsDrawer.md)
- [ProjectDetailsFilterDrawer.tsx](../components/projects/ProjectDetailsFilterDrawer.md)

## Usage Examples

### Task Interface Example

```typescript
// Example of creating a new task
const newTask: Task = {
  id: "task-1",
  text: "Complete documentation for index.ts",
  completed: false
};
```

### Project Interface Example

```typescript
// Example of a project object
const project: Project = {
  id: 1,
  projectName: "Website Redesign",
  client: "Acme Corp",
  pm: "Jane Doe",
  techLead: "John Smith",
  teamSize: 5,
  started: "2023-01-15",
  compliance: 87,
  issues: 3
};
```

### ComplianceDetail Example

```typescript
// Example of detailed compliance information for a project
const complianceDetail: ComplianceDetail = {
  id: 1,
  projectName: "Website Redesign",
  categoryScore: 85,
  development: 90,
  devops: 80,
  qualityMetrics: 85,
  compliancePercentage: 87,
  status: "Compliant",
  metricDetails: {
    compliance: 87,
    development: [
      { name: "Code Coverage", value: 92 },
      { name: "Documentation", value: 88 }
    ],
    devops: [
      { name: "CI/CD Pipeline", value: 85 },
      { name: "Automated Testing", value: 75 }
    ],
    qualityMetrics: [
      { name: "Bug Rate", value: 82 },
      { name: "Code Quality", value: 88 }
    ]
  }
};
```

These type definitions provide structure and type safety throughout the application, ensuring consistent data handling across components.