name: "Lesson Authoring Tool - Visual Educational Content Creator"
description: |
  Comprehensive PRP for building a visual lesson authoring tool that creates educational content compatible with the KGPro Learning App. 
  Features drag-and-drop lesson assembly, asset management, theme editing, and real-time preview capabilities.

## Purpose

Create a production-ready visual lesson authoring tool that empowers educators to create engaging educational content without coding. The tool generates JSON lessons compatible with the KGPro Learning App, providing a complete content creation to delivery pipeline.

## Core Principles

1. **Visual-First Design**: Intuitive drag-and-drop interface for non-technical users
2. **Schema-Driven Validation**: JSON Schema ensures lesson structure consistency
3. **Asset-Centric Workflow**: Comprehensive media management and optimization
4. **Real-time Preview**: Live preview of lessons during creation
5. **Export Compatibility**: Seamless integration with existing learning app ecosystem

---

## Goal

Build a comprehensive lesson authoring tool that allows educators to visually create, edit, and manage educational content. The tool should provide drag-and-drop lesson assembly, asset management, theme customization, and export capabilities while maintaining compatibility with the KGPro Learning App JSON format.

## Why

- **Educator Empowerment**: Enable non-technical educators to create engaging digital lessons
- **Content Scalability**: Streamline lesson creation for large educational institutions
- **Quality Consistency**: Enforce lesson structure standards through validation
- **Asset Optimization**: Ensure media files are web-optimized for performance
- **Ecosystem Integration**: Seamless workflow from creation to delivery via learning app
- **Cost Efficiency**: Reduce dependency on technical teams for content creation

## What

### Core Features
- **Visual Lesson Builder**: Drag-and-drop interface for assembling lesson components
- **Question Editor**: Rich interface for creating multiple choice questions with images
- **Asset Manager**: Upload, organize, and optimize images and media files
- **Theme Editor**: Visual customization of lesson appearance and branding
- **Real-time Preview**: Live preview of lessons as they appear in the learning app
- **Template Library**: Pre-built lesson templates for common educational patterns
- **Export System**: Generate JSON lessons compatible with learning app
- **Validation Engine**: Real-time validation of lesson structure and content

### Technical Requirements
- **React 19** with TypeScript for type safety and modern patterns
- **Vite** build system for optimal development experience
- **@dnd-kit** for high-performance drag-and-drop interactions
- **React Hook Form** with JSON Schema for robust form validation
- **Canvas API** for theme preview and visual editing
- **File Upload** with optimization and validation
- **Responsive Design** for desktop and tablet workflows

### Success Criteria

- [ ] Non-technical users can create complete lessons in under 30 minutes
- [ ] Generated JSON lessons load correctly in KGPro Learning App
- [ ] Real-time validation prevents invalid lesson structures
- [ ] Asset upload and optimization reduces file sizes by 70%+
- [ ] Theme customization reflects accurately in preview and export
- [ ] Export process generates valid, optimized lesson files
- [ ] 80%+ test coverage with comprehensive validation testing
- [ ] WCAG 2.1 AA accessibility compliance for authoring interface

## All Needed Context

### Documentation & References

```yaml
# MUST READ - Include these in your context window
- url: https://dndkit.com/docs/introduction
  why: High-performance drag-and-drop implementation
  section: "Sortable and Droppable patterns"
  critical: Performance optimization for smooth interactions

- url: https://react-hook-form.com/docs/useform
  why: Efficient form handling with minimal re-renders
  section: "Performance optimization and validation"
  critical: Schema integration and error handling

- url: https://json-schema.org/understanding-json-schema/
  why: Comprehensive schema definition for lesson structure
  section: "Schema composition and validation"
  critical: Creating robust, reusable schemas

- url: https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API
  why: Canvas-based theme preview and visual editing
  section: "Canvas rendering and manipulation"
  critical: Real-time visual updates for theme changes

- url: https://web.dev/articles/fast
  why: Performance optimization for file uploads and processing
  section: "Image optimization and lazy loading"
  critical: Asset management best practices

- url: https://www.w3.org/WAI/WCAG21/quickref/
  why: Accessibility compliance for authoring interface
  section: "Keyboard navigation and screen reader support"
  critical: Making authoring tool accessible to all educators

- file: /workspace/PRPs/kgpro-learning-app.md
  why: Lesson JSON format specification and compatibility requirements
  critical: Ensuring exported lessons work with existing player

- file: /workspace/claude_md_files/CLAUDE-REACT.md
  why: React patterns and conventions from codebase
  critical: Following established TypeScript and component patterns

- file: /workspace/PRPs/templates/prp_base.md
  why: PRP structure and validation loop patterns
  critical: Implementing proper validation gates for quality assurance
```

