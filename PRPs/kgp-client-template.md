name: "KGP Client Template - Enhanced Headless WordPress E-commerce System"
description: |

## Purpose

Transform existing headless WordPress client into a comprehensive, extensible e-commerce platform with WooCommerce integration, social media management, and configuration-driven architecture - enabling rapid deployment for multiple client needs while maintaining security, performance, and developer experience standards.

## Core Principles

1. **Configuration-First**: JSON-driven page layouts and feature flags for rapid customization
2. **Security by Design**: PCI compliance, secure token management, and API security best practices
3. **Performance Optimized**: Sub-3-second load times with 10,000+ product support
4. **Modular Architecture**: Plugin-based system for easy feature addition/removal
5. **One-Pass Implementation**: Comprehensive context for immediate production deployment

---

## Goal

Build a production-ready, white-label e-commerce platform that serves as a unified interface for headless WordPress CMS with WooCommerce integration, social media management, and extensible page functionality - all configurable through environment variables and JSON configs, deployable for multiple clients with minimal code changes.

## Why

- **Business Value**: Single codebase serves multiple client e-commerce needs
- **Rapid Deployment**: New client setup in under 2 hours via configuration
- **Competitive Advantage**: Advanced features (social integration, dynamic pages) out-of-the-box
- **Maintenance Efficiency**: Centralized updates benefit all client deployments
- **Revenue Scalability**: Template licensing model with premium feature tiers

## What

### User-Visible Behavior
- **Customers**: Seamless shopping experience with social proof integration
- **Store Owners**: Admin dashboard for inventory, orders, and social media management
- **Developers**: Configuration-driven deployment with comprehensive documentation

### Technical Requirements
- Support 10,000+ products with <3 second load times
- Shopping cart persistence across sessions
- Payment processing (Stripe, PayPal, WooCommerce Payments)
- Social media post scheduling and management
- Dynamic page creation via JSON configuration
- Multi-theme support with white-label customization
- Responsive design with mobile-first approach

### Success Criteria

- [ ] Initial page load under 3 seconds
- [ ] Lighthouse performance score >90
- [ ] 99.9% payment processing uptime
- [ ] Social media post scheduling 95% success rate
- [ ] New page types addable via JSON config only
- [ ] Client deployment in under 2 hours
- [ ] 90%+ test coverage
- [ ] Zero security vulnerabilities in production

## All Needed Context

### Documentation & References

```yaml
# MUST READ - Include these in your context window

- file: PRPs/ai_docs/react_ecommerce_patterns_2024.md
  why: Complete React e-commerce architecture patterns and state management strategies
  critical: Shopping cart state management with Context API performance optimization

- file: PRPs/ai_docs/social_media_apis_2024.md
  why: Social media API integration patterns with 2024 updates
  critical: Instagram Basic Display API deprecation - must use Instagram Graph API

- file: PRPs/ai_docs/config_driven_ui_patterns.md
  why: Configuration-driven architecture implementation patterns
  critical: Component mapping strategies and performance considerations

- url: https://docs.stripe.com/sdks/stripejs-react
  why: Official Stripe React integration with Payment Element
  critical: Payment Element supports 40+ payment methods automatically

- url: https://woocommerce.github.io/woocommerce-rest-api-docs/
  why: WooCommerce REST API v3 documentation
  critical: Authentication with OAuth 1.0a and rate limiting (200 req/hour/user)

- url: https://developers.facebook.com/docs/instagram-api/
  why: Instagram Graph API documentation
  critical: Requires Instagram Business/Creator account, HTTPS for OAuth

- url: https://developer.paypal.com/sdk/js/
  why: PayPal JavaScript SDK integration
  critical: React package @paypal/react-paypal-js for component integration

- url: https://developer.wordpress.org/rest-api/
  why: WordPress REST API documentation
  critical: JWT authentication for headless WordPress

- url: https://www.storyblok.com/tp/react-dynamic-component-from-json
  why: JSON-based dynamic component rendering patterns
  critical: Component mapping and React.createElement patterns

- url: https://css-tricks.com/theming-and-theme-switching-with-react-and-styled-components/
  why: React theming system implementation
  critical: CSS-in-JS performance optimization with styled-components
```

### Current Codebase Tree (React + TypeScript + Vite Stack)

