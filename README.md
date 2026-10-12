# SanityAI website

Static site: a scroll-scrubbed film of seven painted scenes (one character per screen, six continuous camera moves), followed by results, tools, process, FAQs and a contact form.

- `index.html` — page, styles, film engine, FAQ schema and the contact form (no build step)
- `assets/` — PP Mondwest heading font (licensed separately) and the SanityAI logos
- `keys/` — one still per scene (`-d` desktop 1280×720, `-m` phone 540×720 crop)
- `packs/` — transition frames per clip and screen size (uint32 header length | JSON frame sizes | WebP frames)

Contact form posts to FormSubmit, which emails wasim@sanity.ai. The first submission sends a one-time activation email to that address; click it to start receiving messages.
