# Logo Stamp

Apply one logo to many images at once — pick the corner, size, opacity, and
padding, preview every result live, then download the whole batch as a `.zip`.

Everything runs in the browser. No image is ever uploaded to a server, so it is
safe for internal / client assets.

## Features

- Bulk apply a single logo (PNG with transparency recommended) to any number of images
- 9 anchor positions (corners, edge centers, middle) via a 3×3 picker
- Logo size as a **% of each image's width** — stays consistent across mixed image sizes
- Opacity control for watermark-style stamping
- Padding X / Y, also expressed as a % of image width
- PNG or JPEG output
- Per-image "save" or **Download all** as a zip
- Light / dark theme (remembers your choice, otherwise follows the OS)

## Run locally

It is a single static file. Either open `index.html` directly, or serve the
folder:

```bash
npx serve .
# or
python -m http.server 8000
```

## Deploy

No build step. Publish the folder as static hosting.

### Netlify
- Drag the `logo-stamp` folder onto https://app.netlify.com/drop, **or**
- Connect the git repo; `netlify.toml` is already configured (publish dir = `.`).

### Vercel
```bash
npm i -g vercel
vercel        # first run links the project
vercel --prod
```
`vercel.json` is included.

### GitHub Pages
1. Push this folder to a repo.
2. Settings → Pages → Source: `Deploy from a branch` → `main` / `/root`.
3. Site publishes at `https://<org>.github.io/<repo>/`.

### Any other host
Upload `index.html` (and the config files if relevant) to any static host —
S3 + CloudFront, Cloudflare Pages, nginx, an internal share, etc.

## Notes for the team

- The only external request is to **Google Fonts**. If your environment blocks it,
  the app still works with system fonts, or you can self-host the two font files
  and update the `<link>` in `index.html`.
- Large batches of high-resolution images use memory proportional to their size,
  since decoding and compositing happen client-side. A few dozen photos is fine;
  hundreds of 24-megapixel originals may be slow on a low-end laptop.

## License

MIT — see `LICENSE`.
