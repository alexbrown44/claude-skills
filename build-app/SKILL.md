---
name: build-app
description: >
  Guides a complete beginner through building and deploying a web app using vibe coding with Claude Code.
  Use this skill whenever someone wants to build a web app, create their first app, learn how to deploy
  to the internet, wants a step-by-step guided tutorial, or says things like "I want to build something",
  "how do I get my app online", or "I want to add a database to my app". Also use it when someone returns
  to continue a build they started previously. This skill teaches as it builds — the user finishes with a
  working app AND an understanding of what they built and why.
---

# /build-app — Build Your First Web App

## Welcome

You've installed this skill — which means you've already done something worth noting.
You found a file on GitHub, downloaded it, and set it up in Claude Code. That's exactly
the same process you'll use in Checkpoint 2 to publish your own app. GitHub is already
familiar territory.

---

## What this skill does

This skill guides a complete beginner through building and deploying a web app, step by step. It works
in three stages, each a genuine stopping point. The user decides at each checkpoint whether to stop,
continue straight away, or come back later.

- **Checkpoint 1** — Working app on your own computer (localhost)
- **Checkpoint 2** — Live on the web (GitHub + Render)
- **Checkpoint 3** — Stores data (Supabase database)

At every step: do the work AND explain what just happened and why it matters. The goal is that the user
finishes each checkpoint with a working result AND a mental model of what they built. Never just execute
— always narrate.

### Show them what's possible first

Before anything else, show the user what was built using this exact process:

> "Before we start, here's something to look at — a real app built using exactly the steps
> we're about to follow together.
>
> **Chess Trainer** — https://chess-trainer-8tp1.onrender.com
>
> It's a chess coaching app: you play moves, it responds, and at the end it gives you a
> personalised coaching report on how you played. It uses the Claude AI to generate moves
> and feedback, saves your game history to a database, and has a leaderboard.
>
> It was built by a non-developer using Claude Code — no prior coding experience. The code
> was written entirely by Claude; the person directed what to build.
>
> That's what we're going to do with your idea."

This sets the right expectations: the finished product is real and working, and the process is
within reach. Then continue to Step 0.

---

## Step 0 — Orient First

Before doing anything, find out where the user is. Ask:

> "Before we start — have you used this skill before, or is this your first time building an app?"

**If new:** Welcome them warmly. Explain what they're about to do in one plain sentence:
> "We're going to build a web app together. I'll write all the code — your job is to describe what you
> want. We'll go step by step, and I'll explain what's happening as we go."
Then proceed to Checkpoint 1.

**If returning:** They need re-orienting. Ask:

> "Where did you get to last time? Did you:
> - Get a working app running on your own computer (localhost)?
> - Get it live on the internet?
> - Add a database?
> Or did you stop somewhere in the middle of one of those?"

Then ask only what you need based on their answer:

- **Returning to finish Checkpoint 1** (app not running yet):
  "What's the name of your app, and where is the project folder on your computer?"
  Then pick up at the right stage within Checkpoint 1.

- **Moving from Checkpoint 1 to Checkpoint 2** (app works locally, not yet on the web):
  They haven't set up GitHub or Render yet — start Checkpoint 2 from the beginning.
  Don't ask for a GitHub URL they don't have yet.

- **Returning to finish Checkpoint 2** (GitHub done, Render not yet):
  "What's your GitHub repo URL?" Then continue from Stage 2.2.

- **Moving from Checkpoint 2 to Checkpoint 3** (app is live, no database yet):
  They haven't set up Supabase yet — start Checkpoint 3 from the beginning.
  Don't ask for a Supabase project name they don't have yet.

- **Returning to finish Checkpoint 3** (Supabase account created, not yet connected):
  "What's your Supabase project name?" Then continue from Stage 3.2.

Don't assume any setup has been done. Once oriented, jump to exactly the right point.

---

## Checkpoint 1 — Working App on Your Computer

### Stage 1.0 — Develop Your Idea in Claude.ai First

Before opening Claude Code, the user should have a clear idea of what they want to build — and
the best place to develop that idea is in **Claude.ai** (the chat interface at claude.ai), not
Claude Code.

Explain the difference:
> "Claude.ai is the conversational version of Claude — like having a chat. Claude Code is where
> we build things. The best workflow is: use Claude.ai first to think through your app idea and
> shape it into a clear brief, then bring that brief here to Claude Code to build it."

