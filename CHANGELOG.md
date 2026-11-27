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

## V7 — 26 November 2026
- Kept the four-item bottom navigation visible on AI and Settings screens.
- Reordered Home: Good Morning, AI Assistant, Quick Note Box, Study Planner.
- Moved the conditional backup reminder from Home to the Subjects page.
- Bumped the service-worker shell cache to V7.
- Kept the V6 Worker/API protocol unchanged; no Worker deployment needed.


## V8 — Subject Paper Creator
- Added a Paper tab inside every subject.
- Supports random balanced papers and papers following a user-typed or uploaded photo/PDF pattern.
- Uses the subject's readable materials as the syllabus source.
- Saves generated papers locally and in encrypted sync snapshots; includes reopen, delete, print/PDF and answer-key reveal.
- Added Worker `paper` task and bumped Worker compatibility version to 7.
