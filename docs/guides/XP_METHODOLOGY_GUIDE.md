# 🚀 XP Methodology Guide - destravaCV

## 📋 Table of Contents
- [Introduction](#introduction)
- [Implemented XP Practices](#implemented-xp-practices)
- [Environment Setup](#environment-setup)
- [Development Flow](#development-flow)
- [E2E Tests with Cypress](#e2e-tests-with-cypress)
- [Continuous Integration](#continuous-integration)
- [Metrics and Monitoring](#metrics-and-monitoring)

## 🎯 Introduction

This document describes the implementation of the Extreme Programming (XP) methodology in the destravaCV project, focusing on code quality, automated tests, and continuous delivery.

## 🛠️ Implemented XP Practices

### 1. Test-Driven Development (TDD)
```bash
# TDD Flow
1. Write a failing test
2. Implement minimum code to pass
3. Refactor keeping tests green
```

### 2. Pair Programming
- **Pair Rotation**: Switch partners every 2 hours
- **Driver/Navigator**: Switch roles every 30 minutes
- **Remote Pairing**: Use VS Code Live Share or similar

### 3. Continuous Integration
- **Frequent Commits**: At least 3x per day
- **Automated Build**: GitHub Actions
- **Tests on Every Push**: Complete suite

### 4. Small Releases
- **Daily Deploy**: Small and incremental features
- **Feature Flags**: Feature control
- **Quick Rollback**: Maximum 5 minutes

## 🔧 Environment Setup

### Dependency Installation
```bash
# Backend
cd backend
npm install

# Install Cypress
npm install --save-dev cypress@latest
```

### E2E Test Configuration
```javascript
// cypress.config.js
module.exports = defineConfig({
  e2e: {
    baseUrl: 'http://localhost:3001',
    viewportWidth: 1280,
    viewportHeight: 720,
    video: true,
    screenshotOnRunFailure: true
  }
});
```

## 📈 Development Flow

### 1. Planning Game
```markdown
## Sprint Planning
- Duration: 1 week
- Points per Sprint: 20-30
- Daily Standup: 15 minutes
```

### 2. User Stories
```markdown
## User Story Template
As [user type]
I want [feature]
So that [benefit]

### Acceptance Criteria:
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] E2E tests passing
```

### 3. Development
```bash
# 1. Create feature branch
git checkout -b feature/new-feature

# 2. Write E2E test
npm run cypress:open

# 3. Implement code
# ... development ...

# 4. Run tests
npm run test:e2e

# 5. Commit and Push
git add .
git commit -m "feat: implement new feature"
git push origin feature/new-feature
```

## 🧪 E2E Tests with Cypress

### Test Structure
```
backend/cypress/
├── e2e/
│   ├── auth.cy.js              ✅ Implemented
│   ├── payment.cy.js           ✅ Implemented
│   ├── gift-code.cy.js         ✅ Implemented
│   ├── cv-generation.cy.js     ✅ Implemented
│   ├── cv-analysis-complete.cy.js  ✅ New
│   ├── history.cy.js           🚧 Pending
│   ├── password-reset.cy.js   🚧 Pending
│   └── admin-panel.cy.js      🚧 Pending
├── fixtures/
│   └── test-data.json
└── support/
    └── commands.js
```

### Test Commands
```bash
# Run all tests
npm run test:e2e

# Open Cypress UI
npm run cypress:open

# Run specific tests
npm run cypress:run -- --spec "cypress/e2e/auth.cy.js"

# Run with video recording
npm run cypress:run -- --record
```

### E2E Test Example
```javascript
describe('CV Analysis Flow', () => {
  beforeEach(() => {
    cy.login('user@example.com', 'password');
    cy.visit('/analisar');
  });

  it('should complete full analysis', () => {
    // Upload CV
    cy.uploadCV('fixtures/sample-cv.pdf');
    
    // Add job description
    cy.fillJobDescription('Full Stack Developer...');
    
    // Start analysis
    cy.get('[data-cy="analyze-button"]').click();
    
    // Check results
    cy.checkAnalysisResults();
  });
});
```

## 🚀 Continuous Integration

### GitHub Actions Workflow
```yaml
# .github/workflows/ci.yml
name: CI Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    
    - name: Install dependencies
      run: |
        cd backend
        npm ci
    
    - name: Run unit tests
      run: |
        cd backend
        npm test
    
    - name: Run E2E tests
      run: |
        cd backend
        npm run test:e2e:ci
    
    - name: Upload test results
      uses: actions/upload-artifact@v3
      with:
        name: cypress-results
        path: backend/cypress/videos
```

### Automated Deploy
```yaml
# .github/workflows/deploy.yml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    
    steps:
    - name: Deploy to Railway
      run: |
        curl -X POST ${{ secrets.RAILWAY_WEBHOOK_URL }}
```

## 📊 Metrics and Monitoring

### Test Coverage
```bash
# Generate coverage report
npm run test:coverage

# Target Metrics:
- Code coverage: > 80%
- E2E coverage: 100% of critical flows
- Execution time: < 5 minutes
```

### Quality Dashboard
```markdown
## XP Metrics
- ✅ Deploy Frequency: 1-3x/day
- ✅ Lead Time: < 2 hours
- ✅ MTTR: < 30 minutes
- ✅ Success Rate: > 95%
```

### Production Monitoring
```javascript
// Integration with Winston for logs
const logger = require('./utils/logger');

// Log important events
logger.info('CV Analysis started', {
  userId: req.user.id,
  fileSize: file.size,
  timestamp: new Date()
});
```

## 🎯 Next Steps

### Current Sprint
- [x] Implement complete analysis E2E test
- [ ] Create history tests
- [ ] Implement password recovery tests
- [ ] Add admin panel tests
- [ ] Configure complete CI/CD pipeline

### Future Improvements
1. **Performance Tests**
   - Load testing with Artillery
   - Stress testing with K6
   
2. **Security Tests**
   - OWASP ZAP integration
   - Dependency scanning
   
3. **Accessibility Tests**
   - Cypress-axe integration
   - WCAG compliance

## 📚 Useful Resources

- [Cypress Documentation](https://docs.cypress.io)
- [XP Practices Guide](http://www.extremeprogramming.org)
- [TDD by Example - Kent Beck](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530)
- [Continuous Delivery - Jez Humble](https://continuousdelivery.com)

## 🤝 Contributing

1. Always write tests before code
2. Pair program for complex features
3. Keep commits small and frequent
4. Review code before merging
5. Keep documentation updated

---

**Last update**: January 2025
**Maintained by**: destravaCV Development Team