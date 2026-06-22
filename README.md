# QuestTimer ⚔️

An ADHD-friendly Pomodoro and in-house legal time tracker, themed as a 90s Zelda quest. Built plan-first in Claude Code (Joshua's Build-1 challenge).

**Live app:** _(GitHub Pages link goes here once it's live)_

## Why it exists

Most productivity apps assume a brain that sets things up and works a process. This one is built for how an ADHD brain actually works: you dip in only when you are ready to do something, dump it, do it, and leave. The app meets that moment instead of handing you a system to manage.

It is also a real in-house legal time tracker underneath: every quest is tied to a matter, time is logged in 0.1-hour units, and the app derives where legal's time goes (by stakeholder, by work type). No clients, no invoices, internal visibility only.

## How to use it

It is one self-contained HTML file. Open it in a browser. Your data saves in your own browser (localStorage), so if you open the live link you automatically get your own private board. Nothing is sent to a server.

### The three places

1. **🗡 Today** — your daily board. Dump what you are doing today in one field, hit start on a quest (one tap makes it active and starts the focus clock), and complete it when done. Today clears itself each morning.
2. **🏝 Island of Unfinished** — a map where whatever you did not finish drifts off to. Not lost, not done. Rescue one back into Today when you are ready.
3. **📦 Won Quests** — your archive of finished quests and time records, tucked behind a button so it is never in your face.

### The mechanics that keep you honest

- **One active quest at a time.** No multitasking.
- **The Switch Boss.** Try to abandon an active quest and a gate makes you justify a real emergency, or a calmer guide helps you take a smaller next step instead of bailing.
- **The Final Boss.** Completing a quest auto-compiles a summary of what you did and your time vs. your estimate. That doubles as an instant "what I did on this matter" recap.
- **Music.** Original chiptune that you can mute.

North star: it is a game that gets you to do the things. Encouraging, never fear or surveillance.

## Tech

Single file: vanilla HTML, CSS, and JavaScript with localStorage. Zero build step, zero dependencies, runs offline. Music is synthesized in the browser with the Web Audio API (no audio files). See `build-plan.md` for the full design.

## Status

Initial version (v1), shared for feedback. Forks and issues welcome.
