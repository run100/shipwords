# Hop Hop Hop AI — Shipwords site implementation

Domain: https://hophophopai.com/

## Scaffold

From the repository root (Node 24, pnpm 10):

```bash
pnpm install
pnpm new-site hophophopai --domain hophophopai.com
pnpm install
cd sites/hophophopai
pnpm db:generate
pnpm db:migrate:local
pnpm dev
```

Do not modify shared packages unless strictly necessary. Start with `sites/tinydeskai-example/src/site/tool.tsx` for photo-to-video workflow; the default `templates/ai-site` is an image generator. The specific Hop Hop Hop dance template, provider support, music rights, and model cost must be verified before enabling paid generation. Never advertise a working video effect without testing it.

## Landing page SEO

- URL: `/`
- Title: `Hop Hop Hop AI Video Generator – Create Dance Videos`
- Description: `Create a Hop Hop Hop AI dance video from your photos. Upload images, preview the dance template, and make a shareable video online.`
- Canonical: `https://hophophopai.com/`
- H1: `Hop Hop Hop AI Video Generator`
- H2: `How to Make a Hop Hop Hop AI Video`
- H2: `Hop Hop Hop AI Dance Examples`
- H2: `What Is the Hop Hop Hop AI Trend?`
- H2: `Tips for Better Photo-to-Video Results`
- H2: `Frequently Asked Questions`

Implement SEO using `pageHead(site, {title, description, path:'/', jsonLd})` in `src/routes/index.tsx`. Use `WebApplication` structured data. Add `VideoObject` only after publishing an actual owned playable sample with real poster and upload date. FAQ schema must match visible FAQ content; do not promise rich results.

## Functional requirements

- Mobile-first hero: sample video on left, photo upload + generator on right on desktop; stacked on mobile.
- Template selection: Friends, Twins, Pet (only expose variants supported by the chosen model).
- Upload JPEG, PNG, WebP using `uploadReference`; validate size and reference count.
- Generate through `useGeneration`, preserving idempotent billing and failed-job credit refunds.
- Show pending, succeeded and failed job states; video preview and MP4 download.
- Reuse existing authentication, pricing, credits, payments, account and legal pages.
- Preserve form state during sign-in and checkout.
- Consent to use uploaded photos; prohibit unauthorized impersonation.
- Ensure no copyrighted music is bundled without permission.

## Launch gates

1. `pnpm --filter ./sites/hophophopai check`
2. Verify real provider template output with multiple photo combinations.
3. Validate credits, refunds, Stripe webhooks, R2 access and deletion policies.
4. Test iPad and mobile upload and checkout.
5. Check canonical, sitemap, robots, metadata and schema.
6. Deploy to preview before production DNS changes.

Status: implementation plan committed; app scaffolding and runtime checks still pending.
