# Scrunchy - Complete Project Structure

This document provides a comprehensive overview of the entire Scrunchy codebase, including all repositories, their structure, and how they interact.

---

## 🌐 Repository Overview

Scrunchy is organized as a **multi-repository project** with four main components:

### 1. Smart Contracts (scrunchy-contract)
**Repository**: https://github.com/hallelx2/scrunchy-contract  
**Tech Stack**: Rust, Anchor Framework, Solana  
**Purpose**: On-chain programs for asset registry, marketplace, and access control

### 2. Backend API (scrunchy-backend)
**Repository**: https://github.com/hallelx2/scrunchy-backend  
**Tech Stack**: NestJS, TypeScript, Prisma, PostgreSQL, Redis  
**Purpose**: RESTful API, event indexing, caching, and business logic

### 3. Frontend (scrunchy-frontend)
**Repository**: https://github.com/hallelx2/scrunchy-frontend  
**Tech Stack**: Next.js 14, React, TypeScript, Tailwind CSS, shadcn/ui  
**Purpose**: User-facing marketplace and developer portal

### 4. CLI Tool (scrunchy-cli)
**Repository**: https://github.com/hallelx2/scrunchy-cli  
**Tech Stack**: Python, Click  
**Purpose**: Universal CLI for game developers to integrate Scrunchy

---

## 📂 Detailed Structure

### Smart Contracts (scrunchy-contract)

```
scrunchy-contract/
├── programs/                           # Anchor programs
│   ├── asset-registry/                # Asset Registry Program
│   │   ├── src/
│   │   │   ├── lib.rs                # Program entry point
│   │   │   ├── instructions/         # Program instructions
│   │   │   │   ├── initialize_registry.rs
│   │   │   │   ├── register_game.rs
│   │   │   │   ├── create_asset.rs
│   │   │   │   ├── update_asset.rs
│   │   │   │   └── transfer_asset.rs
│   │   │   ├── state/                # Account structures
│   │   │   │   ├── asset_registry.rs
│   │   │   │   ├── game_account.rs
│   │   │   │   └── asset_account.rs
│   │   │   ├── error.rs              # Custom errors
│   │   │   └── events.rs             # Program events
│   │   └── Cargo.toml
│   │
│   ├── marketplace/                   # Marketplace Program
│   │   ├── src/
│   │   │   ├── lib.rs                # Program entry point
│   │   │   ├── instructions/         # Program instructions
│   │   │   │   ├── initialize_marketplace.rs
│   │   │   │   ├── create_listing.rs
│   │   │   │   ├── update_listing.rs
│   │   │   │   ├── rent_asset.rs
│   │   │   │   ├── complete_rental.rs
│   │   │   │   └── extend_rental.rs
│   │   │   ├── state/                # Account structures
│   │   │   │   ├── marketplace_config.rs
│   │   │   │   ├── listing.rs
│   │   │   │   ├── rental.rs
│   │   │   │   └── escrow.rs
│   │   │   ├── error.rs              # Custom errors
│   │   │   └── events.rs             # Program events
│   │   └── Cargo.toml
│   │
│   └── access-control/                # Access Control Program
│       ├── src/
│       │   ├── lib.rs                # Program entry point
│       │   ├── instructions/         # Program instructions
│       │   │   ├── initialize_access_control.rs
│       │   │   ├── verify_ownership.rs
│       │   │   ├── verify_rental.rs
│       │   │   └── record_usage.rs
│       │   ├── state/                # Account structures
│       │   │   ├── access_registry.rs
│       │   │   └── access_record.rs
│       │   ├── error.rs              # Custom errors
│       │   └── events.rs             # Program events
│       └── Cargo.toml
│
├── tests/                             # Integration tests
│   ├── asset-registry.ts             # Asset Registry tests
│   ├── marketplace.ts                # Marketplace tests
│   └── access-control.ts             # Access Control tests
│
├── scripts/                           # Deployment scripts
│   ├── deploy-individual.sh          # Deploy programs individually
│   ├── copy-idl.sh                   # Copy IDL files
│   └── generate-keypairs.sh          # Generate program keypairs
│
├── docs/                              # Program documentation
│   ├── DEPLOY_TO_DEVNET.md          # Deployment guide
│   ├── DEPLOYMENT_COSTS.md          # Cost calculations
│   ├── DEPLOYMENT_ERROR_FIX.md      # Troubleshooting
│   └── AUTO_AIRDROP_GUIDE.md        # Airdrop guide
│
├── target/                            # Build artifacts
│   ├── deploy/                       # Compiled programs
│   ├── idl/                          # Generated IDL files
│   └── types/                        # TypeScript types
│
├── Anchor.toml                        # Anchor configuration
├── Cargo.toml                         # Rust workspace config
├── package.json                       # Node.js dependencies
└── README.md                          # Repository README
```