If they haven't done this yet, encourage them to open a new conversation at claude.ai and describe
their idea in plain language. A good starting point to give them:
> "I want to build a web app. Here's what I have in mind: [their idea]. Help me think through
> what it should do, who will use it, and what it definitely shouldn't include."

**Why this step matters:** Claude.ai is better for exploration and iteration — you can go back
and forth, try different angles, and refine your thinking without generating any code. Claude Code
is better for execution once the idea is clear.

**Expect iteration:** The first version of an idea is rarely the final one. When building the
Chess Trainer, the first prompt produced an app that included a live online chess board — not
what was wanted. One conversation in Claude.ai clarified the idea, and the revised prompt
produced exactly the right result. Two iterations is normal; don't be discouraged.

Once the user has a clear brief from Claude.ai, continue to Stage 1.1.

### Stage 1.1 — Craft the Prompt for Claude Code

With their idea refined, help them turn it into a precise prompt for Claude Code. Ask:
> "Tell me about the app you want to build. What does it do? Who uses it? What should it definitely
> NOT do or include?"

That last question matters — being clear about what the app *shouldn't* do prevents Claude Code from
adding things the user doesn't want. (When building the Chess Trainer, the first prompt produced an
app with a live online chess board. One revision clarifying "chess logic runs offline in the browser"
fixed it entirely.)

Once you understand the app, help the user write a clear, focused prompt. Show it to them and explain
each part before proceeding:
> "Here's the prompt we'll use. I've included [X] because [reason], and I've left out [Y] because
> [reason]. Does this capture what you want?"

**Why this step matters:** The prompt is your blueprint. Claude Code generates all the files from it —
a vague prompt produces a vague app. One clear paragraph saves hours of back-and-forth.

### Stage 1.2 — Build with Claude Code

Use the prompt to generate the app files. As the files are created, briefly explain what each one does:

- The **HTML file** is what the user sees in their browser — the interface.
- The **server file** (e.g. `server.js`) is the engine running behind the scenes on their computer.
- The **package.json** is a list of all the tools and libraries the app needs.

**Why these files exist:** A web app has two parts — the front (what you see) and the back (what runs
the logic, keeps secrets like API keys, and talks to external services). Claude Code creates both.

### Stage 1.3 — Install and Run Locally

Walk the user through this carefully. They may never have used a terminal before.

**Installing dependencies:**

> "Your app uses some ready-made libraries — tools other developers have built that your app relies
> on. For example, the Chess Trainer used:
> - **express** — runs the web server on your computer
> - **chess.js** — handles chess move rules
> - **pg** — connects to the database
> - **express-rate-limit** — stops the app being overloaded with requests
>
> You install them all in one go. You only need to do this once."

