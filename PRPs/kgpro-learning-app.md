name: "KGPro Learning App - Embeddable React Lesson Player"
description: |
  Comprehensive PRP for building a lightweight, embeddable React lesson player for children's educational content. 
  Features theme configuration, progress tracking, and query-string based lesson loading.

## Purpose

Create a production-ready, embeddable React lesson player that can be integrated into any website. The app loads lessons via query parameters, supports dynamic theming, tracks progress locally, and provides a child-friendly interface for educational content.

## Core Principles

1. **Lightweight & Embeddable**: Optimized bundle size (~150kb) for iframe or component embedding
2. **Theme-Driven**: AI-friendly JSON theme configuration for visual customization
3. **Progress Persistence**: LocalStorage-based progress tracking without backend dependency
4. **Query-String Driven**: Automatic lesson loading via URL parameters
5. **Child-Friendly UX**: Accessible, engaging interface for young learners

---

## Goal

Build a standalone React application that serves as an embeddable lesson player for children's educational content. The app should dynamically load lessons from JSON files, support visual theming, track learning progress, and provide immediate feedback to young learners.

## Why

- **Scalable Content Delivery**: Enable easy embedding of educational content across multiple websites
- **Personalized Learning**: Track individual progress and adapt to learner needs
- **Brand Consistency**: Theme customization allows integration with any website's visual design
- **Offline Capability**: LocalStorage persistence works without internet connectivity
- **Development Efficiency**: Reusable component that reduces development time for educational sites

## What

### Core Features
- **Lesson Loading**: Automatic lesson fetching via `?lesson=lesson-id` query parameter
- **Question Rendering**: Support for multiple choice questions with images and text
- **Progress Tracking**: Session-based progress with persistent storage
- **Theme System**: JSON-configurable visual themes for colors, fonts, and styling
- **Feedback System**: Immediate visual feedback for correct/incorrect answers
- **Summary Screen**: End-of-lesson progress summary with retry options

### Technical Requirements
- **React 19** with TypeScript and strict type safety
- **Vite** build system for optimal bundle size
- **CSS Variables** for runtime theme switching
- **LocalStorage** for progress persistence
- **Query String** parsing for lesson identification
- **Responsive Design** for mobile and desktop
- **Accessibility** compliance (WCAG 2.1 AA)

### Success Criteria

- [ ] Lesson loads automatically from query parameter
- [ ] Progress persists across browser sessions
- [ ] Theme changes without component re-renders
- [ ] Bundle size under 150kb gzipped
- [ ] 80%+ test coverage with integration tests
- [ ] WCAG 2.1 AA accessibility compliance
- [ ] Cross-browser compatibility (Chrome, Firefox, Safari, Edge)

## All Needed Context

### Documentation & References

```yaml
# MUST READ - Include these in your context window
- url: https://react.dev/reference/react/useSyncExternalStore
  why: LocalStorage synchronization across tabs
  section: "Subscribing to an external store"
  critical: Prevents state desync in multi-tab scenarios

- url: https://vitejs.dev/guide/build.html#library-mode
  why: Building embeddable components with Vite
  section: "Library Mode"
  critical: UMD format for iframe embedding

- url: https://web.dev/articles/custom-properties-web-components
  why: CSS Variables for theme switching
  section: "Dynamic theming with CSS custom properties"
  critical: Runtime theme changes without re-renders

- url: https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams
  why: Query parameter parsing for lesson loading
  section: "URLSearchParams() constructor"
  critical: Robust URL parameter handling

- url: https://testing-library.com/docs/react-testing-library/intro
  why: Component testing patterns
  section: "Testing user interactions"
  critical: User behavior testing over implementation details

- url: https://web.dev/articles/storage-for-the-web
  why: LocalStorage best practices and quota management
  section: "Storage quota and eviction"
  critical: Handle storage failures gracefully

- file: /workspace/claude_md_files/CLAUDE-REACT.md
  why: React patterns and conventions from codebase
  critical: Follow established TypeScript and component patterns

- file: /workspace/PRPs/templates/prp_base.md
  why: PRP structure and validation loop patterns
  critical: Implement proper validation gates for quality assurance
```

