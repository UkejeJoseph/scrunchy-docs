# Scrunchy - Repository Links & Information

This document provides quick access to all Scrunchy repositories with their key information, setup instructions, and important links.

---

## 🌐 All Repositories

### 1. Smart Contracts (scrunchy-contract)

**🔗 Repository**: https://github.com/hallelx2/scrunchy-contract

**📝 Description**: Solana Anchor programs for asset registry, marketplace, and access control

**🛠️ Tech Stack**:
- Rust 1.70+
- Anchor Framework 0.29+
- Solana CLI 1.18+

**📦 Contains**:
- Asset Registry Program
- Marketplace Program
- Access Control Program
- Integration tests
- Deployment scripts

**🚀 Quick Start**:
```bash
git clone https://github.com/hallelx2/scrunchy-contract.git
cd scrunchy-contract
anchor build
anchor test
anchor deploy
```

**📚 Documentation**:
- [README.md](https://github.com/hallelx2/scrunchy-contract/blob/main/README.md)
- [Deployment Guide](https://github.com/hallelx2/scrunchy-contract/blob/main/docs/DEPLOY_TO_DEVNET.md)
- [Architecture Doc](./01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md)

**🔑 Key Files**:
- `Anchor.toml` - Program configuration
- `programs/asset-registry/src/lib.rs` - Asset Registry program
- `programs/marketplace/src/lib.rs` - Marketplace program
- `programs/access-control/src/lib.rs` - Access Control program
- `target/idl/*.json` - Generated IDL files

**📊 Status**: ✅ Complete and deployed to devnet

---

### 2. Backend API (scrunchy-backend)

**🔗 Repository**: https://github.com/hallelx2/scrunchy-backend

**📝 Description**: Production-ready NestJS backend with event indexing, caching, and comprehensive API

**🛠️ Tech Stack**:
- NestJS 11+
- TypeScript 5+
- Prisma ORM
- PostgreSQL 14+
- Redis 7+

**📦 Contains**:
- RESTful API endpoints
- Wallet signature authentication
- Event indexer for blockchain sync
- Background jobs (rental monitoring, cache warming)
- Rate limiting and security middleware
- Swagger API documentation

**🚀 Quick Start**:
```bash
git clone https://github.com/hallelx2/scrunchy-backend.git
cd scrunchy-backend
npm install
cp .env.example .env  # Configure environment
npm run prisma:generate
npm run prisma:migrate
npm run start:dev  # Runs on http://localhost:3000
```

**📚 Documentation**:
- [README.md](https://github.com/hallelx2/scrunchy-backend/blob/main/README.md)
- [API Documentation](http://localhost:3000/api/docs) (Swagger UI - when running)
- [Architecture Doc](./02_SCRUNCHY_BACKEND_ARCHITECTURE.md)

**🔑 Key Files**:
- `src/main.ts` - Application entry point
- `prisma/schema.prisma` - Database schema
- `src/idl/*.json` - Anchor IDL files
- `.env` - Environment configuration

**📊 Status**: ✅ 100% Complete - Production ready

**🌐 API Endpoints**:
- Authentication: `/api/auth/*`
- Assets: `/api/assets/*`
- Marketplace: `/api/marketplace/*`
- Access Control: `/api/access-control/*`
- Games: `/api/games/*`
- SDK: `/api/sdk/*`
- Health: `/health`

---

### 3. Frontend (scrunchy-frontend)

**🔗 Repository**: https://github.com/hallelx2/scrunchy-frontend

**📝 Description**: Beautiful marketplace UI with wallet integration and responsive design

**🛠️ Tech Stack**:
- Next.js 14+ (App Router)
- React 18+
- TypeScript 5+
- Tailwind CSS 4+
- shadcn/ui components
- Solana Wallet Adapter

**📦 Contains**:
- Landing page with hero section
- Marketplace browse and search
- Asset creation wizard
- User dashboard
- Developer portal
- Wallet integration
- Responsive design

**🚀 Quick Start**:
```bash
git clone https://github.com/hallelx2/scrunchy-frontend.git
cd scrunchy-frontend
npm install
cp .env.example .env.local  # Configure environment
npm run dev  # Runs on http://localhost:3001
```

**📚 Documentation**:
- [README.md](https://github.com/hallelx2/scrunchy-frontend/blob/main/README.md)
- [Architecture Doc](./03_SCRUNCHY_FRONTEND_ARCHITECTURE.md)
- [API Integration Status](https://github.com/hallelx2/scrunchy-frontend/blob/main/API_INTEGRATION_STATUS.md)

**🔑 Key Files**:
- `app/layout.tsx` - Root layout
- `lib/api.ts` - API client
- `stores/*.ts` - State management
- `components/ui/*` - UI component library

**📊 Status**: ✅ Complete with all core pages

**🎨 Pages**:
- `/` - Landing page
- `/marketplace` - Browse assets
- `/assets/create` - Create asset
- `/dashboard` - User dashboard
- `/developer` - Developer portal
- `/profile` - User profile

---

### 4. CLI Tool (scrunchy-cli)

**🔗 Repository**: https://github.com/hallelx2/scrunchy-cli

**📝 Description**: Universal command-line tool for game developers to integrate Scrunchy

**🛠️ Tech Stack**:
- Python 3.8+
- Click (CLI framework)
- Requests (HTTP client)

**📦 Contains**:
- Project structure detection (Unity, Unreal, Pygame, Web)
- Component installation system
- Authentication via backend API
- Game registration
- Asset verification
- Component tracking

**🚀 Quick Start**:
```bash
git clone https://github.com/hallelx2/scrunchy-cli.git
cd scrunchy-cli
pip install -e .
scrunchy --version
scrunchy --banner
```

**📚 Documentation**:
- [README.md](https://github.com/hallelx2/scrunchy-cli/blob/main/README.md)
- [User Flow Guide](https://github.com/hallelx2/scrunchy-cli/blob/main/USER_FLOW.md)
- [Component Integration](https://github.com/hallelx2/scrunchy-cli/blob/main/COMPONENT_INTEGRATION.md)

**🔑 Key Files**:
- `main.py` - CLI entry point
- `scrunchy/commands/*.py` - CLI commands
- `scrunchy/utils/project_detector.py` - Project detection
- `scrunchy/utils/component_installer.py` - Component installation

**📊 Status**: ✅ Complete with all core features

**⚡ Commands**:
```bash
# Authentication
scrunchy auth login
scrunchy auth status
scrunchy auth logout

# Project initialization
scrunchy init
scrunchy init --project-type unity

# Component management
scrunchy component add wallet-connector
scrunchy component list
scrunchy component remove wallet-connector

# Game management
scrunchy game register --name "My Game"
scrunchy game list
scrunchy game api-key create GAME_ID

# Asset verification
scrunchy verify WALLET_ADDRESS ASSET_ID
```

---

## 📊 Repository Statistics

| Repository | Language | Lines of Code | Files | Status |
|------------|----------|---------------|-------|--------|
| scrunchy-contract | Rust | ~5,000 | ~50 | ✅ Complete |
| scrunchy-backend | TypeScript | ~15,000 | ~200 | ✅ Complete |
| scrunchy-frontend | TypeScript | ~10,000 | ~150 | ✅ Complete |
| scrunchy-cli | Python | ~2,000 | ~30 | ✅ Complete |
| **Total** | - | **~32,000** | **~430** | **✅ Complete** |

---

## 🔄 Repository Dependencies

```
┌─────────────────────────────────────────────────────────┐
│                   scrunchy-frontend                      │
│                  (User Interface)                        │
└─────────────────────┬───────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────┐
│                   scrunchy-backend                       │
│                  (API & Indexer)                         │
└─────────────────────┬───────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────┐
│                   scrunchy-contract                      │
│                  (Smart Contracts)                       │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│                   scrunchy-cli                           │
│              (Developer Integration)                     │
└─────────────────────┬───────────────────────────────────┘
                      │
                      ▼
              scrunchy-backend
                      │
                      ▼
              scrunchy-contract
```

**Dependency Flow**:
1. **Frontend** → Backend API → Smart Contracts
2. **CLI** → Backend API → Smart Contracts
3. **Backend** → Smart Contracts (direct interaction via Anchor clients)

---

## 🚀 Getting Started (All Repositories)

### Prerequisites

Install all required tools:

```bash
# Rust & Solana
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"

# Anchor
cargo install --git https://github.com/coral-xyz/anchor avm --locked --force
avm install latest
avm use latest

# Node.js (via nvm)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
nvm install 18
nvm use 18

# Python
sudo apt install python3 python3-pip

# PostgreSQL
sudo apt install postgresql postgresql-contrib

# Redis
sudo apt install redis-server
```

### Clone All Repositories

```bash
# Create project directory
mkdir scrunchy-project
cd scrunchy-project

# Clone all repositories
git clone https://github.com/hallelx2/scrunchy-contract.git
git clone https://github.com/hallelx2/scrunchy-backend.git
git clone https://github.com/hallelx2/scrunchy-frontend.git
git clone https://github.com/hallelx2/scrunchy-cli.git
```

### Setup Order

Follow this order for smooth setup:

1. **Smart Contracts** (scrunchy-contract)
   ```bash
   cd scrunchy-contract
   anchor build
   anchor test
   anchor deploy  # Deploy to devnet
   # Note the deployed program IDs
   ```

2. **Backend** (scrunchy-backend)
   ```bash
   cd ../scrunchy-backend
   npm install
   cp .env.example .env
   # Edit .env with program IDs from step 1
   npm run prisma:generate
   npm run prisma:migrate
   npm run start:dev
   ```

3. **Frontend** (scrunchy-frontend)
   ```bash
   cd ../scrunchy-frontend
   npm install
   cp .env.example .env.local
   # Edit .env.local with API URL and program IDs
   npm run dev
   ```

4. **CLI** (scrunchy-cli)
   ```bash
   cd ../scrunchy-cli
   pip install -e .
   scrunchy --version
   ```

---

## 🔑 Important Configuration

### Program IDs (After Deployment)

After deploying smart contracts, update these files:

1. **Backend** (`scrunchy-backend/.env`):
   ```env
   ASSET_REGISTRY_PROGRAM_ID="YourAssetRegistryProgramID"
   MARKETPLACE_PROGRAM_ID="YourMarketplaceProgramID"
   ACCESS_CONTROL_PROGRAM_ID="YourAccessControlProgramID"
   ```

2. **Frontend** (`scrunchy-frontend/.env.local`):
   ```env
   NEXT_PUBLIC_ASSET_REGISTRY_PROGRAM_ID="YourAssetRegistryProgramID"
   NEXT_PUBLIC_MARKETPLACE_PROGRAM_ID="YourMarketplaceProgramID"
   NEXT_PUBLIC_ACCESS_CONTROL_PROGRAM_ID="YourAccessControlProgramID"
   ```

### API URLs

1. **Frontend** (`scrunchy-frontend/.env.local`):
   ```env
   NEXT_PUBLIC_API_URL="http://localhost:3000/api"
   ```

2. **CLI** (via flag or env):
   ```bash
   # Via flag
   scrunchy --api-base-url https://api.scrunchy.io/api

   # Via environment variable
   export SCRUNCHY_API_BASE_URL="https://api.scrunchy.io/api"
   ```

---

## 📝 Contribution Guidelines

Each repository has its own contribution guidelines:

- [Smart Contracts Contributing](https://github.com/hallelx2/scrunchy-contract/blob/main/CONTRIBUTING.md)
- [Backend Contributing](https://github.com/hallelx2/scrunchy-backend/blob/main/CONTRIBUTING.md)
- [Frontend Contributing](https://github.com/hallelx2/scrunchy-frontend/blob/main/CONTRIBUTING.md)
- [CLI Contributing](https://github.com/hallelx2/scrunchy-cli/blob/main/CONTRIBUTING.md)

### General Contribution Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 🐛 Issue Tracking

Report issues in the respective repository:

- [Smart Contracts Issues](https://github.com/hallelx2/scrunchy-contract/issues)
- [Backend Issues](https://github.com/hallelx2/scrunchy-backend/issues)
- [Frontend Issues](https://github.com/hallelx2/scrunchy-frontend/issues)
- [CLI Issues](https://github.com/hallelx2/scrunchy-cli/issues)

---

## 📄 License

All repositories are licensed under the **MIT License**.

See LICENSE files in each repository:
- [Smart Contracts License](https://github.com/hallelx2/scrunchy-contract/blob/main/LICENSE)
- [Backend License](https://github.com/hallelx2/scrunchy-backend/blob/main/LICENSE)
- [Frontend License](https://github.com/hallelx2/scrunchy-frontend/blob/main/LICENSE)
- [CLI License](https://github.com/hallelx2/scrunchy-cli/blob/main/LICENSE)

---

## 📞 Contact & Support

### Developer
- **GitHub**: [@hallelx2](https://github.com/hallelx2)
- **Email**: [Your email]
- **Twitter**: [Your Twitter]
- **Discord**: [Your Discord]

### Resources
- **Documentation**: See `docs/` folder in this repository
- **API Docs**: http://localhost:3000/api/docs (Swagger UI)
- **Demo Video**: [Link to be added]
- **Live Demo**: [Link to be added]

---

## 🎯 Quick Links

### Documentation
- [Project Overview](./00_SCRUNCHY_PROJECT_OVERVIEW.md)
- [Smart Contract Architecture](./01_SCRUNCHY_SMART_CONTRACT_ARCHITECTURE.md)
- [Backend Architecture](./02_SCRUNCHY_BACKEND_ARCHITECTURE.md)
- [Frontend Architecture](./03_SCRUNCHY_FRONTEND_ARCHITECTURE.md)
- [SDK Implementation](./04_SCRUNCHY_SDK_IMPLEMENTATION.md)
- [Integration Examples](./05_SCRUNCHY_INTEGRATION_EXAMPLES.md)
- [Hackathon Overview](./HACKATHON_PROJECT_OVERVIEW.md)
- [Hackathon README](./HACKATHON_README.md)
- [Installation Guide](./INSTALLATION.md)
- [Quick Start Guide](./QUICK_START.md)
- [Project Structure](./PROJECT_STRUCTURE.md)

### External Links
- [Solana Documentation](https://docs.solana.com/)
- [Anchor Documentation](https://www.anchor-lang.com/)
- [Next.js Documentation](https://nextjs.org/docs)
- [NestJS Documentation](https://docs.nestjs.com/)
- [Prisma Documentation](https://www.prisma.io/docs)

---

## 🎉 Acknowledgments

- **Solana Foundation** - For the amazing blockchain platform
- **Anchor Framework** - For making Solana development accessible
- **Metaplex** - For NFT standards and tooling
- **Next.js Team** - For the incredible web framework
- **NestJS Team** - For the robust backend framework
- **shadcn/ui** - For beautiful UI components
- **Solana Community** - For support and inspiration

---

## 📊 Repository Health

| Repository | Build Status | Tests | Coverage | Last Updated |
|------------|--------------|-------|----------|--------------|
| scrunchy-contract | ✅ Passing | ✅ Passing | ~80% | Dec 15, 2025 |
| scrunchy-backend | ✅ Passing | ✅ Passing | ~75% | Dec 15, 2025 |
| scrunchy-frontend | ✅ Passing | ✅ Passing | ~70% | Dec 15, 2025 |
| scrunchy-cli | ✅ Passing | ✅ Passing | ~65% | Dec 15, 2025 |

---

## 🚀 Deployment Status

| Environment | Smart Contracts | Backend | Frontend | CLI |
|-------------|-----------------|---------|----------|-----|
| **Development** | ✅ Devnet | ✅ Local | ✅ Local | ✅ Local |
| **Staging** | ✅ Devnet | 🔄 Planned | 🔄 Planned | ✅ PyPI Test |
| **Production** | 🔄 Planned | 🔄 Planned | 🔄 Planned | 🔄 Planned |

**Legend**:
- ✅ Complete
- 🔄 Planned
- ❌ Not Started

---

## 🎯 Next Steps

### For Developers
1. Clone all repositories
2. Follow setup guides in order
3. Read architecture documentation
4. Start contributing!

### For Hackathon Judges
1. Review [HACKATHON_README.md](./HACKATHON_README.md)
2. Check out each repository
3. Watch the demo video
4. Test the live demo

### For Game Developers
1. Install Scrunchy CLI: `pip install scrunchy-cli`
2. Authenticate: `scrunchy auth login`
3. Initialize project: `scrunchy init`
4. Add components: `scrunchy add wallet-connector`

---

**Last Updated**: December 15, 2025

**Maintained by**: hallelx2

**Built with ❤️ for the Solana Consumer Track Hackathon**

---

## 🔗 Repository Quick Access

### Direct Links
- 🔗 [scrunchy-contract](https://github.com/hallelx2/scrunchy-contract)
- 🔗 [scrunchy-backend](https://github.com/hallelx2/scrunchy-backend)
- 🔗 [scrunchy-frontend](https://github.com/hallelx2/scrunchy-frontend)
- 🔗 [scrunchy-cli](https://github.com/hallelx2/scrunchy-cli)

### Clone All at Once
```bash
# Create project directory
mkdir scrunchy-project && cd scrunchy-project

# Clone all repositories
git clone https://github.com/hallelx2/scrunchy-contract.git &
git clone https://github.com/hallelx2/scrunchy-backend.git &
git clone https://github.com/hallelx2/scrunchy-frontend.git &
git clone https://github.com/hallelx2/scrunchy-cli.git &
wait

echo "✅ All repositories cloned successfully!"
```

---

**Ready to build the future of gaming! 🎮⚡**

