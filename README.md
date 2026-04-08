# SportKnow 🏈🏀🏒

AI-powered sports stats search for NFL, NBA, and NHL.

---

## Deploy to sportknow.com in ~15 minutes

### Step 1 — Get your Anthropic API key
1. Go to https://console.anthropic.com
2. Sign up / log in
3. Click **API Keys** → **Create Key**
4. Copy the key (starts with `sk-ant-...`) — save it somewhere safe

---

### Step 2 — Put the code on GitHub
1. Go to https://github.com and create a free account
2. Click **+** → **New repository**
3. Name it `sportknow`, set to Public, click **Create**
4. Click **uploading an existing file**
5. Upload ALL three files from this folder:
   - `index.html`
   - `netlify.toml`
   - `netlify/functions/claude.js`
   
   ⚠️ Make sure `netlify/functions/claude.js` keeps its folder structure when uploading

---

### Step 3 — Deploy on Netlify (free)
1. Go to https://netlify.com and sign up with your GitHub account
2. Click **Add new site** → **Import an existing project**
3. Choose **GitHub** → select your `sportknow` repo
4. Leave all build settings blank (auto-detected from netlify.toml)
5. Click **Deploy site**
6. Your site goes live at something like `amazing-name-123.netlify.app`

---

### Step 4 — Add your API key (secret, secure)
1. In Netlify, go to **Site settings** → **Environment variables**
2. Click **Add a variable**
3. Key: `ANTHROPIC_API_KEY`
4. Value: your key from Step 1 (the `sk-ant-...` one)
5. Click **Save** → go to **Deploys** → **Trigger deploy** → **Deploy site**

---

### Step 5 — Connect sportknow.com
1. Buy `sportknow.com` at https://namecheap.com or https://godaddy.com (~$12/year)
2. In Netlify: **Domain management** → **Add custom domain** → type `sportknow.com`
3. Netlify gives you nameservers (like `dns1.p06.nsone.net`)
4. In your domain registrar (Namecheap/GoDaddy): find **Nameservers** → paste Netlify's nameservers
5. Wait 10–30 minutes → your site is live at sportknow.com with free HTTPS ✅

---

## How the API key stays secret
The file `netlify/functions/claude.js` is a serverless function that runs on Netlify's servers.
Your API key lives in Netlify's environment variables — **never in the HTML or visible to users**.
When someone searches on your site, the request goes: Browser → Netlify Function → Anthropic API.

---

## Project structure
```
sportknow/
├── index.html                  ← the website
├── netlify.toml                ← tells Netlify where functions live
└── netlify/
    └── functions/
        └── claude.js           ← secure API proxy (runs on server)
```

---

## Costs
- **Netlify hosting**: Free (up to 100GB bandwidth/month)
- **Domain**: ~$12/year
- **Anthropic API**: Pay per use (~$0.003 per search) — set a budget limit at console.anthropic.com