```bash
# CRITICAL: The 'src' directory will exist in the project root
# All source code must be placed within the src/ directory
kgp-client-template/
├── src/                       # SOURCE DIRECTORY (will exist)
│   ├── api/
│   │   └── client.ts          # Existing HTTP client with Axios
│   ├── components/            # Existing React components
│   ├── pages/                 # React Router pages
│   ├── styles/                # Tailwind CSS configuration
│   └── utils/                 # Utility functions
├── public/                    # Static assets
├── package.json               # React 18 + TypeScript + Vite
├── tailwind.config.js         # Tailwind CSS configuration
├── vite.config.ts            # Vite build configuration
└── tsconfig.json             # TypeScript configuration
```

### Desired Codebase Tree with Enhanced Architecture

```bash
kgp-client-template/
├── src/
│   ├── api/                   # Enhanced API layer
│   │   ├── client.ts          # Base HTTP client (existing)
│   │   ├── wordpress/         # WordPress REST API
│   │   │   ├── posts.ts
│   │   │   ├── pages.ts
│   │   │   └── media.ts
│   │   ├── woocommerce/       # WooCommerce REST API
│   │   │   ├── products.ts
│   │   │   ├── orders.ts
│   │   │   ├── customers.ts
│   │   │   └── cart.ts
│   │   ├── social/            # Social Media APIs
│   │   │   ├── instagram.ts
│   │   │   ├── facebook.ts
│   │   │   └── twitter.ts
│   │   ├── payments/          # Payment Gateways
│   │   │   ├── stripe.ts
│   │   │   ├── paypal.ts
│   │   │   └── woocommerce.ts
│   │   └── config/           # Configuration management
│   │       ├── pages.ts
│   │       └── features.ts
│   │
│   ├── components/            # Enhanced component library
│   │   ├── ui/               # Base UI components (existing patterns)
│   │   ├── ecommerce/        # E-commerce specific components
│   │   │   ├── ProductCard.tsx
│   │   │   ├── ProductGrid.tsx
│   │   │   ├── ShoppingCart.tsx
│   │   │   ├── Checkout.tsx
│   │   │   └── PaymentForm.tsx
│   │   ├── social/           # Social media components
│   │   │   ├── InstagramFeed.tsx
│   │   │   ├── FacebookManager.tsx
│   │   │   └── SocialPostForm.tsx
│   │   ├── forms/            # Dynamic form system
│   │   │   ├── FormBuilder.tsx
│   │   │   ├── FormRenderer.tsx
│   │   │   └── FormValidator.tsx
│   │   ├── templates/        # Template components
│   │   │   ├── TemplateBuilder.tsx
│   │   │   ├── ThemeSelector.tsx
│   │   │   └── ComponentLibrary.tsx
│   │   └── layout/           # Layout components
│   │       ├── PageRenderer.tsx
│   │       └── ConfigDrivenLayout.tsx
│   │
│   ├── hooks/                # Custom React hooks
│   │   ├── useCart.ts        # Shopping cart state management
│   │   ├── useAuth.ts        # Authentication state
│   │   ├── useProducts.ts    # Product data fetching
│   │   ├── useSocialAuth.ts  # Social media authentication
│   │   └── useTheme.ts       # Theme management
│   │
│   ├── store/                # State management
│   │   ├── cartStore.ts      # Zustand cart store
│   │   ├── authStore.ts      # Authentication store
│   │   └── configStore.ts    # Configuration store
│   │
│   ├── types/                # TypeScript definitions
│   │   ├── api.ts           # API response types
│   │   ├── config.ts        # Configuration types
│   │   ├── ecommerce.ts     # E-commerce types
│   │   └── social.ts        # Social media types
│   │
│   ├── utils/                # Utility functions
│   │   ├── auth.ts          # Authentication utilities
│   │   ├── payment.ts       # Payment processing utilities
│   │   ├── validation.ts    # Form validation
│   │   └── config.ts        # Configuration parsing
│   │
│   ├── config/               # Application configuration
│   │   ├── pages.json       # Page configurations
│   │   ├── features.json    # Feature flag configurations
│   │   ├── themes.json      # Theme configurations
│   │   └── social.json      # Social platform configurations
│   │
│   └── tests/               # Test files
│       ├── components/      # Component tests
│       ├── hooks/          # Hook tests
│       ├── api/            # API tests
│       └── utils/          # Utility tests
│
├── public/
│   ├── configs/            # Public configuration files
│   │   ├── client-a.json   # Client-specific configurations
│   │   └── client-b.json
│   └── themes/             # Theme assets
│       ├── default/
│       └── premium/
│
├── docs/                   # Documentation
│   ├── deployment.md       # Deployment guide
│   ├── configuration.md    # Configuration reference
│   └── api-integration.md  # API integration guide
│
├── scripts/                # Build and deployment scripts
│   ├── deploy.sh
│   └── setup-client.sh
│
└── .env.example           # Environment variables template
```

