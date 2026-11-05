# Shrink a video

Compress a video down to a target file size (8, 10, 25, 50 MB or your own number) so it fits Discord and other upload limits.

Everything runs **in your browser** with [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm). Your video is never uploaded to any server.

## Use it

Open the site, drop in a video (mp4, mov, mkv or webm), pick a size, press **Compress**, then **Download**.

## Notes

- The first run downloads the encoder (about 30 MB). Your browser caches it afterwards.
- Encoding happens on your CPU inside the tab, so long or high-resolution videos take a while. Keep the tab open.
- The whole file is loaded into memory. Files over about 1 GB may fail, and files over 2 GB are rejected. A desktop browser works best.
- Output is H.264 video with AAC audio in an MP4, using two-pass encoding (or one pass in "Fast mode"). The result is aimed about 5% under the target.

## Run locally

Opening `index.html` directly from disk will not work. Serve the folder instead:

```
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Host it on GitHub Pages

1. Put `index.html` (and the other files here) at the root of a GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. After a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

No build step and no special headers are needed.

## Credits

Built on ffmpeg.wasm (`@ffmpeg/ffmpeg` 0.12.10 and `@ffmpeg/core` 0.12.6), loaded from the jsDelivr CDN with unpkg as a fallback. FFmpeg is licensed under the LGPL/GPL; the libx264 encoder in the core build is GPL.
