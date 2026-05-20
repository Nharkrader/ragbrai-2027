# CitySouvenirs.Com — BigCommerce to Shopify Migration Plan

**Source:** BigCommerce (CitySouvenirs.Com)  
**Destination:** Shopify — Shop I LOVE NY (shopiloveny.com) — Shopify Plan  
**Currency:** USD | **Timezone:** EDT | **Country:** United States

---

## Overview

This plan moves CitySouvenirs.Com from BigCommerce to Shopify in nine phases. Work through each phase in order. Do not point your live domain to Shopify until Phase 8 (Go-Live).

---

## Phase 1 — Audit & Inventory (Before You Touch Anything)

**Goal:** Know exactly what you have before you move it.

### 1.1 Export a full data snapshot from BigCommerce
1. Log in to BigCommerce Admin.
2. Go to **Products → Export** and export all products (CSV). Include all variants, images, SKUs, pricing, weight, dimensions, and inventory counts.
3. Go to **Customers → Export** and export all customer records.
4. Go to **Orders → Export** and export your full order history (for reference/records — orders do not migrate live).
5. Export your **coupon codes** and **discount rules** from the Promotions section.
6. Document all active **third-party apps and integrations** (payment gateways, shipping carriers, reviews, loyalty programs, email marketing, ERP/POS connections).
7. Screenshot or document your **current navigation menus** (header, footer, mobile).
8. List every **custom page** (About, FAQ, Shipping Policy, Return Policy, etc.) and copy the content.
9. List all **blog posts** with their URLs.
10. Run a **full site crawl** (Screaming Frog free tier or Sitebulb) and export all URLs — you'll need these for 301 redirects.

### 1.2 Catalog sizing
Count the following (shapes your app and plan choices):
- Total number of SKUs / product variants
- Number of product images
- Number of customer records
- Number of historical orders

### 1.3 Confirm your Shopify plan limits
You are on the **Shopify plan** ($79/mo). Key limits relevant to this migration:
- Up to **1,000 inventory locations**
- **2 staff accounts** (upgrade to Advanced if more needed)
- Standard reports included
- Transaction fees apply unless using Shopify Payments

---

## Phase 2 — Shopify Store Foundation Setup

**Goal:** Configure the Shopify store before any data arrives.

### 2.1 Store settings
1. In Shopify Admin → **Settings → General**: confirm store name, address, and contact email match what you want customers to see.
2. **Settings → Taxes**: configure US tax rates (or enable automatic tax calculation).
3. **Settings → Shipping and Delivery**: create shipping zones and rates that match your current BigCommerce setup.
4. **Settings → Payments**: 
   - Enable **Shopify Payments** to eliminate transaction fees (requires SSN/EIN and bank account).
   - If you use a third-party gateway (Authorize.net, PayPal, Stripe directly), add it here — note the 1% transaction fee on the Shopify plan for non-Shopify Payments.
5. **Settings → Checkout**: configure guest checkout, account requirements, and contact fields.
6. **Settings → Notifications**: customize transactional email templates (order confirmation, shipping, etc.).
7. **Settings → Legal**: add your Refund, Privacy, and Terms of Service pages.

### 2.2 Set up your domain (staging mode)
- Do NOT change DNS yet. Keep CitySouvenirs.Com pointing to BigCommerce.
- In Shopify Admin → **Settings → Domains**: add `citysouvenirs.com` as a domain but do not make it primary yet. This lets you preview the Shopify store at your `.myshopify.com` URL while BigCommerce stays live.

---

## Phase 3 — Theme Selection & Design

**Goal:** Match or improve the look and feel of your current store.

### 3.1 Choose a theme
1. Browse the **Shopify Theme Store** — recommended starting points for souvenir/gift/tourism stores:
   - **Impulse** (fast, great for large catalogs with filtering)
   - **Prestige** (premium look, good for branded products)
   - **Debut / Dawn** (free, clean, good for getting started quickly)
2. Purchase or activate your chosen theme.
3. Use the **Theme Editor** (Online Store → Themes → Customize) to:
   - Upload your logo.
   - Set brand colors and fonts to match CitySouvenirs.Com.
   - Configure homepage sections (hero banner, featured collections, announcement bar).
   - Set up header and footer navigation.

### 3.2 Recreate custom pages
For each page you documented in Phase 1:
1. Go to **Online Store → Pages → Add Page**.
2. Paste/reformat the content.
3. Set the SEO URL handle to match the BigCommerce URL slug exactly (e.g., `/about-us`, `/faq`).

### 3.3 Recreate blog content
1. **Online Store → Blog Posts → Add Blog Post** for each post.
2. Match the URL slug exactly to the BigCommerce URL.
3. Set published date, author, and tags.

---

## Phase 4 — Product Catalog Migration

**Goal:** Move all products, variants, images, and inventory into Shopify.

