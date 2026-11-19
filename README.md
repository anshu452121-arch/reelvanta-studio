# REELVANTA STUDIO

A custom React + TypeScript studio website with a small Express backend. No website-builder plugin is used.

## Run locally
1. Install Node.js 20 or newer.
2. Extract this folder and open a terminal in it.
3. Run `npm install`.
4. Copy `.env.example` to `.env`.
5. Run `npm run dev`.
6. Open `http://localhost:5173`.

The Vite dev server serves the frontend. The Express API runs on port 8787. For local development, configure Vite proxy if you want API requests to reach Express (see below).

## Important: enable local API proxy
Add this to `vite.config.ts` inside the `defineConfig` object:
```ts
server: {
  port: 5173,
  proxy: { "/api": "http://localhost:8787" }
}
```
The supplied frontend uses `/api` endpoints.

## Enable real AI
- Create a Gemini API key in Google AI Studio.
- Put it in `.env` as `GEMINI_API_KEY=...`.
- Optionally set `GEMINI_MODEL=gemini-2.0-flash`.
- The key stays on the server and is never exposed to browser code.

## Enable contact form email delivery
- Create a Resend account and verify a sending domain/address.
- Put the API key in `RESEND_API_KEY`.
- Set `CONTACT_FROM` to a sender address approved by Resend.
- Set `CONTACT_TO` to the inbox that should receive enquiries.
- Without these settings, the form deliberately returns a clear configuration message; it does not pretend to send.

## Production
Build with `npm run build`. Deploy the built `dist` frontend and the Express server together, configure the environment variables, and route `/api/*` to the Express server. Use HTTPS. Set a production origin policy appropriate to your deployed domain in `server/index.ts` before launch.

## Before publishing
- Replace portfolio concept cards with original client-approved edits or media you have permission to use.
- Verify and document the licence for each stock image/video you keep. The current remote Unsplash image URLs are visual placeholders, not a completed rights-clearance audit.
- Add actual video previews only after you have the rights and optimized files.
- Confirm package scope, delivery timelines, revision definitions and pricing before accepting orders.
- Add privacy policy and terms pages before collecting customer data at scale.
