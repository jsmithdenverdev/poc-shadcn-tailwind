# Agents Guide - poc-shadcn-tailwind

## Project Overview
This is a proof of concept exploring Shadcn/UI CDN and Tailwind CSS integration with Vite and React.

## Critical Rules

### Git Workflow
- **NEVER** commit to `main` branch - it's protected
- All work must be done on feature branches
- Create feature branches from `main` using: `git checkout -b feature/description`
- After user merges a feature branch, ask if they want cleanup: checkout main, pull latest, clean local branches, prune

### Technology Stack
- **Build Tool:** Vite
- **Framework:** React
- **UI Library:** Shadcn/UI (CDN)
- **Styling:** Tailwind CSS
- **Language:** TypeScript

## Build, Lint, Test Commands

```bash
# Install dependencies
npm install

# Development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Type checking
npm run typecheck

# Linting
npm run lint

# Lint with auto-fix
npm run lint:fix

# Run tests
npm run test

# Run single test (pattern match)
npm run test -- <test-file-pattern>

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage
```

## Code Style Guidelines

### Imports
- Group imports in this order:
  1. React and third-party libraries
  2. Internal components (atomic design hierarchy)
  3. Utilities and helpers
  4. Types and interfaces
- Use absolute imports from `@/` alias for internal modules
- Sort imports alphabetically within groups

### Component Structure (Atomic Design)
Organize components following atomic design pattern:
```
src/
  atoms/        # Basic building blocks (Button, Input, etc.)
  molecules/    # Combinations of atoms (SearchBar, FormField)
  organisms/    # Complex sections (Header, Sidebar)
  templates/    # Page layouts
  pages/        # Complete page implementations
  components/   # Shared components
  lib/          # Utilities and helpers
```

### Naming Conventions
- **Components:** PascalCase (`UserProfile.tsx`)
- **Files:** PascalCase for components, camelCase for utilities (`userUtils.ts`)
- **Variables/Functions:** camelCase (`handleClick`, `userName`)
- **Constants:** UPPER_SNAKE_CASE (`API_BASE_URL`)
- **Interfaces/Types:** PascalCase with `I` prefix only for interfaces (`IUserData`, `UserType`)

### Formatting
- Use Prettier for code formatting (configured in `.prettierrc`)
- Maximum line length: 100 characters
- Use single quotes for strings
- Trailing commas where allowed
- No semicolons (prettier-configured)

### TypeScript
- Strict TypeScript mode enabled
- Always use explicit return types for public functions
- Use interface for object shapes, type for unions/aliases
- Prefer `const assertions` for literal types
- Avoid `any` - use `unknown` with type guards instead

### React Best Practices
- Functional components with hooks only
- Use `useCallback` for event handlers passed to children
- Use `useMemo` for expensive computations
- Extract custom hooks for reusable logic
- Props interfaces defined before component
- Use prop types even with TypeScript for runtime validation if needed

### Error Handling
- Use Error Boundaries for component-level error catching
- Async functions should have try-catch blocks
- Provide user-friendly error messages, not stack traces
- Log errors with context (user action, component name, etc.)
- Use toast notifications for user-facing errors

### Styling (Tailwind + Shadcn/UI)
- Use Tailwind utility classes for styling
- Shadcn/UI components from CDN for base UI elements
- Custom styles in `globals.css` for global theme
- Avoid inline styles except for dynamic values
- Use Tailwind's `@apply` sparingly in component files

### Testing
- Component tests with Testing Library
- Integration tests for user flows
- Unit tests for pure functions
- Test files co-located: `Component.test.tsx`
- Follow AAA pattern: Arrange, Act, Assert
- Mock external dependencies (API calls, localStorage)

### Shadcn/UI CDN Usage
- Import components from CDN: `import { Button } from "shadcn-ui/cdn"`
- Configure theme in Tailwind config
- Customize components through className overrides
- Follow Shadcn/UI component API and prop conventions

### Additional Guidelines
- Keep components under 200 lines
- Extract complex logic to separate functions/hooks
- Write meaningful comments only for complex logic
- Use descriptive variable names, no abbreviations
- Prefer early returns over nested conditionals
- Use TypeScript's `readonly` for immutable data structures
