# Hoop For Hope 2026 - Landing Page

## Project Overview
Landing page for Jewnity Sports' "Hoop For Hope 2026" 3v3 charity basketball tournament supporting Jewnity Sports & Migdal Ohr.

**Live URL:** https://3v3-eta.vercel.app
**WordPress Page:** https://jewnity.ca/3v3
**GitHub Repo:** https://github.com/bestestiscool/hoop-for-hope-2026

---

## WordPress Integration

Since WordPress strips CSS from `<style>` tags and blocks JavaScript via CSP, we host the landing page on Vercel and fetch it via JS.

### WordPress Snippet (paste in Custom HTML block)

```html
<style>
.page-id-7988 main.site-main > .container > .row > div > h1.mb-4 { display: none !important; }
</style>

<div id="h4h-container" style="width: 100vw; margin-left: calc(-50vw + 50%);"></div>

<script>
fetch('https://3v3-eta.vercel.app')
  .then(function(r) { return r.text(); })
  .then(function(html) {
    document.getElementById('h4h-container').innerHTML = html;
  })
  .catch(function(e) { console.error('Failed to load:', e); });
</script>
```

**Note:** The `.page-id-7988` selector hides the default WordPress page title "Jewnity Sports 3v3" that appears above the content.

---

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Main 3v3 landing page (deployed to Vercel) |
| `register/index.html` | Registration hub page |
| `register/featured-image.png` | Featured image for register page |
| `register/jewnity-basketball.png` | Basketball sport image |
| `register/jewnity-soccer.jpg` | Soccer sport image |
| `register/jewnity-football.jpeg` | Football sport image |

---

## Register Page

**Live URL:** https://3v3-eta.vercel.app/register/
**WordPress Page:** https://jewnity.ca/register/
**WordPress Page ID:** 8101

### WordPress Snippet for Register Page

```html
<style>
.page-id-8101 main.site-main > .container > .row > div > h1.mb-4 { display: none !important; }
</style>

<div id="jr-container" style="width: 100vw; margin-left: calc(-50vw + 50%);"></div>

<script>
fetch('https://3v3-eta.vercel.app/register/')
  .then(function(r) { return r.text(); })
  .then(function(html) {
    document.getElementById('jr-container').innerHTML = html;
  })
  .catch(function(e) { console.error('Failed to load:', e); });
</script>
```

---

## Register Page - Problems & Solutions

### Problem 1: WordPress Critical Error (500)
**Issue:** The original /register page showed "There has been a critical error on this website" - a PHP 500 error.

**Root Cause:** The WordPress theme (Emilia) had a custom "Register" template with a bug. The PHP code did `foreach($links as $link)` on an ACF field without checking if it was null first.

**Solution:** Instead of fixing the PHP template (which had multiple errors), we created a Vercel-hosted version like the 3v3 page. Changed the WordPress page template from "Register" to "Default Template" and used JavaScript fetch to load Vercel content.

### Problem 2: Images Not Loading (404 Errors)
**Issue:** After adding images to the register page, they showed 404 errors in the console when viewed on WordPress.

**Root Cause:** Images used relative paths like `src="jewnity-soccer.jpg"`. When WordPress fetches the HTML via JavaScript, relative paths resolve to the WordPress domain (jewnity.ca/register/jewnity-soccer.jpg) instead of Vercel.

**Solution:** Changed all image paths to absolute URLs pointing to Vercel:
```html
src="https://3v3-eta.vercel.app/register/jewnity-soccer.jpg"
```

### Problem 3: Featured Image Too Tall on Mobile
**Issue:** The WordPress featured image (1080x1350 portrait) took up the entire mobile screen, pushing content far down.

**Solution:** Removed the WordPress featured image entirely. Added the image to the Vercel page with constrained dimensions:
```css
max-width: 400px;
max-height: 500px;
object-fit: contain;
```

### Problem 4: Sport Images Cropped
**Issue:** Sport images were cropped using `object-fit: cover` with fixed dimensions.

**Solution:** Used `height: auto` to show full images on desktop, and `width: 100%` on mobile for responsive stacking:
```css
.jr-sport-images img { width: 300px; height: auto; }
@media (max-width: 680px) {
  .jr-sport-images img { width: 100%; }
}
```

### Problem 5: WordPress Page Title Showing
**Issue:** WordPress displayed its own page title "Register" above the Vercel content.

**Solution:** Added CSS in the WordPress snippet to hide the title using the page ID:
```css
.page-id-8101 main.site-main > .container > .row > div > h1.mb-4 { display: none !important; }
```

---

### Register Page Content

