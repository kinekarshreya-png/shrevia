# Shrevia.ai V6 — Update Instructions

1. Back up your existing Shrevia data from Settings → Backup & privacy → Export backup.
2. Upload the website files (`index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.json`, `icon.svg`) to the same hosting location, replacing the V5 files.
3. Open the existing Cloudflare Worker used by Shrevia.
4. Replace its code with the complete `worker/index.js` from this ZIP and deploy.
5. Do not change the existing Worker URL, `GEMINI_API_KEY`, `APP_ACCESS_CODE`, `ALLOWED_ORIGINS`, or `LEARNOVA_KV` binding.
6. Reopen Shrevia. If an old version remains cached, close the installed app/browser tab and reopen it online once.
7. Check AI connection in Settings. The Worker should report version 6.
8. Open Study Planner, select an existing subject, enter its exam date, and add it. Repeat for each exam.

## Important
- Planner data and AI preferences are stored in this browser's local IndexedDB settings and are included in JSON backups.
- The Study Planner uses a default three-block daily schedule (50 + 50 + 40 minutes); it does not ask for chapters, difficulty or daily hours.
- Missed tasks are kept until you choose whether to adjust the plan.
- Device sync remains optional; this release does not require enabling it.
