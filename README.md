# DT SL Paper Generator (no-login version)

Students open the website, generate Paper 1 / Paper 2 / topic tests with markschemes,
and upload scanned answers for feedback. No Claude login needed. Marking is done by
`api/mark.js`, which calls CodeCraft API with YOUR key, kept on the server.

## Deploy on Vercel (about 10 minutes)
1. Create a free account at vercel.com (sign in with GitHub or email).
2. Put this folder in a GitHub repository (or install the Vercel CLI and run `vercel` inside this folder).
3. In Vercel: Add New → Project → import the repository → Deploy.
4. Project → Settings → Environment Variables, add:
   - `CODECRAFT_API_KEY` = your key from https://codecraftapi.com/dashboard
   - `CODECRAFT_MODEL` = a vision-capable model ID (see step 6)
   - optional `CODECRAFT_MODEL_CAREFUL` = a stronger model for "Careful marking"
5. Deployments → Redeploy (variables apply only to new deployments).
6. To see which model IDs your key can use, open `https://YOUR-SITE.vercel.app/api/models`.
   Pick a Claude, GPT-4o-class or Gemini model that supports images, set it as
   `CODECRAFT_MODEL`, and redeploy.
7. Share `https://YOUR-SITE.vercel.app` with students.

## Notes
- Never put the API key in `index.html`. Anyone can read a web page's code.
- There is no access code, so anyone with the link can request feedback and use your
  CodeCraft tokens. Watch usage on your CodeCraft dashboard; if it is misused, change the key.
- Each marking sends up to 12 compressed page images (Vercel limits requests to about 4.5 MB).
- Students' scanned work is sent to CodeCraft (a third-party service) and on to the model provider.
