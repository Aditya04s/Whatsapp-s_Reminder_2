# WhatsApp Booking System

## Overview

A WhatsApp-based booking automation system designed for small businesses (salons, gyms, tutors). The application features a conversion-focused landing page where business owners can sign up for a demo. When users submit the signup form, their information is stored, added to a Google Sheet for tracking, and they receive an automated WhatsApp confirmation message via Twilio.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React with TypeScript for type safety and developer experience
- Vite as the build tool and development server, chosen for fast hot module replacement and optimized production builds
- Wouter for lightweight client-side routing (minimal overhead compared to React Router)

**UI Component System**
- Shadcn/ui component library built on Radix UI primitives for accessible, unstyled components
- TailwindCSS for utility-first styling with custom design tokens
- Custom theme system using CSS variables for consistent colors, spacing, and typography
- Design follows modern SaaS aesthetics (Linear, Framer-inspired) with WhatsApp brand integration

**State Management**
- TanStack Query (React Query) for server state management, caching, and data fetching
- React Hook Form with Zod validation for form state and schema validation
- Local component state via React hooks for UI interactions

**Design System**
- Typography: Inter (primary) and Poppins (alternative) font families
- Color scheme: WhatsApp green (#25D366) as primary brand color with neutral grays
- Responsive breakpoints: Mobile-first approach with 768px tablet breakpoint
- Spacing system: Consistent Tailwind units (4, 6, 8, 12, 16, 20, 24)

### Backend Architecture

**Server Framework**
- Express.js for RESTful API endpoints
- TypeScript throughout for type consistency across full stack
- Custom middleware for request logging and JSON body parsing

**API Design**
- POST `/api/signup` - Creates new signup, sends WhatsApp confirmation (non-blocking)
- GET `/api/signups` - Retrieves all signups (admin functionality)
- PATCH `/api/signups/:id` - Updates lead status for a signup
- RESTful conventions with JSON request/response format

**Data Layer**
- PostgreSQL database using Drizzle ORM (actively used)
- Schema includes: id (serial), business name, owner name, WhatsApp number, business type, preferred demo time, lead status, timestamps
- Database schema pushed and ready for production use
- All CRUD operations use proper database transactions

### External Dependencies

**Admin Dashboard Features**
- View all signups in a table format
- Real-time status updates with dropdown selector
- Statistics cards showing total signups and breakdown by status
- Export to CSV functionality for external analysis
- Accessible at `/admin` route

**Twilio WhatsApp API**
- Twilio SDK for sending WhatsApp messages programmatically
- API key authentication (account SID, API key, API secret)
- Sends automated confirmation messages to users after signup
- **Configuration**: Set up via environment variables (TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN, TWILIO_PHONE_NUMBER)
- Falls back to mock mode if credentials not configured (logs messages to console instead of sending)

**Replit Infrastructure**
- Replit-specific Vite plugins for development banner and error overlay
- Connector system for secure credential management (Google, Twilio)
- Environment-based authentication using `REPL_IDENTITY` or `WEB_REPL_RENEWAL` tokens
- Custom error handling for missing connector credentials

**Development Tools**
- ESBuild for production server bundling
- TypeScript compiler for type checking
- PostCSS with Autoprefixer for CSS processing

### Authentication & Security

**Current Implementation**
- No user authentication system (public landing page and signup form)
- API endpoints are open (appropriate for lead generation use case)
- Replit Connectors handle secure storage of third-party API credentials
- Raw request body preservation for webhook verification (future use)

**Future Considerations**
- Admin authentication for viewing signups via `/api/signups`
- Rate limiting on signup endpoint to prevent spam
- CAPTCHA integration for form abuse prevention

### Deployment Architecture

**Build Process**
- Frontend: Vite builds React app to `dist/public`
- Backend: ESBuild bundles server code to `dist/index.js`
- Single Node.js process serves both static files and API

**Environment Modes**
- Development: Vite dev server with HMR, tsx for live server reload
- Production: Compiled static assets served by Express