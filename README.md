# 🚀 DestravaCV - Intelligent Resume Analysis ATS System

[![Status](https://img.shields.io/badge/Status-In%20Development-yellow)]()
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)]()
[![License](https://img.shields.io/badge/License-MIT-blue)]()

Complete resume analysis system using artificial intelligence, developed with Node.js and OpenAI integration to optimize recruitment processes and ensure compatibility with ATS (Applicant Tracking System).

---

## 📊 Project Status

**Last Update:** December 6, 2025

### ✅ Implemented Features

| Module | Status | Description |
|--------|--------|-------------|
| **Authentication** | ✅ Complete | Login, register, JWT, password recovery |
| **CV Analysis** | ✅ Complete | Upload and intelligent analysis with OpenAI |
| **Admin Dashboard** | ✅ Complete | Complete user and code management |
| **Payments** | ✅ Complete | Stripe integration with multiple plans |
| **Gift Codes** | ✅ Complete | Gift code system |
| **History** | ✅ Complete | View previous analyses |
| **PWA** | ✅ Complete | Progressive Web App with Service Worker |
| **E2E Tests** | ✅ Complete | 14 Cypress test suites |
| **Deploy** | ✅ Configured | Docker + Railway ready |

### 🔄 In Development

- [ ] Performance optimizations
- [ ] UI/UX improvements
- [ ] New AI integrations

---

## 🛠️ Technologies Used

### Backend
| Technology | Version | Usage |
|------------|---------|-------|
| Node.js | 18+ | JavaScript Runtime |
| Express.js | 4.18.2 | Web Framework |
| Sequelize ORM | 6.37.7 | Database ORM |
| SQLite/PostgreSQL | - | Database |
| OpenAI API | - | Intelligent resume analysis |
| Stripe | 18.1.1 | Payment processing |
| JWT | 9.0.2 | Secure authentication |
| Winston | 3.17.0 | Logging system |
| Nodemailer | 7.0.3 | Email sending |

### Frontend
| Technology | Description |
|------------|-------------|
| HTML5/CSS3 | Structure and styling |
| Vanilla JavaScript | Application logic |
| PWA | Progressive Web App |
| Service Worker | Cache and offline support |

### DevOps & Infrastructure
| Tool | Usage |
|------|-------|
| Docker | Containerization |
| Railway | Production Deploy |
| Nginx | Reverse Proxy |
| GitHub Actions | CI/CD |
| Cypress | E2E Tests |
| Jest | Unit Tests |

---

## 📁 Project Structure

```
DestravaCV/
├── 📂 backend/                    # API and business logic
│   ├── controllers/               # 10 controllers (ATS, Admin, Payment, etc.)
│   ├── models/                    # 7 data models
│   ├── routes/                    # 11 API routes
│   ├── services/                  # 7 services (OpenAI, ATS, Email, etc.)
│   ├── utils/                     # 11 utilities and middlewares
│   ├── migrations/                # Database migrations
│   ├── tests/                     # Unit tests (20+ files)
│   └── cypress/e2e/               # 14 E2E test suites
│
├── 📂 frontend/                   # User Interface
│   ├── assets/
│   │   ├── css/                   # 7 style files
│   │   ├── js/                    # 24 JavaScript scripts
│   │   └── img/                   # 17 images and icons
│   ├── *.html                     # 20+ application pages
│   ├── manifest.json              # PWA Configuration
│   └── sw.js                      # Service Worker
│
├── 📂 docs/                       # Complete documentation
│   ├── deployment/                # 9 deployment guides
│   ├── security/                  # 8 security documents
│   └── archive/                   # Historical documentation
│
├── 📄 docker-compose.yml          # Docker Configuration
├── 📄 Dockerfile                  # Application Build
├── 📄 railway.json                # Railway Configuration
└── 📄 package.json                # Project Dependencies
```

---

## 🎯 Key Features

### 1. 📄 Intelligent Resume Analysis
- PDF/DOC/DOCX Upload
- Processing with OpenAI
- ATS compatibility score
- Improvement suggestions
- Keyword analysis

### 2. 🔐 Authentication System
- Secure registration and login
- Encrypted JWT
- Password recovery via email
- Route protection

### 3. 💳 Payment System
- Complete Stripe integration
- Multiple credit plans
- Webhooks for processing
- Transaction history

### 4. 🎁 Gift Code System
- Batch creation
- Customizable codes
- Expiration date
- Usage limit
- CSV Export

### 5. 👑 Admin Panel
- Statistics dashboard
- User management
- Gift code management
- Usage metrics
- Logs and audit

### 6. 📊 Analysis History
- View previous analyses
- Compare results
- Download reports

---

## 🔧 Installation and Configuration

### Prerequisites
- Node.js 18+
- SQLite3 or PostgreSQL
- OpenAI Account with API key
- Stripe Account (for payments)

### Local Installation

```bash
# Clone the repository
git clone https://github.com/rafaelnovaes22/destravaCV.git
cd destravaCV

# Install backend dependencies
cd backend
npm install

# Configure environment variables
cp ../env.example .env
# Edit the .env file with your settings

# Start the server
npm start
```

### Required Environment Variables

```env
# Server
PORT=3000
NODE_ENV=development

# Database
DATABASE_URL=sqlite:./database.sqlite

# Authentication
JWT_SECRET=your-secret-key

# OpenAI
OPENAI_API_KEY=your-api-key

# Stripe
STRIPE_SECRET_KEY=your-stripe-key
STRIPE_WEBHOOK_SECRET=your-webhook-secret

# Email
EMAIL_HOST=smtp.example.com
EMAIL_USER=your-email
EMAIL_PASS=your-password
```

### Docker

```bash
# Build and run with Docker Compose
docker-compose up --build

# Production
docker-compose -f docker-compose.prod.yml up --build
```

---

## 📋 API Endpoints

### Authentication
```
POST /api/auth/login           # User Login
POST /api/auth/register        # New User Registration
POST /api/password-reset/request  # Request Password Reset
POST /api/password-reset/reset    # Reset Password
```

### Resume Analysis
```
POST /api/analysis/upload      # Upload and analyze resume
GET  /api/analysis/history     # Analysis History
GET  /api/analysis/:id         # Analysis Details
```

### Payments
```
POST /api/payment/create-session  # Create payment session
POST /api/payment/webhook         # Stripe Webhook
GET  /api/payment/verify          # Verify status
```

### Gift Codes
```
POST /api/gift-codes/redeem    # Redeem code
GET  /api/admin/gift-codes     # List codes (admin)
POST /api/admin/gift-codes     # Create codes (admin)
```

### Administration
```
GET  /api/admin/users          # List users
GET  /api/admin/stats          # System statistics
```

---

## 🧪 Tests

### Unit Tests (Jest)
```bash
cd backend
npm test                  # Run all tests
npm run test:watch        # Watch mode
npm run test:coverage     # With coverage
```

### E2E Tests (Cypress)
```bash
cd backend
npm run cypress:open      # Interactive mode
npm run cypress:run       # Headless mode
npm run test:e2e          # Alias for cypress run
```

### Available E2E Test Suites
| Suite | Description |
|-------|-------------|
| auth.cy.js | Authentication and login |
| admin.cy.js | Administrative panel |
| contact.cy.js | Contact form |
| cv-analysis-complete.cy.js | Complete CV Analysis |
| cv-generation.cy.js | Resume generation |
| gift-code.cy.js | Gift code system |
| history.cy.js | Analysis history |
| payment.cy.js | Payment flow |
| password-recovery.cy.js | Password recovery |
| performance.cy.js | Performance tests |
| faq.cy.js | FAQ Page |
| terms-privacy.cy.js | Terms and privacy |

---

## 🚀 Production Deploy

### Railway (Recommended)

```bash
# Deploy via Railway CLI
railway login
railway init
railway up
```

See `docs/deployment/RAILWAY_DEPLOY_GUIDE.md` for detailed instructions.

### Docker on VPS

```bash
# Build image
docker build -t destravacv .

# Run container
docker run -d -p 3000:3000 --env-file .env destravacv
```

---

## 🔐 Security

| Feature | Implementation |
|---------|----------------|
| Encryption | AES-256 for sensitive data |
| Validation | Sanitization of all inputs |
| Rate Limiting | Protection against DDoS/brute force |
| CORS | Properly configured |
| Headers | Helmet for security headers |
| Logs | Complete action audit |

For more details, see `docs/security/SEGURANCA_PRODUCAO.md`.

---

## 📚 Additional Documentation

| Document | Description |
|----------|-------------|
| `ADMIN_AND_NAVIGATION_GUIDE.md` | Admin panel guide |
| `RAILWAY_SETUP.md` | Railway Configuration |
| `SERVER_RESTART_INSTRUCTIONS.md` | How to restart the server |
| `TROUBLESHOOTING_HISTORY.md` | Known issues and solutions |
| `SECURITY_URGENT.md` | Urgent security issues |

---

## 🤝 Contribution

This project follows development best practices:

- ✅ Clean and well-documented code
- ✅ Automated tests (unit + E2E)
- ✅ Semantic Commits
- ✅ Mandatory Code Review
- ✅ Automated CI/CD

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Developer

**Rafael de Novaes**

- 📧 Email: rafaeldenovaes@gmail.com
- 🔗 LinkedIn: [linkedin.com/in/rafaeldenovaes](https://www.linkedin.com/in/rafaeldenovaes/)
- 🐙 GitHub: [github.com/rafaelnovaes22](https://github.com/rafaelnovaes22)

---

<div align="center">

**⭐ If this project was useful, please consider giving a star on the repository! ⭐**

</div>