### Current Codebase Structure

```bash
PRPs-agentic-eng/
├── .claude/
│   └── commands/           # 28+ Claude Code commands
├── PRPs/
│   ├── kgpro-learning-app.md  # Learning app PRP (compatibility reference)
│   ├── templates/          # PRP templates with validation
│   ├── scripts/           # PRP runner utilities
│   └── ai_docs/           # Curated documentation
├── claude_md_files/       # Framework-specific CLAUDE.md files
│   ├── CLAUDE-REACT.md    # React patterns and conventions
│   └── CLAUDE-NEXTJS-15.md # Next.js patterns
└── pyproject.toml         # Python package configuration
```

### Desired Authoring Tool Structure

```bash
lesson-authoring-tool/
├── public/
│   ├── templates/         # Lesson templates
│   │   ├── counting-template.json
│   │   ├── reading-template.json
│   │   └── quiz-template.json
│   └── assets/           # Default assets and icons
├── src/
│   ├── components/       # React components
│   │   ├── LessonBuilder/
│   │   │   ├── LessonBuilder.tsx
│   │   │   ├── ComponentPalette.tsx
│   │   │   ├── DesignCanvas.tsx
│   │   │   └── PropertyPanel.tsx
│   │   ├── QuestionEditor/
│   │   │   ├── QuestionEditor.tsx
│   │   │   ├── QuestionForm.tsx
│   │   │   └── AnswerManager.tsx
│   │   ├── AssetManager/
│   │   │   ├── AssetManager.tsx
│   │   │   ├── FileUploader.tsx
│   │   │   ├── AssetGallery.tsx
│   │   │   └── AssetOptimizer.tsx
│   │   ├── ThemeEditor/
│   │   │   ├── ThemeEditor.tsx
│   │   │   ├── ColorPicker.tsx
│   │   │   ├── FontSelector.tsx
│   │   │   └── ThemePreview.tsx
│   │   └── Common/
│   │       ├── PreviewWindow.tsx
│   │       ├── ValidationPanel.tsx
│   │       └── ExportDialog.tsx
│   ├── hooks/           # Custom React hooks
│   │   ├── useLessonBuilder.ts
│   │   ├── useAssetManager.ts
│   │   ├── useThemeEditor.ts
│   │   └── useFileUpload.ts
│   ├── schemas/         # JSON schemas
│   │   ├── lessonSchema.ts
│   │   ├── questionSchema.ts
│   │   └── themeSchema.ts
│   ├── types/           # TypeScript types
│   │   ├── Lesson.ts
│   │   ├── Question.ts
│   │   ├── Theme.ts
│   │   └── Asset.ts
│   ├── utils/           # Utility functions
│   │   ├── lessonValidator.ts
│   │   ├── assetOptimizer.ts
│   │   ├── themeGenerator.ts
│   │   └── exportManager.ts
│   ├── stores/          # State management
│   │   ├── lessonStore.ts
│   │   ├── assetStore.ts
│   │   └── themeStore.ts
│   ├── styles/          # CSS and styling
│   │   ├── global.css
│   │   ├── components.css
│   │   └── themes.css
│   ├── App.tsx
│   └── main.tsx
├── __tests__/           # Test files
│   ├── components/
│   ├── hooks/
│   ├── utils/
│   └── integration/
├── package.json
├── vite.config.ts
├── tsconfig.json
├── tailwind.config.js
└── README.md
```

### Known Gotchas & Library Quirks

```typescript
// CRITICAL: React 19 with TypeScript strict mode
// - Use ReactElement instead of JSX.Element
// - All components must have explicit return types
// - No 'any' types - use 'unknown' instead

// CRITICAL: @dnd-kit performance optimization
// - Use DragOverlay for scrollable containers
// - Implement proper cleanup in useEffect
// - Avoid creating new objects during drag operations
// - Use measuring strategy for dynamic content

// CRITICAL: JSON Schema validation complexity
// - Nested object validation requires careful schema design
// - Circular references must be avoided in schemas
// - Custom validation functions impact performance
// - Schema compilation should be done once at startup

// CRITICAL: File upload security and optimization
// - Always validate file types server-side
// - Implement file size limits to prevent DoS
// - Use progressive JPEG for better perceived performance
// - Sanitize uploaded file names to prevent path traversal

// CRITICAL: Canvas API performance
// - Use requestAnimationFrame for smooth animations
// - Implement proper cleanup of canvas contexts
// - Optimize redraw operations with dirty rectangle tracking
// - Use OffscreenCanvas for background processing

// CRITICAL: Accessibility for authoring tools
// - Drag-and-drop must have keyboard alternatives
// - Screen reader support for complex interactions
// - High contrast mode compatibility
// - Focus management for modal dialogs and popups
```

