# Hoop For Hope 2026 - WordPress Deployment Instructions

## Files Created
- `landing-page.html` - The HTML to paste into WordPress
- `styles.css` - The CSS to add to WordPress

---

## Step 1: Add the CSS

1. Go to WordPress Admin
2. Navigate to **Appearance > Customize**
3. Click **Additional CSS**
4. Paste the entire contents of `styles.css`
5. Click **Publish**

---

## Step 2: Create the Page

1. Go to **Pages > Add New**
2. Set the title to: `3v3` (this will create the URL `/3v3`)
3. In the editor, click the **+** button to add a block
4. Search for **Custom HTML** and add it
5. Paste the entire contents of `landing-page.html`
6. Click **Publish**

---

## Step 3: Replace Placeholder URLs

Before publishing, replace these placeholders in the HTML:

| Placeholder | Replace With |
|-------------|--------------|
| `SMOOTHIE_BAR_IMAGE_URL` | URL to the smoothie bar/food image |
| `OLIVE_BRANCH_LOGO_URL` | URL to the Olive Branch sponsor logo |
| `SPONSORSHIP_PDF_URL` | URL to the sponsorship opportunities PDF |

### How to get image/PDF URLs in WordPress:
1. Go to **Media > Add New**
2. Upload the image or PDF
3. Click on it and copy the **File URL**

---

## Step 4: Optional - Full Width Layout

If the page has sidebars or doesn't go full width, you may need to:

1. On the page edit screen, look for **Page Attributes** in the right sidebar
2. Change the Template to **Full Width** (if available)

Or add this CSS to force full width:
```css
.page-id-YOUR_PAGE_ID .site-content {
  max-width: 100%;
  padding: 0;
}
```
(Replace YOUR_PAGE_ID with the actual page ID)

---

## Troubleshooting

### Page looks narrow/has sidebars
- Try switching to a "Full Width" or "Blank" page template
- Or add the full-width CSS fix above

### Fonts not loading
- Make sure the CSS was added correctly in Additional CSS
- Clear your browser cache

### Colors/styles not applying
- Check that the CSS was saved and published
- Look for any CSS conflicts in browser DevTools

---

## Color Reference

- **Orange (Primary):** #f7931e, #ff6b35
- **Purple (Secondary):** #c084fc
- **Dark Background:** #1a1a2e, #16213e
- **Text:** #fff, #e0e0e0

These match the Jewnity Sports branding.
