# GitHub + Cloudflare Pages Auto-Deploy Setup

## Step 1: Create GitHub Repository

### Option A: GitHub Web Interface
1. Go to **https://github.com/new**
2. Repository name: `reliableboston-website`
3. Description: `Professional aerospace manufacturing website for Reliable Machine Boston`
4. Set to **Public** (required for free Cloudflare Pages)
5. **Do NOT** initialize with README, .gitignore, or license
6. Click **"Create repository"**

### Option B: GitHub CLI (if installed)
```bash
gh repo create reliableboston-website --public --description "Professional aerospace manufacturing website for Reliable Machine Boston"
```

## Step 2: Push Code to GitHub

Copy these commands and run them in your terminal:

```bash
# Navigate to deployment folder
cd cloudflare-deploy

# Initialize git repository
git init
git branch -M main

# Add all files
git add .

# Initial commit
git commit -m "Initial commit - ReliableBoston.com website

- Complete aerospace manufacturing website
- Reliable Machine branding and logo  
- Contact form with Formspree integration
- Employment history conditional fields
- Mobile responsive design
- SEO optimized with sitemap and meta tags
- Security headers and performance optimization
- Ready for Cloudflare Pages deployment"

# Connect to GitHub (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/reliableboston-website.git

# Push to GitHub
git push -u origin main
```

## Step 3: Connect Cloudflare Pages to GitHub

1. Go to **https://dash.cloudflare.com** → **Pages**
2. Click **"Create a project"** → **"Connect to Git"**
3. **Authorize Cloudflare** to access your GitHub
4. Select repository: **`reliableboston-website`**
5. Project name: `reliableboston-com`

### Build Settings:
```
Framework preset: None
Build command: (leave empty)
Build output directory: /
Root directory: /
Environment variables: (none needed)
```

6. Click **"Save and Deploy"**

## Step 4: Configure Custom Domain (No Proxy)

1. In your Pages project → **Custom domains** tab
2. Add domain: `reliableboston.com`
3. Add subdomain: `www.reliableboston.com`  
4. **IMPORTANT**: Set both to **DNS only** (gray cloud ☁️)

## Step 5: DNS Configuration

Add these records at your domain registrar:

```
Type    Name    Content                         Proxy
A       @       [IP from Pages project]         DNS only
CNAME   www     reliableboston-com.pages.dev    DNS only
```

## Auto-Deploy Workflow

Now whenever you make changes:

```bash
# Make your changes to files
# Then commit and push:

git add .
git commit -m "Update website - describe your changes"
git push origin main
```

**Cloudflare Pages will automatically:**
- ✅ Detect the git push
- ✅ Build and deploy your site (takes ~1-2 minutes)
- ✅ Update https://reliableboston.com with your changes
- ✅ Invalidate cache automatically
- ✅ Send deployment notifications

## Branch Protection (Optional)

For production safety, you can:
1. Create `develop` branch for testing
2. Use pull requests to merge to `main`
3. Only `main` branch deploys to production

## Repository Structure

```
reliableboston-website/
├── index.html          # Main website
├── css/
│   └── style.css       # Styles
├── js/
│   └── main.js         # JavaScript
├── images/             # All images including logo
├── _headers           # Cloudflare headers
├── _redirects         # URL redirects  
├── robots.txt         # SEO
├── sitemap.xml        # SEO sitemap
└── test.html          # Test page
```

## Benefits of GitHub Integration

✅ **Version Control** - Track all changes
✅ **Auto-Deploy** - Push to deploy instantly  
✅ **Rollback** - Easy to revert changes
✅ **Collaboration** - Multiple developers can contribute
✅ **Backup** - Code is safely stored on GitHub
✅ **Free** - GitHub public repos and Cloudflare Pages are free

## Deployment Status

Check deployment status at:
- Cloudflare Pages dashboard
- GitHub Actions tab (if using)
- Your website: https://reliableboston.com

**Total setup time: ~10 minutes for auto-deploy on git push!**