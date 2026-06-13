# Advanced Craft Contracts — Website Reference

**Last updated:** 2026-06-13
**Status:** 40/40 files — all passing. Ready for GitHub upload.

---

## Project Overview

Static HTML website for **Advanced Craft Contracts Ltd**, a building and renovation company operating across Edinburgh, Glasgow, and Scotland. All pages are single-file static HTML using Tailwind CSS via CDN — no build tools, no external JS frameworks.

---

## Contact Details (use on every page)

| Type      | Value                                      |
|-----------|--------------------------------------------|
| Freephone | 0800 073 8818 (`tel:08000738818`)          |
| Mobile    | 07542 389947 (`tel:07542389947`)           |
| Email     | advancedcraftcontracts@outlook.com         |
| Social    | Facebook + Instagram (external links)      |

---

## Colour Theme

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        gold:         '#B8960C',
        'gold-light': '#D4AE2C',
        'gold-dark':  '#8A6E08',
        charcoal:     '#1A1A1A',
        'off-white':  '#F9F7F2',
        'warm-gray':  '#6B6B6B',
        'light-gray': '#E8E8E8',
        'mid-gray':   '#3A3A3A',
      },
      fontFamily: {
        playfair: ['"Playfair Display"', 'Georgia', 'serif'],
        inter:    ['"Inter"', 'Arial', 'sans-serif'],
      },
    },
  },
}
```

Key background colours used inline:
- `#0f0f0f` — contact bar, footer
- `#111` / `#1a1a1a` — section alternates
- `#0a0a0a` — deep background
- `#2a2a2a` — borders/dividers
- `#B8960C` — gold accents, CTA buttons

---

## Fonts

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
```

- **Playfair Display** — all headings (`font-playfair`)
- **Inter** — body text, nav, labels (`font-inter`)

---

## Shared Components (must appear on every page)

### 1. Top Contact Bar

Dark background (`#0f0f0f`), three items: Freephone, Mobile, Email. "Get a Free Quote" gold button on the right.

```html
<div style="background:#0f0f0f;" class="py-2 px-4 md:px-8">
  <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-2 text-xs font-inter">
    <div class="flex flex-wrap items-center gap-5 text-gray-300">
      <a href="tel:08000738818" class="flex items-center gap-1.5 hover:text-gold transition-colors">
        <svg class="w-3 h-3 text-gold flex-shrink-0" ...></svg>
        <span class="font-bold text-gold">Freephone:</span>&nbsp;0800 073 8818
      </a>
      <a href="tel:07542389947" class="flex items-center gap-1.5 hover:text-gold transition-colors">
        <span class="font-bold text-gold">Mobile:</span>&nbsp;07542 389947
      </a>
      <a href="mailto:advancedcraftcontracts@outlook.com" class="flex items-center gap-1.5 hover:text-gold transition-colors">
        advancedcraftcontracts@outlook.com
      </a>
    </div>
    <a href="index.html#contact" class="bg-gold hover:bg-gold-light text-black px-4 py-1.5 uppercase tracking-widest text-xs font-bold transition-all whitespace-nowrap">Get a Free Quote</a>
  </div>
</div>
```

> On `index.html` the CTA links to `#contact`. On all other pages it links to `index.html#contact`.

### 2. Header / Logo + Mobile Hamburger Menu

Every page has a sticky header with a desktop nav and a mobile hamburger menu. The hamburger is hidden on md+ screens; the desktop nav is hidden on smaller screens.

