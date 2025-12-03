# Deitalite Landing Page

Professional single-page landing website for Deitalite restaurant demand forecasting service.

## Overview

This is a static website built with plain HTML, CSS, and JavaScript, designed to be hosted on GitHub Pages. The site showcases Deitalite's weather-smart forecasting service with a clean, conversion-focused design.

## Features

- **Single-page layout** with 9 sections (Hero, Problem, How It Works, Features, ROI, Pricing, FAQ, Final CTA, Footer)
- **Mobile-responsive** design with breakpoints for desktop, tablet, and mobile
- **Brand identity** based on #3e573c (dark sage green) color palette
- **Performance optimized** for fast loading (<2.5s target)
- **SEO-friendly** with meta tags, Open Graph, and schema markup
- **Analytics ready** (Plausible or Google Analytics integration)

## File Structure

```
deitalite-webpage/
├── index.html          # Main landing page
├── privacy.html        # Privacy policy
├── terms.html          # Terms of service
├── css/
│   └── main.css        # Design system and styles
├── js/
│   └── main.js         # Smooth scroll and analytics
├── assets/
│   └── images/         # Images, icons, screenshots
└── README.md           # This file
```

## Setup Instructions

### 1. Required Assets

Before deploying, you need to create/add the following assets to `assets/images/`:

**Critical (must have):**
- `hero-dashboard.png` - Screenshot of Shiny dashboard (1200×800px)
- `logo.svg` - Deitalite logo in brand green
- `favicon.ico` - Browser tab icon (32×32px)

**Recommended:**
- `og-image.png` - Social sharing image (1200×630px)
- Feature icons (SVG files for each feature section)

### 2. Stripe Integration

Replace placeholder links in `index.html` with your actual Stripe checkout URL:

1. Go to [Stripe Dashboard](https://dashboard.stripe.com/)
2. Create a Product: "Deitalite Restaurant Forecasting - 30 Day Access"
3. Set price: €49 (or €79 regular price)
4. Generate Payment Link
5. Replace all instances of `#pricing` in `index.html` with your Stripe checkout URL

**Find and replace:**
```html
<!-- Current placeholder -->
<a href="#pricing" class="btn-primary">Get Started for 49€</a>

<!-- Replace with -->
<a href="https://buy.stripe.com/YOUR_LINK_HERE" class="btn-primary">Get Started for 49€</a>
```

### 3. Local Testing

Test the website locally before deploying:

**Option A: Simple HTTP server (Python)**
```bash
cd deitalite-webpage
python3 -m http.server 8000
# Open http://localhost:8000 in your browser
```

**Option B: VS Code Live Server**
1. Install "Live Server" extension
2. Right-click `index.html`
3. Select "Open with Live Server"

**Option C: Open directly**
```bash
open index.html  # macOS
start index.html  # Windows
xdg-open index.html  # Linux
```

### 4. Deploy to GitHub Pages

**Step 1: Push to GitHub**
```bash
cd deitalite-webpage
git add .
git commit -m "Initial landing page deployment"
git push origin main
```

**Step 2: Enable GitHub Pages**
1. Go to your GitHub repository
2. Click **Settings** → **Pages**
3. Under "Source", select branch **main** and folder **/ (root)**
4. Click **Save**
5. Wait 1-2 minutes for deployment

**Step 3: Verify**
- Your site will be live at: `https://dei.github.io/deitalite-webpage/`
- Check all sections render correctly
- Test CTAs and navigation

### 5. Custom Domain (Optional)

If you own `deitalite.com`:

**Step 1: Create CNAME file**
```bash
echo "www.deitalite.com" > CNAME
git add CNAME
git commit -m "Add custom domain"
git push origin main
```

**Step 2: Configure DNS**
At your domain registrar (Namecheap, GoDaddy, etc.):
- Add CNAME record: `www` → `dei.github.io`
- OR for apex domain: Add A records pointing to GitHub IPs:
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`

**Step 3: Enable HTTPS**
- Go to GitHub repo: Settings → Pages
- Check "Enforce HTTPS"
- Wait 1-24 hours for DNS propagation

### 6. Analytics Setup

**Option A: Plausible (Recommended - Privacy-Friendly)**
1. Sign up at [plausible.io](https://plausible.io)
2. Add your domain
3. Copy the tracking script
4. Add to `<head>` in `index.html`:
```html
<script defer data-domain="yoursite.com" src="https://plausible.io/js/script.js"></script>
```

**Option B: Google Analytics 4**
1. Create GA4 property
2. Get tracking ID
3. Add to `<head>` in `index.html`:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## Updating Content

### Change Pricing
Edit the pricing section in `index.html`:
```html
<span class="price-large">€49</span>
<span class="price-regular">Regular €79/month</span>
```

### Update FAQ
Add/edit questions in the FAQ section:
```html
<div class="faq-item">
  <h3>Your Question?</h3>
  <p>Your answer here.</p>
</div>
```

### Modify Brand Colors
Edit CSS variables in `css/main.css`:
```css
:root {
  --color-brand-green: #3e573c;  /* Primary brand color */
  --color-success: #27AE60;      /* Success/positive metrics */
  --color-orange: #e67e22;       /* Urgency/CTAs */
}
```

## Performance Optimization

Before launch, optimize for speed:

1. **Compress Images**
   - Use [TinyPNG](https://tinypng.com) or [Squoosh](https://squoosh.app)
   - Target: <300KB per image
   - Convert to WebP format for better compression

2. **Minify CSS/JS (Optional)**
   ```bash
   # Install minifier
   npm install -g clean-css-cli uglify-js

   # Minify
   cleancss -o css/main.min.css css/main.css
   uglifyjs js/main.js -o js/main.min.js

   # Update index.html to use .min files
   ```

3. **Test Performance**
   - Run [Google PageSpeed Insights](https://pagespeed.web.dev/)
   - Target: >90 score on mobile and desktop
   - Fix any issues flagged by the tool

## Browser Support

Tested and working on:
- Chrome 90+
- Safari 14+
- Firefox 88+
- Edge 90+
- Mobile Safari (iOS 14+)
- Mobile Chrome (Android 10+)

## Troubleshooting

### Images Not Loading
- Check file paths are correct (case-sensitive)
- Ensure images are in `assets/images/`
- Verify image file names match HTML references

### Smooth Scroll Not Working
- Check `js/main.js` is loaded correctly
- Look for JavaScript errors in browser console (F12)
- Ensure anchor links match section IDs

### GitHub Pages Not Deploying
- Verify branch is set to `main` in Settings → Pages
- Check for errors in Actions tab
- Ensure repository is public (or you have GitHub Pro for private Pages)

### Custom Domain Not Working
- Wait 24 hours for DNS propagation
- Verify CNAME record is correct
- Check DNS with: `dig www.deitalite.com`

## Contact & Support

For questions or issues:
- Email: support@deitalite.com
- Response time: 24-48 hours

## License

© 2025 Deitalite. All rights reserved.
