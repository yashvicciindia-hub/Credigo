# Credigo Website (Single-File Build)

The entire Credigo website — all 9 pages, all styling, all behavior — lives inside one file: **`index.html`**. Open it directly in any browser; nothing else needs to run or build.

## How the internal navigation works

There are no separate `.html` files for each section. Instead, every page is a `<div class="page" id="page-...">` inside `index.html`, and JavaScript shows/hides the right one when you click a nav link — so it feels like real page navigation (URL updates with a `#hash`, back/forward buttons work, page title updates) without ever leaving `index.html`.

| Nav item | Internal view id |
|---|---|
| Home | `#home` |
| Platform | `#platform` |
| How It Works | `#how-it-works` |
| Technology | `#technology` |
| For Banks | `#banks` |
| For Borrowers | `#borrowers` |
| Impact | `#impact` |
| About | `#about` |
| Contact | `#contact` |

All content, layout, and animations from the original multi-page build were preserved — this is purely a consolidation into one file, not a redesign.

## Everything you need to change before launch

### 1. Logo
No separate logo file is wired in yet — the navbar and footer use an inline SVG mark as a clean placeholder. Search `index.html` for `<span class="mark">` (appears twice — navbar and footer) and replace it with:
```html
<img src="assets/logo/credigo-logo.png" alt="Credigo" style="height:32px;">
```
**File to add:** `assets/logo/credigo-logo.png`

### 2. Images
Three sections currently use placeholder stock photography (hotlinked so the site works immediately). Search `index.html` for `<!-- MANUAL CHANGE:` comments — each one marks exactly which image to replace and with what:

| Add this file | Appears in view | Section |
|---|---|---|
| `assets/images/platform-preview.jpg` | Home (`#home`) | "What is Credigo?" |
| `assets/images/platform-mockup.jpg` | Platform (`#platform`) | Platform introduction |
| `assets/images/borrower-story.jpg` | For Borrowers (`#borrowers`) | Problem section |

Recommended size: 900×700px, JPG.

### 3. Google Forms
**Location in `index.html`:** find `const FORM_LINKS = {` near the top of the `<script>` block at the bottom of the file:

```javascript
const FORM_LINKS = {
  bankPilot:    "https://forms.gle/PASTE_BANK_PILOT_FORM_HERE",
  borrower:     "https://forms.gle/PASTE_BORROWER_FORM_HERE",
  partnership:  "https://forms.gle/PASTE_PARTNERSHIP_FORM_HERE",
  investor:     "https://forms.gle/PASTE_INVESTOR_FORM_HERE",
  contact:      "https://forms.gle/PASTE_CONTACT_FORM_HERE"
};
```

Paste your real Google Form URLs here — this is the only place you need to edit. Every CTA button across every view (`data-form="..."` attributes) reads from this single object automatically.

**Form mapping:**

| Website location | Google Form |
|---|---|
| Navbar → Partner With Us (every view) | Bank Pilot |
| Home → Partner With Us | Bank Pilot |
| For Banks → Request a Pilot | Bank Pilot |
| For Borrowers → Register Your Interest | Borrower |
| Impact / About → Become a Partner | Partnership |
| About → Investment Opportunity | Investor |
| Contact → General Enquiry | Contact |

### 4. Contact information
Search `index.html` for `<!-- MANUAL CHANGE: update contact details -->` — it appears in the footer and again in the Contact view (`#contact`). Current placeholder values (from the pitch deck): `globalexpressgroup@gmail.com`, `+91 96505 60277`, `+91 99101 96123`.

### 5. Colors
Inside the `<style>` block at the top of `index.html`, find `:root { ... }`:
- `--blue` / `--blue-dark` — primary brand blue
- `--orange` — accent color
- `--ink` — heading/body text (near-black)
- `--sky` / `--sky-2` — light blue section backgrounds

Change these once and the whole site updates.

## Notes on content accuracy

All statistics, features and claims come directly from the Credigo pitch deck. Forward-looking numbers (NPA reduction target, 2M+ borrowers, 50+ banks, seed funding ask) are explicitly labelled **Target** on the Impact and About views rather than presented as already-achieved results.

## Structure

```
Credigo-Website/
├── index.html      ← everything: markup, <style>, <script>
├── assets/
│   ├── images/      ← add your final images here
│   ├── icons/
│   └── logo/        ← add credigo-logo.png here
└── README.md
```