```html
<header class="bg-charcoal sticky top-0 z-50 border-b-2 border-gold shadow-lg">
  <div class="max-w-7xl mx-auto px-6">
    <div class="flex items-center justify-between h-28">
      <a href="index.html" class="flex items-center gap-5">
        <div class="bg-white rounded p-1.5">
          <img src="data:image/png;base64,iVBORw0K..." alt="Advanced Craft Contracts" class="h-20 w-auto" />
        </div>
        <div class="hidden sm:block">
          <p class="font-playfair text-2xl font-bold text-white leading-tight">Advanced Craft</p>
          <p class="font-inter text-xs uppercase tracking-[0.25em] text-gold font-semibold">Contracts</p>
        </div>
      </a>
      <nav class="hidden md:flex items-center gap-8 font-inter text-sm font-medium text-gray-300">
        <a href="index.html#services" class="hover:text-gold transition-colors">Services</a>
        <a href="index.html#about"    class="hover:text-gold transition-colors">About</a>
        <a href="index.html#contact"  class="hover:text-gold transition-colors">Contact</a>
        <a href="index.html#reviews"  class="hover:text-gold transition-colors">Reviews</a>
        <a href="index.html#contact"  class="bg-gold hover:bg-gold-light text-black px-6 py-3 uppercase tracking-widest text-xs font-bold transition-all duration-300">Request a Callback</a>
      </nav>
      <button id="mob-btn" onclick="toggleMob()" class="md:hidden flex flex-col justify-center items-center w-10 h-10 gap-1.5" aria-label="Toggle menu">
        <span id="mob-line1" class="block w-6 bg-gold transition-all duration-300" style="height:2px;"></span>
        <span id="mob-line2" class="block w-6 bg-gold transition-all duration-300" style="height:2px;"></span>
        <span id="mob-line3" class="block w-6 bg-gold transition-all duration-300" style="height:2px;"></span>
      </button>
    </div>
  </div>
  <div id="mob-menu" style="display:none;background:#1a1a1a;border-top:1px solid #B8960C;" class="md:hidden">
    <div class="px-6 py-4 flex flex-col gap-1 font-inter text-sm font-medium">
      <a href="index.html#services" onclick="toggleMob()" class="text-gray-300 hover:text-gold transition-colors py-3 border-b border-gray-800">Services</a>
      <a href="index.html#about"    onclick="toggleMob()" class="text-gray-300 hover:text-gold transition-colors py-3 border-b border-gray-800">About</a>
      <a href="index.html#contact"  onclick="toggleMob()" class="text-gray-300 hover:text-gold transition-colors py-3 border-b border-gray-800">Contact</a>
      <a href="index.html#reviews"  onclick="toggleMob()" class="text-gray-300 hover:text-gold transition-colors py-3 border-b border-gray-800">Reviews</a>
      <a href="index.html#contact"  onclick="toggleMob()" class="mt-3 text-center bg-gold text-black py-3 px-6 uppercase tracking-widest text-xs font-bold">Request a Callback</a>
    </div>
  </div>
</header>
<script>function toggleMob(){var m=document.getElementById('mob-menu'),l1=document.getElementById('mob-line1'),l2=document.getElementById('mob-line2'),l3=document.getElementById('mob-line3'),o=m.style.display!=='none';if(o){m.style.display='none';l1.style.transform='';l2.style.opacity='';l3.style.transform='';}else{m.style.display='';l1.style.transform='rotate(45deg) translate(2px,2px)';l2.style.opacity='0';l3.style.transform='rotate(-45deg) translate(2px,-2px)';}}</script>
```

> On `index.html`: logo href is `href="#"` and mobile menu links use `#services`, `#about`, `#contact`, `#reviews`. On all other pages: logo href is `href="index.html"` and links use `index.html#services` etc.

**CRITICAL:** Logo `src` must always include the full `data:image/png;base64,` URI prefix. Raw base64 without this prefix renders as a broken image in all browsers.

### 3. Compact Certifications Section

```html
<section style="background:#111;border-top:1px solid #2a2a2a;" class="py-7">
  <div class="max-w-7xl mx-auto px-6">
    <p class="font-inter text-gold text-xs uppercase tracking-[0.3em] font-semibold text-center mb-5">Our Accreditations</p>
    <div class="flex flex-wrap justify-center items-center gap-8 md:gap-14">
      <!-- GS | Gas Safe | Registered -->
      <!-- NICEIC | NICEIC | Approved Contractor -->
      <!-- SMAS | SMAS | Worksafe Certified -->
      <!-- CHAS | CHAS | Accredited Member -->
    </div>
  </div>
</section>
```

Badge pattern: `w-10 h-10` rounded-full gold circle. Always `py-7` — never larger.

### 4. Reviews Carousel

Auto-scrolling (4500ms), card width 388px, shows 3 visible.

```js
(function(){
  var t=document.getElementById('reviews-track');
  var total=t.children.length, cur=0, cw=388, vis=3;
  function go(n){var mx=Math.max(0,total-vis);cur=Math.max(0,Math.min(n,mx));t.style.transform='translateX(-'+(cur*cw)+'px)';}
  window.nextReview=function(){go(cur+1);}; window.prevReview=function(){go(cur-1);};
  setInterval(function(){go(cur+1<total-vis+1?cur+1:0);},4500);
})();
```

### 5. Footer

`background:#0f0f0f;border-top:2px solid #B8960C;` — three columns: logo + tagline | contact details | quick links.

Container uses `class="flex flex-col md:flex-row items-start justify-between mb-8 gap-10"` for even symmetric spacing across all three columns. Do **not** add `md:pl-12` to the Quick Links column — this was the old layout and caused uneven spacing.

### 6. Logo

