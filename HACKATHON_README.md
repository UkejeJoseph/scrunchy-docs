# Scrunchy - Solana Consumer Track Hackathon Submission

**A decentralized, rental-first game asset marketplace powered by Solana**

[![Solana](https://img.shields.io/badge/Solana-Blockchain-14F195?style=for-the-badge&logo=solana&logoColor=white)](https://solana.com)
[![Anchor](https://img.shields.io/badge/Anchor-Framework-9945FF?style=for-the-badge)](https://www.anchor-lang.com/)
[![Next.js](https://img.shields.io/badge/Next.js-Frontend-000000?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![NestJS](https://img.shields.io/badge/NestJS-Backend-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)](https://nestjs.com/)

---

## 🎯 Project Overview

**Scrunchy** is the world's first rental-first, cross-game asset marketplace built on Solana. We make blockchain gaming **useful, fun, and seamless** by enabling players to rent premium game items affordably, while asset owners earn passive income.

### Why Solana?

- ⚡ **Sub-second transactions** - Real-time gaming without waiting
- 💰 **Sub-cent costs** - Micro-rentals are economically viable ($0.00001 vs $5-50 on other chains)
- 🚀 **High throughput** - Scale to millions of concurrent users
- 🛠️ **Developer-friendly** - Rich ecosystem and excellent tooling

### The Problem We Solve

1. **For Players**: Premium game items cost $50-200+ to own, but you can rent them for $2-5
2. **For Game Developers**: Adding Web3 features takes weeks - we make it 5 minutes with our CLI
3. **For Asset Creators**: Create once, earn perpetually through rentals across multiple games
4. **For Asset Owners**: Generate passive income from unused game items

---

## 📦 Repository Structure

This project is organized as a **monorepo** with separate repositories for each component:

### 🔗 Remote Repositories

| Component | Repository | Description | Tech Stack |
|-----------|-----------|-------------|------------|
| **Smart Contracts** | [`scrunchy-contract`](https://github.com/hallelx2/scrunchy-contract) | Solana Anchor programs for asset registry, marketplace, and access control | Rust, Anchor, Solana |
| **Backend API** | [`scrunchy-backend`](https://github.com/hallelx2/scrunchy-backend) | Production-ready NestJS backend with event indexing and caching | NestJS, TypeScript, Prisma, PostgreSQL, Redis |
| **Frontend** | [`scrunchy-frontend`](https://github.com/hallelx2/scrunchy-frontend) | Beautiful marketplace UI with wallet integration | Next.js 14, React, Tailwind CSS, shadcn/ui |
| **CLI Tool** | [`scrunchy-cli`](https://github.com/hallelx2/scrunchy-cli) | Universal command-line tool for game integration | Python, Click |

### 📁 Local Project Structure

```
scrunchy/
├── docs/                          # 📚 Complete documentation
│   ├── 00_SCRUNCHY_PROJECT_OVERVIEW.md
│   ├── 01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md
│   ├── 02_SCRUNCHY_BACKEND_ARCHITECTURE.md
│   ├── 03_SCRUNCHY_FRONTEND_ARCHITECTURE.md
│   ├── 04_SCRUNCHY_SDK_IMPLEMENTATION.md
│   ├── 05_SCRUNCHY_INTEGRATION_EXAMPLES.md
│   ├── HACKATHON_PROJECT_OVERVIEW.md
│   ├── HACKATHON_README.md (this file)
│   ├── INSTALLATION.md
│   ├── QUICK_START.md
│   └── README.md
│
├── scrunchy-contract/             # 🔗 Smart Contracts (Solana/Anchor)
│   ├── programs/
│   │   ├── asset-registry/       # Asset creation & management
│   │   ├── marketplace/          # Rental marketplace & escrow
│   │   └── access-control/       # Fast ownership verification
│   ├── tests/                    # Integration tests
│   ├── Anchor.toml               # Anchor configuration
│   └── README.md
│
├── scrunchy-backend/              # 🔗 Backend API (NestJS)
│   ├── src/
│   │   ├── auth/                 # Wallet signature auth + JWT
│   │   ├── users/                # User management
│   │   ├── assets/               # Asset CRUD + on-chain sync
│   │   ├── marketplace/          # Listings + rentals
│   │   ├── access-control/       # Access verification
│   │   ├── games/                # Game registration + API keys
│   │   ├── sdk/                  # SDK endpoints
│   │   ├── marketplace-packages/ # Developer marketplace
│   │   ├── indexer/              # Blockchain event indexer
│   │   ├── jobs/                 # Background jobs
│   │   ├── prisma/               # Database service
│   │   ├── redis/                # Cache service
│   │   └── solana/               # Blockchain integration
│   ├── prisma/                   # Database schema
│   ├── package.json
│   └── README.md
│
├── scrunchy-frontend/             # 🔗 Frontend (Next.js)
│   ├── app/                      # Next.js 14 app router
│   │   ├── (marketing)/          # Landing pages
│   │   ├── marketplace/          # Browse & rent assets
│   │   ├── assets/               # Asset details & creation
│   │   ├── dashboard/            # User dashboard
│   │   ├── developer/            # Developer portal
│   │   └── profile/              # User profiles
│   ├── components/               # Reusable UI components
│   ├── lib/                      # Utilities & API client
│   ├── stores/                   # State management (Zustand)
│   ├── package.json
│   └── README.md
│
├── scrunchy-cli/                  # 🔗 CLI Tool (Python)
│   ├── scrunchy/                 # CLI package
│   │   ├── commands/             # CLI commands
│   │   ├── utils/                # Utilities
│   │   └── __init__.py
│   ├── main.py                   # Entry point
│   ├── pyproject.toml            # Python package config
│   └── README.md
│
├── scrunchy-example/              # 📂 Example integrations (empty - future)
└── scrunchy-docs/                 # 📂 Additional docs (empty - future)
```

---

## 🚀 Quick Start

### Prerequisites

- **Rust** 1.70+
- **Solana CLI** 1.18+
- **Anchor Framework** 0.29+
- **Node.js** 18+
- **PostgreSQL** 14+
- **Redis** 7+
- **Python** 3.8+ (for CLI)

### Installation Guide

See [`INSTALLATION.md`](./INSTALLATION.md) for detailed setup instructions.

### Quick Setup

```bash
# 1. Clone all repositories
git clone https://github.com/hallelx2/scrunchy-contract.git
git clone https://github.com/hallelx2/scrunchy-backend.git
git clone https://github.com/hallelx2/scrunchy-frontend.git
git clone https://github.com/hallelx2/scrunchy-cli.git

# 2. Setup Smart Contracts
cd scrunchy-contract
anchor build
anchor test
anchor deploy  # Deploy to devnet

# 3. Setup Backend
cd ../scrunchy-backend
npm install
cp .env.example .env  # Configure environment
npm run prisma:generate
npm run prisma:migrate
npm run start:dev  # Runs on http://localhost:3000

# 4. Setup Frontend
cd ../scrunchy-frontend
npm install
cp .env.example .env  # Configure environment
npm run dev  # Runs on http://localhost:3001

# 5. Setup CLI
cd ../scrunchy-cli
pip install -e .
scrunchy --version
```

See [`QUICK_START.md`](./QUICK_START.md) for a step-by-step guide.

---

## ✨ Key Features

### 🎮 For Players

- **Browse Marketplace** - Discover game assets with advanced filters
- **Rent Assets** - Affordable hourly/daily rentals instead of expensive purchases
- **Create Assets** - Mint game items as NFTs in minutes
- **Earn Passive Income** - List your assets for rent and earn automatically
- **Cross-Game Use** - Same asset works across multiple integrated games
- **Track Earnings** - Real-time dashboard with rental history and revenue

### 🛠️ For Game Developers

- **Scrunchy CLI** - Universal tool that works with any game engine
  ```bash
  scrunchy init                    # Auto-detect project structure
  scrunchy add wallet-connector    # Add wallet integration
  scrunchy add asset-verifier      # Add asset verification
  scrunchy add rental-manager      # Add rental management
  ```
- **Modular Components** - Install only what you need
- **Zero Configuration** - Works out of the box with sensible defaults
- **Backend Integration** - CLI handles authentication and API calls
- **Developer Dashboard** - Analytics, API keys, and revenue tracking

### 💎 For Asset Creators

- **Easy Creation** - 5-step wizard to mint game assets
- **Rental Marketplace** - List assets and earn from every rental
- **Cross-Game Compatibility** - One asset works across all integrated games
- **Analytics Dashboard** - Track usage, earnings, and popularity

---

## 🏗️ Technical Architecture

### Blockchain Layer (Solana)

**3 Anchor Programs:**

1. **Asset Registry** - Asset creation, metadata, and ownership
2. **Marketplace** - Rental listings, escrow, and payment distribution
3. **Access Control** - Fast ownership/rental verification for SDKs

**Key Features:**
- SPL Token NFTs with Metaplex metadata
- Rental escrow with automated payments
- Cross-program invocation (CPI) for complex flows
- PDA-based account derivation for security

### Backend Layer (NestJS)

**Core Services:**
- **Authentication** - Wallet signature verification + JWT
- **Asset Management** - CRUD operations with on-chain sync
- **Marketplace** - Listing and rental management
- **Access Control** - Fast verification for game SDKs
- **Game Management** - Registration, API keys, configuration
- **Event Indexer** - Blockchain event listener and database sync
- **Background Jobs** - Rental expiry monitoring, cache warming

**Infrastructure:**
- PostgreSQL for primary data storage
- Redis for caching and rate limiting
- Prisma ORM for type-safe database access
- Swagger API documentation

### Frontend Layer (Next.js)

**Pages:**
- **Landing Page** - Hero section, features, testimonials
- **Marketplace** - Browse, search, filter assets
- **Asset Details** - View stats, rental history, initiate rental
- **Asset Creation** - 5-step wizard to mint NFTs
- **Dashboard** - Track rentals, earnings, asset management
- **Developer Portal** - Game registration, API keys, analytics
- **Profile** - User settings, wallet management

**Tech Stack:**
- Next.js 14 with App Router
- React 18 with TypeScript
- Tailwind CSS + shadcn/ui components
- Solana wallet adapter
- Zustand for state management
- React Query for data fetching

### CLI Layer (Python)

**Features:**
- **Smart Detection** - Auto-detect Unity, Unreal, Pygame, Web projects
- **Modular Components** - Install wallet-connector, asset-verifier, etc.
- **Component Tracking** - Manage versions and dependencies
- **Backend Integration** - Authenticate and call APIs automatically
- **Universal Compatibility** - Works with any game engine

---

## 📊 Smart Contract Architecture

### Asset Registry Program

**Accounts:**
- `AssetRegistry` - Global registry state
- `GameAccount` - Registered game information
- `AssetAccount` - Individual asset metadata

**Instructions:**
- `initialize_registry` - Initialize global registry
- `register_game` - Register a game for integration
- `create_asset` - Mint asset as SPL Token NFT
- `update_asset` - Update asset metadata
- `transfer_asset` - Transfer ownership

### Marketplace Program

**Accounts:**
- `MarketplaceConfig` - Global marketplace configuration
- `Listing` - Asset listing for rent/sale
- `Rental` - Active rental agreement
- `Escrow` - Payment escrow account

**Instructions:**
- `initialize_marketplace` - Initialize marketplace
- `create_listing` - List asset for rent/sale
- `update_listing` - Update listing details
- `rent_asset` - Create rental agreement
- `complete_rental` - Complete rental and distribute funds
- `extend_rental` - Extend rental period

### Access Control Program

**Accounts:**
- `AccessRegistry` - Global access control state
- `AccessRecord` - Asset access record

**Instructions:**
- `initialize_access_control` - Initialize access control
- `verify_ownership` - Check asset ownership
- `verify_rental` - Check rental status
- `record_usage` - Track asset usage

---

## 🎯 API Endpoints

### Authentication
- `POST /api/auth/nonce` - Get nonce for wallet signature
- `POST /api/auth/verify` - Verify signature and get JWT
- `GET /api/auth/me` - Get current user

### Assets
- `GET /api/assets` - List assets (with filters)
- `GET /api/assets/:id` - Get asset details
- `POST /api/assets` - Create asset (on-chain)
- `POST /api/assets/sync/:mint` - Sync asset from blockchain

### Marketplace
- `GET /api/marketplace/listings` - List all listings
- `POST /api/marketplace/listings` - Create listing
- `PUT /api/marketplace/listings/:id` - Update listing
- `POST /api/marketplace/rentals` - Rent asset
- `POST /api/marketplace/rentals/:id/complete` - Complete rental

### Access Control
- `GET /api/access-control/verify/:mint/:wallet` - Verify access
- `POST /api/access-control/verify/batch` - Batch verify

### Games
- `POST /api/games` - Register game
- `POST /api/games/:id/api-keys` - Create API key
- `GET /api/games/:id/api-keys` - List API keys
- `GET /api/games/:id/config` - Get game configuration
- `PUT /api/games/:id/config` - Update configuration

### SDK (API Key Auth)
- `POST /api/sdk/check-access` - Check asset access
- `GET /api/sdk/players/:wallet/assets` - Get player's assets
- `GET /api/sdk/assets/:id` - Get asset (transformed)
- `POST /api/sdk/assets/batch` - Batch get assets

Full API documentation available at: `http://localhost:3000/api/docs` (Swagger UI)

---

## 🎨 UI/UX Highlights

- **Modern Design** - Glassmorphism effects, smooth animations
- **Responsive** - Mobile-first design that works on all devices
- **Accessible** - WCAG 2.1 AA compliant
- **Fast** - Optimized performance with code splitting and lazy loading
- **Intuitive** - No blockchain jargon, simple user flows
- **Beautiful** - Custom illustrations, gradients, and micro-interactions

---

## 🔐 Security Features

- **Wallet Signature Authentication** - Secure wallet-based login
- **JWT Tokens** - Stateless authentication with refresh tokens
- **API Key Management** - Per-game API keys with rate limiting
- **Rate Limiting** - Per-user and per-API-key limits
- **Input Validation** - Comprehensive validation with class-validator
- **SQL Injection Protection** - Prisma ORM with parameterized queries
- **XSS Protection** - Content Security Policy headers
- **CORS** - Configurable CORS policies
- **Escrow Pattern** - Secure payment handling on-chain

---

## 📈 Performance Optimizations

### Backend
- **Redis Caching** - Cache frequently accessed data
- **Database Indexing** - Optimized queries with proper indexes
- **Connection Pooling** - Efficient database connections
- **Batch Operations** - Reduce API calls with batch endpoints
- **Background Jobs** - Offload heavy tasks to background workers

### Frontend
- **Code Splitting** - Load only what's needed
- **Image Optimization** - Next.js Image component with WebP
- **Lazy Loading** - Defer loading of non-critical components
- **Memoization** - React.memo and useMemo for expensive computations
- **Virtual Scrolling** - Efficient rendering of large lists

### Smart Contracts
- **PDA Optimization** - Efficient account derivation
- **Compute Unit Optimization** - Minimize compute units per instruction
- **Account Compression** - Efficient data storage on-chain

---

## 🧪 Testing

### Smart Contracts
```bash
cd scrunchy-contract
anchor test  # Run all tests
```

### Backend
```bash
cd scrunchy-backend
npm test              # Unit tests
npm run test:e2e      # End-to-end tests
npm run test:cov      # Coverage report
```

### Frontend
```bash
cd scrunchy-frontend
npm test              # Unit tests
npm run test:e2e      # End-to-end tests
```

---

## 📝 Documentation

### Core Documentation
- [`00_SCRUNCHY_PROJECT_OVERVIEW.md`](./00_SCRUNCHY_PROJECT_OVERVIEW.md) - Complete project overview
- [`01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md`](./01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md) - Smart contract design
- [`02_SCRUNCHY_BACKEND_ARCHITECTURE.md`](./02_SCRUNCHY_BACKEND_ARCHITECTURE.md) - Backend architecture
- [`03_SCRUNCHY_FRONTEND_ARCHITECTURE.md`](./03_SCRUNCHY_FRONTEND_ARCHITECTURE.md) - Frontend design
- [`04_SCRUNCHY_SDK_IMPLEMENTATION.md`](./04_SCRUNCHY_SDK_IMPLEMENTATION.md) - SDK documentation
- [`05_SCRUNCHY_INTEGRATION_EXAMPLES.md`](./05_SCRUNCHY_INTEGRATION_EXAMPLES.md) - Integration examples

### Hackathon Documentation
- [`HACKATHON_PROJECT_OVERVIEW.md`](./HACKATHON_PROJECT_OVERVIEW.md) - Hackathon submission overview
- [`HACKATHON_README.md`](./HACKATHON_README.md) - This file
- [`INSTALLATION.md`](./INSTALLATION.md) - Installation guide
- [`QUICK_START.md`](./QUICK_START.md) - Quick start guide

### Component READMEs
- [`scrunchy-contract/README.md`](../scrunchy-contract/README.md) - Smart contracts
- [`scrunchy-backend/README.md`](../scrunchy-backend/README.md) - Backend API
- [`scrunchy-frontend/README.md`](../scrunchy-frontend/README.md) - Frontend
- [`scrunchy-cli/README.md`](../scrunchy-cli/README.md) - CLI tool

---

## 🎯 Hackathon Deliverables

### ✅ Completed Features

#### Smart Contracts (Solana/Anchor)
- ✅ Asset Registry Program - Asset creation and management
- ✅ Marketplace Program - Rental marketplace with escrow
- ✅ Access Control Program - Fast ownership verification
- ✅ Deployed to Solana Devnet
- ✅ Comprehensive test suite

#### Backend API (NestJS)
- ✅ Wallet signature authentication + JWT
- ✅ Asset CRUD operations with on-chain sync
- ✅ Marketplace listings and rental management
- ✅ Access control verification endpoints
- ✅ Game registration and API key management
- ✅ SDK endpoints for game integration
- ✅ Event indexer for blockchain sync
- ✅ Background jobs for rental monitoring
- ✅ Redis caching layer
- ✅ Rate limiting middleware
- ✅ Swagger API documentation

#### Frontend (Next.js)
- ✅ Landing page with hero section
- ✅ Marketplace browse and search
- ✅ Asset detail pages
- ✅ Asset creation wizard
- ✅ User dashboard
- ✅ Developer portal
- ✅ Wallet integration
- ✅ Responsive design
- ✅ Beautiful UI with animations

#### CLI Tool (Python)
- ✅ Project structure detection
- ✅ Component installation system
- ✅ Authentication via backend API
- ✅ Game registration
- ✅ Asset verification
- ✅ Component tracking

#### Documentation
- ✅ Complete architecture documentation
- ✅ API documentation (Swagger)
- ✅ Installation guides
- ✅ Integration examples
- ✅ Hackathon submission docs

---

## 🎬 Demo Flow

### 1. Landing Page
- Beautiful hero section with value proposition
- Feature highlights
- Call-to-action buttons

### 2. Browse Marketplace
- Search and filter assets
- View asset cards with images and stats
- Sort by price, rarity, popularity

### 3. Asset Details
- View detailed asset information
- See rental history and reviews
- Initiate rental with one click

### 4. Rental Flow
- Connect Solana wallet
- Select rental duration
- Confirm transaction
- Sub-second confirmation ⚡

### 5. Dashboard
- Track active rentals
- View earnings and revenue
- Manage owned assets

### 6. Create Asset
- 5-step wizard
- Upload image
- Set attributes
- Mint as NFT on Solana

### 7. Developer Portal
- Register game
- Create API keys
- View analytics
- Configure asset transformations

### 8. CLI Integration
```bash
# Install CLI
pip install scrunchy-cli

# Authenticate
scrunchy auth login

# Initialize project (auto-detects Unity/Pygame/Web/etc.)
scrunchy init

# Add components
scrunchy add wallet-connector
scrunchy add asset-verifier
scrunchy add rental-manager

# Verify asset access
scrunchy verify <wallet> <asset-id>
```

---

## 💡 Why Scrunchy Wins

### ✅ Consumer-Facing Application
- Primary users are gamers (consumers), not developers
- Beautiful, accessible web interface
- No technical knowledge required

### ✅ Makes Solana Useful
- **Real utility** - Assets used in actual games, not just collected
- **Economic value** - Rental marketplace creates new revenue streams
- **Cross-game utility** - Assets have lasting value beyond single games

### ✅ Makes Solana Fun
- **Gaming focus** - Built for the $200B+ gaming industry
- **Beautiful UX** - Modern, polished interface with smooth animations
- **Social elements** - Marketplace, ratings, activity feeds

### ✅ Makes Solana Seamless
- **Sub-second transactions** - Feel instant, no waiting
- **Sub-cent costs** - Users don't think about fees ($0.00001 vs $5-50)
- **No blockchain jargon** - Simple, intuitive language
- **Easy integration** - Developers use one CLI tool, 5-minute setup

### ✅ Strong Product Thinking
- **Clear problem** - Expensive assets, limited utility, no passive income
- **Clear audience** - Gamers, developers, creators
- **Clear solution** - Rental-first marketplace with cross-game interoperability
- **Clear value proposition** - Affordable access, passive income, easy integration

### ✅ Great UX & Accessibility
- **Modern design** - Glassmorphism, gradients, animations
- **Mobile-responsive** - Works on all devices
- **Accessible** - WCAG 2.1 AA compliant
- **Fast** - Optimized performance

### ✅ Technical Quality
- **Well-architected** - 3 Solana programs with clear separation of concerns
- **Production-ready** - Complete backend with caching, jobs, monitoring
- **Clean codebase** - TypeScript, proper error handling, comprehensive tests
- **Comprehensive docs** - Architecture, API, integration guides

### ✅ Smart Use of Solana's Strengths
- **Speed** - Sub-second transactions enable real-time gaming
- **Cost** - Sub-cent fees make micro-rentals economically viable
- **Scalability** - High throughput ready for mass adoption
- **Developer experience** - Anchor framework, rich ecosystem

### ✅ Creativity & Polish
- **Rental-first design** - Unique approach, not retrofitted
- **Cross-game interoperability** - Innovative asset mapping system
- **Universal CLI** - Works with any game engine or framework
- **Modular components** - Install only what you need
- **Complete MVP** - Fully functional, not just a prototype

---

## 📊 Success Metrics

### Hackathon Phase ✅
- ✅ Working smart contracts on devnet
- ✅ Functional web interface
- ✅ CLI tool with component system
- ✅ Backend API with event indexing
- ✅ Complete documentation
- ✅ Demo video (2-4 minutes)

### Post-Hackathon (Months 1-3)
- 🎯 5 games integrated
- 🎯 100 assets created
- 🎯 50 active users
- 🎯 500 rental transactions

### Growth Phase (Months 4-6)
- 🚀 20 games integrated
- 🚀 1,000 assets created
- 🚀 500 active users
- 🚀 5,000 rental transactions

### Scale Phase (Months 7-12)
- 🚀 50+ games integrated
- 🚀 10,000+ assets created
- 🚀 5,000+ active users
- 🚀 100,000+ rental transactions
- 🚀 Self-sustaining revenue

---

## 🛣️ Roadmap

### Q1 2025: Foundation ✅
- ✅ Core smart contracts
- ✅ Basic marketplace UI
- ✅ CLI tool
- ✅ Backend API
- ✅ Launch on Solana devnet

### Q2 2025: Launch
- Mainnet deployment
- First 10 game integrations
- Marketing campaign
- Developer onboarding program
- Mobile app (React Native)

### Q3 2025: Expansion
- TypeScript SDK for web games
- Unity SDK package
- Asset crafting system
- Tournament features
- 50 game integrations

### Q4 2025: Scale
- Fractional ownership
- Cross-chain bridge
- White-label solution
- Enterprise partnerships
- 100+ game integrations

---

## 🤝 Contributing

We welcome contributions! Please see our contributing guidelines in each repository:

- [Smart Contracts Contributing](https://github.com/hallelx2/scrunchy-contract/blob/main/CONTRIBUTING.md)
- [Backend Contributing](https://github.com/hallelx2/scrunchy-backend/blob/main/CONTRIBUTING.md)
- [Frontend Contributing](https://github.com/hallelx2/scrunchy-frontend/blob/main/CONTRIBUTING.md)
- [CLI Contributing](https://github.com/hallelx2/scrunchy-cli/blob/main/CONTRIBUTING.md)

---

## 📄 License

- **Smart Contracts**: MIT License
- **Backend**: MIT License
- **Frontend**: MIT License
- **CLI**: MIT License

See LICENSE files in each repository for details.

---

## 📞 Contact & Resources

### Links
- **GitHub Organization**: [github.com/hallelx2](https://github.com/hallelx2)
- **Demo Video**: [Link to be added]
- **Live Demo**: [Link to be added]
- **Documentation**: See `docs/` folder
- **API Docs**: `http://localhost:3000/api/docs` (when running backend)

### Repositories
- **Smart Contracts**: [github.com/hallelx2/scrunchy-contract](https://github.com/hallelx2/scrunchy-contract)
- **Backend**: [github.com/hallelx2/scrunchy-backend](https://github.com/hallelx2/scrunchy-backend)
- **Frontend**: [github.com/hallelx2/scrunchy-frontend](https://github.com/hallelx2/scrunchy-frontend)
- **CLI**: [github.com/hallelx2/scrunchy-cli](https://github.com/hallelx2/scrunchy-cli)

### Team
- **Developer**: hallelx2
- **Email**: [Your email]
- **Twitter**: [Your Twitter]
- **Discord**: [Your Discord]

---

## 🙏 Acknowledgments

- **Solana Foundation** - For the amazing blockchain platform
- **Anchor Framework** - For making Solana development accessible
- **Metaplex** - For NFT standards and tooling
- **Next.js Team** - For the incredible web framework
- **NestJS Team** - For the robust backend framework
- **shadcn/ui** - For beautiful UI components
- **Solana Community** - For support and inspiration

---

## 🎉 Conclusion

**Scrunchy** is a complete, production-ready platform that makes blockchain gaming **useful, fun, and seamless**. We've built:

✅ **3 Solana programs** with comprehensive testing
✅ **Production-ready backend** with event indexing and caching
✅ **Beautiful frontend** with modern UI/UX
✅ **Universal CLI tool** that works with any game engine
✅ **Complete documentation** for developers and users
✅ **Real-world utility** that solves actual problems

We leverage Solana's **speed, cost, and scalability** to enable a rental economy that's simply not possible on other blockchains. With **sub-second transactions** and **sub-cent costs**, we make micro-rentals economically viable for the first time.

**The future of gaming is decentralized. The future of gaming is on Solana. The future of gaming is Scrunchy.**

---

**Built with ❤️ for the Solana Consumer Track Hackathon**

*Making blockchain gaming accessible, affordable, and fun for everyone.*

---

## 🚀 Get Started Now

```bash
# Clone the repositories
git clone https://github.com/hallelx2/scrunchy-contract.git
git clone https://github.com/hallelx2/scrunchy-backend.git
git clone https://github.com/hallelx2/scrunchy-frontend.git
git clone https://github.com/hallelx2/scrunchy-cli.git

# Follow the setup guides
# See INSTALLATION.md and QUICK_START.md for detailed instructions

# Or jump straight to the code
cd scrunchy-contract && anchor build
cd ../scrunchy-backend && npm install && npm run start:dev
cd ../scrunchy-frontend && npm install && npm run dev
cd ../scrunchy-cli && pip install -e .
```

**Let's build the future of gaming together! 🎮⚡**

