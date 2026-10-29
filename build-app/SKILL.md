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

# /build-app — Build Your Web App

## Welcome

You've installed this skill — which means you've already done something worth noting.
You found a file on GitHub, downloaded it, and set it up in Claude Code. That's exactly
the same process you'll use in Checkpoint 2 to publish your own app. GitHub is already
familiar territory.

**One thing to know before we start:** Claude Code is not just a code generator — it's more like
having a very generous, very patient software engineer sitting next to you. It will build things
for you, yes. But it will also explain what it's doing and why, answer questions at any point,
help you understand an error message, talk through a decision, or just clarify something that
isn't making sense.

You never need to feel stuck or lost on your own. If something isn't clear, ask. If something
goes wrong, describe it. If you want to understand what just happened, say so. There are no
stupid questions here — the whole point is that you finish this with both a working app and a
genuine understanding of how it was built.

Ask freely. That's what Claude Code is for.

**How long does this take?** About one hour to get a working app live on the internet.
Add another hour if you want a database. You don't need to do it all in one sitting —
each checkpoint is a natural stopping point.

---

## What this skill does

This skill guides a complete beginner through building and deploying a web app, step by step. It works
in three checkpoints, each a genuine stopping point. The user decides at each checkpoint whether to stop,
continue straight away, or come back later.

**Stack:** The app you build will use JavaScript (Node.js) on the backend and plain HTML/CSS on the
frontend. This skill does not support Python, React, Vue, Next.js, or any other language or framework.
If the user's idea requires one of those, this skill won't apply — be upfront about that before starting.

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
> It was built by Alex, a non-developer, using Claude Code — no prior coding experience. The code
> was written entirely by Claude; Alex directed what to build.
>
> That's what we're going to do with your idea."

This sets the right expectations: the finished product is real and working, and the process is
within reach. Then continue to Step 0.

---

## Step 0 — Orient First

Before doing anything, find out where the user is. Ask:

> "Before we start — are you building a new app, or returning to continue one you started before?"

**If building a new app:** Welcome them warmly. Explain what they're about to do in one plain sentence:
> "We're going to build a web app together. I'll write all the code — your job is to describe what you
> want. We'll go step by step, and I'll explain what's happening as we go."
Then proceed to Checkpoint 1.

**If returning to an existing app:** They need re-orienting. Ask:

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

### Stage 1.0 — Shape Your Idea and Craft the Prompt

Before writing any code, you need a clear picture of what you're building. Start by asking:
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

**Important — no database in this prompt.** The first build is deliberately self-contained. If the
user mentions saving data, user accounts, or a leaderboard, note that those are great ideas for
Checkpoint 3 — but keeping them out of the first build means a faster, cleaner start. Tell them:
> "We'll leave the database out for now — that's Checkpoint 3. The first version will be a
> fully working app; we add the ability to save data once it's live."

**Important — check the stack.** Before approving the prompt, verify it doesn't mention React, Vue,
Next.js, Python, Flask, or any other framework or language. If it does, rewrite that part to use
Node.js and plain HTML/CSS. Tell the user:
> "I've kept the tech stack to Node.js and plain HTML — that's what this skill builds with.
> If you specifically need [framework], this skill won't cover it, but for most apps this stack
> works perfectly well."

**Why this step matters:** The prompt is your blueprint. Claude Code generates all the files from it —
a vague prompt produces a vague app. One clear paragraph saves hours of back-and-forth.

### Stage 1.1 — Approve the Prompt

Before writing a single line of code, show the user the full prompt and ask them to read it carefully:

> "Here's the prompt I'll use to build your app. Read it through — does it describe what you want?
> Is anything missing, wrong, or included that you don't want?
> Once you're happy with it, say 'go ahead' and I'll start building."

Do not start building until they explicitly confirm. This is their last easy chance to change
direction — once the build starts, changes require iteration rather than a fresh start.

