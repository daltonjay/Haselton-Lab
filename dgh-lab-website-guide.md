# DGH Lab Website — Deployment & Editing Guide

---

## Part 1 — Editing the website

All edits are made directly in `dgh-lab-website.html`. Open it in any text
editor (VS Code is recommended — free at code.visualstudio.com).

Every editable section is marked with a ✏️ comment in the file. Here are
the most common changes:

---

### 1. Lab name & navigation

Search for `DGH Lab` and replace every instance with your lab's name.
Nav links are `<li><a href="#section-id">Label</a></li>` — edit the label
text freely, but keep the `#section-id` matching the `id=""` on each section.

---

### 2. Hero headline & subheading

```html
<h1>Diagnostics for a<br><em>healthier world</em>,<br>everywhere.</h1>
<p>We develop low-cost, accessible diagnostic tools…</p>
```

Wrap words in `<em>` for italic teal styling.
Change button labels and their `href` targets freely.

---

### 3. Stats strip

```html
<div class="stat-num">12+</div>
<div class="stat-label">Countries reached</div>
```

Replace numbers and labels with your real data.
To add a fifth stat, copy a `<div class="stat">` block and update
`grid-template-columns: repeat(4, 1fr)` in the CSS to `repeat(5, 1fr)`.

---

### 4. Research cards

Each card follows this pattern:

```html
<div class="research-card">
  <div class="research-card-num">01</div>
  <h3>Your research area title</h3>
  <p>Description of the research area.</p>
  <span class="tag">Keyword</span>
</div>
```

Copy/paste the block to add more areas.
The grid fits 3 per row — add cards in multiples of 3 for a clean layout.

---

### 5. Mission panel

The pull quote uses `<span>` for the teal highlight:

```html
<p class="mission-quote">"Quote here with <span>highlighted phrase</span>."</p>
```

The dark navy panel holds four `.mission-pill` items — edit the emoji,
bold title, and description text in each one.

---

### 6. Team members

Each person is a `.team-card` block:

```html
<div class="team-card">
  <div class="team-avatar av-navy">AB</div>  <!-- initials, color: av-navy | av-teal | av-gold -->
  <h4>Dr. Full Name</h4>
  <div class="role">Position Title</div>
  <p>Short bio sentence.</p>
</div>
```

**To use a real headshot photo instead of initials:**
Replace the `<div class="team-avatar">` with:

```html
<img src="photos/name.jpg" alt="Dr. Full Name"
  style="width:72px;height:72px;border-radius:50%;object-fit:cover;margin:0 auto 1rem;display:block;">
```

Put photos in a `photos/` folder next to the HTML file.
The grid shows 4 per row. For more members, the grid auto-wraps.

---

### 7. Publications

Each paper is a `.pub-card`:

```html
<div class="pub-card">
  <div class="pub-year">2024</div>
  <div class="pub-content">
    <h4>Paper title here</h4>
    <p>Journal Name · Author et al.</p>
    <span class="pub-badge featured">Featured</span>  <!-- optional -->
  </div>
</div>
```

Badge options: `class="pub-badge featured"` (gold) or `class="pub-badge recent"` (teal).
To link to the paper's DOI, wrap the title in an anchor:

```html
<h4><a href="https://doi.org/10.XXXX/XXXXX" target="_blank"
  style="color:inherit;text-decoration:underline;text-underline-offset:3px;">
  Paper title here
</a></h4>
```

---

### 8. Join Us section

Edit the intro paragraph and each `.join-option` block — title and description.
Add or remove option blocks freely.

---

### 9. Contact details

Replace the address, email, and department text directly in the HTML.

**To make the contact form actually send emails (free options):**

**Option A — Formspree (easiest, free tier available)**
1. Sign up at formspree.io
2. Create a form, copy your form ID (e.g. `xabc1234`)
3. Change the `<div class="contact-form">` to a `<form>` tag:
   ```html
   <form class="contact-form" action="https://formspree.io/f/xabc1234" method="POST">
   ```
4. Add `name=""` attributes to each input (required by Formspree):
   ```html
   <input type="text" name="first_name" placeholder="Jane">
   ```
5. Change the button from `<button>` to `<button type="submit">`.

**Option B — Netlify Forms (if hosting on Netlify)**
Add `netlify` to the `<form>` tag — Netlify handles the rest automatically.

---

### 10. Colors and fonts (site-wide theming)

All colors are CSS variables at the top of the `<style>` block:

```css
:root {
  --gold:       #CFAA5A;   /* Vanderbilt gold — change to your brand color */
  --navy:       #1A2744;   /* primary dark — headlines, buttons */
  --teal:       #1D7D72;   /* secondary accent — tags, highlights */
  --cream:      #FBF8F2;   /* page background */
}
```

Change any hex value and the update applies everywhere instantly.

---

## Part 2 — Putting the site on the internet

You have two excellent free options for a lab website.

---

### Option A — GitHub Pages (recommended for labs)

**Best for:** Free, permanent hosting, version-controlled, easy to update.
**Your URL will be:** `https://yourusername.github.io/dgh-lab`

**Step-by-step:**

1. Create a free account at github.com
2. Click **New repository** → name it `dgh-lab` → set it to **Public** → click Create
3. Click **Add file → Upload files**
4. Drag and drop `dgh-lab-website.html` and rename it to `index.html` before uploading
   (the file must be named `index.html` to load at the root URL)
5. If you have a `photos/` folder, upload that too
6. Commit the files (click the green **Commit changes** button)
7. Go to **Settings → Pages** (left sidebar)
8. Under **Source**, select **Deploy from a branch → main → / (root)**
9. Click Save — your site will be live within 60 seconds

**To update the site later:** Edit the file locally → go back to your repository
→ click the file → click the pencil (Edit) icon → paste your changes → commit.

---

### Option B — Netlify (easiest, drag-and-drop)

**Best for:** Zero setup, instant deploy, automatic contact form handling.
**Your URL will be:** `https://dgh-lab.netlify.app` (customizable)

**Step-by-step:**

1. Go to netlify.com → click **Sign up** (free)
2. From the dashboard, drag your `index.html` file directly onto the page
3. Netlify deploys it instantly and gives you a random URL like `https://clever-name-abc123.netlify.app`
4. Go to **Site settings → Change site name** to get `https://dgh-lab.netlify.app`

**To update:** Drag the new file onto the Netlify dashboard again — it redeploys automatically.

---

### Adding a custom domain (optional)

If you want a URL like `www.dghlab.org` instead of a github.io or netlify.app address:

1. Buy a domain at namecheap.com or Google Domains (~$12/year for a .org)
2. In your hosting dashboard (GitHub Pages or Netlify), find **Custom domain**
3. Enter your domain name and follow the DNS instructions provided
4. It propagates within a few hours

Vanderbilt may also be able to give you a `vanderbilt.edu` subdomain —
contact Vanderbilt IT or your department's web admin to ask.

---

### Keeping the site updated

Whenever you want to change content:
1. Open `dgh-lab-website.html` in a text editor
2. Make your changes
3. Save and re-upload to GitHub or Netlify using the steps above

No coding knowledge beyond basic HTML is needed for content changes —
every section is clearly labeled with ✏️ comments in the file.

---

## Quick reference: file structure

```
dgh-lab/
├── index.html         ← the website (renamed from dgh-lab-website.html)
└── photos/            ← create this folder for team headshots (optional)
    ├── pi.jpg
    ├── sofia.jpg
    └── ...
```

That's it — one file runs the entire site.
