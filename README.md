# SanityAI website

Static site: a scroll-scrubbed film of seven painted scenes (one character per screen, six continuous camera moves), followed by results, tools, process, FAQs and a contact form.

- `index.html` — page, styles, film engine, FAQ schema and the contact form (no build step)
- `assets/` — PP Mondwest heading font (licensed separately) and the SanityAI logos
- `keys/` — one still per scene (`-d` desktop 1280×720, `-m` phone 540×720 crop)
- `packs/` — transition frames per clip and screen size (uint32 header length | JSON frame sizes | WebP frames)

Contact form posts to FormSubmit, which emails wasim@sanity.ai. The first submission sends a one-time activation email to that address; click it to start receiving messages.

## Google Tag Manager events

Every action pushes its own event name to `window.dataLayer`. To load your container, build with `GTM_ID=GTM-XXXXXXX python3 tools/build_v2.py`. In GTM, add a Custom Event trigger for each name you want to report on.

| Event | When it fires |
|---|---|
| `whatsapp_click_floating_button` | Floating WhatsApp button |
| `whatsapp_click_contact_scene` | WhatsApp button next to the form in the last scene |
| `contact_form_start` | First click or tap into the contact form |
| `contact_form_validation_error` | Submit pressed with missing or invalid fields |
| `contact_form_submit_attempt` | Valid form sent |
| `contact_form_submit_success` | Form delivered (main conversion) |
| `contact_form_submit_error` | Form failed to send |
| `header_request_call_click` | Request a call in the header (desktop) |
| `hero_request_call_click` | Request a call in the first scene |
| `hero_learn_more_click` | Learn more |
| `header_logo_click` | Logo |
| `menu_open_click` | Chapter menu button |
| `footer_email_click` | Email in the footer |
| `film_scene_1_view` … `film_scene_7_view` | Each scene reached (once per visit) |
| `film_watched_to_end` | Last scene reached |

Click events also carry `action_type`, `click_text` and `click_url`.
