# User uploads

For photos users upload to plain storage (Vercel Blob, S3, R2) that doesn't resize images. If the site has a CMS image CDN, use [images.md](images.md).

- **Resize on the uploader's device before upload.** Make a full version (about 2,000 px on the long edge, JPEG quality 0.85) and a thumbnail (about 480 px), and store both URLs. Why: storage doesn't resize, and Vercel's quota is team-wide. (bannquet, Oct 23, 2026)
- **Thumbnails go wherever photos are small; the full file only in the single-photo view.** (bannquet)
- **Render uploads with `unoptimized` or a plain `<img>`.** Same for avatars (capped at upload) and third-party icons. (bannquet)
- **Don't filter file types with `accept` for uncommon formats. Validate on the server.** Why: iPhone greys out `.gpx` files when `accept=".gpx"` is set. (bannquet)
- **One bad file never sinks a batch, and deleting a photo deletes its thumbnail.** → [forms.md](forms.md)
- **Backfill scripts for old photos support `--dry-run` and refuse to write without a confirm env var.** (bannquet)
- **To check:** a phone photo lands as two small files, grids load thumbnails (network tab), and image optimization usage stays near zero.
