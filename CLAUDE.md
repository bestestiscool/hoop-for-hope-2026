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
| `index.html` | Main landing page (deployed to Vercel) |
| `complete-page-inline.html` | Old version with inline styles (for reference) |

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