### Current Codebase Structure

```bash
PRPs-agentic-eng/
├── .claude/
│   └── commands/           # 28+ Claude Code commands
├── PRPs/
│   ├── templates/          # PRP templates with validation
│   ├── scripts/           # PRP runner utilities
│   └── ai_docs/           # Curated documentation
├── claude_md_files/       # Framework-specific CLAUDE.md files
│   ├── CLAUDE-REACT.md    # React patterns and conventions
│   └── CLAUDE-NEXTJS-15.md # Next.js patterns
└── pyproject.toml         # Python package configuration
```

### Desired Application Structure

```bash
kgpro-learning-app/
├── public/
│   ├── lessons/           # JSON lesson files
│   │   ├── counting-1.json
│   │   └── abc-basics.json
│   └── images/            # Lesson images
├── src/
│   ├── components/        # React components
│   │   ├── LessonPlayer.tsx
│   │   ├── QuestionCard.tsx
│   │   ├── ProgressBar.tsx
│   │   └── SummaryScreen.tsx
│   ├── hooks/             # Custom React hooks
│   │   ├── useLocalStorage.ts
│   │   ├── useLesson.ts
│   │   └── useTheme.ts
│   ├── types/             # TypeScript types
│   │   ├── Lesson.ts
│   │   ├── Progress.ts
│   │   └── Theme.ts
│   ├── utils/             # Utility functions
│   │   ├── lessonLoader.ts
│   │   ├── progressTracker.ts
│   │   └── themeManager.ts
│   ├── styles/            # CSS and theme files
│   │   ├── global.css
│   │   ├── themes.css
│   │   └── variables.css
│   ├── App.tsx
│   └── main.tsx
├── __tests__/             # Test files
│   ├── components/
│   ├── hooks/
│   └── utils/
├── package.json
├── vite.config.ts
├── tsconfig.json
└── README.md
```

### Known Gotchas & Library Quirks

```typescript
// CRITICAL: React 19 with TypeScript strict mode
// - Use ReactElement instead of JSX.Element
// - All components must have explicit return types
// - No 'any' types - use 'unknown' instead

// CRITICAL: Vite library mode for embeddable builds
// - UMD format required for iframe embedding
// - External dependencies must be properly configured
// - CSS injection handled automatically

// CRITICAL: LocalStorage quota management
// - 5-10MB limit per domain
// - QuotaExceededError must be handled gracefully
// - Implement cleanup strategy for old data

// CRITICAL: CSS Variables for theming
// - Use data attributes for theme switching
// - Fallback values required for IE11 support
// - Animation-friendly for smooth transitions

// CRITICAL: Query parameter parsing
// - Handle malformed URLs gracefully
// - Validate lesson IDs before fetching
// - Implement fallback to default lesson

// CRITICAL: Educational app considerations
// - COPPA compliance for children under 13
// - Accessibility requirements for learning disabilities
// - Simple, clear UI with large touch targets
```

## Implementation Blueprint

### Data Models and Structure

Create type-safe data models for lesson content, progress tracking, and theme configuration.

```typescript
// Core lesson data structure
interface Lesson {
  id: string;
  title: string;
  description?: string;
  ageGroup: string;
  theme?: Partial<Theme>;
  questions: Question[];
}

interface Question {
  id: string;
  question: string;
  type: 'multiple-choice' | 'true-false';
  image?: string;
  choices: string[];
  correctAnswer: string;
  explanation?: string;
}

// Progress tracking models
interface LessonProgress {
  lessonId: string;
  currentQuestionIndex: number;
  correctAnswers: number;
  totalQuestions: number;
  completedAt?: string;
  timeSpent: number;
}

interface SessionProgress {
  sessionId: string;
  startedAt: string;
  answers: Answer[];
  currentQuestion: number;
}

// Theme configuration model
interface Theme {
  name: string;
  primaryColor: string;
  secondaryColor: string;
  textColor: string;
  backgroundColor: string;
  buttonColor: string;
  correctColor: string;
  incorrectColor: string;
  fontFamily: string;
  fontSize: 'small' | 'medium' | 'large';
  borderRadius: 'none' | 'small' | 'medium' | 'large';
}
```

