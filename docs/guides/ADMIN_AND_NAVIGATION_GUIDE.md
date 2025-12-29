# 🔧 Admin and Navigation Guide - Fixes Applied

## ✅ Fixed Issues

### 1. **Navigation Links on Landing Page** ✨

**Problem:** "Features" and "How It Works" links were not directing correctly.

**Solution:** Updated `frontend/assets/js/header-new.js` to:
- Use correct smooth scroll for anchors on the same page.
- Ensure links work perfectly on the landing page.

**How to test:**
1. Access `landing.html`
2. Click on "Features" → should scroll smoothly to the features section
3. Click on "How It Works" → should scroll smoothly to the how-it-works section

---

### 2. **Access to Admin Panel** 🔐

**Problem:** Unable to access `admin.html`.

**Cause:** The admin panel requires:
1. Being authenticated (having a valid token)
2. Having administrator permission (`isAdmin: true` in the database)

**Solution:** Created a script to promote users to admin.

---

## 🚀 How to Access the Admin Panel

### **Step 1: Create an account (if you don't have one)**

1. Go to: http://localhost:3000/analisar.html
2. Click on "Create account"
3. Fill in your details
4. Log in

### **Step 2: Promote your user to Admin**

Run the promotion script:

```bash
# In the terminal, at the root of the project
node backend/scripts/promover-admin.js your-email@example.com

# Real example:
node backend/scripts/promover-admin.js rafaeldenovaes@gmail.com
```

**Expected output:**
```
🔧 Connecting to database...
✅ Connected successfully!

🔍 Searching for user: rafaeldenovaes@gmail.com

🚀 Promoting Rafael de Novaes to administrator...

🎉 SUCCESS! User promoted to administrator!

📊 Updated information:
   👤 Name: Rafael de Novaes
   📧 Email: rafaeldenovaes@gmail.com
   👑 Admin: YES ✅
   💳 Credits: 5
   📅 Created at: 05/11/2025

✨ Next steps:
   1. Logout if currently logged in
   2. Login again with this email
   3. Go to: http://localhost:3000/admin.html
   4. You will have access to the administrative panel!
```

### **Step 3: Login Again**

**IMPORTANT:** For admin permissions to apply to your token, you must:

1. **Logout**
2. **Login** again

This ensures a new JWT token is generated with `isAdmin: true`.

### **Step 4: Access Admin**

Now you can access: http://localhost:3000/admin.html

---

## 🔍 Verify Admin Permissions

To verify if your user has admin permissions:

```bash
# List all users and their status
node backend/scripts/listar-usuarios.js
```

Or verify a specific user:

```bash
# Verify a specific email
node backend/scripts/verificar-admin.js your-email@example.com
```

---

## 🎯 Admin Panel Features

With administrative access, you can:

### **1. Statistics Dashboard**
- Total gift codes
- Active codes
- Depleted codes
- Uses today
- Codes expiring in 7 days

### **2. Gift Code Management**
- Batch create codes
- Define prefix, quantity, max uses
- Define expiration date
- Activate/Deactivate codes
- Delete codes
- Export to CSV

### **3. Filters and Search**
- Filter by status (active, inactive, depleted, expired)
- Search by specific code
- Result pagination

### **4. Export**
- Export code list to CSV
- Filter before export

---

## 🛠️ Troubleshooting

### **Error: "Access denied. Admins only..."**

**Cause:** Your user is not an admin or you didn't log in again after promotion.

**Solution:**
1. Verify if promoted: `node backend/scripts/verificar-admin.js your-email@example.com`
2. If yes, logout and login again
3. Try accessing admin.html again

### **Error: "Invalid or expired token"**

**Cause:** Your JWT token has expired or is invalid.

**Solution:**
1. Logout
2. Login again
3. Try accessing admin.html

### **Navigation Links not working**

**Cause:** Header JavaScript might not be loaded.

**Solution:**
1. Open Browser Console (F12)
2. Check for JavaScript errors
3. Reload page (Ctrl+F5)
4. Clear browser cache

### **Smooth scroll not working**

**Cause:** Outdated browser or JavaScript disabled.

**Solution:**
1. Use a modern browser (updated Chrome, Firefox, Edge)
2. Enable JavaScript in browser
3. Check for extensions blocking scripts

---

## 📋 Complete Checklist

### **For Landing Navigation:**
- [ ] ✅ Access landing.html
- [ ] ✅ Click "Features" → should scroll smoothly
- [ ] ✅ Click "How It Works" → should scroll smoothly
- [ ] ✅ Links working correctly

### **For Admin Access:**
- [ ] ✅ Have an account created
- [ ] ✅ Run admin promotion script
- [ ] ✅ Logout
- [ ] ✅ Login again
- [ ] ✅ Access admin.html
- [ ] ✅ See administrative panel functioning

---

## 🔐 Security

**IMPORTANT:**
- ⚠️ Do not promote random users to admin in production
- 🔒 Only administrators can access `/api/admin/*`
- 🛡️ All admin routes verify JWT token + isAdmin
- 🔑 Keep admin credentials secure

---

## 📞 Still having problems?

If you still have issues:

1. **Check console logs:**
   - Open F12 → Console
   - Look for red errors

2. **Check server:**
   - Server must be running at http://localhost:3000
   - Check backend logs

3. **Clear cache:**
   - Ctrl+Shift+Delete
   - Clear cookies and cache
   - Close and open browser

4. **Restart server:**
   ```bash
   # Stop server (Ctrl+C)
   # Start again
   npm start
   ```

---

## ✅ Summary

| Item | Status | Action |
|------|--------|------|
| Navigation Links | ✅ Fixed | Just reload the page |
| Admin Access | ✅ Fixed | Run promotion script |
| Smooth Scroll | ✅ Working | Tested and validated |
| Admin Panel | ✅ Available | Access after becoming admin |

---

**🎉 All set! Your system is working perfectly.**
