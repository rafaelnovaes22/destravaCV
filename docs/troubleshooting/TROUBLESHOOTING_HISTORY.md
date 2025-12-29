# 🔧 Troubleshooting - Analysis History

## 📊 Current Status

✅ **Backend working perfectly**
- 23 analyses in database
- 5 user analyses (Rafael)
- APIs `/api/ats/history` and `/api/ats/analysis/:id` working
- Complete and valid data

❌ **Frontend with issue**
- Page remains empty when clicking "View Analysis"
- Syntax error fixed in `results.js`
- Issue might be in loading or processing

## 🔍 Diagnostic Steps

### 1. Verify if Backend Server is Running

```bash
# In backend/ directory
npm start
# or
node server.js
```

**Should appear:**
```
✅ SQLite configured: dev.sqlite
🚀 Server running on port 3000
```

### 2. Test APIs Directly

Open browser and test:

```
http://localhost:3000/api/ats/history
http://localhost:3000/api/ats/analysis/328c0ad4-d927-4dac-95c8-abc8492c4358
```

**Expected result:** JSON with analysis data

### 3. Check Browser Console

1. Open `history.html`
2. Press `F12` to open DevTools
3. Go to **Console** tab
4. Click "View Analysis"
5. Observe logs

**Expected logs:**
```
🔍 Loading analysis: 328c0ad4-d927-4dac-95c8-abc8492c4358
📡 Making request to: http://localhost:3000/api/ats/analysis/...
✅ Analysis loaded successfully
💾 Saving to sessionStorage...
🔄 Redirecting to results.html...
```

### 4. Check SessionStorage

On `results.html` page, in console:

```javascript
// Check if data is in sessionStorage
console.log('atsResult:', !!sessionStorage.getItem('atsResult'));
console.log('fileName:', sessionStorage.getItem('fileName'));
console.log('isHistoricalView:', sessionStorage.getItem('isHistoricalView'));

// View complete data
console.log(JSON.parse(sessionStorage.getItem('atsResult')));
```

### 5. Use Test Pages

We created specific debug pages:

1. **`debug-frontend.html`** - Complete frontend test
2. **`results-simple-test.html`** - Simplified results.js test

## 🚨 Common Problems and Solutions

### Problem 1: "CONFIG not found"

**Symptom:** Console error about CONFIG
**Solution:**
```javascript
// Check if config.js is loading
console.log('CONFIG:', window.CONFIG);
```

### Problem 2: "Token not found"

**Symptom:** 401 error on APIs
**Solution:**
```javascript
// Check token
console.log('Token:', localStorage.getItem('token'));

// If no token, login again
```

### Problem 3: "Page remains empty"

**Symptoms:**
- `results.html` loads but shows no data
- Console without apparent errors

**Solutions:**
1. Check if `results.js` is loading:
   ```javascript
   console.log('Results.js loaded:', typeof displayCompatibilityScores);
   ```

2. Check HTML elements:
   ```javascript
   console.log('Conclusion element:', document.getElementById('conclusion'));
   ```

3. Test with manual data:
   ```javascript
   // Force data into sessionStorage
   sessionStorage.setItem('atsResult', JSON.stringify({
       conclusion: "Manual test",
       fileName: "test.pdf",
       isHistoricalView: true
   }));
   location.reload();
   ```

### Problem 4: "CORS Error"

**Symptom:** CORS error in console
**Solution:** Verify if backend server has CORS enabled

### Problem 5: "CSP Error (Content Security Policy)"

**Symptom:** Error about Google fonts
**Solution:** Temporarily ignore (does not affect functionality)

## 🧪 Available Test Scripts

### Backend:
```bash
node backend/debug-complete-flow.js          # Complete debug
node backend/test-user-analyses.js           # Test user analyses
node backend/scripts/validate-history-fix.js # Complete validation
```

### Frontend:
- `debug-frontend.html` - Interactive debug
- `results-simple-test.html` - Simplified test
- `test-results-page.html` - Test with mocked data

## 📋 Verification Checklist

- [ ] Backend server running on port 3000
- [ ] APIs returning correct data
- [ ] Valid authentication token
- [ ] `config.js` loading correctly
- [ ] `results.js` without syntax errors
- [ ] HTML elements exist on page
- [ ] SessionStorage receiving data
- [ ] Console without critical errors

## 🔧 Useful Debug Commands

### In Browser Console:

```javascript
// Activate detailed debug
historyLogger.toggleDebug();

// Test viewAnalysis function
window.viewAnalysis('328c0ad4-d927-4dac-95c8-abc8492c4358');

// Check dependencies
console.log({
    CONFIG: !!window.CONFIG,
    auth: !!window.auth,
    Sanitizer: !!window.Sanitizer,
    historyLogger: !!window.historyLogger
});

// Clear storage
sessionStorage.clear();
localStorage.clear();

// Download debug logs
historyLogger.downloadLogs();
```

## 🎯 Next Steps

1. **Run backend server**
2. **Open `debug-frontend.html`**
3. **Run tests in order**
4. **Identify where it fails**
5. **Use specific debug commands**

## 📞 If It Still Doesn't Work

If after all these steps it still doesn't work:

1. **Capture complete logs** from console
2. **Test with `results-simple-test.html`**
3. **Check for script blockers**
4. **Test in incognito mode**
5. **Check for interfering extensions**

The backend is 100% functional, so the problem is definitely in the frontend and can be identified with these tests!