### Stage 1.2 — Build with Claude Code

Use the prompt to generate the app files. As the files are created, briefly explain what each one does:

- The **HTML file** is what the user sees in their browser — the interface.
- The **server file** (e.g. `server.js`) is the engine running behind the scenes on their computer.
- The **package.json** is a list of all the tools and libraries the app needs.

**Why these files exist:** A web app has two parts — the front (what you see) and the back (what runs
the logic, keeps secrets like API keys, and talks to external services). Claude Code creates both.

**About API keys — and why they must stay secret:**

If your app connects to an external service, you'll need an API key for it. An API key is a private
password that identifies your app to that service and authorises it to use it (often at a cost).

The Chess Trainer, for example, calls the Claude AI to generate chess moves and coaching feedback.
To do that, it needed an Anthropic API key. That key was created at **console.anthropic.com** — the
Anthropic developer dashboard — and added to the local setup as an environment variable (explained
below). Every time a user plays a move, the app makes a call to Claude using that key, and the
account that owns the key is charged a tiny fraction of a penny for it.

Not every app needs an API key. But if your app uses any external service — AI, maps, weather data,
payment processing, email sending, translation, and so on — it will almost certainly need one.
Examples:
- A weather app might use an **OpenWeatherMap API key**
- A payment feature would use a **Stripe API key**
- An app that sends emails might use a **SendGrid API key**

The fact that you're building with Claude Code doesn't mean your app has to use the Claude AI —
it's just the tool you're building with. Your app can use any external service it needs.

**Why API keys must never appear in your code files:**

Your code files will be uploaded to GitHub (a public website) in Checkpoint 2. If an API key is
written directly into a code file, anyone in the world can find it, copy it, and use your account —
running up charges or accessing your data.

The safe approach is to store API keys as **environment variables** — values that live on your
computer (or server) separately from the code, and are never uploaded anywhere. The code refers to
them by name (e.g. `process.env.ANTHROPIC_API_KEY`) without ever containing the key itself.

For the local build, Claude Code will create a `.env` file in your project folder to hold these
values. This file stays on your computer only — it is never pushed to GitHub.

Claude Code will handle setting this up. When it asks for an API key, that's where to paste it.

**Important — the .env file must never be uploaded to GitHub:**
Claude Code will also create a file called `.gitignore` in your project folder. This is a list
of files that should never be pushed to GitHub — and `.env` is always on it. You don't need to
manage this yourself, but it's worth understanding: the `.gitignore` file is what keeps your
API key off GitHub. If you ever look at your repo on GitHub and notice your `.env` file is
missing — that's correct, and intentional. If it ever does appear there, ask Claude Code
immediately: *"My .env file has been pushed to GitHub — what do I do?"*

**If the app loads but API calls fail** — the first thing to check is whether the `.env` file
exists and contains the correct key. Ask Claude Code: *"Can you check my .env file is set up
correctly?"*

### Stage 1.3 — Install and Run Locally

Walk the user through this carefully. They may never have used a terminal before.

**Installing dependencies:**

