# Rotary E-Club Outback Australia — Implementation Guide

## Quick Start (60-Minute Deployment)

This guide assumes you have an existing Bootstrap 5.3 website. You'll integrate three new components and update one existing section.

---

## PHASE 1: Prepare Your Assets (Week 1)

### Step 1: Gather Leader Photos
Create a folder: `/img/leaders/`

Required photos:
```
/img/leaders/greg-marlow.jpg (500x600px, 300KB max)
/img/leaders/victoria-porter.jpg (500x600px, 300KB max)
/img/leaders/barry.jpg (500x600px, 300KB max)
/img/leaders/tamara.jpg (500x600px, 300KB max)
/img/leaders/pene.jpg (500x600px, 300KB max)
/img/leaders/phil-dempster.jpg (500x600px, 300KB max)
```

**Photo specs:**
- Headshot-style (chest up)
- Professional appearance
- 500x600px minimum (crop to 3:4 ratio)
- Ensure faces are well-lit and recognizable

### Step 2: Update Content Markdown

Replace all old content with structured files:

```
/content/
├── leaders/
│   ├── greg-marlow.md
│   ├── victoria-porter.md
│   ├── barry.md
│   ├── tamara.md
│   ├── pene.md
│   └── phil-dempster.md
│
├── projects/
│   ├── bed-project.md
│   ├── cambodia.md
│   ├── kenya.md
│   ├── polio.md
│   └── timor-leste.md
```

---

## PHASE 2: Create New Pages (Week 1-2)

### Step 1: Deploy Individual Leader Pages

#### Create `/leaders/greg-marlow/index.html`

1. Copy the provided `leader-page-greg-template.html`
2. Update image path: `src="/img/leaders/greg-marlow.jpg"`
3. Update any donation links to your platform
4. Test on mobile (viewport 375px, 768px, 1200px)

**Verification Checklist:**
- [ ] Page loads without JS errors
- [ ] Hero image displays correctly
- [ ] All 3 donation tiers visible
- [ ] Donation buttons clickable
- [ ] Related leaders section links properly
- [ ] Mobile menu works
- [ ] No broken images

#### Repeat for Other Leaders:
- `/leaders/victoria-porter/index.html`
- `/leaders/barry/index.html`
- `/leaders/tamara/index.html`
- `/leaders/pene/index.html`
- `/leaders/phil-dempster/index.html`

**Content customization** (replace template content with actual leader data):

For each leader, update:
1. **H1 & Meta Tags:**
   ```html
   <title>[Name] — [Role] | Rotary E-Club Outback</title>
   <meta name="description" content="[150-160 char description with keywords]">
   ```

2. **Hero Section:**
   - Leader photo path
   - Name + primary role
   - Tagline (e.g., "30+ years in Rotary")
   - 2-3 sentence subtitle

3. **Introduction (250 words):**
   - Personal journey into Rotary
   - Key milestone
   - Current focus
   - Impact context

4. **Projects:**
   - 3-5 project cards per leader
   - Problem → Solution → Impact format
   - Individual donation CTAs
   - Metrics/statistics

5. **Stats Grid:**
   - Customize numbers per leader
   - Update labels to reflect actual achievements

6. **Donation Tiers:**
   - Keep structure (3 tiers)
   - Update suggested amounts based on project needs
   - Customize tier labels

---

### Step 2: Update Homepage (`/index.html`)

#### Remove "Our Core Pillars" Section

Find this section:
```html
<section>
    <h2>Our Core Pillars</h2>
    <div class="row">
        <div class="col-md-4">Community Projects</div>
        <div class="col-md-4">Youth Development</div>
        <div class="col-md-4">International Aid</div>
    </div>
</section>
```

**Delete it entirely.** Replace with the new "Campaigns" + "Meet Our Leaders" sections from `homepage-redesign-section.html`.

#### Add Campaigns Section

Copy this entire section from `homepage-redesign-section.html`:
```html
<!-- CAMPAIGNS SECTION -->
<section class="section-campaigns">
    ...
</section>
```

Insert after the hero section.

#### Add Meet Our Leaders Section

Copy this entire section from `homepage-redesign-section.html`:
```html
<!-- MEET OUR LEADERS SECTION -->
<section class="section-leaders">
    ...
</section>
```

Insert after campaigns.

#### Update Navigation Links

In your header `<nav>`, add:
```html
<li><a href="/leaders">Our Leaders</a></li>
<li><a href="/projects">Projects</a></li>
```

