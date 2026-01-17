# mardi.camp

A Svelte 5 + SvelteKit website for mardi.camp - a Mardi Gras gathering for the twitter/tpot/vibecamp/ingroup community.

## Tech Stack

- **Framework**: SvelteKit with Svelte 5
- **Styling**: Tailwind CSS
- **Deployment**: Vercel (adapter-vercel)
- **Forms**: Web3Forms API (access key: `f9b8439f-cf20-40c1-809e-a88b2a9fcc45`)
- **Analytics**: Plausible.io

## Project Structure

```
src/
├── app.html          # HTML shell with Plausible analytics
├── app.css           # Tailwind directives
├── lib/
│   ├── components/
│   │   ├── Header.svelte  # Win98 style header (2025)
│   │   └── Footer.svelte  # Win98 style footer (2025)
│   ├── mascot.png
│   └── fates.jpeg    # Tweet screenshot
└── routes/
    ├── +layout.svelte
    ├── +page.svelte       # 2026 homepage (current)
    └── 2025/
        └── +page.svelte   # Archived 2025 version
```

## Design

### 2026 Theme (Current)
- Modern gradient: green (#0AA14D) → purple (#582B7D) → gold (#FFD700)
- White text on gradient background
- Purple buttons with yellow borders
- Modal-based UI for events/details

### 2025 Theme (Archived)
- Windows 98 nostalgia aesthetic
- Teal background (#008080)
- Gray panels (#c0c0c0)
- Animated stars and bouncing mascot

## Key Files

- **Homepage**: `src/routes/+page.svelte`
  - Contains commented-out signup form (lines 164-306)
  - Event schedule in modal
  - Form handling with Web3Forms

## Colors
```javascript
const mggreen = '#0AA14D';
const mgpurple = '#582B7D';
const mggold = '#FFD700';
```

## Running Locally

```bash
npm install
npm run dev
```

## Deployment

Automatically deploys to Vercel on push to main/master.