Inline base64 PNG (~315KB). **Always** `src="data:image/png;base64,iVBORw0K..."` — never raw base64 without the prefix. Same value on all 44 pages.

---

## Logo Injection (when adding new pages)

Copy `src="data:image/png;base64,iVBORw0K..."` directly from any existing page, or use the PowerShell inject script with `LOGO_B64` placeholder:

```powershell
$c = [System.IO.File]::ReadAllText("$dir\index.html", [System.Text.Encoding]::UTF8)
$logoSrc = [regex]::Match($c, 'src="(data:image/png;base64,iVBORw0K[A-Za-z0-9+/=]+)"').Groups[1].Value
$newPage = $newPage.Replace("LOGO_B64", $logoSrc)
```

---

## File Inventory

**40 HTML files total — all passing, all saved.**

### Homepage

| File | Size | Description |
|------|------|-------------|
| `index.html` | ~720KB | Hero, guarantee bar, 23-service tab grid, projects carousel, CTA banner, about, reviews, certifications, contact form (Formspree), footer |

### Individual Service Pages (23 files)

All 23 service cards on the homepage link directly to individual pages. Each page has unique hero, description, two project showcases, service-specific reviews, certifications, standard header/footer.

| File | Size | # | Service |
|------|------|---|---------|
| `service-1-new-builds.html` | 635KB | 1 | New Builds |
| `service-2-extensions.html` | 634KB | 2 | Extensions |
| `service-3-kitchens-bathrooms.html` | 634KB | 3 | Kitchens & Bathrooms |
| `service-4-property-maintenance.html` | 634KB | 4 | Property Maintenance |
| `service-5-garden-rooms.html` | 634KB | 5 | Garden Rooms |
| `service-6-flooring.html` | 633KB | 6 | Flooring |
| `service-7-stairs-balustrades.html` | 634KB | 7 | Stairs & Balustrades |
| `service-8-internal-doors.html` | 633KB | 8 | Internal Door Kits |
| `service-9-windows-doors.html` | 633KB | 9 | External Windows & Doors |
| `service-10-decking-fences.html` | 633KB | 10 | Decking, Fences & Cladding |
| `service-11-landscaping.html` | 633KB | 11 | Landscaping & Gardening |
| `service-12-roofing.html` | 633KB | 12 | Roofs, Fascias & Soffits |
| `service-13-heating-systems.html` | 634KB | 13 | Heating Systems |
| `service-14-boiler-changes.html` | 634KB | 14 | Boiler Changes & Gas Safe Certificates |
| `service-15-electrical-rewires.html` | 635KB | 15 | Electrical Rewires |
| `service-16-architects-drawings.html` | 635KB | 16 | Architects Drawings |
| `service-17-planning-permissions.html` | 635KB | 17 | Planning Permissions |
| `service-18-insurance-repairs.html` | 635KB | 18 | Insurance Repairs |
| `service-19-emergency-plumber.html` | 635KB | 19 | Emergency Plumber |
| `service-20-emergency-locksmith.html` | 635KB | 20 | Emergency Locksmith |
| `service-21-plastering.html` | 635KB | 21 | Plastering |
| `service-22-painting-decorating.html` | 634KB | 22 | Painting & Decorating |
| `service-23-tiling.html` | 634KB | 23 | Tiling |

### Individual Project Pages (16 files)

Each has: hero, project overview, 5 bullet works-carried-out, 6-image gallery, client testimonial, CTA banner, certifications, reviews, standard header/footer.

| File | Size | Category | Project |
|------|------|----------|---------|
| `project-extension-1.html` | 635KB | Extensions | Rear Kitchen Extension, Edinburgh |
| `project-extension-2.html` | 635KB | Extensions | Two-Storey Side Extension, Glasgow |
| `project-garage-conversion-1.html` | 635KB | Garage Conversions | Integrated Garage Conversion, Edinburgh |
| `project-garage-conversion-2.html` | 635KB | Garage Conversions | Detached Garage Conversion, Stirling |
| `project-loft-conversion-1.html` | 635KB | Loft Conversions | Dormer Loft Conversion, Edinburgh |
| `project-loft-conversion-2.html` | 635KB | Loft Conversions | Hip-to-Gable Loft Conversion, Glasgow |
| `project-home-refurbishment-1.html` | 635KB | Home Refurbishments | Full Home Refurbishment, Edinburgh |
| `project-home-refurbishment-2.html` | 635KB | Home Refurbishments | Period Property Renovation, Perth |
| `project-kitchen-1.html` | 635KB | Kitchens | Open-Plan Kitchen Renovation, Edinburgh |
| `project-kitchen-2.html` | 635KB | Kitchens | Bespoke Kitchen Installation, Glasgow |
| `project-kitchen-3.html` | 635KB | Kitchens | Kitchen Extension & Renovation, Dundee |
| `project-bathroom-1.html` | 635KB | Bathrooms | Master Bathroom Renovation, Edinburgh |
| `project-bathroom-2.html` | 635KB | Bathrooms | Full Bathroom Suite Renovation, Glasgow |
| `project-bathroom-3.html` | 635KB | Bathrooms | Wet Room Conversion, Perth |
| `project-new-build-1.html` | 635KB | New Builds | Bespoke 4-Bedroom New Build, Perthshire |
| `project-new-build-2.html` | 635KB | New Builds | Contemporary 3-Bedroom New Build, Fife |

