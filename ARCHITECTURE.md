# BKOS Architecture

## Overview

BKOS is a full-stack knowledge intelligence platform built with modern, scalable technologies.

## Technology Stack

### Backend
- **Language:** TypeScript (Node.js)
- **Framework:** Express.js
- **Database:** PostgreSQL 14+
- **Authentication:** JWT (JSON Web Tokens) + bcrypt
- **API Style:** RESTful with JSON responses
- **Runtime:** Node.js 18+

### Frontend
- **Language:** TypeScript
- **Framework:** React 18+
- **Build Tool:** Vite
- **Styling:** Tailwind CSS
- **State Management:** React Context + Hooks
- **HTTP Client:** Axios
- **UI Components:** Headless UI + custom components

### DevOps & Infrastructure
- **Containerization:** Docker & Docker Compose
- **CI/CD:** GitHub Actions
- **Package Managers:** npm (Node.js)
- **Version Control:** Git
- **Env Management:** dotenv

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (React)                      │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Pages: Login, Dashboard, Subjects, Questions,    │   │
│  │ Results, Analytics                               │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
                          │
                  HTTP/REST API
                  (JWT Bearer Token)
                          │
┌─────────────────────────────────────────────────────────┐
│                  Backend (Express)                       │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Routes: Auth, Subjects, Questions, Attempts,     │   │
│  │ Mistakes, Analytics                              │   │
│  ├──────────────────────────────────────────────────┤   │
│  │ Controllers & Business Logic Layer               │   │
│  ├──────────────────────────────────────────────────┤   │
│  │ Middleware: Auth, Validation, Error Handling     │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
                          │
                   Database Connection
                          │
┌─────────────────────────────────────────────────────────┐
│              PostgreSQL Database                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Tables: Users, Subjects, Chapters, Topics,       │   │
│  │ Concepts, Questions, Attempts, Mistakes,         │   │
│  │ Revisions, Skills, CareerPaths                   │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

## Design Principles

### 1. **Concept-First Learning**
- Knowledge graph hierarchy: Subject → Chapter → Topic → Concept → Question
- Questions link to concepts, not standalone
- Every question has learning objectives

### 2. **Lifelong Learning Path**
- Concept → Practice → Mistakes → Analysis → Revision → Mastery → Skill → Career
- Each stage has dedicated modules and analytics
- Progressive difficulty levels

### 3. **Scalability**
- Stateless backend (horizontal scaling)
- Database indexing on high-query columns
- JWT for distributed authentication
- Ready for caching layer (Redis)

### 4. **Security**
- Password hashing with bcrypt
- JWT token expiration (15 min access, 7 day refresh)
- Input validation on all endpoints
- CORS configuration
- SQL injection protection (parameterized queries)

### 5. **Code Organization**
- Clear separation: Controllers → Services → Models → Database
- Middleware for cross-cutting concerns
- Centralized error handling
- Type safety with TypeScript

## Project Structure

```
BKOS/
├── backend/                    # Express API server
│   ├── src/
│   │   ├── index.ts           # Entry point
│   │   ├── config/            # Configuration (DB, env)
│   │   ├── models/            # Database models & schemas
│   │   ├── controllers/       # Request handlers
│   │   ├── services/          # Business logic
│   │   ├── routes/            # API endpoints
│   │   ├── middleware/        # Auth, validation, errors
│   │   ├── utils/             # Helpers & utilities
│   │   ├── database/
│   │   │   └── migrations/    # Schema versions
│   │   └── tests/             # Unit & integration tests
│   ├── Dockerfile
│   ├── docker-compose.yml
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
│
├── frontend/                   # React application
│   ├── src/
│   │   ├── App.tsx            # Main component
│   │   ├── pages/             # Page components
│   │   ├── components/        # Reusable components
│   │   ├── hooks/             # Custom React hooks
│   │   ├── context/           # State management
│   │   ├── services/          # API calls
│   │   ├── types/             # TypeScript interfaces
│   │   ├── styles/            # Tailwind config
│   │   └── tests/             # Jest tests
│   ├── public/                # Static assets
│   ├── Dockerfile
│   ├── docker-compose.yml
│   ├── package.json
│   ├── vite.config.ts
│   └── README.md
│
├── database/                   # Database documentation
│   ├── schema/                # Table definitions
│   ├── migrations/            # Version control
│   ├── seeds/                 # Sample data
│   └── ERD.md                 # Entity diagram
│
├── docs/                       # Comprehensive documentation
│   ├── SETUP.md               # Local development setup
│   ├── API.md                 # API endpoints & examples
│   ├── DATABASE.md            # Schema reference
│   ├── TESTING.md             # Test coverage
│   └── DEPLOYMENT.md          # Production guide
│
└── .github/workflows/         # CI/CD pipelines
    ├── test.yml
    ├── lint.yml
    └── deploy.yml
```

