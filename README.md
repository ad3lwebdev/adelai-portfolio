# Adel Auditor — AI Automation Specialist Portfolio

A premium, production-ready personal portfolio website for Adel Auditor, an AI Automation Specialist.

## Features

- **Dark / Light mode** — user preference persisted in `localStorage`
- **Glassmorphism UI** — frosted glass cards with backdrop-filter blur
- **Animated gradient background** — floating orbs + SVG circuit traces
- **Typing hero effect** — cycles through role titles character by character
- **Smooth scrolling navigation** — sticky navbar with active-link highlight
- **Mobile menu** — hamburger with animated X transform
- **Skills progress bars** — animated on viewport entry via IntersectionObserver
- **Animated stat counters** — count-up on scroll (50+, 30+, 200+, 10 000+)
- **Project showcase cards** — glassmorphism, hover lift, tag chips
- **Workflow visualization** — 5-step horizontal flow diagram with pulse animations
- **Contact form** — client-side validation with success/error states
- **Fully responsive** — mobile-first, breakpoints at 768px and 1024px
- **SEO optimised** — Open Graph, Twitter Card, canonical, meta descriptions

## Contact Form (n8n automation)

The contact form POSTs to an **n8n Webhook**. The included workflow —
`n8n-workflow-contact-automation.json` — does two things on every real
submission:

1. **Notifies you** by email with the lead's name, email, subject, and message.
2. **Auto-replies** to the visitor's own email address with a friendly
   marketing/welcome message — instant lead-capture follow-up, no manual work.

A spam check (the honeypot field, `botcheck`) branches obvious bots into a
silent no-op instead of sending any emails.

**One-time setup:**
1. Open (or sign up for) n8n — self-hosted or [n8n cloud](https://n8n.io).
2. In n8n: **Workflows → Import from File** and select
   `n8n-workflow-contact-automation.json`.
3. Open the **Notify Adel (Owner)** and **Auto-Reply Marketing Email to
   Client** nodes and attach your SMTP credentials (Gmail app password,
   or any SMTP provider). Adjust the `fromEmail` / `toEmail` fields if needed.
4. Feel free to rewrite the HTML in **Auto-Reply Marketing Email to Client**
   — that's the marketing copy the client receives.
5. Click the **Contact Form Webhook** node → copy the **Production URL**.
6. Activate the workflow (toggle in the top-right of the n8n editor).
7. Open `script.js`, find `N8N_WEBHOOK_URL` near the top of the
   `CONTACT FORM` section, and paste your production webhook URL in.
8. Save, commit, push — done. Every submission now emails you *and*
   auto-replies to the client.

## Updating Your Skills & Projects

You no longer need to edit HTML to add a project or skill. Just edit
**`data.json`** — the page renders it automatically. See `AGENTS.md` for the
exact field format. After saving, refresh the page (via a local server or
GitHub Pages) to see your changes.

## Tech Stack

- HTML5 (semantic, accessible, ARIA labels)
- CSS3 (custom properties, backdrop-filter, CSS animations, grid, flexbox)
- Vanilla JavaScript (ES2020, IntersectionObserver, no dependencies)
- [Inter](https://fonts.google.com/specimen/Inter) + [Space Mono](https://fonts.google.com/specimen/Space+Mono) (Google Fonts)
- [Font Awesome 6](https://fontawesome.com/) (CDN icons)

## Running Locally

No build step required, but since skills and projects are now loaded from
`data.json` via `fetch()`, you need to serve the folder over HTTP (opening
`index.html` directly as a `file://` URL will fail to load that content):

```bash
# any static server works
npx serve .
python3 -m http.server 8080
```

Then visit `http://localhost:8080` (or the port shown).

## GitHub Pages Deployment

Push the repository to GitHub and enable **Pages → Deploy from branch → `main` / `/ (root)`**. The site will be live immediately with no build configuration.