**Key Files:**
- `Anchor.toml` - Program IDs, cluster config, test settings
- `programs/*/src/lib.rs` - Program entry points with instruction handlers
- `target/idl/*.json` - Generated IDL files for client integration

---

### Backend API (scrunchy-backend)

```
scrunchy-backend/
├── src/                               # Source code
│   ├── main.ts                       # Application entry point
│   ├── app.module.ts                 # Root module
│   │
│   ├── auth/                         # Authentication module
│   │   ├── auth.controller.ts       # Auth endpoints
│   │   ├── auth.service.ts          # Auth business logic
│   │   ├── auth.module.ts           # Auth module definition
│   │   ├── dto/                     # Data transfer objects
│   │   │   ├── nonce.dto.ts
│   │   │   ├── verify-signature.dto.ts
│   │   │   └── auth-response.dto.ts
│   │   ├── guards/                  # Auth guards
│   │   │   ├── jwt-auth.guard.ts
│   │   │   └── api-key.guard.ts
│   │   └── strategies/              # Passport strategies
│   │       ├── jwt.strategy.ts
│   │       └── api-key.strategy.ts
│   │
│   ├── users/                        # User management module
│   │   ├── users.controller.ts
│   │   ├── users.service.ts
│   │   ├── users.module.ts
│   │   └── dto/
│   │       ├── create-user.dto.ts
│   │       └── update-user.dto.ts
│   │
│   ├── assets/                       # Asset management module
│   │   ├── assets.controller.ts     # Asset endpoints
│   │   ├── assets.service.ts        # Asset business logic
│   │   ├── assets.module.ts
│   │   └── dto/
│   │       ├── create-asset.dto.ts
│   │       ├── update-asset.dto.ts
│   │       ├── asset-filter.dto.ts
│   │       └── asset-response.dto.ts
│   │
│   ├── marketplace/                  # Marketplace module
│   │   ├── marketplace.controller.ts
│   │   ├── marketplace.service.ts
│   │   ├── marketplace.module.ts
│   │   └── dto/
│   │       ├── create-listing.dto.ts
│   │       ├── update-listing.dto.ts
│   │       ├── create-rental.dto.ts
│   │       └── complete-rental.dto.ts
│   │
│   ├── access-control/               # Access control module
│   │   ├── access-control.controller.ts
│   │   ├── access-control.service.ts
│   │   ├── access-control.module.ts
│   │   └── dto/
│   │       ├── verify-access.dto.ts
│   │       └── batch-verify.dto.ts
│   │
│   ├── games/                        # Game management module
│   │   ├── games.controller.ts
│   │   ├── games.service.ts
│   │   ├── games.module.ts
│   │   └── dto/
│   │       ├── register-game.dto.ts
│   │       ├── create-api-key.dto.ts
│   │       ├── game-config.dto.ts
│   │       └── config-history.dto.ts
│   │
│   ├── sdk/                          # SDK endpoints module
│   │   ├── sdk.controller.ts
│   │   ├── sdk.service.ts
│   │   ├── sdk.module.ts
│   │   └── dto/
│   │       ├── check-access.dto.ts
│   │       ├── player-assets.dto.ts
│   │       └── batch-assets.dto.ts
│   │
│   ├── marketplace-packages/         # Developer marketplace module
│   │   ├── marketplace-packages.controller.ts
│   │   ├── marketplace-packages.service.ts
│   │   ├── marketplace-packages.module.ts
│   │   └── dto/
│   │       ├── create-package.dto.ts
│   │       ├── install-package.dto.ts
│   │       └── package-filter.dto.ts
│   │
│   ├── indexer/                      # Blockchain event indexer
│   │   ├── indexer.service.ts       # Event listener
│   │   ├── indexer.module.ts
│   │   └── handlers/                # Event handlers
│   │       ├── asset-created.handler.ts
│   │       ├── listing-created.handler.ts
│   │       └── rental-completed.handler.ts
│   │
│   ├── jobs/                         # Background jobs
│   │   ├── jobs.service.ts
│   │   ├── jobs.module.ts
│   │   └── tasks/
│   │       ├── rental-expiry.task.ts
│   │       ├── expiring-rental-warning.task.ts
│   │       └── cache-warmer.task.ts
│   │
│   ├── prisma/                       # Database service
│   │   ├── prisma.service.ts
│   │   └── prisma.module.ts
│   │
│   ├── redis/                        # Cache service
│   │   ├── redis.service.ts
│   │   └── redis.module.ts
│   │
│   ├── solana/                       # Blockchain integration
│   │   ├── solana.service.ts        # Solana RPC client
│   │   ├── solana.module.ts
│   │   └── clients/                 # Anchor program clients
│   │       ├── asset-registry.client.ts
│   │       ├── marketplace.client.ts
│   │       └── access-control.client.ts
│   │
│   ├── common/                       # Shared utilities
│   │   ├── filters/                 # Exception filters
│   │   │   ├── http-exception.filter.ts
│   │   │   └── all-exceptions.filter.ts
│   │   ├── middleware/              # Middleware
│   │   │   ├── rate-limit.middleware.ts
│   │   │   └── logger.middleware.ts
│   │   ├── guards/                  # Guards
│   │   │   └── roles.guard.ts
│   │   ├── decorators/              # Custom decorators
│   │   │   ├── current-user.decorator.ts
│   │   │   └── api-key.decorator.ts
│   │   ├── interceptors/            # Interceptors
│   │   │   ├── transform.interceptor.ts
│   │   │   └── cache.interceptor.ts
│   │   └── health/                  # Health checks
│   │       ├── health.controller.ts
│   │       └── health.service.ts
│   │
│   └── idl/                          # Anchor IDL files
│       ├── asset_registry.json
│       ├── marketplace.json
│       └── access_control.json
│
├── prisma/                            # Database schema
│   ├── schema.prisma                 # Prisma schema definition
│   ├── migrations/                   # Database migrations
│   └── seed.ts                       # Database seeding
│
├── scripts/                           # Utility scripts
│   ├── copy-idl.sh                   # Copy IDL files from contract repo
│   ├── generate-idl-clients.ts       # Generate Anchor clients
│   ├── test-db-connection.sh         # Test database connection
│   └── check-db-connection.sh        # Check database status
│
├── test/                              # Tests
│   ├── app.e2e-spec.ts              # E2E tests
│   └── jest-e2e.json                # Jest E2E config
│
├── docs/                              # Documentation
│   ├── QUICK_START.md
│   ├── FINAL_IMPLEMENTATION_SUMMARY.md
│   └── IMPLEMENTATION_STATUS.md
│
├── dist/                              # Compiled output
├── node_modules/                      # Dependencies
│
├── .env.example                       # Environment variables template
├── .env                              # Environment variables (gitignored)
├── nest-cli.json                     # NestJS CLI config
├── tsconfig.json                     # TypeScript config
├── tsconfig.build.json               # Build TypeScript config
├── package.json                      # Node.js dependencies
├── pnpm-lock.yaml                    # Lock file
├── Dockerfile                        # Docker configuration
└── README.md                         # Repository README
```

