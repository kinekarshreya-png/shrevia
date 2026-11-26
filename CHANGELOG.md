# Shrevia.ai V6 — Changelog

## Added
- Branded welcome screen: “Created by Shreya”.
- Study Planner with subject/exam-date entry, full automatically generated schedule, balanced exam-date priority, daily task completion, and an explicit confirmation before missed tasks are redistributed.
- Editable AI learning preferences and conservative automatic learning after repeated preference signals.
- Swipe navigation across Home, Subjects, AI and Settings, with safeguards around text inputs and chat/reading content.
- Persistent bottom navigation remains visible behind AI and Settings overlays.
- Updated AI conversation instruction to avoid repeating its introduction.
- Worker protocol version 6.

## Preserved
- Existing IndexedDB database name and schema.
- Existing subject/material/note/card/quiz/chat features.
- Existing Cloudflare Worker connection and optional encrypted sync architecture.
- Existing service-worker/offline shell behaviour.

## Deployment
Upload the website files from this ZIP to the same hosting location. Then deploy `worker/index.js` to the existing Cloudflare Worker. Keep the existing Worker URL, API secret, access code, allowed origins and KV binding. The Worker name in `wrangler.toml` is intentionally unchanged to avoid accidentally creating a second Worker.