### Known Gotchas of Tech Stack & Library Quirks

```typescript
// CRITICAL: Instagram Basic Display API deprecated Dec 4, 2024
// Must use Instagram Graph API with Business/Creator account

// CRITICAL: WooCommerce API rate limiting - 200 requests/hour/user
// Implement request queuing and caching strategy

// CRITICAL: Stripe Payment Element requires specific DOM structure
// Cannot be rendered conditionally - use CSS display:none instead

// CRITICAL: PayPal SDK must be loaded before component render
// Use PayPalScriptProvider at app level, not component level

// CRITICAL: React 18 Concurrent Features affect state updates
// Use startTransition for non-urgent updates to prevent UI blocking

// CRITICAL: Vite development server CORS issues with external APIs
// Configure proxy in vite.config.ts for development

// CRITICAL: Tailwind CSS purging can remove dynamic classes
// Add safelist for dynamically generated theme classes

// CRITICAL: TypeScript strict mode with external APIs
// API responses need runtime validation with zod or similar

// CRITICAL: Shopping cart state persistence
// localStorage has 5-10MB limit, use IndexedDB for large carts
```

## Implementation Blueprint

### Data Models and Structure

Create comprehensive TypeScript interfaces for type safety:

```typescript
// Core E-commerce Types
interface Product {
  id: string;
  name: string;
  description: string;
  price: number;
  images: ProductImage[];
  categories: Category[];
  inventory: InventoryInfo;
  seo: SEOData;
}

interface CartItem {
  productId: string;
  quantity: number;
  variant?: ProductVariant;
  addedAt: Date;
}

interface Order {
  id: string;
  customerId: string;
  items: CartItem[];
  payment: PaymentInfo;
  shipping: ShippingInfo;
  status: OrderStatus;
  total: number;
}

// Configuration-Driven Types
interface PageConfig {
  id: string;
  title: string;
  layout: string;
  components: ComponentConfig[];
  permissions: string[];
  socialPlatforms?: SocialPlatform[];
  customFields?: CustomField[];
}

interface ComponentConfig {
  id: string;
  type: string;
  props: Record<string, any>;
  children?: ComponentConfig[];
  conditions?: RenderCondition[];
}

// Social Media Types
interface SocialPost {
  id: string;
  platform: 'instagram' | 'facebook' | 'twitter' | 'linkedin';
  content: string;
  media?: MediaFile[];
  scheduledAt?: Date;
  status: 'draft' | 'scheduled' | 'published' | 'failed';
}

// Payment Types
interface PaymentMethod {
  id: string;
  type: 'stripe' | 'paypal' | 'woocommerce';
  isDefault: boolean;
  metadata: PaymentMetadata;
}
```

### List of Tasks in Implementation Order