**Key Files:**
- `src/main.ts` - Application bootstrap with Swagger setup
- `prisma/schema.prisma` - Complete database schema
- `src/idl/*.json` - Anchor IDL files for on-chain interaction
- `.env` - Environment configuration (database, Redis, Solana RPC)

---

### Frontend (scrunchy-frontend)

```
scrunchy-frontend/
├── app/                               # Next.js 14 App Router
│   ├── layout.tsx                    # Root layout
│   ├── page.tsx                      # Home page
│   ├── providers.tsx                 # Context providers
│   │
│   ├── (marketing)/                  # Marketing pages group
│   │   ├── layout.tsx               # Marketing layout
│   │   ├── page.tsx                 # Landing page
│   │   ├── about/                   # About page
│   │   ├── features/                # Features page
│   │   └── pricing/                 # Pricing page
│   │
│   ├── marketplace/                  # Marketplace pages
│   │   ├── page.tsx                 # Browse marketplace
│   │   ├── [id]/                    # Asset detail page
│   │   │   └── page.tsx
│   │   └── layout.tsx
│   │
│   ├── assets/                       # Asset management pages
│   │   ├── create/                  # Create asset wizard
│   │   │   └── page.tsx
│   │   ├── [id]/                    # Asset detail
│   │   │   ├── page.tsx
│   │   │   └── edit/                # Edit asset
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   │
│   ├── dashboard/                    # User dashboard
│   │   ├── page.tsx                 # Dashboard home
│   │   ├── rentals/                 # Active rentals
│   │   │   └── page.tsx
│   │   ├── earnings/                # Earnings tracking
│   │   │   └── page.tsx
│   │   ├── my-assets/               # Owned assets
│   │   │   └── page.tsx
│   │   └── layout.tsx
│   │
│   ├── developer/                    # Developer portal
│   │   ├── page.tsx                 # Developer home
│   │   ├── games/                   # Game management
│   │   │   ├── page.tsx
│   │   │   ├── [id]/                # Game details
│   │   │   │   ├── page.tsx
│   │   │   │   ├── api-keys/        # API key management
│   │   │   │   │   └── page.tsx
│   │   │   │   ├── config/          # Game configuration
│   │   │   │   │   └── page.tsx
│   │   │   │   └── analytics/       # Game analytics
│   │   │   │       └── page.tsx
│   │   │   └── register/            # Register new game
│   │   │       └── page.tsx
│   │   ├── components/              # Component marketplace
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   │
│   ├── profile/                      # User profile
│   │   ├── page.tsx                 # Profile view
│   │   ├── edit/                    # Edit profile
│   │   │   └── page.tsx
│   │   └── settings/                # User settings
│   │       └── page.tsx
│   │
│   └── api/                          # API routes (if needed)
│       └── health/
│           └── route.ts
│
├── components/                        # Reusable components
│   ├── ui/                           # shadcn/ui components
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── dialog.tsx
│   │   ├── input.tsx
│   │   ├── select.tsx
│   │   ├── tabs.tsx
│   │   ├── toast.tsx
│   │   └── ... (50+ components)
│   │
│   ├── layout/                       # Layout components
│   │   ├── header.tsx
│   │   ├── footer.tsx
│   │   ├── sidebar.tsx
│   │   └── navigation.tsx
│   │
│   ├── marketplace/                  # Marketplace components
│   │   ├── asset-card.tsx
│   │   ├── asset-grid.tsx
│   │   ├── asset-filters.tsx
│   │   ├── rental-modal.tsx
│   │   └── listing-form.tsx
│   │
│   ├── assets/                       # Asset components
│   │   ├── asset-detail.tsx
│   │   ├── asset-stats.tsx
│   │   ├── asset-history.tsx
│   │   └── create-asset-wizard.tsx
│   │
│   ├── dashboard/                    # Dashboard components
│   │   ├── stats-card.tsx
│   │   ├── earnings-chart.tsx
│   │   ├── rental-list.tsx
│   │   └── activity-feed.tsx
│   │
│   ├── developer/                    # Developer components
│   │   ├── game-card.tsx
│   │   ├── api-key-list.tsx
│   │   ├── config-editor.tsx
│   │   └── analytics-dashboard.tsx
│   │
│   ├── wallet/                       # Wallet components
│   │   ├── wallet-button.tsx
│   │   ├── wallet-modal.tsx
│   │   └── wallet-provider.tsx
│   │
│   └── shared/                       # Shared components
│       ├── loading-spinner.tsx
│       ├── error-boundary.tsx
│       ├── empty-state.tsx
│       └── pagination.tsx
│
├── lib/                               # Utilities and helpers
│   ├── api.ts                        # API client
│   ├── utils.ts                      # Utility functions
│   ├── constants.ts                  # Constants
│   ├── validations.ts                # Validation schemas (Zod)
│   ├── solana.ts                     # Solana utilities
│   └── wallet-adapter.ts             # Wallet adapter config
│
├── stores/                            # State management (Zustand)
│   ├── auth-store.ts                 # Auth state
│   ├── wallet-store.ts               # Wallet state
│   ├── marketplace-store.ts          # Marketplace state
│   └── ui-store.ts                   # UI state
│
├── hooks/                             # Custom React hooks
│   ├── use-auth.ts                   # Auth hook
│   ├── use-wallet.ts                 # Wallet hook
│   ├── use-assets.ts                 # Assets hook
│   ├── use-marketplace.ts            # Marketplace hook
│   └── use-toast.ts                  # Toast notifications
│
├── types/                             # TypeScript types
│   ├── api.ts                        # API types
│   ├── asset.ts                      # Asset types
│   ├── marketplace.ts                # Marketplace types
│   └── user.ts                       # User types
│
├── styles/                            # Global styles
│   └── globals.css                   # Global CSS with Tailwind
│
├── public/                            # Static assets
│   ├── images/
│   ├── icons/
│   └── fonts/
│
├── docs/                              # Documentation
│   ├── API_INTEGRATION_COMPLETE.md
│   ├── API_INTEGRATION_STATUS.md
│   ├── IMPLEMENTATION_SUMMARY.md
│   └── PAGES_STATUS.md
│
├── node_modules/                      # Dependencies
├── .next/                            # Next.js build output
│
├── .env.local                        # Local environment variables
├── .env.example                      # Environment template
├── next.config.ts                    # Next.js configuration
├── tailwind.config.ts                # Tailwind CSS config
├── tsconfig.json                     # TypeScript config
├── package.json                      # Node.js dependencies
├── components.json                   # shadcn/ui config
└── README.md                         # Repository README
```