---

## Homepage Structure (in order)

1. Top Contact Bar
2. Header / Navigation
3. Hero — `photo-1565008447742-97f6f38c985c?w=1800&q=80`, dark gradient overlay, "From Design to Completion" heading
4. Guarantee Bar — gold strip
5. Comprehensive Services — 4 tab buttons + 4 inline panels, 23 service cards
6. Recent & Current Projects carousel — 16 cards, links to individual project pages
7. "Off Track?" CTA banner
8. About section
9. Reviews carousel
10. Compact Certifications
11. Contact form
12. Footer

---

## Services Tab System (homepage)

Tab buttons use `onclick="showTab(N)"` — all panels are inline, no page navigation required.

```html
<button onclick="showTab(1)" id="tab-btn-1" ...>Services 1–6</button>
<button onclick="showTab(2)" id="tab-btn-2" ...>Services 7–12</button>
<button onclick="showTab(3)" id="tab-btn-3" ...>Services 13–18</button>
<button onclick="showTab(4)" id="tab-btn-4" ...>Services 19–23</button>
```

```js
function showTab(n) {
  for (var i = 1; i <= 4; i++) {
    var panel = document.getElementById('tab-panel-' + i);
    var btn   = document.getElementById('tab-btn-' + i);
    if (i === n) {
      panel.style.display = '';
      btn.style.background = '#B8960C';
      btn.style.color = '#000';
    } else {
      panel.style.display = 'none';
      btn.style.background = 'transparent';
      btn.style.color = '#B8960C';
    }
  }
}
```

Panel IDs: `tab-panel-1` (services 1–6), `tab-panel-2` (7–12), `tab-panel-3` (13–18), `tab-panel-4` (19–23).

---

## Projects Carousel (homepage)

```js
(function(){
  var pt=document.getElementById('projects-track');
  var total=pt.children.length, cur=0, cardW=314, vis=3;
  function goToP(n){var max=Math.max(0,total-vis);cur=Math.max(0,Math.min(n,max));pt.style.transform='translateX(-'+(cur*cardW)+'px)';}
  window.nextProject=function(){goToP(cur+1);}; window.prevProject=function(){goToP(cur-1);};
  setInterval(function(){goToP(cur+1<total-vis+1?cur+1:0);},4200);
})();
```

---

## Design Rules

- **Dark theme throughout** — #0a0a0a / #111 / #1a1a1a backgrounds. No white-background pages.
- **Gold accents** — `#B8960C` for labels, borders, badge initials, buttons, hover states.
- **Headings** — always `font-playfair`. Section labels use `font-inter text-gold text-xs uppercase tracking-[0.3em] font-semibold`.
- **Section alternation** — between `#0f0f0f` and `#111`.
- **Max width** — `max-w-7xl mx-auto px-6` on all containers.
- **CTA banner** — `linear-gradient(135deg,#B8960C,#8A6E08)`, black text, black button.
- **Logo** — `<div class="bg-white rounded p-1.5">` wrapper, `class="h-20 w-auto"`, `data:image/png;base64,` prefix on src, "Advanced Craft / Contracts" text beside it.
- **Header** — always `<header class="bg-charcoal sticky top-0 z-50 border-b-2 border-gold shadow-lg">`.
- **Contact bar** — always `<div style="background:#0f0f0f;">`.
- **Footer** — always `background:#0f0f0f;border-top:2px solid #B8960C;`.
- **Accreditations** — always `py-7`, always `w-10 h-10` badges.
- **Internal links** on non-homepage pages — always prefixed with `index.html` (e.g. `index.html#contact`).
- **Images** — always Unsplash CDN. Never placeholder.co.

---

## Technical Stack

- **Tailwind CSS** via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- **Google Fonts** via CDN in `<head>`
- **No build tools** — all HTML self-contained
- **No external JS** — all carousel/tab logic inline vanilla JS
- **Logo** — inline `data:image/png;base64,` (~315KB), identical across all 44 files
- **Images** — Unsplash CDN, lazy-loaded

