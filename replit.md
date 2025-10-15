# West Coast South Office Display

## Overview

A professional office TV display system featuring live news, weather, and real-time information for West Coast South offices. The application is designed for non-interactive display on office TVs, showing BBC News top stories and local weather for Rugby, UK. Built as a static HTML page with vanilla JavaScript, Express backend for API endpoints, and West Coast South branding (teal blue and yellow color scheme).

## User Preferences

Preferred communication style: Simple, everyday language.
Display purpose: Non-interactive TV display for office environments.

## System Architecture

### Frontend Architecture

**Static HTML Page**
- **Vanilla JavaScript** for dynamic content loading and clock functionality
- **Embedded CSS** with custom styling matching West Coast South branding
- **No build process required** - static HTML file served directly
- **Fetch API** for retrieving news and weather data from backend endpoints
- **Non-interactive design** for TV displays (no hover effects, no clickable links)

**Styling**
- Custom CSS with West Coast South branding: Teal blue (#1B8C9B) primary and yellow (#FFD500) accent colors
- Dark theme with high contrast for TV viewing
- Responsive grid layout using CSS Grid

**Design System**
- 3-column responsive grid layout (9 news tiles on desktop, 2 on tablet, 1 on mobile)
- 16:9 aspect ratio for news cards with minimum height of 280px
- West Coast South logo displayed in header
- Live clock showing real-time and date
- Weather widget for Rugby, UK with 3-day forecast
- Custom color palette: Teal blue primary (#1B8C9B) and yellow accent (#FFD500)
- Typography: Inter/Roboto fonts with bold headlines for distance readability
- Card design: Full-bleed images (65% height) with gradient overlays for text readability

### Backend Architecture

**Server Framework**
- **Express.js** as the HTTP server
- **Node.js** runtime with ESM (ECMAScript Modules) support
- Custom middleware for request logging with response capture

**Data Flow**
- RSS feed parsing using **fast-xml-parser** to convert BBC's XML feed to JSON
- Data transformation layer that extracts and normalizes article information (title, description, image, category, etc.)
- Fetches top 9 articles from `http://feeds.bbci.co.uk/news/rss.xml`
- `/api/news` endpoint serves processed article data to the frontend
- Fetches weather data from BBC Weather RSS feed for Rugby, UK
- `/api/weather` endpoint parses 3-day forecast and current conditions

**State Management**
- In-memory storage implementation (MemStorage class) for user data
- Storage abstraction via IStorage interface for future database migration
- Auto-refresh mechanism: Client polls every 5 minutes for new content

### Data Models

**News Article Schema (Zod validation)**
```typescript
{
  title: string
  description: string  
  link: URL string
  pubDate: ISO date string
  category: optional string (extracted from title brackets)
  imageUrl: optional URL (from media:thumbnail or enclosure)
  guid: unique identifier
}
```

**User Schema (Drizzle ORM)**
- PostgreSQL-ready schema defined but currently using in-memory storage
- User authentication structure prepared for future implementation

### Development Tools & Quality

**Type Safety**
- Strict TypeScript configuration across client, server, and shared code
- Path aliases for clean imports: `@/` (client), `@shared/` (shared schemas)
- Shared Zod schemas between frontend and backend for contract validation

**Development Experience**
- Vite dev server with custom error overlay plugin
- Source map support for debugging
- Hot reload for both client and server code
- Custom logging system with timestamps and color-coded output

**Build & Deployment**
- Client: Vite builds optimized static assets to `dist/public`
- Server: esbuild bundles Node.js code with external packages
- Production mode serves static files from Express

## External Dependencies

### Third-Party Services
- **BBC RSS Feed API**: `http://feeds.bbci.co.uk/news/rss.xml` - Primary news data source with XML format
- **BBC Weather RSS Feed**: `https://weather-broker-cdn.api.bbci.co.uk/en/forecast/rss/3day/2639965` - Weather data for Rugby, UK with 3-day forecast

### Database (Configured but Not Active)
- **Neon Database** (@neondatabase/serverless) - Serverless PostgreSQL provider
- **Drizzle ORM** - Type-safe SQL query builder and migration tool
- Connection expects `DATABASE_URL` environment variable
- Schema defined in `shared/schema.ts` with migrations in `./migrations`

### UI Component Libraries
- **Radix UI** - Headless UI primitives (40+ components including Dialog, Dropdown, Toast, etc.)
- **shadcn/ui** - Pre-styled components built on Radix with Tailwind
- **Lucide React** - Icon library used throughout the interface
- **cmdk** - Command menu component
- **embla-carousel-react** - Carousel/slider functionality
- **vaul** - Drawer component library

### Utility Libraries
- **date-fns** - Date formatting and manipulation (displays "time ago" for articles)
- **class-variance-authority (CVA)** - Type-safe variant styling
- **clsx & tailwind-merge** - Conditional className utilities
- **nanoid** - Unique ID generation

### Form Management
- **React Hook Form** - Form state and validation
- **@hookform/resolvers** - Zod schema validation integration
- **Drizzle Zod** - Auto-generate Zod schemas from Drizzle tables

### Development Dependencies
- **@replit/vite-plugin-cartographer** - Replit-specific dev tooling
- **@replit/vite-plugin-dev-banner** - Development environment indicators
- **@replit/vite-plugin-runtime-error-modal** - Enhanced error reporting

### Session Management (Configured)
- **connect-pg-simple** - PostgreSQL session store for Express sessions (prepared for future auth implementation)