**Key Files:**
- `app/layout.tsx` - Root layout with providers
- `lib/api.ts` - API client for backend communication
- `stores/*.ts` - Zustand stores for state management
- `components/ui/*` - shadcn/ui component library

---

### CLI Tool (scrunchy-cli)

```
scrunchy-cli/
├── scrunchy/                          # Main package
│   ├── __init__.py                   # Package initialization
│   ├── __main__.py                   # CLI entry point
│   │
│   ├── commands/                     # CLI commands
│   │   ├── __init__.py
│   │   ├── auth.py                  # Authentication commands
│   │   ├── init.py                  # Project initialization
│   │   ├── component.py             # Component management
│   │   ├── project.py               # Project management
│   │   ├── game.py                  # Game management
│   │   └── verify.py                # Asset verification
│   │
│   ├── utils/                        # Utilities
│   │   ├── __init__.py
│   │   ├── api_client.py            # API client
│   │   ├── config.py                # Configuration management
│   │   ├── project_detector.py      # Project type detection
│   │   ├── component_installer.py   # Component installation
│   │   ├── wallet.py                # Wallet utilities
│   │   └── logger.py                # Logging utilities
│   │
│   ├── templates/                    # Component templates
│   │   ├── unity/                   # Unity templates
│   │   │   ├── wallet-connector/
│   │   │   ├── asset-verifier/
│   │   │   └── rental-manager/
│   │   ├── pygame/                  # Pygame templates
│   │   │   ├── wallet-connector/
│   │   │   ├── asset-verifier/
│   │   │   └── rental-manager/
│   │   ├── web/                     # Web templates
│   │   │   ├── wallet-connector/
│   │   │   ├── asset-verifier/
│   │   │   └── rental-manager/
│   │   └── generic/                 # Generic templates
│   │       ├── wallet-connector/
│   │       ├── asset-verifier/
│   │       └── rental-manager/
│   │
│   └── config/                       # Configuration files
│       ├── components.json          # Available components
│       └── defaults.json            # Default settings
│
├── tests/                             # Tests
│   ├── test_auth.py
│   ├── test_init.py
│   ├── test_component.py
│   └── test_project_detector.py
│
├── docs/                              # Documentation
│   ├── USER_FLOW.md                 # User flow guide
│   └── COMPONENT_INTEGRATION.md     # Component integration guide
│
├── main.py                            # CLI entry point
├── pyproject.toml                     # Python package config
├── setup.py                          # Setup script
├── requirements.txt                  # Python dependencies
└── README.md                         # Repository README
```

