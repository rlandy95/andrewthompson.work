# andrewthompson.work

Personal portfolio site with Milo AI assistant, built as a static site + Vercel serverless function.

---

## Project Structure

```
andrewthompson-work/
├── index.html      ← The portfolio site
├── api/
│   └── chat.js     ← Serverless function: proxies to Anthropic API
├── vercel.json     ← Vercel configuration
└── README.md
```

---

## Setup & Deployment

### Step 1 — Push to GitHub

In your terminal:

```bash
cd andrewthompson-work
git init
git add .
git commit -m "Initial commit"
gh repo create andrewthompson-work --public --push --source=.
```

> If you don't have the GitHub CLI (`gh`), go to github.com/new instead, create a repo called `andrewthompson-work`, then follow the "push existing repo" instructions it gives you.

---

### Step 2 — Deploy on Vercel

1. Go to **vercel.com** and sign up / log in with your GitHub account
2. Click **Add New → Project**
3. Import your `andrewthompson-work` repository
4. Leave all settings as default — Vercel will detect it automatically
5. Click **Deploy**

Your site will be live at something like `andrewthompson-work.vercel.app` within a minute.

---

### Step 3 — Add your Anthropic API key

Milo needs your API key to work:

1. In Vercel, go to your project → **Settings → Environment Variables**
2. Add a new variable:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** your key from console.anthropic.com
   - **Environments:** Production, Preview, Development (tick all three)
3. Click **Save**
4. Go to **Deployments** and redeploy (click the three dots → Redeploy) so the variable takes effect

---

### Step 4 — Connect your custom domain

1. In Vercel, go to your project → **Settings → Domains**
2. Type `andrewthompson.work` and click **Add**
3. Vercel will give you DNS records to add — typically an **A record** and a **CNAME**

**At your domain registrar** (wherever you bought andrewthompson.work):
- Delete any existing A records for `@` and `www`
- Add the records Vercel shows you (usually takes 5–30 minutes to propagate)

Once DNS propagates, your site will be live at **https://andrewthompson.work** with a free SSL certificate automatically provisioned.

---

## Making Updates

Any time you push a new commit to the `main` branch on GitHub, Vercel automatically redeploys — no manual steps needed.

```bash
git add .
git commit -m "Update bio"
git push
```

---

## Costs

- **Vercel:** Free tier covers this comfortably (100GB bandwidth, 100k serverless function invocations/month)
- **Anthropic API:** claude-haiku is very cheap — roughly $0.001 per conversation. For a portfolio site, this will cost pennies a month unless it goes viral.