If you have a main CTA button in the nav:
```html
<!-- OLD -->
<a href="/donate" class="btn btn-primary">Donate</a>

<!-- NEW (More prominent) -->
<a href="/leaders" class="btn btn-primary">Meet Our Leaders</a>
```

---

## PHASE 3: Create Support Pages (Week 2)

### Create `/leaders/index.html` (Leaders Hub)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Our Leaders | Rotary E-Club Outback</title>
    <meta name="description" content="Meet the six visionary leaders driving Rotary's impact across Australia, Cambodia, Kenya, and Timor-Leste.">
</head>
<body>

<section style="background: linear-gradient(135deg, #003366, #004080); color: white; padding: 60px 0;">
    <div class="container-lg">
        <h1 style="color: white; font-size: 2.5rem; margin-bottom: 1rem;">Our Leaders</h1>
        <p style="font-size: 1.1rem; max-width: 600px;">Six passionate Rotarians, multiple continents, one mission: serve humanity.</p>
    </div>
</section>

<!-- Use the same leader grid from homepage -->
<section style="padding: 80px 0;">
    <div class="container-lg">
        <div class="leaders-grid">
            <!-- Copy 6 leader cards from homepage here -->
        </div>
    </div>
</section>

</body>
</html>
```

### Create `/projects/index.html` (Projects Hub)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Our Projects | Rotary E-Club Outback</title>
    <meta name="description" content="Explore our transformative projects across Australia, Cambodia, Kenya, and Timor-Leste.">
</head>
<body>

<section style="background: #F5F7FA; padding: 80px 0;">
    <div class="container-lg">
        <h1 style="font-size: 2.5rem; margin-bottom: 1rem; color: #003366;">Our Projects</h1>
        <p style="font-size: 1.1rem; color: #4A4A4A; max-width: 700px;">
            Six major initiatives creating measurable impact. Each project is led by dedicated Rotarians committed to service.
        </p>
    </div>
</section>

<!-- Project cards grid -->
<section style="padding: 80px 0;">
    <div class="container-lg">
        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem;">
            
            <!-- Project Card 1 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">🛏️ The Bed Project</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">Transforming plastic waste into safe sleeping spaces for remote Australian communities.</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Led by:</strong> Greg Marlow<br>
                    <strong>Status:</strong> 100+ beds installed, 67% funded for Phase 2
                </p>
                <a href="/leaders/greg-marlow" style="color: #003366; font-weight: 600; text-decoration: none;">Learn more →</a>
            </div>

            <!-- Project Card 2 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">💧 Cambodia Water & Schools</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">Building water wells, schools, and clinics to break poverty cycles.</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Led by:</strong> Barry<br>
                    <strong>Status:</strong> Active fundraising for LRDE
                </p>
                <a href="/leaders/barry-cambodia" style="color: #003366; font-weight: 600; text-decoration: none;">Learn more →</a>
            </div>

            <!-- Project Card 3 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">👩‍⚖️ Kenya Gender Justice</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">Integrated programs addressing maternal health, prison dignity & youth empowerment.</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Led by:</strong> Victoria Porter<br>
                    <strong>Status:</strong> 3,400+ youth engaged
                </p>
                <a href="/leaders/victoria-porter" style="color: #003366; font-weight: 600; text-decoration: none;">Learn more →</a>
            </div>

            <!-- Project Card 4 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">💙 Polio Eradication</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">Sustained fundraising to eliminate polio globally by 2026.</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Led by:</strong> Tamara<br>
                    <strong>Status:</strong> Donations matched 2:1 by Gates Foundation
                </p>
                <a href="/leaders/tamara-polio" style="color: #003366; font-weight: 600; text-decoration: none;">Learn more →</a>
            </div>

            <!-- Project Card 5 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">🏥 Timor-Leste Malaria</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">$850K+ mobilized to help declare Timor-Leste malaria-free (achieved 2025).</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Led by:</strong> Phil Dempster<br>
                    <strong>Status:</strong> Victory achieved
                </p>
                <a href="/leaders/phil-timor" style="color: #003366; font-weight: 600; text-decoration: none;">Learn more →</a>
            </div>

            <!-- Project Card 6 -->
            <div style="background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                <h3 style="color: #003366; margin-bottom: 1rem; font-size: 1.3rem;">🌍 All Initiatives</h3>
                <p style="color: #4A4A4A; margin-bottom: 1.5rem;">Explore sub-projects under each major initiative, from prisons to medical training.</p>
                <p style="color: #757575; font-size: 0.9rem; margin-bottom: 1.5rem;">
                    <strong>Scope:</strong> Australia, Cambodia, Kenya, Timor-Leste
                </p>
                <a href="/leaders" style="color: #003366; font-weight: 600; text-decoration: none;">View all leaders →</a>
            </div>

        </div>
    </div>
</section>

</body>
</html>
```