**Key Files:**
- `main.py` - CLI entry point with Click commands
- `scrunchy/utils/project_detector.py` - Auto-detect project structure
- `scrunchy/utils/component_installer.py` - Install components
- `scrunchy/templates/` - Component templates for different platforms

---

## 🔄 Component Interactions

### Data Flow

```
┌─────────────────────────────────────────────────────────────┐
│                         User Layer                           │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Web App    │  │  Mobile App  │  │     Game     │      │
│  │   (Next.js)  │  │   (React N)  │  │  (+ CLI)     │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                      Backend Layer                           │
│  ┌──────────────────────────────────────────────────────┐   │
│  │              REST API (NestJS)                       │   │
│  │  • Authentication  • Asset Management  • Analytics   │   │
│  └──────────────────────────────────────────────────────┘   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  PostgreSQL  │  │    Redis     │  │   BullMQ     │      │
│  │  (Primary)   │  │   (Cache)    │  │   (Jobs)     │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│  ┌──────────────────────────────────────────────────────┐   │
│  │            Event Listener (Indexer)                  │   │
│  │  • Syncs blockchain events to database               │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                    Blockchain Layer                          │
│  ┌──────────────────────────────────────────────────────┐   │
│  │                  Solana Blockchain                   │   │
│  │  ┌────────────┐  ┌────────────┐  ┌────────────┐    │   │
│  │  │   Asset    │  │Marketplace │  │  Access    │    │   │
│  │  │  Registry  │  │  Program   │  │  Control   │    │   │
│  │  └────────────┘  └────────────┘  └────────────┘    │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Request Flow Examples

#### 1. Create Asset Flow
```
Frontend → Backend API → Smart Contract → Blockchain
   ↓           ↓              ↓              ↓
