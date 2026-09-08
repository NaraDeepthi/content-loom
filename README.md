# ContentLoom

**AI-powered social media content generator for Real Estate, Jewellery, Perfume, and FMCG/Food brands.**

ContentLoom generates a full, ready-to-publish social media content plan — captions, visual
direction, and hashtags — tuned to the tone, vocabulary, and content pillars of four industries.
Upload reference material (brochures, price lists, product shots, decks) and it's used as
context for the generated posts.

## Features

- **Industry selection** — Real Estate, Jewellery, Perfume, FMCG/Food, each with a distinct
  voice, tone, and set of content pillars (e.g. Location/Amenities/Investment for Real Estate,
  Craftsmanship/Occasion/Emotion for Jewellery, Fragrance notes/Mood/Gifting for Perfume,
  Taste/Ingredients/Family for FMCG).
- **Content duration & quantity** — 1 Week (3 posts), 2 Weeks (6 posts), 1 Month (12 posts).
- **Reference file upload** — PDF, DOC/DOCX, PPT/PPTX, XLS/XLSX, TXT, and images, parsed
  client-side and passed to the AI as context (images are sent as real vision input).
- **Content format selection** — Feed Post, Carousel, Reel/Video Idea, Story — mixable across
  the plan.
- **Generated posts include** post number/date, a ready-to-publish caption, a visual direction
  (what image/video to create or use), and relevant hashtags.
- **Copy / export** — copy an individual post or the whole plan, or download it as a `.txt` file.

## Tech stack

- Plain **HTML5 / CSS3 / vanilla JavaScript** — single self-contained file, no build step
- **Mammoth.js**, **SheetJS (xlsx)**, **PDF.js** (loaded via CDN) for in-browser reference file parsing
- **Anthropic Claude API** (`claude-sonnet-4-6`) for content generation

## Running it

This is a single HTML file with no dependencies to install.

1. Clone the repo and open `content-loom.html` directly in a browser, or serve it locally
   (e.g. the VS Code "Live Server" extension).
2. All of the UI — industry/plan/format selection, drag-and-drop file upload — works immediately.

### ⚠️ About the "Generate Content" button

The file calls the Anthropic API directly from the browser
(`fetch('https://api.anthropic.com/v1/messages')`). This works inside Anthropic's own hosted
preview environments, but **will not work from a plain static page** because:

- there's no API key attached to the request, and
- the Anthropic API blocks direct cross-origin browser calls (CORS).

To make generation work when self-hosting this file, add a small backend proxy that holds your
`ANTHROPIC_API_KEY` server-side (Node/Express, Python/Flask, or a serverless function all work),
and point the `fetch()` call in the script to your proxy's endpoint instead of
`api.anthropic.com` directly. See [Anthropic's API docs](https://docs.claude.com) for details.

## License

MIT — feel free to reuse and adapt.