```yaml
Phase 1: Foundation & API Integration (Week 1-2)

Task 1 - Setup Enhanced Project Structure:
CREATE enhanced directory structure:
  - ENSURE src/ directory exists in project root
  - FOLLOW desired codebase tree exactly within src/
  - CREATE all directories and index files
  - SETUP TypeScript path aliases in tsconfig.json
  - CONFIGURE Vite proxy for development API calls

Task 2 - WordPress/WooCommerce API Integration:
CREATE src/api/wordpress/* and src/api/woocommerce/*:
  - IMPLEMENT OAuth 1.0a authentication for WooCommerce
  - CREATE product fetching with caching and pagination
  - IMPLEMENT cart operations (add, remove, update quantities)
  - ADD order creation and management
  - FOLLOW rate limiting patterns (200 req/hour/user)

Task 3 - State Management Setup:
CREATE src/store/* and src/hooks/*:
  - IMPLEMENT Zustand stores for cart, auth, and config
  - CREATE custom hooks for data fetching and state management
  - ADD cart persistence with localStorage fallback to IndexedDB
  - IMPLEMENT optimistic updates for cart operations

Phase 2: E-commerce Core Features (Week 3-4)

Task 4 - Product Catalog Implementation:
CREATE src/components/ecommerce/*:
  - IMPLEMENT ProductGrid with virtualization for 10,000+ products
  - CREATE ProductCard with lazy loading and image optimization
  - ADD filtering, sorting, and search functionality
  - IMPLEMENT category navigation and breadcrumbs

Task 5 - Shopping Cart & Checkout:
CREATE cart and checkout components:
  - IMPLEMENT ShoppingCart with real-time updates
  - CREATE multi-step Checkout flow with validation
  - ADD address validation and shipping calculation
  - IMPLEMENT inventory checking and stock warnings

Task 6 - Payment Gateway Integration:
CREATE src/api/payments/* and payment components:
  - INTEGRATE Stripe Payment Element (supports 40+ methods)
  - IMPLEMENT PayPal SDK with @paypal/react-paypal-js
  - ADD WooCommerce Payments as fallback option
  - CREATE secure token handling and PCI compliance measures

Phase 3: Social Media Integration (Week 5-6)

Task 7 - Social Media API Setup:
CREATE src/api/social/* with OAuth implementations:
  - IMPLEMENT Instagram Graph API with Business account flow
  - CREATE Facebook Graph API integration for page management
  - ADD Twitter API v2 for post management
  - SETUP OAuth 2.0 flows with secure token storage

Task 8 - Social Media Management UI:
CREATE src/components/social/*:
  - IMPLEMENT InstagramFeed with Graph API data
  - CREATE SocialPostForm with multi-platform support
  - ADD post scheduling and calendar view
  - IMPLEMENT social media analytics dashboard

Phase 4: Configuration System (Week 7-8)

Task 9 - Configuration-Driven Architecture:
CREATE src/config/* and configuration system:
  - IMPLEMENT JSON-based page configuration loader
  - CREATE component registry and dynamic renderer
  - ADD theme system with CSS custom properties
  - IMPLEMENT feature flags via environment variables

Task 10 - Dynamic Page System:
CREATE src/components/layout/* and page rendering:
  - IMPLEMENT PageRenderer with recursive component rendering
  - CREATE FormBuilder for dynamic form generation
  - ADD template system with version control
  - IMPLEMENT white-label customization options

Phase 5: Advanced Features & Optimization (Week 9-10)

Task 11 - Performance Optimization:
OPTIMIZE entire application:
  - IMPLEMENT React.memo and useMemo for performance
  - ADD code splitting with React.lazy for route-level
  - OPTIMIZE images with WebP format and lazy loading
  - IMPLEMENT service worker for offline functionality

Task 12 - Security & Testing:
SECURE and test application:
  - IMPLEMENT comprehensive error boundaries
  - ADD input validation and XSS protection
  - CREATE test suite with 90%+ coverage
  - IMPLEMENT security audit with automated scanning

Task 13 - Documentation & Deployment:
DOCUMENT and prepare for deployment:
  - CREATE deployment guides and configuration documentation
  - IMPLEMENT automated deployment scripts
  - ADD monitoring and analytics setup
  - CREATE client onboarding templates
```

### Implementation Pseudocode with Critical Details