**Open Registration (with TeamLinkt links):**
- Men's Basketball (Summer 2026) - cid=61787
- Men's Soccer (Now Open) - cid=51757
- Men's Flag Football (Now Open) - cid=52557

**Coming Soon:**
- Men's Hockey, Men's Pickleball, High School Basketball (Boys/Girls), NY 3v3 Tournament

---

## How to Update

1. Edit `index.html` locally
2. Commit and push to GitHub:
   ```bash
   git add . && git commit -m "Update landing page" && git push
   ```
3. Deploy to Vercel:
   ```bash
   vercel --prod
   ```

Changes go live instantly. No WordPress changes needed.

---

## External Links

| Link | URL |
|------|-----|
| Register (Zeffy) | https://www.zeffy.com/en-CA/ticketing/hoop-for-hope-2026-jewnity-sports-and-migdal-ohr-3v3-basketball-tournament |
| Donate (Zeffy) | https://www.zeffy.com/en-CA/peer-to-peer/hoop-for-hope--2026 |
| Leaderboard Embed | https://www.zeffy.com/embed/leaderboard/hoop-for-hope--2026 |
| Sponsorship Deck | https://www.canva.com/design/DAG-mYW3cJU/9LfphGP1PMr9jee7gLtn_g/view |

---

## WordPress Media URLs (Images)

```
https://www.jewnity.ca/wp-content/uploads/2026/01/Hoop-for-hope.png
https://www.jewnity.ca/wp-content/uploads/2026/01/Migdal-Ohr-and-Jewnity.png
https://www.jewnity.ca/wp-content/uploads/2026/01/Event-overview.png
https://www.jewnity.ca/wp-content/uploads/2026/01/Parnter-with-us.png
https://www.jewnity.ca/wp-content/uploads/2026/01/Thank-you.png
https://www.jewnity.ca/wp-content/uploads/2026/01/smoothie-bar.png
https://www.jewnity.ca/wp-content/uploads/2026/01/olive-branch-logo.png
https://www.jewnity.ca/wp-content/uploads/2026/01/FF_Hoope-For-Hope-Flyer-scaled.jpg
```

---

## Event Details

- **Date:** Sunday, March 22nd, 2026
- **Location:** HoopDome, 75 Carl Hall Rd, Unit 17, North York, ON
- **Registration Fee:** $36/player
- **Team Fundraising Minimum:** $500
- **Prize:** $1,800 for 1st place
- **Eligibility:** Men aged 16+
- **Team Size:** 3-5 players (4+ recommended)

---

## Changelog

### 2026-02-12
- Created Register page as Vercel subfolder (`/register/`)
- Bypassed WordPress PHP critical error by using Vercel-hosted solution
- Added featured image + 3 sport images (basketball, soccer, football)
- Fixed image 404 errors by using absolute Vercel URLs
- Made images responsive: full display on desktop, stacked on mobile
- Documented all problems and solutions in CLAUDE.md

### 2026-01-28 (Update 2)
- Added Zeffy popup script for Register/Donate buttons (modal popups instead of new tabs)
- Updated Register button: `zeffy-form-link="https://www.zeffy.com/embed/ticketing/hoop-for-hope-2026-jewnity-sports-and-migdal-ohr-3v3-basketball-tournament-2?modal=true"`
- Updated Donate button: `zeffy-form-link="https://www.zeffy.com/embed/donation-form/hoop-for-hope--2026-2?modal=true"`
- Added Campaign embed + Leaderboard embed side by side (new URLs with `-2`)
- Changed "7 games" to "5 games minimum"
- Added highlighted "Multiple Divisions" section with emphasis styling
- Added "Lounge: Non-stop kosher & delicious food all day — breakfast & lunch included!"
- Replaced text logo with logo.png image

### 2026-01-28
- Created landing page with all sections (hero, prize banner, flyer, causes, food/lounge, leaderboard, tournament info, sponsors, CTAs)
- Deployed to Vercel for WordPress integration
- Added responsive 2x2 grid for info cards (stacks on mobile via CSS media query)
- Added "Tap to view" badges on banner images that open full-size in new tab
- Documented WordPress snippet and update process

---

## Troubleshooting

**Page shows blank in WordPress:**
- Check browser console for CSP errors
- Verify Vercel URL is accessible
- Make sure the fetch script wasn't stripped by WordPress

**Styles not applying:**
- The CSS is inside the fetched HTML, so it should work
- Check if WordPress is blocking the fetch request

**Images not loading:**
- Images are hosted on jewnity.ca WordPress media
- Verify the URLs are still valid
