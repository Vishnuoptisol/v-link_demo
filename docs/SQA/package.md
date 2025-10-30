# package.json Documentation

## Overview

The `package.json` file is the configuration file for this Next.js project, defining the project's metadata, scripts, and dependencies. It establishes the project as a private Next.js application with various UI components and integrations, particularly focusing on a modern React application with Tailwind CSS styling and AI capabilities through Genkit.

## Package Configuration

### Metadata
- **Name**: `nextn`
- **Version**: `0.1.0`
- **Private**: `true` (This project is not intended to be published as a npm package)

### Scripts

| Script | Description |
|--------|-------------|
| `dev` | Starts the Next.js development server with Turbopack on port 9002 |
| `genkit:dev` | Runs the Genkit AI development script using tsx |
| `genkit:watch` | Runs the Genkit AI development script in watch mode |
| `build` | Creates a production build of the Next.js application |
| `start` | Starts the production server for the built Next.js application |
| `lint` | Runs ESLint to check code quality |
| `typecheck` | Runs TypeScript type checking without emitting files |

## Dependencies

### Core Framework
- **next**: `15.3.3` - The Next.js framework used for server-side rendering and routing
- **react**: `^18.3.1` - The React library for building user interfaces
- **react-dom**: `^18.3.1` - React's DOM rendering functionality

### AI Integration
- **genkit**: `^1.14.1` - AI toolkit integration
- **@genkit-ai/googleai**: `^1.14.1` - Google AI integration for Genkit
- **@genkit-ai/next**: `^1.14.1` - Next.js specific Genkit integration

### UI Components
The project uses [Radix UI](https://www.radix-ui.com/), a collection of accessible, unstyled UI components:
- **@radix-ui/react-accordion**: `^1.2.3` - For collapsible accordion components
- **@radix-ui/react-alert-dialog**: `^1.1.6` - For important alert dialogs
- **@radix-ui/react-avatar**: `^1.1.3` - For user avatars
- **@radix-ui/react-checkbox**: `^1.1.4` - For checkbox inputs
- **@radix-ui/react-collapsible**: `^1.1.11` - For collapsible sections
- **@radix-ui/react-dialog**: `^1.1.6` - For dialog windows
- **@radix-ui/react-dropdown-menu**: `^2.1.6` - For dropdown menus
- **@radix-ui/react-label**: `^2.1.2` - For form labels
- **@radix-ui/react-menubar**: `^1.1.6` - For menu bars
- **@radix-ui/react-popover**: `^1.1.6` - For popover components
- **@radix-ui/react-progress**: `^1.1.2` - For progress indicators
- **@radix-ui/react-radio-group**: `^1.2.3` - For radio button groups
- **@radix-ui/react-scroll-area**: `^1.2.3` - For custom scrollable areas
- **@radix-ui/react-select**: `^2.1.6` - For select dropdown components
- **@radix-ui/react-separator**: `^1.1.2` - For visual separators
- **@radix-ui/react-slider**: `^1.2.3` - For slider inputs
- **@radix-ui/react-slot**: `^1.2.3` - For component composition
- **@radix-ui/react-switch**: `^1.1.3` - For toggle switches
- **@radix-ui/react-tabs**: `^1.1.3` - For tabbed interfaces
- **@radix-ui/react-toast**: `^1.2.6` - For toast notifications
- **@radix-ui/react-tooltip**: `^1.1.8` - For tooltips

### Styling and UI Utilities
- **tailwindcss**: `^3.4.1` (dev dependency) - Utility-first CSS framework
- **tailwind-merge**: `^3.0.1` - For merging Tailwind CSS classes
- **tailwindcss-animate**: `^1.0.7` - Animation utilities for Tailwind
- **class-variance-authority**: `^0.7.1` - For creating variant-based components
- **clsx**: `^2.1.1` - For conditional className joining
- **lucide-react**: `^0.475.0` - Icon library for React
- **embla-carousel-react**: `^8.6.0` - Carousel/slider component

### Form and Validation
- **react-hook-form**: `^7.54.2` - Form state management for React
- **@hookform/resolvers**: `^4.1.3` - Form validation resolvers
- **zod**: `^3.24.2` - TypeScript-first schema validation

### Date Handling
- **date-fns**: `^3.6.0` - Date utility library
- **react-day-picker**: `^8.10.1` - Flexible date picker component

### Data Visualization
- **recharts**: `^2.15.1` - Charting library for React applications

### Backend and Services
- **firebase**: `^11.9.1` - Firebase SDK for authentication and database services, used in [firebase.ts](../src/lib/firebase.md)
- **dotenv**: `^16.5.0` - For loading environment variables

### Developer Tools
- **typescript**: `^5` - TypeScript language
- **@types/node**: `^20` - TypeScript definitions for Node.js
- **@types/react**: `^18` - TypeScript definitions for React
- **@types/react-dom**: `^18` - TypeScript definitions for React DOM
- **postcss**: `^8` - Tool for transforming CSS with JavaScript
- **patch-package**: `^8.0.0` - For patching node modules
- **genkit-cli**: `^1.14.1` - Command line interface for Genkit

## Project Structure Dependencies

This configuration supports the project's component structure:

- **Dashboard Components**: Files like [Header.tsx](../src/components/dashboard/Header.md), [Overview.tsx](../src/components/dashboard/Overview.md), and [ProjectChart.tsx](../src/components/dashboard/ProjectChart.md) likely use Radix UI components and Recharts for data visualization
  
- **Projects Components**: The project management interfaces in [ProjectsTable.tsx](../src/components/projects/ProjectsTable.md) and various drawer components leverage UI components and forms

- **Tasks Components**: Task management components such as [TaskForm.tsx](../src/components/tasks/TaskForm.md) and [TaskList.tsx](../src/components/tasks/TaskList.md) rely on form handling and UI components

- **UI Component Library**: The extensive collection of UI components in the `src/components/ui` directory are built using the Radix UI primitives, Tailwind CSS, and other styling utilities

- **Firebase Integration**: The application uses Firebase for backend services as defined in [firebase.ts](../src/lib/firebase.md)

- **Utilities**: Helper functions in [utils.ts](../src/lib/utils.md) and TypeScript type definitions in [index.ts](../src/types/index.md)

## Configuration Files

The project includes several configuration files that work together with package.json:

- [next.config.ts](../next.config.md) - Next.js configuration
- [tailwind.config.ts](../tailwind.config.md) - Tailwind CSS configuration
- [postcss.config.mjs](../postcss.config.md) - PostCSS configuration
- [tsconfig.json](../tsconfig.json.md) - TypeScript configuration
- [components.json](../components.json.md) - Component configuration