---

## Accreditations

| Badge  | Name     | Subtitle            |
|--------|----------|---------------------|
| GS     | Gas Safe | Registered          |
| NICEIC | NICEIC   | Approved Contractor |
| SMAS   | SMAS     | Worksafe Certified  |
| CHAS   | CHAS     | Accredited Member   |

---

## Image Sources

Pattern: `https://images.unsplash.com/photo-{ID}?w=600&q=80`
Heroes use `?w=1800&q=80`. Service/project content images use `?w=600&q=80`.

---

## Adding New Pages

1. Copy an existing service page (e.g. `service-1-new-builds.html`).
2. Replace all service-specific content (hero h1, description, showcase sections, reviews).
3. Ensure logo src has full `data:image/png;base64,iVBORw0K...` — copy from any existing page.
4. Add a service card in the correct `tab-panel-N` div in `index.html`.
5. Run `full_audit_fix.ps1` to validate all shared components.

---

## Audit Scripts (`C:\Users\Advan\AppData\Local\Temp\`)

| Script | Purpose |
|--------|---------|
| `full_audit_fix.ps1` | Checks all 43 non-index files: logo data:URI, contact bar phones/email, header class, footer style, accreditations padding and badge size. Auto-fixes against index.html master. |
| `full_status_check.ps1` | Read-only audit — reports pass/fail per file with issue details. No changes made. |
| `fix_all_three.ps1` | Historical: added data:image prefix to logo, fixed hero URL, fixed tab link. |
| `inject_logos.ps1` | Historical: injected logo B64 from index.html into template files. |

---

## Issues Fixed (history)

| Date | Issue | Fix |
|------|-------|-----|
| 2026-03-29 | Wrong contact bar (gold bg, old phone numbers) on services 13–23 and all 16 project pages | Replaced with correct dark bar from service-1 master |
| 2026-03-29 | Wrong header style on services 13–23 and project pages | Replaced with `bg-charcoal` header |
| 2026-03-29 | Wrong footer style on services 13–23 and project pages | Replaced with `#0f0f0f;border-top:2px solid #B8960C` footer |
| 2026-03-29 | Oversized accreditations badges on services-1 to services-4 group pages | Replaced section with compact `py-7` / `w-10 h-10` version |
| 2026-03-30 | Logo showing as broken white box on all 44 pages | Added `data:image/png;base64,` URI prefix to all img src values |
| 2026-03-30 | Hero background image not loading on homepage | Updated URL to `photo-1565008447742-97f6f38c985c?w=1800&q=80` |
| 2026-03-30 | Services 7–12 tab opening grouped `services-2.html` instead of individual pages | Replaced `<a href>` tab buttons with `<button onclick="showTab(N)">` + `showTab()` JS |
| 2026-06-13 | No mobile navigation on any page | Added hamburger menu + toggleMob() JS to all 40 pages |
| 2026-06-13 | services-1.html to services-4.html kept as dead files (not linked) | Deleted all 4 files |
| 2026-06-13 | White gap visible between hero section and guarantee bar | Added `background:#0a0a0a` to hero section style |
| 2026-06-13 | Trust stats showing 20+ Trades Covered | Changed to 25+ |
| 2026-06-13 | Footer Quick Links column unevenly spaced | Changed footer container to `flex md:flex-row justify-between`, removed `md:pl-12` from Quick Links |
| 2026-06-13 | Contact form had no backend (no action, broken label tags, no name attrs) | Added Formspree action placeholder, fixed `</label>` tags, added name attributes to all inputs |

---

## Outstanding Items / Next Steps

### No blocking issues
All 40 files pass audit (logo, contact bar, header, footer, accreditations, hamburger menu).

### ONE action required from Justin — Formspree form ID
The contact form on `index.html` is wired up and ready but uses a placeholder:
`action="https://formspree.io/f/YOUR_FORM_ID"`

To activate it:
1. Go to **https://formspree.io** and sign up (use advancedcraftcontracts@outlook.com)
2. Click **New Form**, give it a name (e.g. "ACC Website")
3. Copy the 8-character Form ID shown (e.g. `xpzgkpzl`)
4. In `index.html`, find `YOUR_FORM_ID` and replace it with your actual ID
5. Test by submitting the form — you'll receive an email at advancedcraftcontracts@outlook.com

### Remaining recommended steps
1. **Real photography** — all images are Unsplash stock photos. Replace with actual project photography when available.
2. **GitHub upload** — all 40 files are saved locally and ready to push.
