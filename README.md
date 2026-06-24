# Union Station South Website

Fast, optimized static website for Union Station South HOA.

## Structure

- **index.html** — Main website (optimized, ~54 KB)
- **images/** — Optimized images (~1.1 MB total, cached by CDN)
- **fonts/** — Hanken Grotesk web fonts (~220 KB total, cached by CDN)
- **js/** — Support scripts (~15 KB)

## Deployment (Cloudflare Pages)

This repo is connected to Cloudflare Pages. Every push to `main` auto-deploys.

### Build Settings
- **Framework preset:** None
- **Build command:** *(empty)*
- **Build output directory:** `/`

### Performance Optimizations

✅ **Unbundled structure** — Assets served separately, allowing:
- Browser caching of images and fonts
- Cloudflare CDN caching of all assets
- Gzip compression on text files
- Parallel downloads

✅ **Fast load times** — Originally 2 MB bundled HTML → now:
- HTML: ~54 KB
- Images: ~1.1 MB (cached by CDN after first load)
- Fonts: ~220 KB (cached by CDN after first load)

✅ **Modern formats**
- WOFF2 fonts (40% smaller than WOFF)
- Optimized JPEG and PNG images
- Minified inline CSS/JS

## Cloudflare Configuration

Recommended settings for best performance:

1. **Caching Rules** (in Cloudflare dashboard)
   ```
   Match: /fonts/* → Cache everything, 30 days
   Match: /images/* → Cache everything, 30 days
   Match: /js/* → Cache everything, 30 days
   Match: / → Cache HTML, 1 hour (so updates propagate)
   ```

2. **Enable**
   - Auto Minify (CSS, JS)
   - Brotli compression
   - HTTP/2 Server Push (optional)

3. **Image Optimization** (Cloudflare Image Optimization)
   - Enable for WebP/Avif conversion on the fly

## Local Development

```bash
# Serve locally
python3 -m http.server 8000

# Visit http://localhost:8000
```

## Contact Form

Uses Web3Forms API (free tier). The form sends to the configured email address.

---

**File size savings:** From 2 MB bundled → ~1.4 MB total (unbundled, uncompressed)
**Gzip savings:** Additional 60-70% reduction in transit