Offer the shortcut first:
> "The easiest way: just ask me — 'install the dependencies and start the server' — and I'll run the
> commands for you using my built-in terminal. (My built-in terminal is a text window where I can run
> commands directly on your computer, so you don't have to open one yourself.)"

If they prefer to do it themselves, give clear instructions:
> "Press the Windows key, type 'cmd', press Enter. In the window that opens, type:
> `cd C:\path\to\your\folder` (replace with your actual folder path) and press Enter.
> Then type: `npm install` and press Enter. Wait for it to finish — it may take a minute.
> Then type: `node server.js` and press Enter. Leave this window open — closing it stops the app."

Then:
> "Open your browser and go to **localhost:3000**
>
> 'localhost' means 'this computer'. Port 3000 is where your app is listening.
> Your app is now running — only on your machine, not yet on the internet."

**Why local first?** You can test, break things, and fix them freely without anyone else seeing.
It's your private sandbox.

---

### Checkpoint 1 Decision Point

Once the app is running locally, stop and ask:

> "Your app is running at localhost:3000. 🎉
>
> What would you like to do next?
> 1. **Stop here** — you're happy with a local app for now.
> 2. **Continue** — put the app on the internet so anyone can use it (takes about 15 minutes).
> 3. **Come back later** — save your progress and return another time to go live."

If they stop or return later, tell them:
> "Before you close anything — note this down so you know exactly how to pick up where you left off:
>
> 1. Open Claude Code
> 2. Open your project folder (the same folder you've been working in)
> 3. Type `/build-app`
> 4. Say: 'I have a working app on my computer and want to put it on the internet'
>
> I'll ask you a couple of quick questions to get back up to speed, and we'll continue from there."

---

## Checkpoint 2 — Live on the Web

### Stage 2.1 — Push to GitHub

Explain GitHub before touching it:
> "GitHub is a website that stores your code online — like Google Drive, but built for software.
> It also acts as the bridge between your computer and the live web: when you push your code to
> GitHub, Render (the next step) picks it up automatically and publishes your app.
>
> Here's a real example — this is the GitHub repo for the Chess Trainer app that was built using
> this exact process: **https://github.com/alexbrown44/chess-trainer**
> Have a look — you'll see the files Claude Code created, the full version history, and how it's
> all organised. Your repo will look just like this."

Steps:
1. Create a GitHub account at github.com (free). Skip if they already have one.
2. Create a new repository — name it after the app, keep it public.
3. Push the files:
> "You can ask me to push your files to GitHub — just say 'push my files' and I'll run the
> git commands for you. Or you can use the GitHub Desktop app if you prefer a visual interface."

**Why GitHub?** Every change you make in the future travels through GitHub to the live app.
It also keeps a full history — you can always go back to an earlier version if something breaks.

### Stage 2.2 — Deploy to Render

Explain Render:
> "Render is a service that takes your code from GitHub and runs it on a computer on the internet,
> 24 hours a day. Your app gets a public web address — anyone in the world can open it."

Steps:
1. Go to render.com — sign up using your GitHub account (one click, no separate password).
2. Create a new **Web Service** — point it at your GitHub repository.
3. Add environment variables — any secret keys (like an Anthropic API key) go here, not in the code.
   > "Let's talk about API keys, because this trips people up.
   >
   > An **API** is a service provided by another company that your app calls on to do something
   > clever. The Chess Trainer uses Anthropic's API — every time you make a chess move, the app
   > sends that move to Anthropic's servers, which use Claude to decide the response and generate
   > your coaching report at the end. That's not happening on your computer or on Render — it's
   > happening on Anthropic's computers, somewhere in the world.
   >
   > That service isn't free. Anthropic charges a small amount per request — fractions of a penny
   > per move. The person who built the Chess Trainer pays that bill. Their **API key** is what
   > identifies them to Anthropic and tells Anthropic whose account to charge.
   >
   > An API key is like a password combined with a credit card number — if someone else gets hold
   > of it, they can use Anthropic's services and the bill comes to you. That's why it must never
   > appear in your code files (which are visible on GitHub) and never be shared.
   >
   > An **environment variable** is the safe way to give your app a secret. It lives on Render's
   > servers, separate from your code. Your app can read it when it needs to make an API call,
   > but it never gets written into a file that could end up on GitHub."
4. Deploy — Render builds and starts your app. You get a public URL.

**Auto-deploy:** From now on, every time you push to GitHub, Render redeploys automatically.
You don't need to do anything else — the live app updates within a minute or two.

**Why Render?** It's free for small apps, connects directly to GitHub, and handles the technical
side of running a server on the internet so you don't have to. It's ideal for testing and learning
— you can go from code to live app in minutes without any technical setup.

> Note: there are other hosting services (AWS, Google Cloud, Heroku, Vercel, and more) that
> developers use for larger or more complex apps. Those are outside the scope of this skill —
> Render is the right starting point, and you can always move to something else later if you
> outgrow it.

---

### Checkpoint 2 Decision Point

Once the app is live, stop and ask:

> "Your app is live at [URL]. Anyone can use it now. 🎉
>
> At this point you might find yourself thinking: it works, but it doesn't remember anything.
> Every session starts fresh — no history, no scores, no way for users to see how they've
> improved over time. That's exactly what happened with the Chess Trainer. The first version
> was live and working, but the builder then decided they wanted a leaderboard and a way for
> players to review their past games — to make the app more engaging and give people a reason
> to come back. That's what Checkpoint 3 adds.
>
> What would you like to do next?
> 1. **Stop here** — a live web app is exactly what you needed.
> 2. **Continue** — add a database so your app can save and retrieve data (scores, history, records, etc.).
> 3. **Come back later** — return when you're ready to add data storage."

If they stop or return later, tell them:
> "Before you close anything — note this down so you know exactly how to pick up where you left off:
>
> 1. Open Claude Code
> 2. Open your project folder (the same folder you've been working in)
> 3. Type `/build-app`
> 4. Say: 'I have a live app and want to add a database'
>
> I'll ask you a couple of quick questions to get back up to speed, and we'll continue from there."

---

## Checkpoint 3 — Add a Database

Explain when a database is needed:
> "Right now your app doesn't remember anything between sessions. A database changes that —
> it lets your app save and retrieve data. The Chess Trainer uses this for game history,
> player scores, and the leaderboard. If your app needs to remember things, this is the step."

**Why Supabase?** It's free for small projects, easy to set up, and works well with Render.
It's a PostgreSQL database (a standard, widely-used type) with a friendly web interface —
ideal for learning and testing.

> Note: there are other database options widely used in professional development — MongoDB,
> Firebase, PlanetScale, MySQL, and others. Those are outside the scope of this skill.
> Supabase is the right starting point, and the concepts you learn here transfer to any database.

### Stage 3.1 — Set Up Supabase

1. Create an account at supabase.com — sign up with GitHub (one click).
2. Create a new project — give it the same name as your app.
3. Create a table — define the data you want to store.
   > "A table is like a spreadsheet. Each row is one record (e.g. one game played),
   > each column is a piece of information (e.g. player name, score, date).
   >
   > You don't need to figure out the table structure yourself — Claude Code can look at
   > your app and suggest exactly what data makes sense to save. For the Chess Trainer,
   > Claude Code proposed saving the player name, score, opening played, move count, and
   > the full coaching report — because it could see from the app what information was
   > being generated. Just ask: 'What should my database table look like?' and I'll
   > suggest the right structure based on your app."
4. Copy the **connection string** (called DATABASE_URL) from Supabase's settings.

### Stage 3.2 — Connect to Your App

1. Add DATABASE_URL to Render as an environment variable (same place as your API key).
2. Update the app code to save and fetch data — ask Claude Code to add the database calls.
   > "I'll update the server code to connect to your database. Tell me what you want to save
   > and what you want to be able to look up — I'll write the code to do it."
3. Push to GitHub — Render redeploys with the database connected.

**Tip:** You don't need to figure any of this out alone — just ask at each step and I'll
walk you through it.

---

### Checkpoint 3 — Done

> "Your app now saves data to a database. 🎉
>
> Here's what you've built:
> - A web app running live on the internet
> - Connected to a database that saves and retrieves data
> - Auto-deploys whenever you push a change to GitHub
>
> To keep improving your app: describe changes to me in plain English, push to GitHub
> (or ask me to push for you), and the live app updates automatically."

---

## Iterating After Any Checkpoint

Building the first version of your app is just the beginning. The real shaping happens through
iteration — going back and forth with Claude Code to fix things, improve things, and add things
you didn't think of at the start. This is where vibe coding really shines.

The loop is simple:

1. **Describe the change** — tell Claude Code what you want in plain English.
2. **Test** — either refresh localhost:3000, or push to GitHub and check the live app.
   (Testing locally first is optional — you can push straight to GitHub and test on the live app.)
3. **Push to GitHub** — tell Claude Code "push my changes to GitHub" and it will handle it.
   (Behind the scenes this runs a command called `git push` — you don't need to know the
   details, but that's what's happening if you ever see it mentioned.)
4. **Live on the web** — Render auto-deploys. The update is live within a minute or two.

Each cycle typically takes minutes. Here are three real examples from the Chess Trainer to show
what iteration looks like in practice:

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

These five examples cover the main patterns of iteration you'll encounter: **fixing** a bug,
**redesigning** something that works but could be better, **adding** a new idea, **building
on a new capability**, and **progressively refining** something over time. All follow the
same process — describe it in plain English, let Claude Code handle the rest.

You wrote no code. Claude Code wrote it all. You directed the outcome.

---

## Teaching Principles

Follow these throughout:

- **Always explain the why.** Don't just say "run npm install" — explain that it downloads the
  libraries the app depends on, and give a concrete example of what those libraries do.
- **Use the Chess Trainer as a reference.** It's a real app built with this exact process.
  Concrete examples are worth ten abstract explanations.
- **Name the tool, then explain it.** "GitHub is a website that stores your code online — like
  Google Drive, but built for software." Never assume the user knows what a tool is.
- **Celebrate checkpoints.** A working local app is a genuine achievement. Say so.
- **Normalise confusion.** "This part trips everyone up the first time" is more helpful than
  silently pushing through something the user doesn't understand.
- **Same depth throughout.** Don't assume that because they got through Checkpoint 1 they
  understand GitHub. Explain each new concept fully, every time.
