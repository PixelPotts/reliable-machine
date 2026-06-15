# ReliableBoston.com Deployment Checklist ✅

## Pre-Deployment ✅ COMPLETE
- [x] Website files optimized
- [x] Images compressed and optimized  
- [x] SSL configuration prepared
- [x] SEO meta tags added
- [x] Sitemap.xml created
- [x] Robots.txt configured
- [x] Security headers set
- [x] Contact form with Formspree ready
- [x] Employment history fields configured

## Deployment Steps

### 1. Cloudflare Pages Upload
- [ ] Go to dash.cloudflare.com → Pages
- [ ] Create new project → Upload assets  
- [ ] Project name: `reliableboston-com`
- [ ] Upload: `reliableboston-website.zip` OR drag contents of `cloudflare-deploy/` folder
- [ ] Deploy (takes ~2 minutes)

### 2. Get Pages URL
After deployment, note your Pages URL:
- Format: `https://reliableboston-com.pages.dev`
- This is your staging URL for testing

### 3. DNS Configuration (NO PROXY)

#### Option A: At Your Domain Registrar
Add these DNS records where you bought reliableboston.com:

```
Type    Name    Value                           TTL
A       @       [See Pages project for IP]     300
CNAME   www     reliableboston-com.pages.dev    300  
```

#### Option B: Cloudflare DNS (DNS Only)
1. Add reliableboston.com to Cloudflare (free plan)
2. Change nameservers at registrar
3. Add records with GRAY CLOUD (DNS only):

```
A       @       [Pages IP]
CNAME   www     reliableboston-com.pages.dev
```

### 4. Connect Custom Domain
- [ ] In Pages project → Custom domains
- [ ] Add `reliableboston.com`
- [ ] Add `www.reliableboston.com`  
- [ ] Set both to DNS-only (gray cloud)
- [ ] Wait for SSL certificate provisioning (~5-15 minutes)

### 5. Verification
- [ ] Visit https://reliableboston.com
- [ ] Test contact form submission
- [ ] Test employment history fields
- [ ] Verify mobile responsiveness
- [ ] Check SSL certificate (green lock)

## Post-Deployment (Optional)

### Email Setup
- [ ] Choose provider (Google Workspace, Microsoft 365, etc.)
- [ ] Add MX records for email
- [ ] Set up info@reliableboston.com

### Analytics (Optional)  
- [ ] Google Analytics
- [ ] Google Search Console
- [ ] Cloudflare Web Analytics (built-in)

### Performance Monitoring
- [ ] GTmetrix speed test
- [ ] Google PageSpeed Insights
- [ ] Pingdom monitoring

## Troubleshooting

**If site doesn't load:**
1. Check DNS propagation: whatsmydns.net
2. Verify A record points to Pages IP
3. Ensure SSL certificate is active

**If contact form doesn't work:**
1. Check Formspree endpoint: https://formspree.io/f/mojzkppd
2. Verify form action URL in index.html
3. Test employment history dropdown

## Support Contacts
- Cloudflare Pages: docs.cloudflare.com/pages
- DNS Issues: Your registrar support
- Formspree: formspree.io/help

**Estimated Total Setup Time: 15-30 minutes**