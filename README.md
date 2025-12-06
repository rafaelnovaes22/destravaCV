# 🚀 DestravaCV - Sistema ATS de Análise Inteligente de Currículos

[![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)]()
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)]()
[![License](https://img.shields.io/badge/License-MIT-blue)]()

Sistema completo de análise de currículos utilizando inteligência artificial, desenvolvido com Node.js e integração OpenAI para otimização de processos de recrutamento e compatibilidade com sistemas ATS (Applicant Tracking System).

---

## 📊 Status Atual do Projeto

**Última atualização:** 06 de Dezembro de 2025

### ✅ Funcionalidades Implementadas

| Módulo | Status | Descrição |
|--------|--------|-----------|
| **Autenticação** | ✅ Completo | Login, registro, JWT, recuperação de senha |
| **Análise de CV** | ✅ Completo | Upload e análise inteligente com OpenAI |
| **Dashboard Admin** | ✅ Completo | Gestão completa de usuários e códigos |
| **Pagamentos** | ✅ Completo | Integração Stripe com múltiplos planos |
| **Gift Codes** | ✅ Completo | Sistema de códigos de presente |
| **Histórico** | ✅ Completo | Visualização de análises anteriores |
| **PWA** | ✅ Completo | Progressive Web App com Service Worker |
| **Testes E2E** | ✅ Completo | 14 suites de testes Cypress |
| **Deploy** | ✅ Configurado | Docker + Railway ready |

### 🔄 Em Desenvolvimento

- [ ] Otimizações de performance
- [ ] Melhorias na UI/UX
- [ ] Novas integrações de IA

---

## 🛠️ Tecnologias Utilizadas

### Backend
| Tecnologia | Versão | Uso |
|------------|--------|-----|
| Node.js | 18+ | Runtime JavaScript |
| Express.js | 4.18.2 | Framework web |
| Sequelize ORM | 6.37.7 | ORM para banco de dados |
| SQLite/PostgreSQL | - | Banco de dados |
| OpenAI API | - | Análise inteligente de currículos |
| Stripe | 18.1.1 | Processamento de pagamentos |
| JWT | 9.0.2 | Autenticação segura |
| Winston | 3.17.0 | Sistema de logging |
| Nodemailer | 7.0.3 | Envio de emails |

### Frontend
| Tecnologia | Descrição |
|------------|-----------|
| HTML5/CSS3 | Estrutura e estilização |
| JavaScript Vanilla | Lógica de aplicação |
| PWA | Progressive Web App |
| Service Worker | Cache e offline support |

### DevOps & Infraestrutura
| Ferramenta | Uso |
|------------|-----|
| Docker | Containerização |
| Railway | Deploy em produção |
| Nginx | Proxy reverso |
| GitHub Actions | CI/CD |
| Cypress | Testes E2E |
| Jest | Testes unitários |

---

## 📁 Estrutura do Projeto

```
DestravaCV/
├── 📂 backend/                    # API e lógica de negócio
│   ├── controllers/               # 10 controladores (ATS, Admin, Payment, etc.)
│   ├── models/                    # 7 modelos de dados
│   ├── routes/                    # 11 rotas da API
│   ├── services/                  # 7 serviços (OpenAI, ATS, Email, etc.)
│   ├── utils/                     # 11 utilitários e middlewares
│   ├── migrations/                # Migrations do banco
│   ├── tests/                     # Testes unitários (20+ arquivos)
│   └── cypress/e2e/               # 14 suites de testes E2E
│
├── 📂 frontend/                   # Interface do usuário
│   ├── assets/
│   │   ├── css/                   # 7 arquivos de estilo
│   │   ├── js/                    # 24 scripts JavaScript
│   │   └── img/                   # 17 imagens e ícones
│   ├── *.html                     # 20+ páginas da aplicação
│   ├── manifest.json              # Configuração PWA
│   └── sw.js                      # Service Worker
│
├── 📂 docs/                       # Documentação completa
│   ├── deployment/                # 9 guias de deploy
│   ├── security/                  # 8 documentos de segurança
│   └── archive/                   # Documentação histórica
│
├── 📄 docker-compose.yml          # Configuração Docker
├── 📄 Dockerfile                  # Build da aplicação
├── 📄 railway.json                # Configuração Railway
└── 📄 package.json                # Dependências do projeto
```

---

## 🎯 Funcionalidades Principais

### 1. 📄 Análise Inteligente de Currículos
- Upload de PDF/DOC/DOCX
- Processamento com OpenAI
- Score de compatibilidade ATS
- Sugestões de melhorias
- Análise de palavras-chave

### 2. 🔐 Sistema de Autenticação
- Registro e login seguro
- JWT com criptografia
- Recuperação de senha por email
- Proteção de rotas

### 3. 💳 Sistema de Pagamentos
- Integração Stripe completa
- Múltiplos planos de créditos
- Webhooks para processamento
- Histórico de transações

### 4. 🎁 Sistema de Gift Codes
- Criação em lote
- Códigos personalizáveis
- Data de expiração
- Limite de usos
- Exportação CSV

### 5. 👑 Painel Administrativo
- Dashboard de estatísticas
- Gestão de usuários
- Gestão de gift codes
- Métricas de uso
- Logs e auditoria

### 6. 📊 Histórico de Análises
- Visualização de análises anteriores
- Comparação de resultados
- Download de relatórios

---

## 🔧 Instalação e Configuração

### Pré-requisitos
- Node.js 18+
- SQLite3 ou PostgreSQL
- Conta OpenAI com API key
- Conta Stripe (para pagamentos)

### Instalação Local

```bash
# Clone o repositório
git clone https://github.com/rafaelnovaes22/destravaCV.git
cd destravaCV

# Instale as dependências do backend
cd backend
npm install

# Configure as variáveis de ambiente
cp ../env.example .env
# Edite o arquivo .env com suas configurações

# Inicie o servidor
npm start
```

### Variáveis de Ambiente Necessárias

```env
# Servidor
PORT=3000
NODE_ENV=development

# Banco de Dados
DATABASE_URL=sqlite:./database.sqlite

# Autenticação
JWT_SECRET=sua-chave-secreta

# OpenAI
OPENAI_API_KEY=sua-api-key

# Stripe
STRIPE_SECRET_KEY=sua-chave-stripe
STRIPE_WEBHOOK_SECRET=seu-webhook-secret

# Email
EMAIL_HOST=smtp.example.com
EMAIL_USER=seu-email
EMAIL_PASS=sua-senha
```

### Docker

```bash
# Build e execução com Docker Compose
docker-compose up --build

# Produção
docker-compose -f docker-compose.prod.yml up --build
```

---

## 📋 Endpoints da API

### Autenticação
```
POST /api/auth/login           # Login de usuário
POST /api/auth/register        # Registro de novo usuário
POST /api/password-reset/request  # Solicitar reset de senha
POST /api/password-reset/reset    # Resetar senha
```

### Análise de Currículos
```
POST /api/analysis/upload      # Upload e análise de currículo
GET  /api/analysis/history     # Histórico de análises
GET  /api/analysis/:id         # Detalhes de uma análise
```

### Pagamentos
```
POST /api/payment/create-session  # Criar sessão de pagamento
POST /api/payment/webhook         # Webhook do Stripe
GET  /api/payment/verify          # Verificar status
```

### Gift Codes
```
POST /api/gift-codes/redeem    # Resgatar código
GET  /api/admin/gift-codes     # Listar códigos (admin)
POST /api/admin/gift-codes     # Criar códigos (admin)
```

### Administração
```
GET  /api/admin/users          # Listar usuários
GET  /api/admin/stats          # Estatísticas do sistema
```

---

## 🧪 Testes

### Testes Unitários (Jest)
```bash
cd backend
npm test                  # Executar todos os testes
npm run test:watch        # Modo watch
npm run test:coverage     # Com cobertura
```

### Testes E2E (Cypress)
```bash
cd backend
npm run cypress:open      # Modo interativo
npm run cypress:run       # Modo headless
npm run test:e2e          # Alias para cypress run
```

### Suites de Testes E2E Disponíveis
| Suite | Descrição |
|-------|-----------|
| auth.cy.js | Autenticação e login |
| admin.cy.js | Painel administrativo |
| contact.cy.js | Formulário de contato |
| cv-analysis-complete.cy.js | Análise completa de CV |
| cv-generation.cy.js | Geração de currículo |
| gift-code.cy.js | Sistema de gift codes |
| history.cy.js | Histórico de análises |
| payment.cy.js | Fluxo de pagamentos |
| password-recovery.cy.js | Recuperação de senha |
| performance.cy.js | Testes de performance |
| faq.cy.js | Página de FAQ |
| terms-privacy.cy.js | Termos e privacidade |

---

## 🚀 Deploy em Produção

### Railway (Recomendado)

```bash
# Deploy via Railway CLI
railway login
railway init
railway up
```

Consulte `docs/deployment/RAILWAY_DEPLOY_GUIDE.md` para instruções detalhadas.

### Docker em VPS

```bash
# Build da imagem
docker build -t destravacv .

# Executar container
docker run -d -p 3000:3000 --env-file .env destravacv
```

---

## 🔐 Segurança

| Recurso | Implementação |
|---------|---------------|
| Criptografia | AES-256 para dados sensíveis |
| Validação | Sanitização de todos os inputs |
| Rate Limiting | Proteção contra DDoS/brute force |
| CORS | Configurado adequadamente |
| Headers | Helmet para headers de segurança |
| Logs | Auditoria completa de ações |

Para mais detalhes, consulte `docs/security/SEGURANCA_PRODUCAO.md`.

---

## 📚 Documentação Adicional

| Documento | Descrição |
|-----------|-----------|
| `GUIA_ADMIN_E_NAVEGACAO.md` | Guia do painel administrativo |
| `RAILWAY_SETUP.md` | Configuração do Railway |
| `INSTRUCOES_REINICIAR_SERVIDOR.md` | Como reiniciar o servidor |
| `TROUBLESHOOTING_HISTORICO.md` | Problemas conhecidos e soluções |
| `SECURITY_URGENT.md` | Questões de segurança urgentes |

---

## 🤝 Contribuição

Este projeto segue as melhores práticas de desenvolvimento:

- ✅ Código limpo e bem documentado
- ✅ Testes automatizados (unitários + E2E)
- ✅ Commits semânticos
- ✅ Code review obrigatório
- ✅ CI/CD automatizado

---

## 📄 Licença

MIT License - Consulte o arquivo [LICENSE](LICENSE) para detalhes.

---

## 👨‍💻 Desenvolvedor

**Rafael de Novaes**

- 📧 Email: rafaeldenovaes@gmail.com
- 🔗 LinkedIn: [linkedin.com/in/rafaeldenovaes](https://www.linkedin.com/in/rafaeldenovaes/)
- 🐙 GitHub: [github.com/rafaelnovaes22](https://github.com/rafaelnovaes22)

---

<div align="center">

**⭐ Se este projeto foi útil, considere dar uma estrela no repositório! ⭐**

</div>
