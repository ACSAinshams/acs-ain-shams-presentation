# ACS Ain Shams — Beyond Chemistry

A premium Dark Electric Blue Slidev presentation built from the supplied ACS chapter portfolio and its original event photography.

## Requirements
- Node.js 20+

## Run locally
```bash
npm install
npm run dev
```

## Build / export
```bash
npm run build
npm run export:pptx
npm run export:pdf
```

The web version contains the Three.js animated object and CSS visual effects. Advanced 3D, transitions, and interactive behavior may be flattened or differ in PowerPoint/PDF exports.

## GitHub Pages
1. Create a GitHub repository and upload this project.
2. Push the default branch as `main`.
3. In repository Settings → Pages, choose **GitHub Actions** as the source.
4. The included workflow builds and deploys the deck on every push to `main`.

## Customize
- Edit slide content in `slides.md`.
- Replace or reorder images in `public/images/`.
- Main chapter logo: `public/images/acs-logo.png`.
- Three.js object: `src/components/ThreeOrb.vue`.

## Source integrity
Content and photographs are drawn from the supplied `ACS POTFOLIO.pdf`. The portfolio states that the chapter has impacted more than 2,000 students and covers the 2019–2026 journey. No additional performance metrics have been invented.