### Lesson JSON Format Compatibility

```typescript
// MUST match KGPro Learning App format exactly
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

## Implementation Blueprint

### Data Models and Structure

Create comprehensive data models for lesson authoring with strict type safety and validation.

```typescript
// Authoring-specific extensions to lesson format
interface LessonDraft extends Lesson {
  version: string;
  lastModified: string;
  authorId: string;
  status: 'draft' | 'review' | 'published';
  metadata: {
    createdAt: string;
    updatedAt: string;
    tags: string[];
    category: string;
    difficulty: 'beginner' | 'intermediate' | 'advanced';
  };
}

// Asset management models
interface Asset {
  id: string;
  filename: string;
  originalFilename: string;
  mimeType: string;
  size: number;
  optimizedSize: number;
  url: string;
  thumbnailUrl?: string;
  alt?: string;
  tags: string[];
  uploadedAt: string;
}

// Drag-and-drop component models
interface DraggableComponent {
  id: string;
  type: 'question' | 'image' | 'text' | 'spacer';
  position: number;
  data: unknown;
  validation: ValidationResult;
}

// Theme editor models
interface ThemePreset {
  id: string;
  name: string;
  description: string;
  theme: Theme;
  preview: string; // base64 encoded preview image
  category: 'educational' | 'playful' | 'professional';
}
```

### Task Implementation Order

```yaml
Task 1: Project Setup and Core Architecture
CREATE lesson-authoring-tool/package.json:
  - CONFIGURE Vite with React 19 and TypeScript
  - ADD dependencies: @dnd-kit/core, @dnd-kit/sortable, react-hook-form
  - ADD dev dependencies: vitest, @testing-library/react, @types/react
  - CONFIGURE build scripts for production deployment

CREATE lesson-authoring-tool/vite.config.ts:
  - CONFIGURE path aliases for clean imports
  - SET up CSS modules and PostCSS
  - CONFIGURE asset optimization and bundling
  - ADD development server configuration

CREATE lesson-authoring-tool/tsconfig.json:
  - ENABLE strict mode with React 19 settings
  - CONFIGURE path mapping for clean imports
  - SET target to ES2020 for modern browsers
  - ADD DOM lib for Canvas API support

Task 2: Type Definitions and Schemas
CREATE src/types/Lesson.ts:
  - DEFINE LessonDraft interface extending base Lesson
  - DEFINE Asset interface for media management
  - DEFINE DraggableComponent interface for builder
  - EXPORT type guards and utilities

CREATE src/schemas/lessonSchema.ts:
  - IMPLEMENT comprehensive JSON Schema for lesson validation
  - DEFINE nested schemas for questions and themes
  - CREATE validation functions with detailed error messages
  - IMPLEMENT schema compilation for performance

CREATE src/schemas/questionSchema.ts:
  - DEFINE question validation with type-specific rules
  - IMPLEMENT choice validation and correctness checks
  - CREATE image validation for question assets
  - VALIDATE explanation text requirements

Task 3: State Management and Stores
CREATE src/stores/lessonStore.ts:
  - IMPLEMENT lesson state management with Zustand
  - HANDLE lesson loading, saving, and validation
  - MANAGE undo/redo functionality
  - IMPLEMENT auto-save with debouncing

CREATE src/stores/assetStore.ts:
  - IMPLEMENT asset management state
  - HANDLE file uploads and optimization
  - MANAGE asset organization and tagging
  - IMPLEMENT asset search and filtering

CREATE src/stores/themeStore.ts:
  - IMPLEMENT theme management state
  - HANDLE theme presets and customization
  - MANAGE theme preview and application
  - IMPLEMENT theme validation and export

Task 4: Core Utility Functions
CREATE src/utils/lessonValidator.ts:
  - IMPLEMENT comprehensive lesson validation
  - HANDLE real-time validation with debouncing
  - PROVIDE detailed error messages and suggestions
  - VALIDATE lesson completeness and structure