## Data Flow

### User Authentication Flow
```
1. User submits login credentials
   ↓
2. Backend validates email/password against database
   ↓
3. Password verified with bcrypt
   ↓
4. JWT token generated (access + refresh)
   ↓
5. Token sent to frontend
   ↓
6. Frontend stores in secure session/local storage
   ↓
7. All subsequent requests include JWT in Authorization header
```

### Question Attempt Flow
```
1. User selects question from topic
   ↓
2. Frontend loads question data (question, options, metadata)
   ↓
3. User submits answer + time spent
   ↓
4. Backend validates answer against database
   ↓
5. Backend records attempt (correct/incorrect)
   ↓
6. Backend stores confidence level if provided
   ↓
7. Backend updates user analytics
   ↓
8. Frontend displays result with explanation
   ↓
9. Backend tracks for revision engine (spaced repetition)
```

### Knowledge Graph Navigation
```
Subject (e.g., Physics)
  ├── Chapter (e.g., Mechanics)
  │   ├── Topic (e.g., Force & Motion)
  │   │   ├── Concept (e.g., Newton's Laws)
  │   │   │   └── Questions (e.g., Q1, Q2, Q3)
  │   │   │       └── Attempts (User answers)
  │   │   │           └── Analytics (Performance)
```

## API Design Principles

### Response Format
```json
{
  "success": true,
  "data": { /* response payload */ },
  "error": null,
  "timestamp": "2024-01-15T10:30:00Z"
}
```

### Error Format
```json
{
  "success": false,
  "data": null,
  "error": {
    "code": "UNAUTHORIZED",
    "message": "Invalid token",
    "details": null
  },
  "timestamp": "2024-01-15T10:30:00Z"
}
```

## Version & Roadmap

- **Current Version:** 0.2 (Foundation + MVP development)
- **Phase 1 (v1.0):** Login, Dashboard, Subjects, Questions, Results
- **Phase 2 (v1.1):** Confidence Engine, Mistake Tracking
- **Phase 3 (v1.2):** Revision Engine with spaced repetition
- **Phase 4 (v2.0):** AI Teacher integration
- **Phase 5 (v2.1):** Career Graph
- **Phase 6 (v2.2):** Scholarships
- **Phase 7 (v3.0):** AI Agents Ecosystem

## Scaling Strategy

### Current (MVP)
- Monolithic backend
- Single PostgreSQL instance
- JWT-based stateless auth

### Phase 2
- Add Redis for session caching
- Database read replicas
- CDN for static assets

### Phase 3+
- Microservices (Auth, Questions, Analytics)
- Event streaming (Kafka/RabbitMQ)
- Elasticsearch for full-text search
- GraphQL for complex queries

## Next Steps

1. ✅ Complete backend implementation
2. ✅ Complete frontend implementation
3. ✅ Database schema & migrations
4. ✅ Docker & local development setup
5. ✅ API documentation (Swagger)
6. ✅ Testing framework
7. ✅ GitHub Actions CI/CD
8. ✅ Deployment guide

See `docs/SETUP.md` for getting started.
