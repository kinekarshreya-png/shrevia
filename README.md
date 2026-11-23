# Shrevia AI — V5 release

## Update steps
1. **GitHub:** upload/replace the site files from this ZIP: `index.html`, `app.js`, `styles.css`, `manifest.json`, `icon.svg`, and `README.md`. Keep the files at the same website root as V4.
2. Refresh the website twice (or close and reopen the installed app).
3. **Settings → Connection:** keep your existing Worker URL and access code, then tap *Save & test connection*.

**Cloudflare Worker:** no Worker update is required for V5. The existing V4 Worker API and sync protocol are deliberately retained.

## Turn on Sync between laptop and phone (one-time, free)
1. Cloudflare dashboard → *Storage & databases* → **KV** → *Create a namespace* (e.g. `learnova-sync`).
2. Your Worker → *Settings* → *Bindings* → *Add* → **KV namespace** → variable name **`LEARNOVA_KV`** → pick that namespace → Deploy.
3. Make sure the Worker has the secret **`APP_ACCESS_CODE`** (Sync refuses to run without it).
4. On every device: Settings → Connection → the **same Worker URL and access code** → Save & test. The top bar shows "☁ Synced".

How it works: all data is gzip-compressed and **encrypted in your browser (AES-GCM, key derived from your access code)** before it is uploaded, so Cloudflare only ever stores unreadable bytes. The Worker never decrypts or merges. Newest edit of each item wins, deletions are propagated, and the AI chat is merged message by message. Original photo/PDF files are NOT synced (only the text read from them). Free KV has a daily write limit; Shrevia AI batches uploads (about 12 seconds after you stop editing) to stay far below it.
If you ever change the access code, use *Settings → Sync → Reset cloud copy* (it re-uploads this device's data under the new code).

## Links
Add → **Links** saves the address as a normal clickable link (opens the original site in a new tab). Nothing is copied. When you tick a link in *Create notes*, the Worker reads that page at that moment, the text is used only for that note, and it is not stored. Pages that need a login, are paywalled, are PDFs/files, or build their content with JavaScript cannot be read: Shrevia AI says so and you can use Select Files or Text instead.

## Add chooser
Camera · Gallery / Photos · Links · Text · Select Files. Select Files never forces the camera and accepts PDF, Word (.docx), text/Markdown/CSV and PNG/JPG/WebP images. If the in-app camera is blocked, a "phone camera app" fallback appears.

## Layout
Home, Subjects, AI and Settings are separate pages (bottom bar on phones, side rail on laptops). Each page fits the screen; only long lists scroll inside their own box. Subject screens keep their header and tabs fixed.

## Privacy & security
Nothing is public. The Worker only answers your site (`ALLOWED_ORIGINS`), requires your access code, rate-limits requests, and refuses to fetch private/internal web addresses. CORS is not authentication; the access code is.

## Known limits
- Link reading runs inside a free-plan Worker (10 ms CPU limit); very large pages may fail and are capped at about 1 MB of HTML.
- Sync uses clocks of your devices to decide "newest edit"; keep device time automatic.
- The AI can be wrong. Check important answers and marked work yourself.


## V5 updates
- Rebranded the app as Shrevia AI (including app manifest and icon).
- Added subject and saved-material topic selectors to flashcard generation and quiz generation.
- New flashcards retain their source topic metadata; due-card review can be scoped to the selected topic.
- Refreshed the Assistant and Settings panel headers and visual hierarchy.
- Existing IndexedDB database name, sync encryption format, Worker API and storage protocol are intentionally preserved for upgrade compatibility.
