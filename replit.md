# PacePal - Personal Habit & Routine Builder

## Overview

PacePal is a modern habit tracking and routine building application built with a fullstack TypeScript architecture. The application allows users to create, track, and maintain daily habits with smart reminders, progress analytics, and personalized routines. It features a responsive design that works seamlessly across desktop and mobile devices.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **UI Framework**: Radix UI components with Tailwind CSS for styling
- **State Management**: TanStack Query (React Query) for server state management
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **API Pattern**: RESTful API design
- **Development**: TSX for TypeScript execution in development

### Data Layer
- **ORM**: Drizzle ORM for type-safe database operations
- **Database**: PostgreSQL (configured for Neon Database)
- **Schema**: Centralized schema definition in `shared/schema.ts`
- **Migrations**: Drizzle Kit for database migrations

## Key Components

### Database Schema
The application uses four main tables:
- **users**: User authentication and profile information
- **habits**: Individual habit definitions with categories, targets, and settings
- **habitCompletions**: Daily completion tracking with timestamps
- **routines**: Grouped habits for morning, evening, or custom routines

### API Structure
RESTful endpoints following standard conventions:
- `GET /api/habits` - Fetch user habits
- `POST /api/habits` - Create new habit
- `PATCH /api/habits/:id` - Update habit
- `POST /api/habits/:id/toggle` - Toggle habit completion

### UI Components
- **Layout**: Responsive sidebar navigation with mobile-first design
- **Forms**: Reusable form components with validation
- **Cards**: Habit cards with completion tracking and streak display
- **Modals**: Add/edit habit modals with comprehensive form fields

## Data Flow

1. **Client Requests**: React components use TanStack Query hooks for data fetching
2. **API Layer**: Express routes handle HTTP requests and validate input with Zod
3. **Storage Layer**: Currently implements in-memory storage with interface for database integration
4. **Response**: Type-safe responses using shared TypeScript types

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Neon Database PostgreSQL driver
- **drizzle-orm**: Type-safe SQL query builder
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Accessible UI component primitives
- **tailwindcss**: Utility-first CSS framework
- **react-hook-form**: Performant form library
- **zod**: TypeScript schema validation

### Development Tools
- **tsx**: TypeScript execution for development
- **esbuild**: Fast JavaScript bundler for production
- **drizzle-kit**: Database migration tool
- **vite**: Frontend build tool with HMR

## Deployment Strategy

### Development
- **Command**: `npm run dev` starts both frontend and backend in development mode
- **Hot Reload**: Vite provides instant frontend updates
- **Database**: Uses environment variable `DATABASE_URL` for PostgreSQL connection

### Production Build
- **Frontend**: Vite builds optimized static assets to `dist/public`
- **Backend**: esbuild bundles server code to `dist/index.js`
- **Deployment**: Configured for Replit autoscale deployment

### Environment Configuration
- **Port**: Server runs on port 5000 (configurable via environment)
- **Database**: PostgreSQL connection via `DATABASE_URL` environment variable
- **Static Assets**: Express serves built frontend from `dist/public`

### Key Architectural Decisions

1. **Monorepo Structure**: Frontend, backend, and shared code in single repository for easier development and type sharing
2. **Type Safety**: End-to-end TypeScript with shared types between client and server
3. **Component System**: Radix UI + Tailwind for accessible, customizable components
4. **Database Strategy**: Drizzle ORM chosen for type safety and PostgreSQL compatibility
5. **State Management**: TanStack Query for server state, avoiding complex client state management
6. **Mobile-First**: Responsive design with dedicated mobile navigation components