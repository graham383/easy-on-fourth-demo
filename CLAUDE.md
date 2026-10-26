# Easy on Fourth (concept demo): project instructions

Static site, no build step. Everything served lives in `public/` (`index.html` + `images/`).
Hosting: Vercel project `easy-on-fourth-photos`, deployed from this GitHub repo's `main` branch.

## Deploying
- Deploy ONLY by committing and pushing to `main` on GitHub. Vercel deploys automatically.
- Never deploy via base64/text uploads (Vercel MCP `upload_file`/inline `create_deployment`) or any route that re-encodes images.
- Do not create a new Vercel project or change the public URL (easy-on-fourth-photos-fc-f93a.vercel.app).
- Never commit `.env`, tokens or credentials.

## Image quality rules (do not break)
- Source of truth: the lossless originals (kept by Graham). Files in `public/images/` are generated: WebP q82 + AVIF q58, named `<name>-<width>.webp|avif`.
- Never replace an image with a smaller or recompressed copy. Never upscale a source or enlarge it with CSS to fake quality.
- Generate variants only downward from the original; every variant must be <= the original's pixel width.
- Keep `<picture>` markup: AVIF then WebP sources, `srcset` with `w` descriptors, accurate `sizes`, explicit `width`/`height`, `fetchpriority="high"` on the hero only, `loading="lazy"` elsewhere.
- Art direction: `dining-m-*` (4:3) and `bar-m-*` (portrait) apply at `max-width:480px` only; other widths use the landscape files.
- Known limits: no true portrait bar original (mobile bar crop is ~1.2x enlarged at 2x DPR); retina desktop needs ~2800px-wide originals for hero and bar.
- After any image change, verify in a browser at 390, 820, 1440 and 1920 wide: `currentSrc`, real file pixel size vs rendered size, and that the bar section shows its photo.

## Content
- Preserve copy, layout and contact details (481 North Service Road West, Unit A37, Oakville ON L6M 2V6; 905-465-4000; easymanager4@gmail.com) unless Graham asks otherwise.
- Writing style for Graham: Canadian English, dollar amounts as figures, dates month-first.
