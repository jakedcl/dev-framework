# Images

For CMS-backed sites on Vercel. For photos users upload themselves, see [user-uploads.md](user-uploads.md).

- **CMS photos go through the CMS's own image CDN with a per-image `next/image` loader,** never Vercel Image Optimization. Why: the Hobby quota of 5,000 transformations is shared by the whole team, and jasiahpowers alone pushed it to 75%. (jasiahpowers, Oct 23, 2026)
- **Apply the loader per image, to CMS URLs only, not as a global custom loader.** Why: small local `/public` assets can keep Vercel's optimizer. (jasiahpowers)
- **Always set `sizes` on responsive images, and keep `remotePatterns` limited to the CMS host.** Why: each width is a separate transformation, and stray hosts bypass the loader. (jasiahpowers)
- **Blur placeholders must swap to the sharp image,** including after a hard refresh. Why: drewdella's cover stayed blurry until a normal reload. (drewdella#16)
- **Note the setup in the project's existing README.** No separate doc. (jasiahpowers)

## How it works
- **Vercel bills one transformation per unique image × width × format, on a cache miss.** Once made, a size is cached and shared by every visitor, so traffic costs bandwidth, not transformations.
- **Spikes come from many new combinations at once:** redesigns, new pages, bulk uploads, new breakpoints.
- **Sanity resizes on its own CDN at no extra cost.** Its free-plan quotas are per project (100 GB assets, 100 GB bandwidth a month).
- **To check:** srcset URLs point at the CMS CDN, not `/_next/image`, and Vercel → Usage → Image Optimization stays near zero.
