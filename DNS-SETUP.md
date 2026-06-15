# DNS Setup for reliableboston.com (NO PROXY MODE)

## Option 1: Direct DNS Records (Recommended - No Cloudflare Proxy)

Add these DNS records to your domain registrar (like GoDaddy, Namecheap, etc.):

```
Type    Name    Value                           TTL     Proxy
A       @       Pages IP (will be provided)     300     DNS Only
CNAME   www     reliableboston.pages.dev        300     DNS Only
TXT     @       "v=spf1 include:_spf.google.com ~all"  300     DNS Only
```

## Option 2: Cloudflare DNS Only (No Proxy)

If using Cloudflare for DNS management only:

1. Add domain to Cloudflare
2. Set these records with GRAY CLOUD (DNS only):

```
Type    Name    Content
A       @       [Pages IP Address]
CNAME   www     reliableboston.pages.dev
TXT     @       "v=spf1 -all"
```

## Cloudflare Pages Setup Steps

### 1. Upload Website
1. Go to Cloudflare Dashboard → Pages
2. "Create a project" → "Upload assets"
3. Project name: `reliableboston-com`
4. Upload contents of cloudflare-deploy/ folder

### 2. Custom Domain Configuration
1. In Pages project → Custom domains tab
2. Add domain: `reliableboston.com`
3. Add subdomain: `www.reliableboston.com`
4. **IMPORTANT**: Set both to "DNS only" (gray cloud)

### 3. Pages Project Settings
```
Build command: (none - static site)
Build output directory: /
Root directory: /
Environment variables: (none needed)
```

### 4. SSL Certificate
- Cloudflare will auto-provision SSL even with DNS-only mode
- Certificate authority: Let's Encrypt
- Force HTTPS: Enabled

## Email Setup (Optional)

For professional email (info@reliableboston.com):

### Google Workspace
```
Type    Name    Value                   Priority
MX      @       smtp.google.com         10
TXT     @       "v=spf1 include:_spf.google.com ~all"
```

### Microsoft 365
```
Type    Name    Value                   Priority  
MX      @       reliableboston-com.mail.protection.outlook.com    10
TXT     @       "v=spf1 include:spf.protection.outlook.com ~all"
```

## Verification Steps

1. Deploy to Cloudflare Pages
2. Get Pages IP address from project settings
3. Update DNS A record with that IP
4. Wait 5-15 minutes for propagation
5. Visit https://reliableboston.com

## No Proxy Benefits
- Direct connection to origin
- No Cloudflare caching interference  
- Full control over headers and responses
- Faster initial setup
- No proxy-related issues