CREATE src/utils/assetOptimizer.ts:
  - IMPLEMENT image optimization and compression
  - HANDLE multiple format generation (WebP, AVIF)
  - CREATE thumbnail generation for previews
  - IMPLEMENT progressive loading strategies

CREATE src/utils/exportManager.ts:
  - IMPLEMENT JSON export compatible with learning app
  - HANDLE asset bundling and optimization
  - CREATE lesson validation before export
  - GENERATE export manifests and metadata

Task 5: Custom React Hooks
CREATE src/hooks/useLessonBuilder.ts:
  - IMPLEMENT drag-and-drop state management
  - HANDLE component reordering and insertion
  - MANAGE validation state for builder
  - IMPLEMENT auto-save functionality

CREATE src/hooks/useAssetManager.ts:
  - IMPLEMENT file upload with progress tracking
  - HANDLE asset optimization and processing
  - MANAGE asset state and organization
  - IMPLEMENT asset search and filtering

CREATE src/hooks/useThemeEditor.ts:
  - IMPLEMENT theme state management
  - HANDLE real-time theme preview
  - MANAGE theme validation and export
  - IMPLEMENT theme preset management

Task 6: Asset Management Components
CREATE src/components/AssetManager/FileUploader.tsx:
  - IMPLEMENT drag-and-drop file upload interface
  - HANDLE multiple file selection and validation
  - SHOW upload progress and error handling
  - IMPLEMENT file type and size validation

CREATE src/components/AssetManager/AssetGallery.tsx:
  - IMPLEMENT grid-based asset browsing
  - HANDLE asset search and filtering
  - SHOW asset details and metadata
  - IMPLEMENT asset selection and management

CREATE src/components/AssetManager/AssetOptimizer.tsx:
  - IMPLEMENT image optimization interface
  - HANDLE format conversion and compression
  - SHOW optimization results and file size reduction
  - IMPLEMENT batch optimization capabilities

Task 7: Theme Editor Components
CREATE src/components/ThemeEditor/ThemeEditor.tsx:
  - IMPLEMENT comprehensive theme editing interface
  - HANDLE color picker and font selection
  - MANAGE theme preset loading and saving
  - IMPLEMENT theme validation and preview

CREATE src/components/ThemeEditor/ColorPicker.tsx:
  - IMPLEMENT advanced color picker with palette
  - HANDLE color accessibility validation
  - SUPPORT hex, RGB, and HSL color formats
  - IMPLEMENT color harmony suggestions

CREATE src/components/ThemeEditor/ThemePreview.tsx:
  - IMPLEMENT real-time theme preview using Canvas API
  - HANDLE preview updates on theme changes
  - SHOW theme applied to sample lesson content
  - IMPLEMENT preview export for documentation

Task 8: Lesson Builder Components
CREATE src/components/LessonBuilder/LessonBuilder.tsx:
  - IMPLEMENT main lesson building interface
  - COORDINATE drag-and-drop interactions
  - HANDLE component palette and property panels
  - MANAGE lesson state and validation

CREATE src/components/LessonBuilder/ComponentPalette.tsx:
  - IMPLEMENT draggable component library
  - HANDLE component categorization and search
  - SHOW component previews and descriptions
  - IMPLEMENT component insertion and configuration

CREATE src/components/LessonBuilder/DesignCanvas.tsx:
  - IMPLEMENT drag-and-drop canvas with @dnd-kit
  - HANDLE component positioning and reordering
  - MANAGE component selection and editing
  - IMPLEMENT canvas zoom and pan functionality

Task 9: Question Editor Components
CREATE src/components/QuestionEditor/QuestionEditor.tsx:
  - IMPLEMENT comprehensive question editing interface
  - HANDLE question types and validation
  - MANAGE answer choices and correctness
  - IMPLEMENT question preview and testing

CREATE src/components/QuestionEditor/QuestionForm.tsx:
  - IMPLEMENT form-based question editing
  - HANDLE React Hook Form integration
  - MANAGE form validation and error display
  - IMPLEMENT question type-specific fields

CREATE src/components/QuestionEditor/AnswerManager.tsx:
  - IMPLEMENT answer choice management
  - HANDLE answer validation and correctness
  - MANAGE answer reordering and editing
  - IMPLEMENT answer explanation editing

