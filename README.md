# THE SECRET GARDEN — V3

A mobile-friendly, silent, browser-based romantic mini-site. Open `index.html` in a modern browser to preview it. No app install is needed. The flower uses canvas drawing/particles; the final bouquet is hand-drawn in canvas, not emoji artwork.

## Private answer submissions (optional)
The site works as a local demo without a backend. To collect custom answers privately:

1. Create a Supabase project.
2. Run `schema.sql` in its SQL Editor. Replace `YOUR_AUTH_USER_UUID` with your own authenticated user UUID before creating the owner policies.
3. Set `SUPABASE_URL` and `SUPABASE_ANON_KEY` in `index.html` to the project URL and public anon/publishable key. Never use a service-role key in client-side code.
4. Create an owner account in Supabase Authentication and sign in at `admin.html` with that account. Paste the same project URL/key into the fields.
5. Test with a custom answer in a private/incognito visitor window. Confirm it appears after owner sign-in and that an unauthenticated visitor cannot read rows.

Important: the current SQL intentionally lets visitors submit answers without identifying themselves. `owner_id` may be null for anonymous inserts; the owner dashboard policies restrict reading to your authenticated UUID. If you change schema/policies, re-test access before sharing.

## Hosting and QR code
For a real QR code, deploy the folder to a public HTTPS host first (for example, GitHub Pages, Netlify, or Cloudflare Pages), then make a QR code for the final public URL. Do not make a QR code for a local file path. `admin.html` should not be linked from the public landing page; its data access is protected by Supabase authentication and RLS, not by hiding the URL.

## Notes
- Silent animation; no audio is used.
- The custom answer box tells the visitor that submitted text goes to the page creator.
- The flower growth animation is a browser recreation inspired by the supplied reference video, not a pixel-identical copy.
