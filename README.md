# Stream — Site

A plain HTML/JSON static site. No build tools. Publish from the iOS app, deploys instantly.

## One-click deploy

[![Deploy with Vercel](https://vercel.com/button)]([https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/stream-site](https://github.com/withlowe/stream.git))

After clicking:
1. Log in with GitHub
2. Vercel clones the repo and deploys automatically
3. You get a live URL like `yourname.vercel.app`
4. Paste that URL into the app under **Site URL**

## Repo structure

```
/
├── index.html          ← the feed page
├── style.css           ← all styles
├── feed.xml            ← RSS feed (auto-updated by the app)
├── posts.json          ← all posts data (auto-updated by the app)
└── assets/
    └── images/         ← uploaded images (added by the app)
```

## App setup

1. Open the app, tap the servers icon → **+** to add a site
2. Fill in:
   - **App label** — name shown inside the app
   - **Site header name** — name shown on the website
   - **Site URL** — your Vercel URL (e.g. `https://yourname.vercel.app`)
   - **Owner** — your GitHub username
   - **Repository** — your repo name
   - **Branch** — `main`
   - **Token** — GitHub Personal Access Token with `repo` scope
     *(github.com → Settings → Developer settings → Personal access tokens)*

## How it works

When you publish from the app:
1. Image (if any) is uploaded to `assets/images/`
2. `posts.json` is read, new post prepended, written back
3. `feed.xml` is regenerated with the latest 20 posts using absolute image URLs

The site fetches `posts.json` on load and renders the feed client-side. No build step needed.
