# Shrevia.ai V7 — Update Instructions

1. Keep a current backup of your Shrevia data if possible.
2. Upload/replace the website files from this ZIP at the same website root: `index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.json`, `icon.svg`, and `README.md`.
3. **No Cloudflare Worker replacement is required for V7.** Keep the V6 Worker, Worker URL, `GEMINI_API_KEY`, `APP_ACCESS_CODE`, `ALLOWED_ORIGINS`, and `LEARNOVA_KV` binding unchanged.
4. Close and reopen the installed app/browser. If the old layout remains, refresh twice while online or fully close and reopen the app.
5. Check that the bottom navigation is visible in AI and Settings.
6. Check Home order: Good Morning → Shrevia AI → Quick Note Box → Study Planner.
7. Check Subjects: the backup reminder appears below the subject list when a backup reminder is due. Backup export/import also remains in Settings → Backup & privacy.

## Notes
- V7 is a frontend/layout update. Existing IndexedDB data and the V6 Worker protocol are preserved.
- AI and Settings are displayed as non-modal main screens so the fixed bottom navigation remains accessible. Other dialogs (planner, subject, camera, etc.) retain their existing modal behaviour.


## V8 deployment
Upload the updated website files and deploy the updated `worker/index.js` to the existing Cloudflare Worker. V8 adds the `paper` AI task and requires Worker version 7. Keep the existing Worker name, URL, `GEMINI_API_KEY`, `APP_ACCESS_CODE`, `ALLOWED_ORIGINS`, and `LEARNOVA_KV` binding unchanged. The browser database upgrades automatically from version 3 to 4; existing subjects and notes are preserved.