User fills   Validates    Mints NFT      Confirms
form         data         via CPI        transaction
   ↓           ↓              ↓              ↓
Submit    → Create asset → Asset Registry → Event emitted
             in database    Program          ↓
                ↓                         Indexer syncs
             Return asset ID              to database
```

#### 2. Rent Asset Flow
```
Frontend → Backend API → Smart Contract → Blockchain
   ↓           ↓              ↓              ↓
User selects Validates    Creates rental   Escrows
asset        listing      agreement        payment
   ↓           ↓              ↓              ↓
Confirm   → Create rental → Marketplace  → Event emitted
             in database    Program          ↓
                ↓                         Indexer syncs
             Return rental ID             to database
```

#### 3. Verify Access Flow (Game SDK)
```
Game (CLI) → Backend API → Cache/Database → Response
   ↓              ↓              ↓              ↓
Player uses   Check cache   If miss, query   Return
asset         first         blockchain       access status
   ↓              ↓              ↓              ↓
Apply bonus → Verify access → Access Control → Game applies
in game       via API         Program          bonus
```

---

## 🗄️ Database Schema

### Core Tables (Prisma)

```prisma
// User Management
model User {
  id              String    @id @default(uuid())
  walletAddress   String    @unique
  username        String?   @unique
  email           String?   @unique
  profileImage    String?
  bio             String?
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  assets          Asset[]
  listings        Listing[]
  rentals         Rental[]
  games           Game[]
  reviews         Review[]
}

// Asset Management
model Asset {
  id              String    @id @default(uuid())
  mint            String    @unique
  name            String
  description     String?
  imageUrl        String
  category        String
  rarity          String
  attributes      Json
  creatorId       String
  creator         User      @relation(fields: [creatorId], references: [id])
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  listings        Listing[]
  rentals         Rental[]
  reviews         Review[]
}

// Marketplace
model Listing {
  id              String    @id @default(uuid())
  assetId         String
  asset           Asset     @relation(fields: [assetId], references: [id])
  ownerId         String
  owner           User      @relation(fields: [ownerId], references: [id])
  listingType     String    // "RENT" | "SALE"
  pricePerHour    Float?
  pricePerDay     Float?
  salePrice       Float?
  isActive        Boolean   @default(true)
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  rentals         Rental[]
}

// Rentals
model Rental {
  id              String    @id @default(uuid())
  listingId       String
  listing         Listing   @relation(fields: [listingId], references: [id])
  renterId        String
  renter          User      @relation(fields: [renterId], references: [id])
  assetId         String
  asset           Asset     @relation(fields: [assetId], references: [id])
  startTime       DateTime
  endTime         DateTime
  totalPrice      Float
  deposit         Float?
  status          String    // "ACTIVE" | "COMPLETED" | "EXPIRED" | "OVERDUE"
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
}

// Game Management
model Game {
  id              String    @id @default(uuid())
  name            String
  description     String?
  developerId     String
  developer       User      @relation(fields: [developerId], references: [id])
  website         String?
  logo            String?
  isActive        Boolean   @default(true)
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  apiKeys         ApiKey[]
  configs         GameConfig[]
}

// API Keys
model ApiKey {
  id              String    @id @default(uuid())
  gameId          String
  game            Game      @relation(fields: [gameId], references: [id])
  name            String
  key             String    @unique
  isActive        Boolean   @default(true)
  rateLimit       Int       @default(1000)
  createdAt       DateTime  @default(now())
  expiresAt       DateTime?
}