> "Your app uses some ready-made libraries — tools other developers have built that your app relies
> on. For example, the Chess Trainer used:
> - **express** — runs the web server on your computer
> - **chess.js** — handles chess move rules
> - **express-rate-limit** — stops the app being overloaded with requests
>
> (If you add a database later, more libraries get added at that point — for example **pg**, which
> connects to a PostgreSQL database. But that's Checkpoint 3, not now.)
>
> You install them all in one go. You only need to do this once."

Present both options together so they can see what's involved either way:

> "There are two ways to do this:
>
> **Option 1 (easiest):** Just tell me — 'install the dependencies and start the server' — and I'll
> run the commands for you using my built-in terminal. (My built-in terminal is a text window where
> I can run commands directly on your computer, so you don't have to open one yourself.)
>
> **Option 2 (do it yourself):**
> Open a terminal window:
> - **Windows:** Press the Windows key, type **cmd**, press Enter. A black window opens — that's the Command Prompt.
> - **Mac:** Press **Cmd + Space**, type **Terminal**, press Enter.
>
> Type: `cd /path/to/your/folder` (replace with your actual folder path) and press Enter.
> On Windows the path looks like `C:\Users\yourname\my-app`; on Mac it looks like `/Users/yourname/my-app`.
> This navigates to your project folder — like opening a drawer before you can use what's inside.
>
> Then run these two commands, one at a time:
>
> `npm install`
> This reads your **package.json** file and downloads all the libraries your app needs. npm stands
> for Node Package Manager — think of it as an app store for code libraries. You only need to run
> this once.
>
> `node server.js`
> This starts your app. 'node' is the engine that runs JavaScript on your computer (outside of a
> browser). 'server.js' is your app's main file. Leave this window open — closing it stops the app."

**To stop the server:** When you're done testing, go back to the terminal window and press
**Ctrl+C**. This stops the app. (This is also useful if you need to restart it after making
changes — stop it with Ctrl+C, then run `node server.js` again.)

**Common problems at this stage:**

- **'npm is not recognised' or 'command not found'** — Node.js isn't installed yet. Go to
  nodejs.org, download the LTS version, and install it. Then close and reopen your terminal
  and try again.
- **Not sure of your folder path** — ask Claude Code: *"What is the full path to my project
  folder?"* and it will tell you exactly what to type.
- **'EADDRINUSE', 'port already in use', or 'address already in use'** — your app is trying
  to start but something else is already using port 3000 (often a previous run of your app
  that didn't close properly). Ask Claude Code: *"Port 3000 is already in use — can you stop
  whatever is running there?"* Or the quickest fix: restart your computer.
- **localhost:3000 shows nothing** — check whether your terminal window is still open. If it
  closed, run `node server.js` again.

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
> 1. **Continue** — put the app on the internet so anyone can use it (takes about 15 minutes).
> 2. **Stop for now** — you're done for today and will come back to go live another time."

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

**If the push fails with an authentication error** — GitHub no longer accepts your account
password for this. It requires a separate security token (a long auto-generated password
called a personal access token). You don't need to understand the details — just ask Claude
Code: *"My git push failed with an authentication error — can you walk me through fixing it?"*
and it will guide you through generating one in your GitHub settings and using it.

**Why GitHub?** Every change you make in the future travels through GitHub to the live app.
It also keeps a full history — you can always go back to an earlier version if something breaks.
If a change ever makes things worse, just ask Claude Code: *"The last change broke something —
can we go back to how it was before?"* It will use the version history to undo it.

### Stage 2.2 — Deploy to Render

Explain Render:
> "Render is a service that takes your code from GitHub and runs it on a computer on the internet,
> 24 hours a day. Your app gets a public web address — anyone in the world can open it."

Steps:
1. Go to render.com — sign up using your GitHub account (one click, no separate password).
2. Create a new **Web Service** — point it at your GitHub repository.
3. Add environment variables — any API keys go here.
   > "Remember the `.env` file on your computer that kept your API key safe locally? Render has
   > the same concept, but for the live app. Instead of a file on your computer, you add the key
   > directly into Render's settings — it stores it securely on their servers, separate from your
   > code. Your app reads it the same way as before, but now it works on the internet too.
   >
   > This is the step where your live app gets access to any external services it needs."
4. Deploy — Render builds and starts your app. You get a public URL.

**Auto-deploy:** From now on, every time you push to GitHub, Render redeploys automatically.
You don't need to do anything else — the live app updates within a minute or two.

**If something goes wrong:** Deploys don't always work first time — the Chess Trainer hit errors
here too. Render shows a build log with the error message. If that happens, copy the error and
paste it into Claude Code: "My Render deploy failed with this error: [paste it here]". Claude Code
can diagnose the problem and fix the code, and the next push will trigger a new deploy automatically.

**App deploys but crashes immediately** — the most common cause is a missing environment variable
on Render. Check that every key from your local `.env` file has been added to Render's environment
settings.

**App is slow to load or takes a long time on first visit** — on Render's free tier, apps go to
sleep after about 15 minutes of inactivity. The next visitor waits 30–60 seconds while it wakes
up. This is normal, not a bug. Render's paid plans prevent it, but the free tier is fine for
testing and learning.

**Why Render?** It's free for small apps, connects directly to GitHub, and handles the technical
side of running a server on the internet so you don't have to. It's ideal for testing and learning
— you can go from code to live app in minutes without any technical setup.

> Note: there are other hosting services (AWS, Google Cloud, Heroku, Vercel, and more) that
> developers use for larger or more complex apps. Those are outside the scope of this skill —
> Render is the right starting point, and you can always move to something else later if you
> outgrow it.

---

### Checkpoint 2 Decision Point

Once the app is live, take a moment to mark it properly before moving on:

> "Your app is live at [URL]. 🎉
>
> Let that sink in for a second. You just built and published a working web app. It has a real
> URL. Anyone in the world can open it. You wrote none of the code — you described what you wanted
> and directed the outcome. That's a genuinely impressive thing to have done.
>
> Share that link with someone. You've earned it.
>
> When you're ready — at this point you might find yourself thinking: it works, but it doesn't remember anything.
> Every session starts fresh — no history, no scores, no way for users to see how they've
> improved over time. That's exactly what happened with the Chess Trainer. The first version
> was live and working, but Alex then decided he wanted a leaderboard and a way for
> players to review their past games — to make the app more engaging and give people a reason
> to come back. That's what Checkpoint 3 adds.
>
> What would you like to do next?
> 1. **Continue** — add a database so your app can save and retrieve data (scores, history, records, etc.).
> 2. **Stop here** — your app is live and that's enough. Not every app needs a database."

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
3. Create a table — ask Claude Code to do this for you.
   > "A table is like a spreadsheet. Each row is one record (e.g. one game played),
   > each column is a piece of information (e.g. player name, score, date).
   >
   > Ask Claude Code: 'I've created a Supabase project. Can you create the database table
   > for my app and set it up in Supabase?' — give it your DATABASE_URL and it will handle
   > the rest. For the Chess Trainer, Claude Code created a table storing the player name,
   > score, opening played, move count, and full coaching report.
   >
   > Once Claude Code confirms the table is created, come back here.
   >
   > If Claude Code can't create it directly, you can do it yourself: in your Supabase
   > project go to **Table Editor** in the left sidebar → **New table**. Give it a name,
   > then add columns one by one — each needs a name and a type (`text` for words, `int8`
   > for whole numbers, `float8` for decimals, `timestamp` for dates/times)."
4. Copy the **connection string** (called DATABASE_URL) from Supabase's settings.

**If your database stops working unexpectedly** — Supabase's free tier pauses projects after
a week of inactivity. Log in to supabase.com, find your project — it will show a
**"Restore project"** button on the project card. Click it and wait about a minute for it
to restart.

**Errors containing 'does not exist' or 'relation not found'** — this usually means the name
of a table or column in the code doesn't exactly match what you created in Supabase (even a
small difference like a capital letter will cause it). Ask Claude Code: *"I'm getting a 'does
not exist' error with the database — can you check the table and column names in the code
match what I set up in Supabase?"*

### Stage 3.2 — Connect to Your App

1. Add DATABASE_URL to Render as an environment variable (same place as your API key).
   This is so the live app on Render can connect to the database when it's running.
2. Tell Claude Code to connect the database to the app — paste the same DATABASE_URL here too,
   so Claude Code can write the connection code. (Render needs it to run the app; Claude Code
   needs it to write the code that uses it — both steps are necessary.) Just say:
   > "Connect my Supabase database to the app. Here's my DATABASE_URL: [paste it]. The table
   > is called [your table name] with columns [list them]."
   Claude Code will write all the code to save and retrieve data using the table you already
   created. For the Chess Trainer, this is how the game history, leaderboard, and My Games
   features were connected — the table was already in Supabase, Claude Code wired it up.
3. Claude Code will also add `pg` (the PostgreSQL library) to your app — run `npm install`
   when prompted, just as you did in Checkpoint 1.
4. At this point, ask Claude Code what new features the database makes possible:
   > "Now that the database is connected, what features can we add?"
   For the Chess Trainer, this unlocked a leaderboard and a My Games section — features
   that weren't possible before because there was nowhere to save the data. Your database
   will open up similar possibilities for your app.
5. Push to GitHub — Render redeploys with the database connected.

**If something goes wrong:** The same applies here as with the first deploy — errors will appear
in Render's build log or in your app's behaviour. Copy any error message and paste it into Claude
Code: "I'm getting this error after connecting the database: [paste it]". Claude Code will
diagnose it and fix the code.

**Tip:** You don't need to figure any of this out alone — just ask at each step and I'll
walk you through it.

---

### Checkpoint 3 — Done

> "Your app now saves data to a database. 🎉
>
> That's a genuinely significant step. Your app can now do things a static website
> fundamentally cannot — remember users, track history, rank scores, personalise
> experiences. The database doesn't just store data; it's what makes the app feel alive.
>
> Here's what you've built:
> - A web app running live on the internet
> - Connected to a database that saves and retrieves data
> - Continues to auto-deploy whenever you push a change to GitHub
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
2. **Push to GitHub** — tell Claude Code "push my changes to GitHub" and it will handle it.
   (Behind the scenes this runs a command called `git push` — you don't need to know the
   details, but that's what's happening if you ever see it mentioned.)
3. **Live on the web** — Render auto-deploys. The update is live within a minute or two.

**Optional: test locally first.** Before pushing, you can refresh localhost:3000 to check
the change looks right on your own computer. This is useful for catching obvious problems
before they go live, but it's not required — you can push straight to GitHub and test on
the live app if you prefer.

Each cycle typically takes minutes. The Chess Trainer grew entirely this way — fixing a bug where
castling was always rejected, redesigning the coaching report into a traffic-light card, adding a
chess trivia easter egg, and building a leaderboard once the database was connected. None of it was
planned upfront; each change came from using the app and noticing what was missing. That's what
iteration looks like in practice.

If `references/iteration-examples.md` exists, read it now and share a brief summary of the five
examples with the user, so they can see the full range of what iteration can look like.

**What makes a good change description:**
The iteration examples all worked because they described the *symptom or outcome*, not the technical
solution. You don't need to know how to fix something — just describe what you're seeing or what
you want. A few principles that help:
- **Be specific.** "The button doesn't work" is harder to act on than "When I click Submit, nothing happens."
- **Describe what you expected vs what you got.** "I expected the score to appear at the end, but the page just refreshes."
- **For new features, say who does what.** "I want players to be able to type their name before starting, and see it on the coaching report at the end."
- **For redesigns, say what's wrong with it now.** "The report is too long to read quickly — I want the key points at a glance."

You never need to suggest a solution. That's Claude Code's job.

If `references/iteration-examples.md` is not present, continue without it.

---

## What next?

Your app is built and live. The skills you've picked up — describing what you want, iterating
on what exists, reading error messages, asking for help — are the same ones used to build
anything more ambitious. There's no ceiling on where this goes next.

If `references/what-next.md` exists, read it and share it with the user. It covers: what's
still within easy reach (iteration, design, sharing, custom domains), what gets significantly
more complex (auth, payments, scaling), an honest closing note, and a full costs summary table.
If the file is not present, share a brief summary of those topics from the description above.

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
