# Zealact Blog setup execution log

Date: 2026-06-13

## Inputs

- Project: Personal Blog
- Repository: https://github.com/wayfull/zealact
- Blog name: Zealact Blog
- Description: personal blog of product developments.
- Author: Zealact <wfu8255@gmail.com>
- Locales: en, zh
- Primary language: en
- Requested domain: zealact.ai
- Current public URL: https://zealact.ai
- Fallback workers.dev URL: https://zealact-blog.wfu8255.workers.dev
- Theme preset: apple
- Layout preset: journal
- Comments: enabled, approval required
- GitHub login: disabled
- Google login: disabled
- Email Sending: disabled
- R2: enabled

## Cloudflare account

- Account name: Wfu8255@gmail.com's Account
- Account ID: 99d699abb5eb1c73428bb1719a980671

## Resources

- Worker: zealact-blog
- Worker URL: https://zealact-blog.wfu8255.workers.dev
- Custom domain: zealact.ai
- Worker version: c523123b-be01-4cee-8bdc-927e90fdfaab
- D1: zealact-blog-cms
- D1 database ID: 91c2c477-4dfd-4da5-8502-94094fb93fd2
- KV namespace: zealact-blog-cache
- KV namespace ID: 2f54afc861a84b579823f1c37f484a6e
- R2 bucket: zealact-blog-assets

## Completed

- Cloned empty target repository.
- Copied 01MVP/blog-starter template into the target repository.
- Installed dependencies with pnpm 11.2.2.
- Authenticated Wrangler to Cloudflare.
- Created D1 database.
- Created KV namespace.
- Created R2 bucket after the account owner enabled R2.
- Wrote Worker/D1/KV/R2 wrangler configuration.
- Generated and uploaded BETTER_AUTH_SECRET.
- Generated Worker types.
- Built the web app successfully.
- Applied all remote D1 migrations through 0016_comment_ai_moderation_audit.sql.
- Deployed the Worker to workers.dev and bound the custom domain `zealact.ai`.
- Verified R2 object put/get with `verification/test.txt`.

## Verification

- Node.js: v24.16.0
- pnpm: 11.2.2 via npx
- Wrangler login: successful
- Build: successful
- D1 migrations: successful
- Deploy: successful
- Custom domain DNS: successful
- `/`: 200 text/html
- `/blog`: 200 text/html at https://zealact.ai/blog?q=&tag=&series=&page=1
- `/admin`: 200 text/html via redirect to https://zealact.ai/login
- `/openapi.json`: 200 application/json
- `/rss.xml`: 200 application/rss+xml
- `/sitemap.xml`: 200 application/xml
- `/robots.txt`: 200 text/plain
- D1 query: successful
- R2 put/get: successful
- Admin user D1 row: successful
- API token D1 row: successful
- Authenticated export: successful
- Authenticated backup: successful

## Pending

1. Custom domain verification completed: `zealact.ai` resolves through Cloudflare nameservers (`austin.ns.cloudflare.com`, `nadia.ns.cloudflare.com`) and returns 200 for public routes.
2. GitHub push is blocked until GitHub CLI or HTTPS credentials are configured on this machine.
3. First admin account created: `wfu8255@gmail.com` with role `admin`.
4. API token created: `token_7073c450-4884-47d5-b4fe-0991b7534b08` (`blogcms_d85ee79d...` prefix). Secret stored outside the repository at `/Users/davidf/.zealact-api-token`.
5. Authenticated export verified: `GET /api/export` returned 200 JSON.
6. Authenticated backup verified: `POST /api/backups` returned 201 and wrote a ZIP backup record to R2.