// Game Configuration
model GameConfig {
  id              String    @id @default(uuid())
  gameId          String
  game            Game      @relation(fields: [gameId], references: [id])
  version         Int
  config          Json      // Visual mappings, attribute mappings, etc.
  isActive        Boolean   @default(true)
  createdAt       DateTime  @default(now())
}

// Reviews
model Review {
  id              String    @id @default(uuid())
  assetId         String
  asset           Asset     @relation(fields: [assetId], references: [id])
  reviewerId      String
  reviewer        User      @relation(fields: [reviewerId], references: [id])
  rating          Int
  comment         String?
  createdAt       DateTime  @default(now())
}
```

---

## 🔧 Configuration Files

### Environment Variables

#### Backend (.env)
```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/scrunchy"

# Redis
REDIS_URL="redis://localhost:6379"

# Solana
SOLANA_RPC_URL="https://api.devnet.solana.com"
SOLANA_NETWORK="devnet"

# Program IDs
ASSET_REGISTRY_PROGRAM_ID="AssetRegistry11111111111111111111111111111"
MARKETPLACE_PROGRAM_ID="Mktplce11111111111111111111111111111111111"
ACCESS_CONTROL_PROGRAM_ID="AccssCtrl111111111111111111111111111111"

# JWT
JWT_SECRET="your-secret-key"
JWT_EXPIRES_IN="7d"

# Platform
PLATFORM_TREASURY_WALLET="YourTreasuryWalletAddress"
PLATFORM_FEE_PERCENTAGE=2.5
```

#### Frontend (.env.local)
```env
# API
NEXT_PUBLIC_API_URL="http://localhost:3000/api"

# Solana
NEXT_PUBLIC_SOLANA_RPC_URL="https://api.devnet.solana.com"
NEXT_PUBLIC_SOLANA_NETWORK="devnet"

# Program IDs
NEXT_PUBLIC_ASSET_REGISTRY_PROGRAM_ID="AssetRegistry11111111111111111111111111111"
NEXT_PUBLIC_MARKETPLACE_PROGRAM_ID="Mktplce11111111111111111111111111111111111"
NEXT_PUBLIC_ACCESS_CONTROL_PROGRAM_ID="AccssCtrl111111111111111111111111111111"
```

---

## 📚 Additional Resources

### Documentation Files
- [`00_SCRUNCHY_PROJECT_OVERVIEW.md`](./00_SCRUNCHY_PROJECT_OVERVIEW.md) - Complete project overview
- [`01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md`](./01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md) - Smart contract design
- [`02_SCRUNCHY_BACKEND_ARCHITECTURE.md`](./02_SCRUNCHY_BACKEND_ARCHITECTURE.md) - Backend architecture
- [`03_SCRUNCHY_FRONTEND_ARCHITECTURE.md`](./03_SCRUNCHY_FRONTEND_ARCHITECTURE.md) - Frontend design
- [`04_SCRUNCHY_SDK_IMPLEMENTATION.md`](./04_SCRUNCHY_SDK_IMPLEMENTATION.md) - SDK documentation
- [`05_SCRUNCHY_INTEGRATION_EXAMPLES.md`](./05_SCRUNCHY_INTEGRATION_EXAMPLES.md) - Integration examples
- [`HACKATHON_README.md`](./HACKATHON_README.md) - Hackathon submission overview
- [`INSTALLATION.md`](./INSTALLATION.md) - Installation guide
- [`QUICK_START.md`](./QUICK_START.md) - Quick start guide

### API Documentation
- Swagger UI: `http://localhost:3000/api/docs` (when backend is running)

---

## 🎯 Quick Navigation

### For Developers
1. **Setting up locally**: See [`INSTALLATION.md`](./INSTALLATION.md)
2. **Understanding architecture**: Read component-specific docs
3. **API reference**: Visit Swagger UI at `/api/docs`
4. **Integration guide**: See [`05_SCRUNCHY_INTEGRATION_EXAMPLES.md`](./05_SCRUNCHY_INTEGRATION_EXAMPLES.md)

### For Hackathon Judges
1. **Project overview**: [`HACKATHON_README.md`](./HACKATHON_README.md)
2. **Technical details**: [`00_SCRUNCHY_PROJECT_OVERVIEW.md`](./00_SCRUNCHY_PROJECT_OVERVIEW.md)
3. **Repository links**: All repos listed in [`HACKATHON_README.md`](./HACKATHON_README.md)

---

**Last Updated**: December 15, 2025

**Maintained by**: hallelx2

**License**: MIT

