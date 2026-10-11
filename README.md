# SanityAI scroll film

Static landing page: a scroll-scrubbed film of the lighthouse keeper's story.

- `index.html` — page, styles and the film engine (no build step)
- `keys/` — one still per scene (`-d` desktop 1280×720, `-m` phone 540×720 crop)
- `packs/` — transition frames, one pack per clip and screen size
  (uint32 header length | JSON list of frame sizes | WebP frames)

Before launch: replace `FORM_ENDPOINT` in `index.html` with a form service endpoint
(e.g. Formspree) and the footer contact placeholder with a real address.
