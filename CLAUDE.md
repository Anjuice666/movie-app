# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

tMovies is a React-based movie application that allows users to search and view trailers for movies and TV series. The app uses TMDB API for data and integrates Google Analytics and AdSense.

## Tech Stack

- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **Routing**: React Router v6
- **State Management**: Redux Toolkit RTK Query
- **Styling**: Tailwind CSS with custom configuration
- **UI Components**: Framer Motion for animations, Swiper for carousels
- **Icons**: React Icons
- **Performance**: React Lazy Load, Skeleton loading
- **Analytics**: Google Analytics 4
- **Ads**: Google AdSense

## Common Development Commands

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production (TypeScript + Vite)
npm run preview      # Preview production build

# Linting (configured via eslint-plugin-react-app)
npm run lint         # Lint code (run via vite-plugin-eslint)
```

## Environment Variables Required

Create a `.env` file in the root with:
```env
VITE_API_KEY=<your-tmdb-api-key>
VITE_TMDB_API_BASE_URL=https://api.themoviedb.org/3
VITE_GA_MEASUREMENT_ID=<your-google-analytics-id>
VITE_GOOGLE_AD_CLIENT=<your-ad-client-id>
VITE_GOOGLE_AD_SLOT=<your-ad-slot-id>
```

## Architecture Overview

### File Structure
- `src/pages/` - Main page components (Home, Catalog, Detail, NotFound)
- `src/common/` - Reusable UI components (Header, Footer, VideoModal, etc.)
- `src/context/` - React contexts (global state, theme)
- `src/services/` - API service layer (RTK Query setup)
- `src/utils/` - Utility functions and constants
- `src/hooks/` - Custom React hooks

### Key Patterns

1. **Lazy Loading**: All page components are lazy-loaded for performance
2. **RTK Query**: Used for all API calls with centralized caching
3. **Context API**: Global state for video modal, sidebar, and theme
4. **Responsive Design**: Tailwind with custom breakpoints (xs: 380px)
5. **Dark Mode**: Class-based dark mode support
6. **Throttling**: Search throttled at 150ms using lodash.throttle

### Component Organization

Common components in `src/common/` follow a pattern:
- Each component has its own directory with `index.tsx`
- Components are exported from `src/common/index.ts`
- Structured UI components (Header, Footer, SideBar)
- Media components (MovieCard, Poster, Image)
- Interactive components (VideoModal, Search, ThemeMenu)

### API Service Layer

The TMDB API service uses RTK Query with two main endpoints:
- `getShows`: For listing movies/series with search, pagination, and similar shows
- `getShow`: For detailed movie/series data with videos and credits

### Global State

- **Video Modal**: Controls YouTube video playback
- **Sidebar**: Mobile navigation state
- **Theme**: Dark/light mode switching

### Custom Hooks

- `useMotion`: Framer motion utilities
- `useOnClickOutside`: For closing modals/sidebars
- `useOnKeyPress`: Keyboard shortcuts

## Important Features

1. **Video Modal**: YouTube trailers integrated with backdrop
2. **Themed Icons**: Theme-aware icon components
3. **Responsive Navigation**: Header and sidebar for different screen sizes
4. **Infinite Scroll**: Catalog pages with lazy loading
5. **Search Functionality**: Debounced search with results display
6. **Skeleton Loading**: Loading states for better UX

## Build Configuration

- TypeScript paths: `@` resolves to `src/`
- ESLint: Extends react-app config
- PostCSS: Autoprefixer for Tailwind
- No test suite currently configured