### 4.1 Option A — Shopify Importer (recommended for most stores)
1. Install the free **Matrixify (Excelify)** app from the Shopify App Store — the most reliable bulk importer for BigCommerce data.
2. Download the Matrixify BigCommerce import template.
3. Map your BigCommerce CSV columns to Matrixify's column format. Key mappings:
   - Product title, body (description), vendor, product type, tags
   - Variants: SKU, price, compare-at price, weight, dimensions
   - Inventory: quantity, tracked vs. untracked
   - Images: URLs (Matrixify will pull them from BigCommerce CDN automatically)
   - SEO: meta title, meta description, URL handle
4. Run a **test import** with 10–20 products first. Verify in Shopify that products, variants, and images look correct.
5. Run the **full import** once the test passes.

### 4.2 Option B — Store Migration Apps (faster, less control)
- **Cart2Cart** or **LitExtension** can automate the BigCommerce → Shopify migration for an additional fee (~$99–$299 depending on catalog size). They handle products, customers, and orders in one pass. Good option if your catalog is large (1,000+ SKUs).

### 4.3 Post-import product QA checklist
- [ ] Spot-check 20+ products across different categories
- [ ] Verify all variants (size, color, style) are present
- [ ] Confirm images loaded correctly and are not broken
- [ ] Check prices, compare-at prices, and sale pricing
- [ ] Verify inventory quantities match BigCommerce
- [ ] Confirm product URLs (handles) match intended SEO slugs
- [ ] Check product weights/dimensions for shipping calculations

### 4.4 Collections (categories)
1. In Shopify, BigCommerce "Categories" become **Collections**.
2. Create collections manually or use Matrixify to bulk-create them.
3. Use **smart collections** (auto-assign by tag, product type, or vendor) where possible to reduce ongoing maintenance.
4. Recreate your category hierarchy using collection nesting in navigation menus.

---

## Phase 5 — Customer Data Migration

**Goal:** Move customer accounts so returning buyers can log in.

### 5.1 Import customers
1. Format your BigCommerce customer export to match Shopify's customer CSV format (First Name, Last Name, Email, Phone, Address fields, Tags, Note).
2. In Shopify Admin → **Customers → Import**: upload the CSV.
3. **Important:** Passwords cannot be migrated — BigCommerce hashes passwords with a different algorithm. Shopify will send customers a **password reset email** the first time they try to log in. Communicate this proactively in your launch announcement.

### 5.2 Customer segments and tags
- Apply tags during import to recreate any customer groups you used in BigCommerce (e.g., `wholesale`, `vip`, `newsletter`).

---

## Phase 6 — Apps, Integrations & Functionality

**Goal:** Restore all the features your BigCommerce store had.

### 6.1 Map BigCommerce apps to Shopify equivalents

| BigCommerce Feature | Shopify Equivalent |
|---|---|
| Product Reviews | Judge.me (free tier available) or Shopify Product Reviews |
| Abandoned Cart Emails | Built into Shopify (Settings → Checkout) |
| Email Marketing | Shopify Email (free up to 10k/mo) or Klaviyo |
| Loyalty / Rewards | Smile.io or LoyaltyLion |
| Subscription / Recurring | Recharge or Seal Subscriptions |
| Wholesale / B2B | Shopify B2B (Plus) or Wholesale Club app |
| Size Chart | Free size chart apps or theme built-in |
| Live Chat | Tidio, Gorgias, or Shopify Inbox (free) |
| SEO Tools | Plug in SEO or SEO Manager |
| Upsell / Cross-sell | Frequently Bought Together or ReConvert |
| Google Shopping Feed | Google & YouTube channel (free, built-in) |
| Facebook/Instagram | Facebook & Instagram channel (free, built-in) |

### 6.2 Install and configure chosen apps
- Install apps one at a time and test each before adding the next.
- Check that apps do not conflict with each other or slow down your theme.

### 6.3 Discount codes
- Recreate discount codes manually in Shopify Admin → **Discounts**.
- For large numbers of codes, use the **Bulk Discounts** app or Matrixify.

---

## Phase 7 — SEO Preservation

**Goal:** Protect your Google rankings — this is the highest-risk part of any migration.

### 7.1 301 redirect map
1. Take the full URL list you crawled in Phase 1.
2. For each BigCommerce URL, map it to the new Shopify URL. Common patterns:
   - `/product-name/` → `/products/product-name`
   - `/category-name/` → `/collections/category-name`
   - `/pages/page-name` → `/pages/page-name` (usually same)
   - `/blog/post-name` → `/blogs/news/post-name`
3. Build a CSV with `old_url, new_url` columns.

### 7.2 Upload redirects to Shopify
1. In Shopify Admin → **Online Store → Navigation → URL Redirects**.
2. Import your redirect CSV (Shopify supports bulk CSV upload).
3. Test 20+ redirects manually after upload.

### 7.3 Preserve on-page SEO
- Ensure every product, collection, and page has a **meta title** and **meta description** imported from BigCommerce.
- Match URL handles (slugs) exactly where possible — this eliminates the need for redirects on those URLs.
- Submit a new XML sitemap to Google Search Console after launch (`yourstore.com/sitemap.xml` — Shopify generates this automatically).

### 7.4 Canonical tags
- Shopify handles canonical tags automatically. No action needed.

---

## Phase 8 — Pre-Launch Testing