Task 10: Preview and Export Components
CREATE src/components/Common/PreviewWindow.tsx:
  - IMPLEMENT real-time lesson preview
  - HANDLE preview updates on content changes
  - SHOW lesson as it appears in learning app
  - IMPLEMENT preview modes and responsive testing

CREATE src/components/Common/ValidationPanel.tsx:
  - IMPLEMENT real-time validation feedback
  - HANDLE validation error display and suggestions
  - MANAGE validation state and progress
  - IMPLEMENT validation rule explanations

CREATE src/components/Common/ExportDialog.tsx:
  - IMPLEMENT lesson export interface
  - HANDLE export format selection and options
  - MANAGE export progress and error handling
  - IMPLEMENT export validation and confirmation

Task 11: Main Application Components
CREATE src/App.tsx:
  - IMPLEMENT main application layout
  - HANDLE routing and navigation
  - MANAGE global state and context
  - IMPLEMENT error boundaries and loading states

CREATE src/main.tsx:
  - IMPLEMENT React 19 application bootstrap
  - HANDLE root component mounting
  - CONFIGURE global styles and providers
  - IMPLEMENT development tool integration

Task 12: Styling and Responsive Design
CREATE src/styles/global.css:
  - IMPLEMENT global styles and CSS reset
  - DEFINE CSS custom properties for theming
  - IMPLEMENT responsive design breakpoints
  - DEFINE accessibility-friendly defaults

CREATE src/styles/components.css:
  - IMPLEMENT component-specific styles
  - HANDLE drag-and-drop visual feedback
  - MANAGE focus states and hover effects
  - IMPLEMENT animation and transition styles

CREATE tailwind.config.js:
  - CONFIGURE Tailwind CSS with custom theme
  - DEFINE component-specific utility classes
  - IMPLEMENT responsive design utilities
  - CONFIGURE accessibility-friendly defaults
```

### Integration Points

```yaml
LESSON_COMPATIBILITY:
  - format: "JSON structure matching KGPro Learning App exactly"
  - validation: "Shared schema validation between authoring and player"
  - assets: "Optimized assets compatible with learning app requirements"

ASSET_MANAGEMENT:
  - upload: "Multi-file drag-and-drop with progress tracking"
  - optimization: "Automatic image optimization and format conversion"
  - organization: "Tag-based asset categorization and search"

THEME_SYSTEM:
  - editor: "Visual theme customization with real-time preview"
  - compatibility: "Theme export compatible with learning app"
  - validation: "Color accessibility and contrast validation"

EXPORT_SYSTEM:
  - format: "JSON lesson export with bundled assets"
  - validation: "Pre-export validation ensuring compatibility"
  - optimization: "Asset optimization and bundling for delivery"
```

## Validation Loop

### Level 1: Syntax & Style

```bash
# Run these FIRST - fix any errors before proceeding
npm run lint                    # ESLint with React 19 and accessibility rules
npm run type-check             # TypeScript compilation with strict mode
npm run format                 # Prettier formatting with consistent style

# Expected: No errors or warnings
# If errors: Read carefully and fix before proceeding
```

### Level 2: Unit Tests

```typescript
// CREATE __tests__/components/LessonBuilder.test.tsx
describe('LessonBuilder', () => {
  it('handles drag-and-drop component reordering', async () => {
    const mockLesson = createMockLesson();
    render(<LessonBuilder lesson={mockLesson} />);
    
    // Simulate drag-and-drop reordering
    const question1 = screen.getByTestId('question-1');
    const question2 = screen.getByTestId('question-2');
    
    await userEvent.drag(question1, question2);
    
    // Verify reordering
    expect(screen.getByTestId('question-1')).toBeInTheDocument();
    expect(mockLesson.questions[0].id).toBe('question-2');
  });
  
  it('validates lesson structure in real-time', async () => {
    render(<LessonBuilder lesson={createEmptyLesson()} />);
    
    // Add invalid question
    await userEvent.click(screen.getByText('Add Question'));
    
    // Verify validation error
    expect(screen.getByText('Question text is required')).toBeInTheDocument();
  });
});

// CREATE __tests__/utils/lessonValidator.test.ts
describe('lessonValidator', () => {
  it('validates complete lesson structure', () => {
    const lesson = createValidLesson();
    const result = validateLesson(lesson);
    
    expect(result.isValid).toBe(true);
    expect(result.errors).toHaveLength(0);
  });
  
  it('detects missing required fields', () => {
    const lesson = createInvalidLesson();
    const result = validateLesson(lesson);
    
    expect(result.isValid).toBe(false);
    expect(result.errors).toContain('Title is required');
  });
});

