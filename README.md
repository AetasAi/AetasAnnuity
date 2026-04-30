# FlexiblePensionAnnuity — Aetas Wealth Adviser Dashboard

Live site: [fpa.aetaspartners.com](https://fpa.aetaspartners.com)

A single-page adviser dashboard and resource hub for the Flexible Pension Annuity — a structured product that eliminates the combined IHT and income tax charge on DC pension funds under Finance Act 2026.

---

## What this site does

Provides UK financial advisers with:
- A live tax calculator showing the before/after impact of Finance Act 2026 on a specific client's pension
- Five detailed client case studies
- The full BPR legal basis (s105(1)(bb) IHTA 1984) and Threesixty Services confirmation
- Executor liability analysis
- Cost comparison vs life assurance
- Insight articles indexed by Google
- A lead capture form (GHL) that emails calculator results to the adviser

---

## Repository structure

```
FlexiblePensionAnnuity/
│
├── index.html                        ← Main adviser dashboard (SPA with tab navigation)
├── about.html                        ← Peter Rose biography and credentials
├── thank-you.html                    ← Post-form submission confirmation page
├── 404.html                          ← Branded error page
│
├── insight-double-whammy.html        ← Insight: The pension double whammy explained
├── insight-bpr-legal-basis.html      ← Insight: BPR legal basis (s105(1)(bb) IHTA 1984)
├── insight-executor-liability.html   ← Insight: Executor personal liability risk
│
├── FPA-Adviser-Compliance-Pack.pdf   ← Downloadable compliance pack (6 pages)
├── peter-rose.jpg                    ← Peter Rose headshot (used in hero and contact blocks)
├── og-image.svg                      ← Open Graph social sharing image (1200×630)
├── favicon.svg                       ← Browser tab icon
├── favicon.ico                       ← Fallback favicon
│
├── sitemap.xml                       ← Submitted to Google Search Console
├── robots.txt                        ← Allows all crawlers, references sitemap
└── CNAME                             ← GitHub Pages custom domain (fpa.aetaspartners.com)
```

---

## Key files explained

### index.html
The main page. Structured as a single-page application with JavaScript tab switching.

**Tab IDs and their content:**
| Tab ID | Nav label | Content |
|--------|-----------|---------|
| `tab-overview` | Overview | Hero, stat blocks, timeline, solution summary |
| `tab-problem` | The Problem | Double whammy explained, before/after comparison |
| `tab-solution` | The Solution | FPA product detail, BPR basis, FSCS/FCA credentials |
| `tab-how` | *(hidden from nav)* | 5-stage transfer process |
| `tab-cases` | Case Studies | 5 client scenarios with full numbers |
| `tab-costs` | *(hidden from nav)* | Cost comparison vs life assurance |
| `tab-calc` | Calculator | Live IHT calculator with GHL email capture |
| `tab-insights` | Insights | Links to insight articles |
| `tab-faqs` | FAQs | 7 FAQs + Peter Rose contact block |

**Key JavaScript functions:**
- `showTab(id, btn)` — switches active tab, scrolls to top
- `showTabGroup(ids, btn)` — shows multiple tabs simultaneously (used for merged nav groups)
- `calc()` — runs the live IHT calculator
- `toggleCalcEmail()` — opens/closes the GHL email capture below calculator results
- `toggleCase(card)` — expands/collapses case study detail
- `toggleFaq(el)` — expands/collapses FAQ items

**Tracking:**
- GA4 (G-7VFMY2YCH3) — page views, tab navigation, calculator usage, booking clicks
- Microsoft Clarity (wjn1hr8102) — heatmaps and session recordings

### insight pages
Three standalone HTML pages, each targeting specific search queries. Share the same nav, CSS variables, risk warning footer, and GA4 tracking as index.html. Each has:
- Canonical URL pointing to `fpa.aetaspartners.com`
- Article JSON-LD schema
- BreadcrumbList schema
- Person schema for Peter Rose
- Navigation links back to Calculator, Case Studies, FAQs, and All Insights

---

## Making changes

### Adding a new insight article
1. Copy `insight-double-whammy.html` as a template
2. Update: `<title>`, `<meta name="description">`, `<link rel="canonical">`, all `og:` and `twitter:` meta tags
3. Update the JSON-LD schema: headline, description, url, datePublished
4. Replace the article content between the `<div class="article">` tags
5. Add the new page to `sitemap.xml`
6. Add a link to the new article in the Insights tab section of `index.html`

### Updating the calculator
The calculator logic lives in the `calc()` function in `index.html`. Input element IDs:
- `#fundInput` — pension fund value
- `#ageOver` / `#ageUnder` — client age radio buttons
- `#spouseYes` / `#spouseNo` — spousal exemption radio buttons
- `input[name="tax"]` — beneficiary income tax rate radio buttons

Output element IDs:
- `#res-net-without` — net to beneficiaries without FPA
- `#res-net-with` — net to beneficiaries with FPA
- `#res-saving` — saving

### Updating Peter Rose's contact details
His details appear in three places:
1. Hero section (below stat blocks) — `index.html` approx line 558
2. FAQs contact card — `index.html` in the `tab-faqs` section
3. `about.html` — full biography page

### Adding a page to the sitemap
Open `sitemap.xml` and add a new `<url>` block:
```xml
<url>
  <loc>https://fpa.aetaspartners.com/new-page.html</loc>
  <lastmod>2026-04-30</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.8</priority>
</url>
```
Then re-submit the sitemap in Google Search Console.

---

## Deployment

Hosted on GitHub Pages. Custom domain `fpa.aetaspartners.com` via 123-reg DNS (CNAME record pointing to `aetasai.github.io`).

**To update the live site:** commit and push changes to the `main` branch. GitHub Pages rebuilds automatically — allow 30–90 seconds for changes to propagate.

**To verify changes are live:**
```bash
curl -s "https://aetasai.github.io/FlexiblePensionAnnuity/index.html" | grep "your-search-term"
```

---

## Analytics

| Tool | Property | What it tracks |
|------|----------|---------------|
| GA4 | G-7VFMY2YCH3 | Page views, tab navigation, calculator runs, booking clicks, scroll depth |
| Clarity | wjn1hr8102 | Heatmaps, session recordings, rage clicks |
| Search Console | fpa.aetaspartners.com | Keyword positions, indexing status, crawl errors |

---

## Contacts

**Peter Rose APFS** · Chartered Financial Planner · Pensions Specialist  
peter.rose@aetas-wealth.com · [Book a meeting](https://link.aetas-wealth.com/widget/booking/65kC9dm2WgkoxziAWlFE)

**Aetas Wealth** is a trading style of Insight Financial Associates Ltd  
FCA Registration No. 458421 · Authorised and regulated by the Financial Conduct Authority

---

*For professional adviser use only. Not for client distribution.*