### Task Implementation Order

```yaml
Task 1: Project Setup and Configuration
CREATE kgpro-learning-app/package.json:
  - CONFIGURE Vite with TypeScript and React 19
  - ADD dependencies: react, react-dom, typescript, vite
  - ADD dev dependencies: vitest, @testing-library/react, @types/react
  - CONFIGURE build scripts for library mode

CREATE kgpro-learning-app/vite.config.ts:
  - CONFIGURE library mode with UMD format
  - SET external dependencies (react, react-dom)
  - CONFIGURE CSS injection for embeddable build
  - ADD path aliases for clean imports

CREATE kgpro-learning-app/tsconfig.json:
  - ENABLE strict mode with React 19 settings
  - CONFIGURE path mapping for clean imports
  - SET target to ES2020 for modern browsers

Task 2: Core Type Definitions
CREATE src/types/Lesson.ts:
  - DEFINE Lesson interface with validation
  - DEFINE Question interface with multiple choice support
  - EXPORT type guards for runtime validation

CREATE src/types/Progress.ts:
  - DEFINE LessonProgress interface
  - DEFINE SessionProgress interface
  - DEFINE Answer interface for tracking responses

CREATE src/types/Theme.ts:
  - DEFINE Theme interface with all visual properties
  - DEFINE ThemeConfig type for partial overrides
  - EXPORT default theme configuration

Task 3: Utility Functions
CREATE src/utils/lessonLoader.ts:
  - IMPLEMENT getLessonIdFromUrl function
  - IMPLEMENT fetchLesson function with error handling
  - IMPLEMENT validateLessonData function
  - HANDLE malformed URLs and missing lessons

CREATE src/utils/progressTracker.ts:
  - IMPLEMENT saveProgress function with quota handling
  - IMPLEMENT loadProgress function with error recovery
  - IMPLEMENT clearOldProgress function for cleanup
  - HANDLE LocalStorage quota exceeded errors

CREATE src/utils/themeManager.ts:
  - IMPLEMENT applyTheme function with CSS variables
  - IMPLEMENT loadThemeFromLesson function
  - IMPLEMENT resetToDefaultTheme function
  - HANDLE theme validation and fallbacks

Task 4: Custom React Hooks
CREATE src/hooks/useLocalStorage.ts:
  - IMPLEMENT useLocalStorage hook with TypeScript generics
  - HANDLE storage quota exceeded errors
  - IMPLEMENT cross-tab synchronization
  - ADD debouncing for performance optimization

CREATE src/hooks/useLesson.ts:
  - IMPLEMENT lesson fetching with loading states
  - HANDLE lesson not found errors
  - IMPLEMENT lesson validation
  - CACHE lessons for performance

CREATE src/hooks/useTheme.ts:
  - IMPLEMENT theme management with CSS variables
  - HANDLE theme switching without re-renders
  - IMPLEMENT theme persistence
  - VALIDATE theme configuration

Task 5: Core Components
CREATE src/components/QuestionCard.tsx:
  - IMPLEMENT multiple choice question rendering
  - HANDLE answer selection and feedback
  - IMPLEMENT image support with loading states
  - ADD accessibility attributes (ARIA labels)

CREATE src/components/ProgressBar.tsx:
  - IMPLEMENT visual progress indicator
  - SHOW current question and total questions
  - ADD percentage completion display
  - IMPLEMENT smooth animations

CREATE src/components/SummaryScreen.tsx:
  - IMPLEMENT lesson completion summary
  - SHOW final score and time spent
  - ADD retry and continue options
  - IMPLEMENT encouraging messages for children

Task 6: Main Application Component
CREATE src/components/LessonPlayer.tsx:
  - IMPLEMENT main lesson player logic
  - HANDLE lesson loading and error states
  - IMPLEMENT question progression
  - COORDINATE all child components

CREATE src/App.tsx:
  - IMPLEMENT app initialization
  - HANDLE theme loading from lesson
  - IMPLEMENT error boundary for graceful failures
  - COORDINATE lesson loading from URL

Task 7: Styling and Themes
CREATE src/styles/variables.css:
  - DEFINE CSS custom properties for theming
  - IMPLEMENT default theme values
  - SET up responsive design variables
  - DEFINE accessibility-friendly sizes

CREATE src/styles/themes.css:
  - IMPLEMENT theme switching classes
  - DEFINE pre-built theme variations
  - IMPLEMENT smooth transition animations
  - ENSURE high contrast for accessibility

CREATE src/styles/global.css:
  - IMPLEMENT global styles for child-friendly UI
  - DEFINE component-specific styles
  - IMPLEMENT responsive design patterns
  - ENSURE large touch targets for mobile

Task 8: Sample Content and Configuration
CREATE public/lessons/counting-1.json:
  - IMPLEMENT sample counting lesson
  - INCLUDE proper theme configuration
  - ADD child-friendly content and images
  - VALIDATE JSON structure

CREATE public/lessons/default.json:
  - IMPLEMENT fallback lesson for missing content
  - INCLUDE basic theme configuration
  - ADD simple, engaging content
  - ENSURE error-free structure

Task 9: Build Configuration
MODIFY vite.config.ts:
  - CONFIGURE production build optimization
  - IMPLEMENT code splitting for optimal loading
  - SET up CSS minification and injection
  - CONFIGURE asset optimization

CREATE build scripts:
  - IMPLEMENT development server configuration
  - ADD build validation scripts
  - CONFIGURE deployment preparation
  - IMPLEMENT bundle size analysis
```

