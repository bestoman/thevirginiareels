# The Virginia Reels website

One static page: `index.html`. No build step, no dependencies.

```
index.html          the whole site (HTML, CSS and the player script)
images/band.webp    the band photo shown on the page
images/share.jpg    the preview image used when the link is shared
fonts/              the Special Elite typeface and its licence
audio/*.mp3         the three tracks (128 kbps)
netlify.toml        Netlify settings (publish folder and cache headers)
```

## Deploy with GitHub and Netlify

1. Create a new GitHub repository and push this folder to it.
2. In Netlify choose Add new site, Import an existing project, then pick the repository.
3. Leave the build command empty and set the publish directory to `.` (netlify.toml already says this).
4. Deploy. Every push to the main branch redeploys the site.
5. Under Domain management, add `thevirginiareels.com` and follow Netlify's DNS steps.

## Common changes

- **Change the text:** edit the paragraphs in `index.html` under `class="about"`.
- **Replace a track:** put the new MP3 in `audio/`, then update that track's `data-src`, its title and its `data-d` (length in whole seconds) in the `tracks` list in `index.html`.
- **Add a track:** copy one `<li>` in the `tracks` list and change its values.
- **Change the photo:** replace `images/band.webp`, keeping the same file name, or update the `<img>` tag.
- **Re-encode audio** (needs ffmpeg): `ffmpeg -i in.mp3 -vn -c:a libmp3lame -b:a 128k out.mp3`

## Notes

- The Special Elite font is bundled in `fonts/` (WOFF first, TTF as a fallback), so the page makes no requests to Google. Its licence is `fonts/LICENSE.txt`.
- `og:image` in `index.html` assumes the site will live at `https://thevirginiareels.com`. Change it if the address differs.
- The email address and Instagram link are written directly in `index.html`.