**Goal:** Validate everything before going live. Test on your `.myshopify.com` URL.

### 8.1 Functional testing checklist
- [ ] Place a **test order** end-to-end (add to cart → checkout → payment → confirmation email)
- [ ] Test with a real credit card using Shopify Payments test mode
- [ ] Test PayPal checkout if applicable
- [ ] Test **guest checkout** and **account checkout**
- [ ] Apply a discount code at checkout
- [ ] Verify order confirmation email arrives and looks correct
- [ ] Verify shipping notification email
- [ ] Test the **Returns / Contact** forms
- [ ] Test on mobile (iOS Safari, Android Chrome)
- [ ] Test page speed (Google PageSpeed Insights — aim for 70+ mobile)
- [ ] Test all navigation menus (header, footer, mobile hamburger)
- [ ] Verify all collection pages load and filter correctly
- [ ] Verify search works and returns relevant results
- [ ] Test 404 page looks branded

### 8.2 Inventory accuracy check
- Run a spot-check comparing BigCommerce inventory quantities to Shopify before go-live.
- If there is a gap between migration and go-live, do a final inventory sync the night before launch.

---

## Phase 9 — Go-Live & Post-Launch

**Goal:** Cut over the domain with minimal downtime and monitor closely.

### 9.1 Domain cutover (schedule for low-traffic window — Tuesday–Thursday night)
1. In Shopify Admin → **Settings → Domains**: confirm `citysouvenirs.com` is added.
2. Log in to your domain registrar (GoDaddy, Namecheap, etc.).
3. Update DNS records:
   - **@ (root) record**: change `A` record to point to Shopify's IP: `23.227.38.65`
   - **www record**: change `CNAME` to `shops.myshopify.com`
4. Back in Shopify → **Settings → Domains**: click **"Make primary"** for `citysouvenirs.com`.
5. Enable **Redirect all traffic to this domain**.
6. DNS propagation takes 15 minutes to 48 hours. Your `.myshopify.com` URL stays live throughout.

### 9.2 SSL certificate
- Shopify auto-provisions a free SSL certificate (Let's Encrypt) within minutes of DNS propagation. No action needed.

### 9.3 Immediately after go-live
- [ ] Place a live test order (then refund it)
- [ ] Verify SSL padlock shows in browser
- [ ] Check that `citysouvenirs.com` and `www.citysouvenirs.com` both load Shopify
- [ ] Test 5–10 redirects from BigCommerce URLs
- [ ] Check Google Search Console → verify property still shows data (add Shopify domain property if needed)
- [ ] Submit new sitemap in Google Search Console: `https://citysouvenirs.com/sitemap.xml`
- [ ] Update any Google Ads, Meta Ads, or email links that point to old BigCommerce URLs
- [ ] Update your Google Business Profile URL if applicable
- [ ] Notify your email list about the new store (mention password reset requirement)

### 9.4 Keep BigCommerce on standby
- Do NOT cancel your BigCommerce subscription for at least **30 days** after go-live.
- Keep it in a read-only / password-protected state as a fallback.
- After 30 days, if all is stable, cancel BigCommerce.

### 9.5 Post-launch monitoring (first 30 days)
- Monitor **Google Search Console** weekly for crawl errors or ranking drops.
- Monitor **Shopify Analytics** → Sessions, Conversion Rate, Top Products daily for the first two weeks.
- Check **404 error reports** in Search Console and add any missing redirects.
- Monitor site speed in **PageSpeed Insights** — Shopify themes can slow down with too many apps.

---

## Timeline Estimate

| Phase | Task | Est. Time |
|---|---|---|
| 1 | Audit & data export | 1–2 days |
| 2 | Shopify store setup | 1 day |
| 3 | Theme & design | 2–5 days |
| 4 | Product import & QA | 2–4 days |
| 5 | Customer import | 0.5 days |
| 6 | Apps & integrations | 1–2 days |
| 7 | SEO redirects | 1–2 days |
| 8 | Testing | 1–2 days |
| 9 | Go-live & monitoring | Ongoing |
| **Total** | | **~2–3 weeks** |

---

## Cost Considerations

| Item | Notes |
|---|---|
| Shopify plan | $79/mo (you're already on this) |
| Premium theme | $180–$350 one-time (optional) |
| Matrixify app | Free tier or $20/mo for large imports |
| Cart2Cart / LitExtension | $99–$299 one-time (if using migration service) |
| Apps (reviews, email, etc.) | $0–$100/mo depending on choices |
| Shopify Payments transaction fees | 0% (vs. 1% with third-party gateway) |

---

## Key Risks & Mitigations

| Risk | Mitigation |
|---|---|
| SEO ranking drop | Thorough 301 redirect map; submit new sitemap immediately |
| Customer password loss | Communicate proactively; Shopify auto-sends reset emails |
| Inventory mismatch | Do a final sync the night before go-live |
| Payment gateway downtime | Test payments before DNS cutover |
| App incompatibility | Install and test apps one at a time before launch |
| Data loss | Keep BigCommerce active for 30 days post-launch |

---

*Generated: 2026-05-20*