### Integration Points

```yaml
EMBEDDING:
  - iframe: "Standalone HTML with query parameters"
  - component: "React component export for parent apps"
  - pattern: "UMD build with global variable access"

CONFIGURATION:
  - lessons: "JSON files in public/lessons/ directory"
  - themes: "JSON theme objects in lesson files"
  - pattern: "Automatic theme application on lesson load"

STORAGE:
  - key: "lesson-progress:{lessonId}"
  - pattern: "Namespaced localStorage with cleanup"
  - fallback: "Graceful degradation without storage"

ROUTING:
  - query: "?lesson=lesson-id&theme=theme-name"
  - pattern: "Single-page app with URL-based configuration"
  - fallback: "Default lesson when no parameters provided"
```

## Validation Loop

### Level 1: Syntax & Style

```bash
# Run these FIRST - fix any errors before proceeding
npm run lint                    # ESLint with React 19 rules
npm run type-check             # TypeScript compilation
npm run format                 # Prettier formatting

# Expected: No errors or warnings
# If errors: Read carefully and fix before proceeding
```

### Level 2: Unit Tests

```typescript
// CREATE __tests__/components/LessonPlayer.test.tsx
describe('LessonPlayer', () => {
  it('loads lesson from query parameter', async () => {
    // Mock URL with lesson parameter
    const mockUrl = '?lesson=counting-1';
    Object.defineProperty(window, 'location', {
      value: { search: mockUrl }
    });
    
    render(<LessonPlayer />);
    
    // Verify lesson loads
    expect(screen.getByText('Learn to Count')).toBeInTheDocument();
  });
  
  it('handles missing lesson gracefully', async () => {
    // Mock URL with invalid lesson
    const mockUrl = '?lesson=nonexistent';
    Object.defineProperty(window, 'location', {
      value: { search: mockUrl }
    });
    
    render(<LessonPlayer />);
    
    // Verify fallback behavior
    expect(screen.getByText('Default Lesson')).toBeInTheDocument();
  });
  
  it('persists progress to localStorage', async () => {
    render(<LessonPlayer />);
    
    // Simulate answering questions
    await userEvent.click(screen.getByText('Answer 1'));
    
    // Verify progress is saved
    const savedProgress = localStorage.getItem('lesson-progress:counting-1');
    expect(savedProgress).toBeTruthy();
  });
});

// CREATE __tests__/hooks/useLocalStorage.test.tsx
describe('useLocalStorage', () => {
  it('handles quota exceeded errors', () => {
    // Mock localStorage to throw quota error
    const mockSetItem = jest.fn(() => {
      throw new DOMException('QuotaExceededError');
    });
    
    Object.defineProperty(window, 'localStorage', {
      value: { setItem: mockSetItem, getItem: jest.fn() }
    });
    
    const { result } = renderHook(() => useLocalStorage('test', 'value'));
    
    // Should not crash on quota error
    expect(result.current[0]).toBe('value');
  });
});
```

