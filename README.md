# AI Prompt Studio

Turn rough notes into clean, structured AI prompts, then send them to ChatGPT, Claude, Perplexity and seven other assistants.

**Live:** https://aiprompt-studio.com

- One HTML file (~150 KB): all CSS and JS inline, no build step, no server, no sign-up.
- 6 tools: rephrase, summarise, reply, e-mail, translate, general prompt.
- 9 interface and output languages, chosen independently.
- Design: "Bant" personal design system (petrol palette, light and dark).
- Plan and decisions: `KARAR-VE-PLAN.md`.
- Settings and history stay in the browser (`localStorage`).
- The app does not call any AI itself; it builds the prompt and hands it over.

## Deploy

Hosted on Netlify. Every push to `main` deploys automatically.
`_redirects` sends the `netlify.app` subdomain to the custom domain with a 301.

By Kemal Beydilli.
