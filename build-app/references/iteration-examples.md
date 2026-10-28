# Iteration Examples — Chess Trainer

Five real examples of iteration from the Chess Trainer build, covering the main patterns
a beginner will encounter.

---

**Example 1 — Fixing a bug**
Players noticed that typing `0-0` to castle was always rejected as an illegal move, even when
castling was perfectly valid. The fix wasn't obvious, but the description was simple:
*"Every time I try to castle with 0-0, the app says it's illegal. I then have to challenge the
move and it gets resolved. Why does this happen every time?"*
Claude Code diagnosed the cause — the chess library only accepts `O-O` (the letter O, not the
number zero) — and added a one-line fix that converts one to the other automatically.
The user didn't need to understand the fix, just describe the symptom.

**Example 2 — Redesigning a feature**
The original coaching report was a long block of prose — useful, but hard to read quickly.
The ask was: *"I think the feedback report is too long. Can we simplify it so it remains
valuable but is more easily digestible?"*
Claude Code proposed several options. The chosen one replaced the prose with a compact
traffic-light card: a score out of 100, four coloured indicators (green/amber/red) for
opening, tactics, development, and king safety, plus three bullet-point takeaways.
Same information, far easier to scan. One conversation, no code written by the user.

**Example 3 — Adding something new**
Late in development, an idea came up: *"I'd like to add a nugget of chess history or trivia
at the end of each report — like an easter egg. It should be random so you don't see the same
thing twice. Is this doable?"*
Claude Code added it in a single session — a "Did you know?" card with a gold left border,
pulling a different piece of chess history each time. A small touch that makes the app more
memorable. It wasn't in the original plan; it emerged through iteration.

**Example 4 — A new capability unlocks new features**
Once the Supabase database was connected to the Chess Trainer, two features that weren't
possible before suddenly became straightforward to build:

- *"Can we add a leaderboard that shows players ranked by their average score?"*
- *"Can we add a My Games section where a player can look back at all their previous games
  and re-read their coaching reports?"*

Both were added in a single session, because the data was already being saved. The database
didn't just store things — it opened the door to a whole category of features. This is a
common pattern: each new capability you add multiplies what becomes possible next.

**Example 5 — Progressive refinement over multiple sessions**
The How to Play section started as a simple collapsible panel with basic instructions.
Over several sessions it grew — each time a gap was spotted or a new user got confused:

- *"Can we add an explanation of the Your Name field?"*
- *"Can we add an About section?"*
- *"New players don't know which side of the board is which — can we add something to explain that?"*
- *"Can we show what check and checkmate notation looks like, and how to handle two knights
  that can both move to the same square?"*

Each addition was a single request. No session took more than a few minutes. The section
became genuinely useful not because it was planned in full at the start, but because it was
refined in response to real gaps as they emerged. That's the real rhythm of building — ship
something, use it, notice what's missing, fix it.

---

These five examples cover the main patterns of iteration: **fixing** a bug, **redesigning**
something that works but could be better, **adding** a new idea, **building on a new
capability**, and **progressively refining** something over time. All follow the same process
— describe it in plain English, let Claude Code handle the rest.

You wrote no code. Claude Code wrote it all. You directed the outcome.
