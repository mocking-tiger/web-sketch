# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a React TypeScript project called "web-sketch" (퍼블리싱 연습장) - a publishing/frontend practice playground. It's a collection of interactive UI examples and animations demonstrating various frontend techniques.

## Development Commands

- `npm start` - Start development server
- `npm run build` - Build for production
- `npm test` - Run tests

## Tech Stack

- **React 18.3.1** with TypeScript
- **styled-components 6.1.14** - All styling is done using styled-components with keyframe animations
- **react-router-dom 7.1.3** - Client-side routing
- **Create React App** - Project is bootstrapped with CRA

## Project Structure

### Route Architecture

The app uses a simple numeric routing system:
- `/` - Home page with links to all examples
- `/1` through `/7` - Individual example pages (Ex1WeAre through Ex7DelayedSearch)

Routes are centrally defined in `src/App.tsx` using react-router-dom.

### Component Organization

- `src/Pages/` - All page components (Home.tsx and Ex*.tsx files)
- `src/Components/` - Reusable components (currently just DefaultPageComponent.tsx)
- `src/App.tsx` - Main routing configuration
- `src/index.tsx` - Entry point with GlobalStyle

### Styling Patterns

All components follow these styling conventions:

1. **styled-components with keyframes** - Animations are defined as keyframes at the top of each file
2. **Wrapper pattern** - Most pages extend a `Wrapper` component from `Home.tsx` for consistent centering
3. **Prop-based styling** - Use transient props (prefixed with `$`, e.g., `$isLast`, `$isLoaded`) to pass dynamic values to styled components
4. **GlobalStyle** - Defined in `index.tsx` with Pretendard-Regular font and CSS reset

Example structure from Ex1WeAre.tsx:
```typescript
const slideUp = keyframes`...`;
const Wrapper2 = styled(Wrapper)<{ $isLast: boolean }>`...`;
```

### Example Pages

Each example demonstrates a specific UI technique:
1. **Ex1WeAre** - Vertical infinite slider with text rotation
2. **Ex2Prologue** - Web novel-style text presentation
3. **Ex3LandingClip** - Landing page with video playback
4. **Ex4EmailAutoComplete** - Email input with autocomplete
5. **Ex5DynamicLoading** - Loading screen with progress indicator
6. **Ex6WarningSlider** - Horizontal infinite slider animation
7. **Ex7DelayedSearch** - Debounced search input

## Common Development Patterns

### Animation Implementation

Infinite sliders are implemented by:
- Duplicating content elements to create seamless loops
- Using CSS transforms (`translateX` or `translateY`) with percentages
- Keyframe animations with `linear infinite` timing
- State management to control animation reset/loop

### State Management

Components use React hooks:
- `useState` for component state (animation positions, loading states)
- `useEffect` for side effects (image loading, intervals)
- No global state management - each example is self-contained

### TypeScript Configuration

- Strict mode enabled
- Target: ES2016
- JSX: react-jsx (automatic runtime)
- Module: CommonJS

## Adding New Examples

When adding a new example:
1. Create `src/Pages/ExNName.tsx` following the existing pattern
2. Import and add route in `src/App.tsx`
3. Add navigation link in `src/Pages/Home.tsx`
4. Use the `Wrapper` component from Home.tsx as base styling
5. Define keyframes and styled components at the top of the file