```typescript
// Task 2: WooCommerce API Integration
// PATTERN: Follow OAuth 1.0a with proper signature generation
class WooCommerceAPI {
  private baseURL: string;
  private consumerKey: string;
  private consumerSecret: string;
  
  constructor(config: WooCommerceConfig) {
    // CRITICAL: Never expose keys in frontend, use backend proxy
    this.baseURL = config.baseURL;
    // Keys should come from secure backend endpoint
  }
  
  async getProducts(params: ProductParams): Promise<Product[]> {
    // PATTERN: Implement caching to respect rate limits
    const cacheKey = `products_${JSON.stringify(params)}`;
    const cached = await this.cache.get(cacheKey);
    if (cached && !this.isExpired(cached)) return cached.data;
    
    // CRITICAL: Use exponential backoff for rate limit handling
    const response = await this.requestWithRetry('/products', params);
    await this.cache.set(cacheKey, response, { ttl: 300000 }); // 5 min cache
    return response.data;
  }
}

// Task 5: Shopping Cart State Management
// PATTERN: Optimistic updates with rollback on failure
const useCartStore = create<CartState>((set, get) => ({
  items: [],
  addItem: async (product: Product, quantity: number) => {
    // PATTERN: Optimistic update first
    const optimisticItem = { productId: product.id, quantity, addedAt: new Date() };
    set(state => ({ items: [...state.items, optimisticItem] }));
    
    try {
      // PATTERN: Sync with backend
      await api.cart.addItem(product.id, quantity);
      // PATTERN: Persist to localStorage with IndexedDB fallback
      await persistCart(get().items);
    } catch (error) {
      // PATTERN: Rollback on failure
      set(state => ({ items: state.items.filter(item => item !== optimisticItem) }));
      throw error;
    }
  }
}));

// Task 6: Payment Processing with Security
// PATTERN: Never store payment data in frontend state
const PaymentForm: React.FC = () => {
  const stripe = useStripe();
  const elements = useElements();
  
  const handlePayment = async (orderData: OrderData) => {
    // CRITICAL: Use Stripe Payment Element for PCI compliance
    const { error, paymentIntent } = await stripe.confirmPayment({
      elements,
      confirmParams: {
        return_url: `${window.location.origin}/payment/success`,
      },
    });
    
    if (error) {
      // PATTERN: Secure error handling without exposing sensitive data
      logSecureError(error, { orderId: orderData.id });
      throw new Error('Payment processing failed');
    }
    
    return paymentIntent;
  };
};

// Task 7: Social Media OAuth Flow
// PATTERN: Secure OAuth with PKCE for public clients
const useSocialAuth = (platform: SocialPlatform) => {
  const initializeOAuth = async () => {
    // CRITICAL: Generate PKCE challenge for security
    const codeVerifier = generateCodeVerifier();
    const codeChallenge = await generateCodeChallenge(codeVerifier);
    
    const authURL = buildAuthURL({
      platform,
      codeChallenge,
      state: generateRandomState(), // CSRF protection
      redirectUri: `${window.location.origin}/auth/callback/${platform}`
    });
    
    // PATTERN: Store verifier securely for callback
    sessionStorage.setItem(`${platform}_code_verifier`, codeVerifier);
    window.location.href = authURL;
  };
};

// Task 9: Configuration-Driven Component Rendering
// PATTERN: Type-safe dynamic component rendering with error boundaries
const ComponentRenderer: React.FC<{ config: ComponentConfig }> = ({ config }) => {
  const Component = componentRegistry[config.type];
  
  if (!Component) {
    console.error(`Component type "${config.type}" not found in registry`);
    return <ErrorFallback componentType={config.type} />;
  }
  
  // PATTERN: Recursive rendering for nested components
  const children = config.children?.map(childConfig => (
    <ComponentRenderer key={childConfig.id} config={childConfig} />
  ));
  
  return (
    <ErrorBoundary fallback={<ErrorFallback />}>
      <Component {...config.props}>
        {children}
      </Component>
    </ErrorBoundary>
  );
};
```

### Integration Points

```yaml
ENVIRONMENT CONFIGURATION:
  - file: .env.production
  - pattern: |
      # WordPress/WooCommerce
      VITE_WORDPRESS_URL=https://client-site.com
      VITE_WOOCOMMERCE_CONSUMER_KEY=ck_xxxxx
      VITE_WOOCOMMERCE_CONSUMER_SECRET=cs_xxxxx
      
      # Payment Gateways
      VITE_STRIPE_PUBLISHABLE_KEY=pk_live_xxxxx
      VITE_PAYPAL_CLIENT_ID=AxxxxX
      
      # Social Media
      VITE_FACEBOOK_APP_ID=1234567890
      VITE_INSTAGRAM_APP_ID=1234567890
      
      # Feature Flags
      VITE_ENABLE_ECOMMERCE=true
      VITE_ENABLE_SOCIAL_MEDIA=true
      VITE_PAYMENT_GATEWAYS=stripe,paypal,woocommerce
      VITE_SOCIAL_PLATFORMS=instagram,facebook,twitter

PACKAGE DEPENDENCIES:
  - add: "@stripe/react-stripe-js @stripe/stripe-js"
  - add: "@paypal/react-paypal-js"
  - add: "@woocommerce/woocommerce-rest-api"
  - add: "zustand react-query"
  - add: "zod react-hook-form"
  - add: "workbox-webpack-plugin"

CONFIGURATION FILES:
  - create: src/config/pages.json
  - create: src/config/themes.json
  - create: src/config/features.json
  - pattern: JSON schema validation with zod
```

