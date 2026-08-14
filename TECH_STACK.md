# BKOS Technology Stack

## Backend Stack

### Core
| Component | Technology | Version | Purpose |
|-----------|-----------|---------|----------|
| Language | TypeScript | 5.0+ | Type-safe JavaScript |
| Runtime | Node.js | 18+ | JavaScript runtime |
| Framework | Express.js | 4.18+ | Web server & routing |
| Database | PostgreSQL | 14+ | Relational database |

### Authentication & Security
| Package | Version | Purpose |
|---------|---------|----------|
| jsonwebtoken | 9.0+ | JWT token generation/verification |
| bcryptjs | 2.4+ | Password hashing |
| cors | 2.8+ | Cross-origin resource sharing |
| helmet | 7.0+ | Security headers |
| dotenv | 16.0+ | Environment variables |

### Database
| Package | Version | Purpose |
|---------|---------|----------|
| pg | 8.10+ | PostgreSQL client |
| typeorm | 0.3+ | ORM for database abstraction |
| typeorm-migrations | Included | Database versioning |

### Development
| Package | Version | Purpose |
|---------|---------|----------|
| nodemon | 3.0+ | Auto-reload on file changes |
| ts-node | 10.0+ | Run TypeScript directly |
| typescript | 5.0+ | TypeScript compiler |
| @types/node | 20.0+ | Node.js type definitions |
| @types/express | 4.17+ | Express type definitions |

### Testing
| Package | Version | Purpose |
|---------|---------|----------|
| jest | 29.0+ | Test runner |
| ts-jest | 29.0+ | TypeScript support for Jest |
| supertest | 6.3+ | HTTP assertion library |

### Linting & Formatting
| Package | Version | Purpose |
|---------|---------|----------|
| eslint | 8.0+ | Code quality |
| prettier | 3.0+ | Code formatter |

---

## Frontend Stack

### Core
| Component | Technology | Version | Purpose |
|-----------|-----------|---------|----------|
| Language | TypeScript | 5.0+ | Type-safe JavaScript |
| Framework | React | 18+ | UI library |
| Build Tool | Vite | 4.0+ | Fast build tool |
| Styling | Tailwind CSS | 3.0+ | Utility-first CSS |

### UI & Components
| Package | Version | Purpose |
|---------|---------|----------|
| @headlessui/react | 1.7+ | Headless UI components |
| react-router-dom | 6.0+ | Client-side routing |
| axios | 1.4+ | HTTP client |

### State Management
| Package | Version | Purpose |
|---------|---------|----------|
| zustand | 4.0+ | Lightweight state management |
| jotai | 2.0+ | Primitive atoms |

### Form Handling
| Package | Version | Purpose |
|---------|---------|----------|
| react-hook-form | 7.0+ | Lightweight form management |
| zod | 3.0+ | TypeScript-first validation |

### Development
| Package | Version | Purpose |
|---------|---------|----------|
| @vitejs/plugin-react | 4.0+ | React plugin for Vite |
| typescript | 5.0+ | TypeScript compiler |
| @types/react | 18.0+ | React type definitions |
| @types/react-dom | 18.0+ | React DOM type definitions |
| tailwindcss | 3.0+ | Tailwind CSS framework |
| autoprefixer | 10.0+ | CSS prefixer |
| postcss | 8.0+ | CSS processor |

### Testing
| Package | Version | Purpose |
|---------|---------|----------|
| vitest | 0.34+ | Vite test runner |
| @testing-library/react | 14.0+ | React component testing |
| @testing-library/user-event | 14.0+ | User interaction simulation |

### Build & Deployment
| Package | Version | Purpose |
|---------|---------|----------|
| vite-plugin-compression | 0.5+ | Gzip compression |

---

## DevOps Stack

### Containerization
| Technology | Version | Purpose |
|-----------|---------|----------|
| Docker | 24.0+ | Container runtime |
| Docker Compose | 2.0+ | Multi-container orchestration |