```bash
# Run and iterate until passing:
npm test                        # Run all tests
npm run test:coverage          # Generate coverage report
npm run test:watch             # Run tests in watch mode

# Expected: 80%+ coverage, all tests passing
# If failing: Read test output, fix issues, re-run
```

### Level 3: Integration Testing

```bash
# Start the development server
npm run dev

# Test lesson loading with different parameters
curl -I "http://localhost:5173?lesson=counting-1"
# Expected: 200 OK, lesson loads correctly

curl -I "http://localhost:5173?lesson=nonexistent"
# Expected: 200 OK, fallback lesson loads

# Test theme switching
curl -I "http://localhost:5173?lesson=counting-1&theme=dark"
# Expected: 200 OK, dark theme applied

# Test localStorage persistence
# 1. Complete a lesson in browser
# 2. Refresh page
# 3. Verify progress is restored
```

### Level 4: Build and Deployment Validation

```bash
# Build for production
npm run build

# Validate bundle size
npm run analyze-bundle
# Expected: Main bundle < 150kb gzipped

# Test built application
npm run preview
# Expected: Production build works identically to dev

# Validate embeddable build
npm run build:embed
# Expected: UMD bundle created for iframe embedding

# Test cross-browser compatibility
npm run test:browsers
# Expected: Works in Chrome, Firefox, Safari, Edge
```

### Level 5: Accessibility and UX Testing

```bash
# Accessibility testing
npm run test:a11y
# Expected: WCAG 2.1 AA compliance

# Performance testing
npm run lighthouse
# Expected: 90+ scores in all categories

# Mobile responsiveness
npm run test:mobile
# Expected: Works on mobile devices with touch

# Color contrast validation
npm run test:contrast
# Expected: 4.5:1 minimum contrast ratio
```

## Final Validation Checklist

- [ ] All tests pass: `npm test`
- [ ] No linting errors: `npm run lint`
- [ ] No type errors: `npm run type-check`
- [ ] Bundle size under 150kb: `npm run analyze-bundle`
- [ ] Lesson loads from query parameter: Manual test with `?lesson=counting-1`
- [ ] Progress persists across sessions: Complete lesson, refresh, verify
- [ ] Theme switching works: Test with `?theme=dark`
- [ ] Accessibility compliance: `npm run test:a11y`
- [ ] Mobile responsiveness: Test on mobile devices
- [ ] Cross-browser compatibility: Test in Chrome, Firefox, Safari, Edge
- [ ] Error handling works: Test with invalid lesson IDs
- [ ] LocalStorage quota handling: Test with storage full
- [ ] Graceful degradation: Test without localStorage support

---

## Anti-Patterns to Avoid

- ❌ Don't use CSS-in-JS for themes - CSS variables are more performant
- ❌ Don't re-render all components on theme change - use CSS custom properties
- ❌ Don't ignore localStorage quota errors - implement cleanup strategies
- ❌ Don't hardcode lesson paths - use configurable base URLs
- ❌ Don't skip accessibility attributes - critical for educational apps
- ❌ Don't use complex state management - keep it simple with hooks
- ❌ Don't ignore mobile users - implement touch-friendly interfaces
- ❌ Don't skip error boundaries - graceful failure is critical
- ❌ Don't assume localStorage is available - implement fallbacks
- ❌ Don't create overly complex lesson JSON - keep it simple and validatable

## Confidence Score: 9/10

This PRP provides comprehensive context for one-pass implementation success including:
- Complete technical specifications with modern React patterns
- Detailed implementation blueprint with specific tasks
- Extensive validation loops covering all aspects
- Real-world considerations for educational apps
- Production-ready build configuration
- Accessibility and performance requirements

The high confidence score reflects the thorough research conducted on micro-frontends, theming systems, localStorage patterns, and educational app best practices, combined with the structured approach following the PRP framework methodology.