## Validation Loop

### Level 1: Syntax & Style

```bash
# TypeScript and linting validation
npm run type-check          # TypeScript compilation check
npm run lint                # ESLint + Prettier
npm run lint:fix            # Auto-fix linting issues

# Expected: No errors. If errors, READ and fix before proceeding.
```

### Level 2: Unit Tests for Each Component

```bash
# Component and hook testing
npm run test                # Vitest test runner
npm run test:coverage       # Generate coverage report
npm run test:ui            # Interactive test UI

# Expected: 90%+ coverage, all tests passing
# Test shopping cart operations, payment flows, API integrations
```

### Level 3: Integration Testing

```bash
# E2E testing with real APIs (using test/sandbox accounts)
npm run test:e2e           # Playwright end-to-end tests

# Test critical user journeys:
# 1. Product browsing and search
# 2. Add to cart and checkout flow
# 3. Payment processing (test mode)
# 4. Social media authentication
# 5. Dynamic page configuration

# Expected: All user journeys complete successfully
```

### Level 4: Performance & Security Validation

```bash
# Performance testing
npm run build              # Production build
npm run preview            # Preview production build
npm run lighthouse         # Lighthouse performance audit

# Security testing
npm audit                  # Check for vulnerabilities
npm run security:scan      # Custom security scan script

# Load testing for large product catalogs
npm run test:load          # Load test with 10,000+ products

# Expected: 
# - Lighthouse score >90
# - No high/critical vulnerabilities
# - <3 second load times with 10,000 products
# - Payment processing security validated
```

### Level 5: Configuration & Deployment Validation

```bash
# Configuration validation
npm run validate:config    # Validate JSON configurations
npm run test:themes       # Test theme switching

# Deployment testing
npm run build:staging     # Build for staging environment
npm run deploy:staging    # Deploy to staging
npm run test:staging      # Run tests against staging

# Client setup validation
./scripts/setup-client.sh --client test-client
npm run test:client-config

# Expected:
# - All configurations valid
# - Successful deployment
# - Client setup completes in <2 hours
```

## Final Validation Checklist

- [ ] All TypeScript errors resolved: `npm run type-check`
- [ ] No linting errors: `npm run lint`
- [ ] 90%+ test coverage: `npm run test:coverage`
- [ ] E2E tests passing: `npm run test:e2e`
- [ ] Lighthouse performance >90: `npm run lighthouse`
- [ ] No security vulnerabilities: `npm audit`
- [ ] Load testing with 10,000+ products: `npm run test:load`
- [ ] Payment processing in test mode: Manual verification
- [ ] Social media OAuth flows working: Manual verification
- [ ] Configuration-driven pages rendering: Manual verification
- [ ] Theme switching functional: Manual verification
- [ ] Client deployment script working: `./scripts/setup-client.sh`
- [ ] Documentation complete and accurate
- [ ] Production environment variables configured
- [ ] Monitoring and analytics setup

---

## Anti-Patterns to Avoid

- ❌ Don't store payment credentials or API keys in frontend code
- ❌ Don't ignore rate limiting for external APIs (especially WooCommerce 200/hour)
- ❌ Don't render Stripe Payment Element conditionally (causes initialization issues)
- ❌ Don't use Instagram Basic Display API (deprecated Dec 4, 2024)
- ❌ Don't skip OAuth PKCE flow for public client applications
- ❌ Don't implement shopping cart without persistence strategy
- ❌ Don't create themes without performance testing for large catalogs
- ❌ Don't skip error boundaries for dynamic component rendering
- ❌ Don't hardcode configuration values that should be environment-driven
- ❌ Don't deploy without comprehensive security testing

## Quality Score: 9/10

**Confidence Level for One-Pass Implementation Success**: This PRP provides comprehensive context including:
- ✅ Complete technical architecture with existing patterns
- ✅ Detailed API integration guides with 2024 updates
- ✅ Step-by-step implementation tasks with critical details
- ✅ Security best practices and compliance requirements
- ✅ Performance optimization strategies for scale
- ✅ Comprehensive validation gates at multiple levels
- ✅ Real-world gotchas and library-specific considerations
- ✅ Configuration-driven approach for rapid client deployment

The extensive research and context provided should enable successful implementation in a single pass with Claude Code.