// CREATE __tests__/hooks/useAssetManager.test.ts
describe('useAssetManager', () => {
  it('handles file upload with optimization', async () => {
    const { result } = renderHook(() => useAssetManager());
    
    const mockFile = new File(['test'], 'test.jpg', { type: 'image/jpeg' });
    
    await act(async () => {
      await result.current.uploadAsset(mockFile);
    });
    
    expect(result.current.assets).toHaveLength(1);
    expect(result.current.assets[0].optimizedSize).toBeLessThan(mockFile.size);
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

# Test lesson creation workflow
curl -X POST "http://localhost:5173/api/lessons" \
  -H "Content-Type: application/json" \
  -d '{"title": "Test Lesson", "ageGroup": "5-7"}'
# Expected: 200 OK, lesson created

# Test asset upload
curl -X POST "http://localhost:5173/api/assets" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@test-image.jpg"
# Expected: 200 OK, asset uploaded and optimized

# Test lesson export
curl -X GET "http://localhost:5173/api/lessons/test-lesson/export"
# Expected: 200 OK, valid JSON lesson compatible with learning app
```

### Level 4: End-to-End Workflow Testing

```bash
# Complete lesson creation workflow
npm run test:e2e:create-lesson
# Expected: Full lesson creation from start to export

# Asset management workflow
npm run test:e2e:asset-management
# Expected: Upload, optimize, organize, and use assets

# Theme customization workflow
npm run test:e2e:theme-editor
# Expected: Create, preview, and export custom themes

# Export and compatibility testing
npm run test:e2e:export-compatibility
# Expected: Exported lessons load correctly in learning app
```

### Level 5: Performance and Accessibility Testing

```bash
# Performance testing
npm run lighthouse
# Expected: 90+ scores in all categories

# Accessibility testing
npm run test:a11y
# Expected: WCAG 2.1 AA compliance

# Bundle size analysis
npm run analyze-bundle
# Expected: Main bundle < 500kb gzipped

# Cross-browser compatibility
npm run test:browsers
# Expected: Works in Chrome, Firefox, Safari, Edge
```

## Final Validation Checklist

- [ ] All tests pass: `npm test`
- [ ] No linting errors: `npm run lint`
- [ ] No type errors: `npm run type-check`
- [ ] Lesson creation workflow complete: Manual test
- [ ] Asset upload and optimization works: Upload test images
- [ ] Theme editor generates valid themes: Create and preview themes
- [ ] Export generates valid JSON: Export and validate with learning app
- [ ] Real-time validation works: Test invalid lesson structures
- [ ] Drag-and-drop is smooth: Test component reordering
- [ ] Accessibility compliance: `npm run test:a11y`
- [ ] Performance requirements met: `npm run lighthouse`
- [ ] Cross-browser compatibility: Test in multiple browsers
- [ ] Mobile responsiveness: Test on tablet devices
- [ ] File upload security: Test with various file types
- [ ] Bundle size optimization: `npm run analyze-bundle`

---

## Anti-Patterns to Avoid

- ❌ Don't create new drag-and-drop implementations - use @dnd-kit
- ❌ Don't skip JSON Schema validation - ensures compatibility
- ❌ Don't ignore accessibility - authoring tools must be accessible
- ❌ Don't implement custom file upload - use proven libraries
- ❌ Don't skip asset optimization - impacts learning app performance
- ❌ Don't create incompatible lesson formats - follow existing schema
- ❌ Don't ignore real-time validation - prevents invalid lessons
- ❌ Don't skip performance testing - affects user experience
- ❌ Don't hardcode theme values - use configurable system
- ❌ Don't ignore mobile users - support tablet-based authoring
- ❌ Don't skip error boundaries - graceful failure is critical
- ❌ Don't create complex state management - use proven patterns

## Confidence Score: 9/10

This PRP provides comprehensive context for one-pass implementation success including:
- Complete technical architecture with modern React patterns
- Detailed task breakdown with specific implementation steps
- Comprehensive validation loops covering all aspects
- Integration with existing KGPro Learning App ecosystem
- Advanced features like drag-and-drop, asset management, and theme editing
- Performance and accessibility requirements
- Real-world considerations for educational content creation

The high confidence score reflects the thorough research conducted on authoring tool architectures, drag-and-drop patterns, asset management systems, and educational content creation workflows, combined with the structured approach following the PRP framework methodology and compatibility requirements with the existing learning app.