I nw# Pomodoro + Tasklist — Build Plan
*Joshua's challenge. Plan first, build second. We fill this in together, one step at a time. No code until it's done.*

**Joshua's 3 must-haves (the target, for reference):**
1. Track time spent per task within a cycle (e.g. in a 1-hour block: Task A 15m, B 20m, C 25m), viewable per task.
2. Categories / filters on tasks (toggle to see only Project A, or A + B).
3. Daily stats on time spent.
*Stretch (parked for v2): multi-user login/OAuth; a non-AI-looking theme.*

**★ NORTH STAR (the vibe, non-negotiable):** This makes accountability feel *good*. Fun, happy, game-like, encouraging. **Never** pressure, fear, or surveillance ("you'll get fired" energy). Going over your estimate = "that dragon was tougher than you thought," not a failure. The win: Alexis can effortlessly explain **what** she's working on, **why**, **how long**, **estimate vs. actual**, and **what she did**, and feel good doing it, with zero manual status-summary writing (it's automated).

---

## Step 1 — Name the win

**What it is (Alexis's words):** An ADHD-friendly time-management app modeled on the Pomodoro system, themed as a 90s Zelda-style quest game (dark mode, old-school pixel graphics, mages/sorcerers/dragons). Each task is a quest; finishing focus time completes quests. Deliberately does NOT look AI/Claude-made.

**The 3 must-haves, with "done when":**
1. **Track time per task within a cycle.** *Done when:* after a focus block, I can see the minutes each task ate (e.g. Task A 15m, B 20m, C 25m).
2. **Categorize + filter tasks.** *Done when:* I can toggle to show only Project A, or A + B, and the list updates.
3. **Daily stats, comprehensive breakdown.** *Done when:* I can open it and see a clear breakdown of how my time went today.

**Theme vision (captured here, placed properly at Step 3):** 90s Zelda / old-school pixel, dark mode, magic/mages/dragons, tasks-as-quests, badges, leveling up, ADHD-friendly side characters that motivate + remind. Non-Claude look.

## Step 2 — Name the user and the moment

**Who:** mainly Alexis (ADHD; needs to focus without losing track of time), and Joshua (he'll use it too, hence hosted).

**Rollout (phased audience):** v1 = Alexis + Joshua use it and confirm it's good → then open it to other LQ residents/members. *Implication:* "other people using it with their own data" is exactly why **multi-user login/OAuth** is the key v2 unlock (already parked). Could eventually become an **LQ.AI contribution** (ties to the bounty board).

**The moment:** "I'm about to start working. I open it, pick the quest I'm tackling, start the timer, and at the end I can see where my hour actually went, without my ADHD brain having to track it."

**Also wanted (captured):** a **dashboard** you can open at any time via a button, a global view of everything you have, with the estimated time-to-completion for each task. Could look like a **game map / Zelda overworld**, each quest is a location on the map. (Sorted into v1/v2 at Step 3; adds an "estimate" field to tasks at Step 4.)

## Step 3 — In vs. parked

**IN — v1 (ship this week, exchange with Joshua by Thu 6/25):**
1. Pomodoro timer; tasks shown as **quests**.
2. Per-task time tracking within a cycle *(must-have #1)*.
3. Categories + filter toggle *(must-have #2)*.
4. Daily stats breakdown *(must-have #3)*.
5. **Dashboard button** → global view of all quests + estimate vs. actual time, laid out map-style (cards as "locations"), simple layout (no hand-drawn art yet).
6. **Magic vibe:** dark mode, retro/pixel font, Zelda-ish palette, quest language ("Begin Quest," "Quest Complete").
7. **Character art + animations** — done the LEAN way: free open-license (CC0) pixel-art asset packs for the mage / side characters + simple CSS/sprite animations. No hand-drawn art. Magic on screen, shippable this week.
8. **Single-active-quest lock (defeat the ADHD multitasking dragon)** + a **HARD boss-gate to switch**: real-emergency-only, typed justification, daily cap (1, max 2). Emotional/avoidance urge → the **Master Mage** calms + summarizes + breaks down work instead of letting you flee. (Full detail under Step 5.)
9. **Billing marriage:** time captured in 0.1-hr (6-min) units, by matter/client, with a narrative per entry. (Detail in Step 4.)
10. **Login intro:** a short jingle + animation ("Let's go on an adventure!") on login, then drops you at Home. (Lean v1 magic.)
11. **Auto-generated quest summary → the Final Boss:** when you finish a quest, the app compiles an exact summary of what you did (from the logged narratives + time) — the Final Boss "reads" it to let you level up to the next quest. Doubles as an instant in-house "what I did on this matter" recap. *(Lean v1: compile the logged narratives + totals — no AI needed; AI-polish optional later.)*
12. **Save-point on pause/stop:** like a video game, pausing or stopping a quest auto-writes your progress (elapsed time + note) to the ticket before you step away. No lost work.
13. **Attach file/link to a quest (lean v1):** add a filename + a Drive/SharePoint/file link to a ticket so references live on the quest.
14. **Map = real Zelda overworld** (CSS terrain + pixel markers), quests are locations you click. (Not a card grid.)

**PARKED — v2 (after v1 works; promised, not forgotten):**
- Full **custom** pixel-art overworld map (hand-tailored art).
- **Full file import:** Google Drive OAuth + Word/PDF content parsing + real file storage.
- Badges, leveling up, XP systems.
- Side characters that actively motivate + **send reminders** (needs notification logic).
- Multi-user login / OAuth.

## Step 4 — The data model (the big decision)

**Framing (IN-HOUSE, not law-firm billing).** Keep the *discipline* of legal time-tracking (consistent time units, tracked to a matter, with a description), but the purpose is internal visibility: **where does legal's time go** — which business teams, which work types — so you can manage capacity, show turnaround, and prove the function's value. No clients, no invoices. *(First pass; revisable, this is your domain.)*

Three "spreadsheets" (tables). Each row = one entry.

**Matters** (a project / piece of legal work, e.g. "Acme MSA," "Q3 DSAR backlog," "handbook update")
- name
- **stakeholder / business unit served** (Sales, Product, HR, Procurement, Finance, Exec, Board…)
- **work type / practice area** (Commercial, Privacy, Employment, Corporate, IP, Regulatory, Litigation, Ad-hoc advice)
- status

**Quests** (tasks under a matter)
- name (quest title)
- **why / purpose** (the reason / the need it serves — so you can always explain *why*)
- matter (inherits stakeholder + work type)
- estimate (minutes → powers the dashboard + estimate-vs-actual)
- intake date (when the work came in)
- deadline date
- priority (high / med / low)
- reactive vs. proactive (optional — a metric in-house teams love)
- status: `available` / `active` / `complete` — **only ONE quest may be `active` at a time** (the ADHD-dragon rule)
- *(derived on complete)* **auto-summary**: what you did (from narratives) · why · time spent · estimate vs. actual. No manual writing; framed as a win, not a verdict.

**Time Logs** (one per focus chunk)
- which quest / matter
- date
- minutes (tracked precisely; can display in 0.1-hr units, the legal convention)
- narrative (what you did)

**How they connect:** Stakeholder/Matter → Quest → Time Logs. The dashboard derives the in-house metrics that matter: **time by stakeholder/business unit**, **time by work type**, **time by matter**, **turnaround (intake → complete)**, **reactive vs. proactive split**, and open-work backlog.

**Also tracked: Switch Events** (date, reason: emergency vs. emotional, typed justification) → powers the daily switch cap + a gentle honesty stat. Emergency switches spawn a new tracked Quest. The Master Mage reads the active quest's logs to build its summary + breakdown.

## Step 5 — Screens + flow sketch
*Architecture diagram: `app-architecture.txt` (terminal/ASCII).*

**Entry — Login intro:** short jingle + animation ("Let's go on an adventure!") → drops you at Home.

**1. The Quest (home):** your ONE active quest + Pomodoro timer + "Begin Quest." Block ends → "what did you do?" box → logs narrative + 0.1-hr billing time.

**2. The Quest Log:** all quests (matter, priority, deadline, intake date); filter toggle by matter; tap to activate (→ Boss-Gate if one's already active); add a new quest.

**3. The Map (dashboard) — the global brain:** Zelda overworld; each quest is a location on the map. Per quest: estimate vs. actual time, billable total, % toward done, status. The "press a button anytime" overview. This is where stats stop feeling like stats.

**4. The Boss-Gate (switch flow):** only when you try to leave an active quest. **HARD gate** (see detail below).

**Flow:** Login intro → Home ⇄ Quest Log ⇄ Map. Any quest-switch routes through the Boss-Gate → Home.

### Switch Boss-Gate — detail (HARD)
You cannot leave an active quest unless it clears this. The bar = "did someone take poison / get stabbed by an enemy" level. A real emergency, not a feeling.

1. **Why are you switching?**
   - **A person asked** (mom, friend, boss, colleague, partner) for something that's *task-trackable* AND *time-sensitive (must be today)* → go to step 2.
   - **Stress / emotion / avoidance / imposter syndrome** → **DENIED.** Summon the **Master Mage** (below). Back to your quest.
2. **Type the justification (required):** who asked, what it is, and *why it must be today and can't wait.* Saved as a record; the new task becomes a tracked Quest.
3. **Daily switch budget:** **1/day** normally; a **2nd only if it's a true emergency**; **hard cap 2/day.** Beyond that: *"Two battles already today, hero. This dragon waits till tomorrow."*
4. Pass → battle → portal → new quest active.

**The Master Mage (the emotional-branch rescue, v1):** a calming master-mage figure who, instead of letting you flee, (a) tells you you *can* do this (encouraging, never pressure), (b) summarizes everything you've already done on this quest (from your logs), (c) breaks what's left into small, manageable next steps, then gently returns you to your quest. This is the imposter-syndrome / overwhelm intervention, the most important non-obvious feature. *(Lean v1: progress summary from logs + calming copy + a "split the next step" prompt; AI-assist optional.)*

## Step 6 — Tech choices + why
- **Claude Code** to build it (residency rule + you own the harness).
- **One file: `index.html`** with plain HTML/CSS/JS (no framework). *Why:* zero build step, it runs the second you open it, no dependencies (ponytail-lean).
- **localStorage** for data. *Why:* covers every v1 feature, no server needed.
- **Visuals:** dark Zelda-ish theme via CSS + a retro pixel font + emoji characters for v1. *Why:* magic on screen today without an art pipeline; real sprites swap in for v2.
- **Hosting (so Joshua can use it):** static deploy (Vercel / Netlify / GitHub Pages) once it works locally; can do same day.

## Step 7 — The build spec (what drives the build)
Build a single-file `index.html` (HTML/CSS/JS, localStorage), dark Zelda/retro theme, **north-star tone: encouraging game, never fear.** Implement:
- Login intro ("Let's go on an adventure" + short jingle) → Home.
- Home: one ACTIVE quest + Pomodoro timer; on block end, prompt for a narrative + log time (0.1-hr units).
- Quest Log: add/list quests (name, why, matter, estimate, intake, deadline, priority); filter by matter; activate (→ Boss-Gate if one active).
- Map/Dashboard: quests as locations; estimate vs actual, % done; metrics by stakeholder/work type/matter.
- **Switch Boss-Gate (HARD):** emergency (person asked + time-sensitive + typed justification → spawns quest, daily cap 1/2) vs **emotional → Master Mage** (encourage + summarize progress + break down next steps).
- **Final Boss:** on complete, auto-generate the summary (what/why/time/estimate-vs-actual).
Build the skeleton first, then layer. Test live after each piece (Jamie's lessons). Log every fix to `learnings.md`.

## Step 8 — Build loop + workspace
- Folder: `~/mage/projects/2026-06-21-pomodoro-tasklist-build-for-joshua/` (here).
- Files: `index.html` (the app), `build-plan.md`, `app-architecture.txt`, `learnings.md`.
- **learnings.md loop** active: every mistake/preference gets logged.
- No node_modules (vanilla), so nothing new to exclude from backup.
- Quick build-gate (Rule 4): personal learning app · no PII/client data · all local + static host · minimum access · ✅ safe to build.