---

## PHASE 4: Set Up Donation Integration (Week 2-3)

### Update Donation Button Handlers

Replace all donation button `onclick` placeholders with your actual donation platform.

**Example 1: Direct to donation platform**

```html
<!-- Before -->
<button onclick="alert('Redirecting...')">Donate $50</button>

<!-- After - Option A: Direct URL -->
<a href="https://donations.yourplatform.com/greg-bed-project" class="btn-donate">
    Donate $50
</a>

<!-- After - Option B: Modal/Form -->
<button class="btn-donate" data-project="bed-project" data-amount="50">
    Donate $50
</button>
```

### Add JavaScript Donation Handler

Add to every leader page (`<script>` before `</body>`):

```javascript
<script>
// Donation handler
document.querySelectorAll('[data-project]').forEach(btn => {
    btn.addEventListener('click', function() {
        const project = this.dataset.project;
        const amount = this.dataset.amount;
        
        // Route to your donation platform
        window.location.href = 
            `https://donations.yourplatform.com/?project=${project}&amount=${amount}`;
    });
});

// Monthly giving setup
document.querySelectorAll('[data-monthly]').forEach(btn => {
    btn.addEventListener('click', function() {
        const project = this.dataset.project;
        window.location.href = 
            `https://donations.yourplatform.com/monthly?project=${project}`;
    });
});
</script>
```

### Integration Checklist

- [ ] Test donation flow on mobile (375px)
- [ ] Test donation flow on desktop
- [ ] Verify redirect URLs work
- [ ] Confirm donation platform receives parameters
- [ ] Test thank-you page redirect
- [ ] Verify email confirmations send

---

## PHASE 5: SEO & Meta Tags (Week 3)

### Update Meta Tags on Every Leader Page

```html
<!-- Greg Marlow -->
<title>Greg Marlow — District Governor & Bed Project Leader | Rotary</title>
<meta name="description" content="Meet Greg Marlow, Rotary District Governor 2025-26. See how his Bed Project transforms plastic waste into dignity for 200+ people in remote Australia.">
<meta name="keywords" content="rotary, bed project, greg marlow, district governor">

<!-- Victoria Porter -->
<title>Victoria Porter — Kenya Gender Justice Leader | Rotary</title>
<meta name="description" content="Victoria leads transformative programs in Kenya: prison dignity, maternal health, youth leadership. 3,400+ youth engaged. Paul Harris Fellow.">
<meta name="keywords" content="rotary, kenya, gender justice, victoria porter, maternal health">

<!-- Repeat for each leader with unique keywords -->
```

### Add Schema Markup

Add to each leader page `<head>`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Greg Marlow",
  "jobTitle": "District Governor",
  "worksFor": {
    "@type": "Organization",
    "name": "Rotary E-Club of Outback Australia"
  },
  "image": "https://yoursite.com/img/leaders/greg-marlow.jpg",
  "description": "Rotary District Governor driving the Bed Project initiative",
  "url": "https://yoursite.com/leaders/greg-marlow"
}
</script>
```

### Internal Linking Strategy

- Every leader page links to 2-3 related leaders
- Every project mentions its lead leader with link
- Homepage leader cards link to full profiles
- Footer includes links to all major sections

---

## PHASE 6: Testing & QA (Week 3-4)

### Performance Testing

```bash
# Check page load speed
# Use https://pagespeed.web.dev

# Critical metrics to monitor:
- Largest Contentful Paint (LCP): < 2.5s
- First Input Delay (FID): < 100ms
- Cumulative Layout Shift (CLS): < 0.1

# Image optimization:
# - Compress all images with TinyPNG (max 300KB each)
# - Use WebP format where possible
# - Implement lazy loading for below-fold images
```

### Cross-Browser Testing

Test on:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile Safari (iOS 15+)
- Chrome Mobile (Android 12+)

### Content Accuracy Check

- [ ] All leader names spelled correctly
- [ ] All statistics verified (double-check numbers)
- [ ] All donation links functional
- [ ] All images display correctly
- [ ] All internal links work
- [ ] No orphaned pages (every page linked from somewhere)
- [ ] Mobile menu collapses properly

---

## PHASE 7: Launch & Promotion (Week 4)