### CI/CD
| Technology | Purpose |
|-----------|----------|
| GitHub Actions | Continuous integration & deployment |
| GitHub Workflows | Automated testing, linting, deployment |

### Monitoring & Logging (Future)
| Technology | Purpose |
|-----------|----------|
| Winston | Structured logging |
| Sentry | Error tracking |

---

## Database Stack

### RDBMS
| Technology | Version | Purpose |
|-----------|---------|----------|
| PostgreSQL | 14+ | Relational database |
| pgAdmin | Latest | Database management UI |

### ORM
| Package | Version | Purpose |
|---------|---------|----------|
| TypeORM | 0.3+ | Object-Relational Mapping |
| TypeORM Migrations | Included | Schema versioning |

---

## Package Installation

### Backend Dependencies
```bash
npm install express cors helmet dotenv jsonwebtoken bcryptjs pg typeorm axios
npm install --save-dev typescript ts-node nodemon jest ts-jest @types/node @types/express eslint prettier
```

### Frontend Dependencies
```bash
npm install react react-dom react-router-dom axios zustand react-hook-form zod @headlessui/react
npm install --save-dev typescript vite @vitejs/plugin-react tailwindcss postcss autoprefixer vitest @testing-library/react @types/react @types/react-dom
```

---

## Environment Requirements

### Development
- Node.js 18+ with npm 9+
- PostgreSQL 14+ with pgAdmin
- Docker 24+ & Docker Compose 2+
- Git for version control

### Recommended Tools
- VS Code with extensions:
  - ES7+ React/Redux/React-Native snippets
  - Thunder Client or Postman for API testing
  - PostgreSQL Explorer extension
  - Docker extension

---

## Deployment Stack

### Staging & Production
| Layer | Technology | Details |
|-------|-----------|----------|
| Containerization | Docker | Both backend & frontend |
| Orchestration | Docker Compose (dev/staging) | Multi-container management |
| Cloud Platform | AWS/DigitalOcean/Heroku | Production hosting |
| Database | PostgreSQL RDS | Managed database |
| Cache | Redis (future) | Session & query caching |
| CDN | CloudFront/CloudFlare | Static asset delivery |

---

## Version Compatibility Matrix

| Component | Min Version | Recommended | Max Version |
|-----------|-------------|-------------|-------------|
| Node.js | 18.0 | 20.0 | Latest LTS |
| PostgreSQL | 14.0 | 15.0 | Latest |
| React | 18.0 | 18.2 | Latest |
| TypeScript | 5.0 | 5.2 | Latest |

---

## Future Technology Additions

### Phase 2
- **Caching:** Redis for session management
- **Search:** Elasticsearch for full-text search
- **Real-time:** Socket.io for live updates

### Phase 3+
- **GraphQL:** Apollo Server for complex queries
- **Message Queue:** Kafka/RabbitMQ for events
- **Microservices:** Separate services per domain
- **AI/ML:** OpenAI API for AI Teacher

---

## Why These Technologies?

### TypeScript
✅ Type safety reduces bugs  
✅ Better IDE support  
✅ Self-documenting code  
✅ Scalable for large projects

### Express.js
✅ Lightweight & flexible  
✅ Large ecosystem  
✅ Perfect for REST APIs  
✅ Easy middleware integration

### React
✅ Component-based architecture  
✅ Large community  
✅ Easy to learn & scale  
✅ Performance optimized

### PostgreSQL
✅ Robust ACID compliance  
✅ JSON support for flexible schemas  
✅ Advanced indexing  
✅ Free & open-source

### Docker
✅ Consistent dev/prod environments  
✅ Easy onboarding for new developers  
✅ Simplified deployment  
✅ Microservices ready

---

## Support & Updates

All chosen technologies are:
- ✅ Actively maintained
- ✅ Have large communities
- ✅ Receive regular security updates
- ✅ Have extensive documentation

Next: See `DEVELOPMENT.md` for local setup guide.
