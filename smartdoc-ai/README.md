# SmartDoc AI — Vercel Deployment Guide

## Project Structure
```
smartdoc-ai/
├── api/
│   └── gemini.js        ← Serverless function (holds your API key securely)
├── public/
│   └── index.html       ← Frontend (no API key here)
├── vercel.json          ← Routing config
├── package.json
└── README.md
```

## How It Works
```
User browser  →  /api/gemini (Vercel function)  →  Gemini API
                     ↑ API key lives here (env var)
                     ↑ Never exposed to users
```

---

## Deploy to Vercel (Step-by-Step)

### Step 1 — Create a GitHub Repo
1. Go to https://github.com/new
2. Create a new **private** repository called `smartdoc-ai`
3. Upload all files from this folder (drag & drop or use Git)

### Step 2 — Import to Vercel
1. Go to https://vercel.com and sign in (free account)
2. Click **"Add New Project"**
3. Click **"Import"** next to your `smartdoc-ai` repo
4. Click **"Deploy"** (leave all settings as default)

### Step 3 — Add Your Gemini API Key
1. After deploy, go to your project dashboard on Vercel
2. Click **Settings** → **Environment Variables**
3. Click **"Add New"**
   - Name:  `GEMINI_API_KEY`
   - Value: `your-actual-gemini-api-key-here`
   - Environment: ✅ Production  ✅ Preview  ✅ Development
4. Click **Save**

### Step 4 — Redeploy
1. Go to **Deployments** tab
2. Click the **three dots (...)** on the latest deployment
3. Click **"Redeploy"**
4. Wait ~30 seconds — your site is live! 🎉

---

## Get a Free Gemini API Key
1. Go to: https://aistudio.google.com/app/apikey
2. Click "Create API Key"
3. Copy the key and paste it in Step 3 above

---

## Local Development (Optional)
```bash
npm install -g vercel
vercel dev
```
Then set your key in a `.env.local` file:
```
GEMINI_API_KEY=your-key-here
```

---

## Security
- ✅ API key stored in Vercel env vars (encrypted at rest)
- ✅ Key never sent to the browser
- ✅ Users see no API key prompt
- ✅ All AI calls go through your serverless proxy