### Pre-Launch Checklist

- [ ] All pages deployed and tested
- [ ] Donation integration working
- [ ] Analytics tracking installed
- [ ] Google Search Console submitted
- [ ] 301 redirects from old URLs set up (if applicable)
- [ ] Robots.txt updated
- [ ] Sitemap.xml generated and submitted

### Post-Launch Activities

1. **Social Media Posts**
   ```
   "Meet [Name]! 👥 Leading [Project] across [Region]. 
   Explore their impact: [URL] | Support their work: [Donate URL]"
   ```
   - Post 1 per leader (6 posts spread across 2 weeks)

2. **Email Campaign**
   ```
   Subject: "Introducing Our Leaders — Meet the Team Driving Change"
   
   Hi [Name],
   
   We're thrilled to unveil the stories behind Rotary E-Club's greatest 
   impact. Six visionary leaders. Multiple continents. One mission.
   
   [6 leader links]
   
   Support their work: [Main Donate URL]
   ```

3. **Google Analytics Setup**
   ```
   Track:
   - Visits per leader page
   - Donation button clicks
   - Project page engagement
   - Time on page (goal: 2+ min)
   - Bounce rate (goal: <50%)
   ```

4. **Monthly Newsletter**
   Include section:
   ```
   "Leader Spotlight: [Name]'s Latest Update"
   - New achievement or milestone
   - Link to full profile
   - Donation CTA
   ```

---

## PHASE 8: Maintenance & Content Updates (Ongoing)

### Monthly Tasks

- Update campaign progress bars (% funded)
- Add new project updates to news section
- Update impact statistics
- Check for broken links
- Monitor donation conversion rate

### Quarterly Tasks

- Review page analytics
- Update leader achievements
- Add new photos/stories
- Audit SEO performance
- Refresh campaigns

### Yearly Tasks

- Refresh all leader bios (update roles, achievements)
- Update annual statistics
- Add year-end impact report
- Archive completed projects
- Plan new campaigns

---

## File Structure Summary

```
Website Root/
├── index.html (Updated with campaigns + leaders section)
├── css/
│   └── custom.css (Contains new styles)
├── js/
│   └── donations.js (Donation handler)
├── img/
│   └── leaders/
│       ├── greg-marlow.jpg
│       ├── victoria-porter.jpg
│       ├── barry.jpg
│       ├── tamara.jpg
│       ├── pene.jpg
│       └── phil-dempster.jpg
├── leaders/
│   ├── index.html (Leaders hub)
│   ├── greg-marlow/
│   │   └── index.html
│   ├── victoria-porter/
│   │   └── index.html
│   ├── barry/
│   │   └── index.html
│   ├── tamara/
│   │   └── index.html
│   ├── pene/
│   │   └── index.html
│   └── phil-dempster/
│       └── index.html
├── projects/
│   ├── index.html (Projects hub)
│   ├── bed-project.html
│   ├── cambodia.html
│   ├── kenya.html
│   ├── polio.html
│   └── timor-leste.html
└── donate/
    └── index.html (Donation gateway)
```

---

## Troubleshooting

### Images Not Loading
```
Check:
1. File path is relative: /img/leaders/name.jpg
2. Image file exists in correct folder
3. Filename matches exactly (case-sensitive on Linux)
4. Image format is .jpg, .png, or .webp
```

### Donation Buttons Not Working
```
Check:
1. onclick handlers have correct syntax
2. URLs are properly formatted
3. Donation platform URLs are public (not behind login)
4. Test in incognito mode (clear cookies)
```

### Mobile Layout Broken
```
Check:
1. Bootstrap CSS loaded: <link href="...bootstrap.min.css">
2. Viewport meta tag present: <meta name="viewport">
3. No inline fixed widths (use max-width instead)
4. Test with Chrome DevTools mobile view
```

---

## ROI & Success Metrics

### Expected Outcomes (3-6 months)

- **Donation volume:** +40-60% increase from improved visibility & CTAs
- **Page engagement:** 2+ min average time on leader pages
- **Conversion rate:** 5-8% of visitors clicking donation CTA
- **Mobile traffic:** >50% of all traffic (expected for nonprofit)
- **Return visitors:** +30% month-over-month

### Tracking

Use Google Analytics 4 goals:
```
Goal 1: Donation CTA Click (conversion)
Goal 2: 2+ minute time on page (engagement)
Goal 3: Visit leader page then donation (funnel)
```

---

**Questions? Contact your development team or refer to the original restructure document for strategy details.**
