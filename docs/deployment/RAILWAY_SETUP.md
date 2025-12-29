# 🚂 Railway Configuration Guide - CV Sem Frescura

## ⚠️ **CRITICAL STEP: Add PostgreSQL**

Your build worked, but the server needs a PostgreSQL database.

### 📋 **Step by Step:**

#### **1. Access Railway Dashboard**
1. Go to: https://railway.app
2. Enter your project **cvsemfrescura**

#### **2. Add PostgreSQL**
1. In the project dashboard, click **"+ New"** or **"Add Service"**
2. Select **"Database"**
3. Choose **"PostgreSQL"**
4. Railway will automatically create:
   - ✅ PostgreSQL Database
   - ✅ `DATABASE_URL` variable (automatic)
   - ✅ Connection between services

#### **3. Wait for Creation (1-2 minutes)**
- Railway will provision the database automatically
- The `DATABASE_URL` variable will be injected into your app

#### **4. Backend Redeploy**
After PostgreSQL is ready:
1. Go to the **backend** service (your main app)
2. Click **"Redeploy"** in the top right corner
3. OR wait for automatic redeploy (detects changes)

### ✅ **Required Environment Variables:**

Besides `DATABASE_URL` (created automatically), configure these in your service:

```env
# Essential (REQUIRED)
NODE_ENV=production
PORT=3000
JWT_SECRET=your_secure_256bit_jwt_key_here
OPENAI_API_KEY=sk-your_openai_key_here
STRIPE_SECRET_KEY=sk_live_your_stripe_key_here

# URLs (Railway configures automatically)
FRONTEND_URL=${{RAILWAY_PUBLIC_DOMAIN}}
BACKEND_URL=${{RAILWAY_PUBLIC_DOMAIN}}
CORS_ORIGIN=${{RAILWAY_PUBLIC_DOMAIN}}

# Email (optional but recommended)
SMTP_HOST=smtp.sendgrid.net
SMTP_PORT=587
SMTP_USER=apikey
SMTP_PASS=SG.your_sendgrid_key
FROM_EMAIL=noreply@cvsemfrescura.com.br

# Stripe Webhook (configure later)
STRIPE_PUBLISHABLE_KEY=pk_live_your_key
STRIPE_WEBHOOK_SECRET=whsec_your_webhook_secret

# Security
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100
```

### 📊 **Verify If It Worked:**

After adding PostgreSQL and redeploying:

1. **Check Logs:**
   ```
   ✅ "PostgreSQL configured for production"
   ✅ "Database synchronized successfully"
   ✅ "Server running on port 3000"
   ```

2. **Test Health Check:**
   ```bash
   curl https://your-app.up.railway.app/health
   ```
   
   Expected response:
   ```json
   {
     "status": "ok",
     "message": "Service working correctly",
     "timestamp": "2025-11-05T...",
     "version": "1.0.0",
     "environment": "production"
   }
   ```

### 🚨 **If Errors Persist:**

#### **Error: `read ECONNRESET`**
- PostgreSQL has not been created yet
- Wait 1-2 minutes after creating the database
- Force a backend redeploy

#### **Error: Missing environment variables**
The health check will return which variables are missing:
```json
{
  "status": "error",
  "message": "Missing environment variables",
  "missing": ["JWT_SECRET", "OPENAI_API_KEY", "STRIPE_SECRET_KEY"]
}
```

Configure missing variables in:
- Railway Dashboard → Your Service → **Variables**

### 💰 **Railway Costs:**

| Plan | Price | Features |
|------|-------|----------|
| **Trial** | Free | $5 initial credit |
| **Hobby** | $5/month | Sufficient for MVP |
| **Pro** | $20/month | Recommended for production |

**PostgreSQL is included** in all plans! 🎉

### 🎯 **Next Steps After Deploy:**

1. ✅ **Test functionalities**:
   - CV Upload
   - OpenAI Analysis
   - Authentication
   - Stripe Payments

2. ✅ **Configure Stripe Webhook**:
   - Stripe Dashboard → Webhooks
   - Endpoint: `https://your-app.up.railway.app/api/stripe/webhook`
   - Events: `payment_intent.succeeded`, `payment_intent.payment_failed`

3. ✅ **Custom Domain** (optional):
   - Railway Dashboard → Settings → Domains
   - Add your domain

---

## 📞 **Support:**

- **Railway Docs**: https://docs.railway.app
- **Railway Discord**: https://discord.gg/railway
- **Status Railway**: https://status.railway.app

---

**🚀 Your "CV Sem Frescura" will be running in a few minutes!** 🎊
