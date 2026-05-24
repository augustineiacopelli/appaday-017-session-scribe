# AppADay · 017 · Session Scribe

**Category:** A · AI-Powered Tools
**Built:** 2026-05-24
**Live:** [augustineiacopelli.github.io/appaday-017-session-scribe](https://augustineiacopelli.github.io/appaday-017-session-scribe)

## What It Does

Record any conference session or lecture directly in the browser. The Web Speech API transcribes audio in real time as you record. When you stop, the full transcript is sent to Claude, which returns structured session notes: a 2–3 sentence summary, a Roman-numeral outline, key takeaways, notable quotes, and follow-up questions. Notes can be copied to clipboard or emailed via your device's default mail app.

## How to Use

1. Enter your Anthropic API key — it is saved to localStorage automatically and reloaded on every visit. Use the "Forget Key" button to clear it if you are on a shared device.
2. Optionally fill in session title, speaker name, and conference name. These are embedded in the output.
3. Tap the red circle to begin recording. Grant microphone permission when prompted.
4. Watch the live transcript accumulate in the transcript box.
5. Tap the button again to stop recording.
6. Tap **Generate Outline & Summary** to send the transcript to Claude.
7. Review the structured notes, then Copy or tap **Email Me** to open your mail app pre-filled.

## Technical Notes

- Uses the browser Web Speech API for real-time speech-to-text (requires Chrome or Safari; requires internet connection — audio is processed by Google's speech servers)
- Only the text transcript is sent to the Anthropic API — no audio is uploaded
- Handles sessions of any length; even a 60-minute session produces a transcript well within Claude's context window
- API key persisted in localStorage for convenience; never in source code
- Email uses `mailto:` protocol to open the device's default mail app pre-filled with subject and body
- Direct browser-to-Anthropic API calls using `anthropic-dangerous-direct-browser-access: true`
- Single `index.html`, no frameworks, no dependencies

## Definition of Complete

- [x] Records microphone audio in the browser with live transcript display
- [x] Sends transcript to Claude and returns structured outline, summary, takeaways, and follow-up questions
- [x] Session metadata (title, speaker, conference) embedded in output
- [x] API key persists across page loads via localStorage with clear/forget option
- [x] Copy-to-clipboard works
- [x] Email button opens mail app pre-filled with notes
- [x] Mobile-friendly at 375px viewport
- [x] API key entered at runtime, never in source code
