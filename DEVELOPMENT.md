# BKOS Development Setup Guide

## Quick Start (5 minutes)

### Prerequisites
- Node.js 18+ ([download](https://nodejs.org/))
- PostgreSQL 14+ ([download](https://www.postgresql.org/download/))
- Docker & Docker Compose ([download](https://www.docker.com/products/docker-desktop))
- Git

### One-Command Setup (Recommended)

```bash
# Clone the repository
git clone https://github.com/rajkumar-40/BKOS.git
cd BKOS

# Switch to development branch
git checkout development

# Start everything with Docker Compose
docker-compose up -d

# Create database tables & seed data
docker-compose exec backend npm run migrate
docker-compose exec backend npm run seed

# ✅ Backend: http://localhost:5000
# ✅ Frontend: http://localhost:5173
# ✅ PostgreSQL: localhost:5432
```

---

## Manual Setup (Development)

### 1. Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env with your configuration
cat > .env << EOF
NODE_ENV=development
PORT=5000
DATABASE_URL=postgresql://postgres:password@localhost:5432/bkos_dev
JWT_SECRET=your-secret-key-here-change-in-production
JWT_EXPIRE=15m
JWT_REFRESH_EXPIRE=7d
CORS_ORIGIN=http://localhost:5173
EOF

# Create database (ensure PostgreSQL is running)
psql -U postgres -c "CREATE DATABASE bkos_dev;"

# Run migrations
npm run migrate

# Seed sample data
npm run seed

# Start development server
npm run dev

# ✅ Backend running on http://localhost:5000
```

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Default config should work (VITE_API_URL=http://localhost:5000)

# Start development server
npm run dev

# ✅ Frontend running on http://localhost:5173
```

---

## Available Commands

### Backend

```bash
cd backend

# Development
npm run dev              # Start with hot-reload
npm run build            # Build for production
npm start                # Run production build

# Database
npm run migrate          # Run pending migrations
npm run migrate:revert   # Revert last migration
npm run seed             # Seed sample data

# Testing
npm test                 # Run all tests
npm run test:watch       # Run tests in watch mode
npm run test:coverage    # Generate coverage report

# Code Quality
npm run lint             # Check code style
npm run format           # Format code with Prettier

# Database
npm run db:reset         # Reset database (dev only)
```

### Frontend

```bash
cd frontend

# Development
npm run dev              # Start dev server
npm run build            # Build for production
npm run preview          # Preview production build

# Testing
npm test                 # Run tests
npm run test:watch       # Watch mode
npm run test:coverage    # Coverage report

# Code Quality
npm run lint             # Check code
npm run format           # Format code
```

---

## Docker Compose Usage

### Start All Services

```bash
# From root directory
docker-compose up -d

# View logs
docker-compose logs -f backend
docker-compose logs -f frontend
docker-compose logs -f postgres

# Stop all services
docker-compose down

# Reset everything (WARNING: deletes database)
docker-compose down -v
docker-compose up -d
```

### Services Available

| Service | URL | Credentials |
|---------|-----|-------------|
| Backend | http://localhost:5000 | - |
| Frontend | http://localhost:5173 | - |
| PostgreSQL | localhost:5432 | postgres / password |
| pgAdmin | http://localhost:5050 | admin@admin.com / admin |

---

## Database Access

### Via psql (CLI)

```bash
# Connect to development database
psql -U postgres -d bkos_dev -h localhost

# List tables
\dt

# View schema
\d table_name

# Exit
\q
```

### Via pgAdmin (Web UI)

1. Open http://localhost:5050
2. Login: `admin@admin.com` / `admin`
3. Add server: localhost:5432 with postgres:password
4. Browse & manage database

### Via Docker

```bash
# Access database inside container
docker-compose exec postgres psql -U postgres -d bkos_dev
```

---

## Environment Variables

### Backend (.env)

```env
# Environment
NODE_ENV=development              # development, staging, production
PORT=5000                         # Server port

# Database
DATABASE_URL=postgresql://postgres:password@localhost:5432/bkos_dev
DATABASE_POOL_MIN=2             # Min connections
DATABASE_POOL_MAX=10            # Max connections

# Authentication
JWT_SECRET=your-super-secret-key-change-this
JWT_EXPIRE=15m                   # Access token expiry
JWT_REFRESH_EXPIRE=7d            # Refresh token expiry

# CORS
CORS_ORIGIN=http://localhost:5173

# Logging
LOG_LEVEL=debug                  # debug, info, warn, error

# Optional: AI/ML
OPENAI_API_KEY=                  # For AI Teacher (Phase 4)
```

### Frontend (.env)

```env
# API Configuration
VITE_API_URL=http://localhost:5000

# Optional: Analytics
VITE_GA_ID=                      # Google Analytics ID
```

---

## Project Structure

### Backend

```
backend/
├── src/
│   ├── index.ts                 # Entry point
│   ├── config/
│   │   ├── database.ts          # Database connection
│   │   ├── env.ts               # Environment variables
│   │   └── server.ts            # Server configuration
│   ├── models/                  # TypeORM entities
│   │   ├── User.ts
│   │   ├── Subject.ts
│   │   ├── Question.ts
│   │   ├── Attempt.ts
│   │   └── ...
│   ├── controllers/             # Request handlers
│   │   ├── authController.ts
│   │   ├── subjectsController.ts
│   │   ├── questionsController.ts
│   │   └── ...
│   ├── services/                # Business logic
│   │   ├── authService.ts
│   │   ├── subjectsService.ts
│   │   └── ...
│   ├── routes/                  # API routes
│   │   ├── auth.ts
│   │   ├── subjects.ts
│   │   ├── questions.ts
│   │   └── ...
│   ├── middleware/              # Express middleware
│   │   ├── auth.ts              # JWT verification
│   │   ├── errorHandler.ts      # Error handling
│   │   └── validation.ts        # Input validation
│   ├── utils/                   # Utility functions
│   │   ├── jwt.ts               # Token utilities
│   │   ├── validators.ts        # Validation helpers
│   │   └── logger.ts            # Logging utility
│   ├── database/
│   │   ├── migrations/          # Database migrations
│   │   └── seeds/               # Sample data
│   └── tests/                   # Test files
├── .env.example
├── Dockerfile
├── docker-compose.yml
├── package.json
├── tsconfig.json
└── README.md
```

### Frontend

```
frontend/
├── src/
│   ├── App.tsx                  # Root component
│   ├── main.tsx                 # Entry point
│   ├── pages/
│   │   ├── LoginPage.tsx
│   │   ├── DashboardPage.tsx
│   │   ├── SubjectsPage.tsx
│   │   ├── QuestionsPage.tsx
│   │   ├── ResultsPage.tsx
│   │   └── ...
│   ├── components/
│   │   ├── Auth/                # Auth-related components
│   │   ├── Layout/              # Layout components
│   │   ├── Question/            # Question components
│   │   ├── Dashboard/           # Dashboard components
│   │   └── Common/              # Reusable components
│   ├── hooks/
│   │   ├── useAuth.ts           # Auth hook
│   │   ├── useFetch.ts          # Data fetching hook
│   │   └── ...
│   ├── context/
│   │   ├── AuthContext.tsx      # Auth state
│   │   ├── UserContext.tsx      # User state
│   │   └── ...
│   ├── services/
│   │   ├── api.ts               # Axios instance
│   │   ├── authService.ts       # Auth API calls
│   │   ├── questionsService.ts  # Questions API calls
│   │   └── ...
│   ├── types/
│   │   ├── index.ts             # TypeScript interfaces
│   │   └── ...
│   ├── styles/
│   │   ├── globals.css          # Global styles
│   │   └── tailwind.config.ts   # Tailwind config
│   └── tests/
├── public/                      # Static assets
├── .env.example
├── Dockerfile
├── package.json
├── vite.config.ts
├── tsconfig.json
└── README.md
```

---

## Testing

### Backend Tests

```bash
cd backend

# Run all tests
npm test

# Run specific test file
npm test -- auth.test.ts

# Watch mode (re-run on changes)
npm run test:watch

# Coverage report
npm run test:coverage
```

### Frontend Tests

```bash
cd frontend

# Run tests
npm test

# Watch mode
npm test -- --watch

# Coverage report
npm test -- --coverage
```

---

## API Testing

### Using Thunder Client (VS Code)

1. Install "Thunder Client" extension
2. Import collection: `.thunder/BKOS.json`
3. Test endpoints with pre-configured requests

### Using Postman

1. Import: `docs/postman-collection.json`
2. Set environment variables
3. Test endpoints

### Using curl

```bash
# Login
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'

# Get subjects
curl http://localhost:5000/api/subjects \
  -H "Authorization: Bearer <your-token>"
```

---

## Common Issues & Solutions

### Port Already in Use

```bash
# Find process using port 5000
lsof -i :5000

# Kill process
kill -9 <PID>

# Or change port in .env
```

### Database Connection Error

```bash
# Check PostgreSQL is running
psql -U postgres

# Create database if missing
psql -U postgres -c "CREATE DATABASE bkos_dev;"

# Check DATABASE_URL in .env
```

### Node Modules Issue

```bash
# Clean install
rm -rf node_modules package-lock.json
npm install
```

### Docker Issues

```bash
# Rebuild containers
docker-compose build --no-cache

# Check logs
docker-compose logs backend

# Reset everything
docker-compose down -v
docker-compose up -d
```

---

## Code Style & Conventions

### TypeScript
- Use `interface` for contracts
- Use `type` for unions/aliases
- Always specify return types
- Use strict mode in tsconfig.json

### File Naming
- Components: PascalCase (UserProfile.tsx)
- Utilities/Services: camelCase (userService.ts)
- Types: PascalCase (User.ts)
- Tests: *.test.ts or *.spec.ts

### Formatting
- Prettier: 2-space indent, single quotes
- ESLint: Airbnb config
- Run before committing: `npm run format && npm run lint`

---

## Debugging

### Backend

```bash
# Debug mode (requires Chrome)
node --inspect-brk -r ts-node/register src/index.ts

# Open Chrome DevTools: chrome://inspect
```

### Frontend

```bash
# React DevTools extension
# Redux DevTools (if using Redux)
# Network tab in browser DevTools
```

---

## Git Workflow

```bash
# Create feature branch
git checkout -b feature/add-login

# Make changes
git add .
git commit -m "feat: Add login functionality"

# Format & lint before push
npm run format
npm run lint
npm test

# Push & create pull request
git push origin feature/add-login

# After review, merge to development
```

---

## Next Steps

1. Complete backend setup → See `backend/README.md`
2. Complete frontend setup → See `frontend/README.md`
3. View API documentation → See `docs/API.md`
4. Run tests → `npm test`
5. Check database schema → `docs/DATABASE.md`

**Happy coding! 🚀**
