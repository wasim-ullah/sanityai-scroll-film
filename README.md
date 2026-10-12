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
| `whatsapp_click_floating_button` | Floating WhatsApp button (bottom right) |
| `whatsapp_click_film_scene` | WhatsApp button in the last film scene |
| `whatsapp_click_contact_section` | WhatsApp button in the contact section |
| `whatsapp_click_footer` | WhatsApp link in the footer |
| `contact_form_start` | First click or tap into the contact form |
| `contact_form_validation_error` | Submit pressed with missing or invalid fields |
| `contact_form_submit_attempt` | Valid form sent |
| `contact_form_submit_success` | Form delivered (main conversion) |
| `contact_form_submit_error` | Form failed to send |
| `header_book_call_click` | Book a call in the header |
| `hero_book_call_click` | Book a call in the first scene |
| `hero_see_how_it_works_click` | See how it works |
| `film_write_to_us_click` | Write to us in the last scene |
| `header_logo_click` | Logo |
| `menu_marketing_click`, `menu_search_click`, `menu_automation_click`, `menu_paid_media_click`, `menu_contact_click` | Desktop menu |
| `tablet_menu_*_click` | Same links on tablet |
| `footer_results_click`, `footer_how_we_work_click`, `footer_faqs_click`, `footer_send_message_click` | Footer links |
| `film_scene_1_view` … `film_scene_7_view` | Each film scene reached (once per visit) |
| `film_watched_to_end` | Last scene reached |
| `film_read_more_open` | Read more opened on a scene card (phone and tablet) |
| `faq_question_open` | An FAQ opened (`faq_question` parameter) |
| `section_view_results`, `section_view_process`, `section_view_faq`, `section_view_contact` | Section scrolled into view (once per visit) |

Click events also carry `action_type`, `click_text` and `click_url`.
