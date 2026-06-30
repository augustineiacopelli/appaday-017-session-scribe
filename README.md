# AppADay · 017 · Session Scribe

**Category:** A · AI-Powered Tools
**Built:** 2026-05-24
**Live:** [augustineiacopelli.github.io/appaday-017-session-scribe](https://augustineiacopelli.github.io/appaday-017-session-scribe)

## What It Does

Record any conference session or lecture directly in Safari on iPad or desktop. As you record, the browser's Web Speech API transcribes audio in real time. When you stop, the full transcript is sent to Claude, which returns a complete set of structured session notes: a 2–3 sentence summary, a Roman-numeral outline, key takeaways, notable quotes, follow-up questions, and a fully cleaned and punctuated version of the transcript. Notes can be copied to clipboard or emailed via your device's default mail app.

## How to Use

1. Tap the gear icon (⚙) and enter your Anthropic API key, default conference name, and default email address. These are saved to your browser's localStorage and persist across sessions.
2. Fill in the session title and speaker name on the main screen. The conference name auto-fills from Settings but can be overridden for any session.
3. Tap the red circle button to begin recording. Grant microphone permission when prompted by Safari.
4. Watch the live transcript accumulate in the transcript box on the right.
5. Tap **■ Stop Recording** when the session ends.
6. Tap **✦ Generate Outline & Summary** to send the transcript to Claude.
7. Review the structured notes, then tap **Copy** or **Email Me** to send them to yourself.

## Transcript Safety & Recovery

The app auto-saves the transcript to localStorage continuously as you record — roughly every sentence. If the page is refreshed, the tab is closed, or Safari terminates the session unexpectedly, a green recovery banner appears on next load showing when the draft was saved and how many words it contains. Tap **Restore** to pick up exactly where you left off. The draft clears automatically after a successful Generate or when a new recording begins.

## Transcript Portability

Between sessions or when internet is unavailable for processing, the transcript can be preserved four ways:

- **↓ Save** — downloads a labeled `.txt` file (Safari will present a share sheet; save to Files or AirDrop)
- **⎘ Copy** — copies the full transcript to clipboard for pasting into Notes or Mail
- **↑ Load** — reads a previously saved `.txt` file back into the app
- **✎ Paste** — opens a text area to paste a copied transcript back in

All four formats include a self-describing header (date, session, speaker, conference, duration) that is stripped automatically before Claude processes the text.

## Output Format

Claude returns a single structured document containing:

- **Session header** — title, speaker, conference, date, start time, end time, and duration
- **Summary** — 2–3 sentences capturing the core argument or purpose
- **Outline** — Roman numeral structure with lettered sub-points
- **Key Takeaways** — 3–7 concise bullet points
- **Notable Quotes / Moments** — verbatim quotes worth preserving
- **Questions / Follow-Up** — unanswered questions and action items
- **Cleaned Transcript** — the full transcript rewritten with proper punctuation, capitalization, paragraph breaks, and filler words removed

## Technical Notes

- Uses the browser Web Speech API for real-time speech-to-text; audio is processed by Google's speech servers and requires an active internet connection
- **Must be used in Safari browser on iPad — not as a Home Screen web app.** Apple restricts Web Speech API to the Safari browser context; the Home Screen (standalone) mode does not support it
- Only the text transcript is sent to the Anthropic API — no audio is ever uploaded
- Handles sessions of any length; a 60-minute session produces roughly 8,000–9,000 words, well within Claude's context window
- API key, conference name, and email address persist via localStorage; never stored in source code
- Auto-save draft also uses localStorage; clears on successful generate or new recording start
- Email uses `mailto:` protocol to open the device's default mail app pre-filled with subject and body
- Direct browser-to-Anthropic API calls using `anthropic-dangerous-direct-browser-access: true`
- Responsive two-column layout in landscape (controls left, transcript right), single-column stack in portrait
- Single `index.html`, no frameworks, no dependencies

## Definition of Complete

- [x] Records microphone audio in Safari with live transcript display
- [x] Sends transcript to Claude and returns summary, outline, takeaways, quotes, follow-up, and cleaned transcript
- [x] Session metadata (title, speaker, conference, date, start time, end time, duration) embedded in output
- [x] API key, conference name, and email persist via localStorage with clear option in Settings
- [x] Auto-saves transcript draft to localStorage continuously during recording
- [x] Recovery banner on load if unsaved draft detected
- [x] Save, Copy, Load File, and Paste transcript options for offline portability
- [x] Copy-to-clipboard for final notes
- [x] Email button opens mail app pre-filled with notes
- [x] Responsive landscape (two-column) and portrait (single-column) layout
- [x] Safari browser chrome clearance via `env(safe-area-inset-bottom)`
- [x] API key entered at runtime via Settings panel, never in source code
