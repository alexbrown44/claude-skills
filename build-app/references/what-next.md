# What next?

You've now covered everything this skill teaches. But the app is yours, and there's plenty
more you can do with it. Here's an honest picture of what's still within easy reach — and
what starts to get more complex:

**Still very much within reach:**
- Keep iterating — new features, redesigns, bug fixes. The loop you've already learned works
  for all of it. Claude Code remains your partner here.
- Add more database tables — if your app grows and needs to save new types of data, the same
  Supabase process applies.
- Improve the design — describe what you want to look different and Claude Code will update it.
- **Share it and get feedback** — send the URL to people and ask them specific questions:
  *"What confused you? What would you add? What felt missing?"* Vague feedback ("looks good")
  is hard to act on; specific feedback ("I didn't know where to start") gives you something
  to fix. The Chess Trainer improved most through real users noticing things the builder
  had stopped seeing.
- **Get a custom domain** — your Render URL (something like `chess-trainer-8tp1.onrender.com`)
  works perfectly, but you can replace it with your own address like `alexchesscoach.co.uk`.
  You buy a domain name from a registrar (Namecheap, GoDaddy, and Google Domains are common
  options — typically $10–$20 per year; prices vary by region), then point it at your Render
  app in a few steps. Render has a straightforward guide for this, and Claude Code can walk
  you through it.

**Possible but significantly more complex:**
- **User accounts and login** — letting people sign in with a username and password involves
  authentication, session management, and security considerations. Doable with Claude Code,
  but it's a bigger step.
- **Taking payments** — integrating something like Stripe requires understanding payment flows
  and security requirements. Claude Code can help, but you'll want to research what's involved
  before starting.
- **Scaling up** — if your app gets a lot of users, Render's free tier will hit its limits.
  Moving to a paid plan or a different hosting provider (AWS, Google Cloud) is possible but
  involves more configuration.

**The honest truth:** you don't need to figure out what's next right now. The most valuable
thing is to keep using what you've built, notice what's missing, and ask for it. That's how
the Chess Trainer grew — not from a grand plan, but from using it and improving it one step
at a time.

**Costs to be aware of:**

Everything in this skill uses free tiers — but each has limits worth knowing about:

| Service | Free tier | When costs start |
|---|---|---|
| **Render** | Free, but app sleeps after 15 min inactivity | ~$7/month for a plan that stays awake |
| **Supabase** | Free up to 500MB storage and 50,000 rows | Paid plans from $25/month |
| **Anthropic API** | No free tier — pay per use from the start | Fractions of a penny per call; monitor at console.anthropic.com |
| **Domain name** | N/A | ~$10–$20/year from a registrar (optional; prices vary by region) |

The API cost is the one to watch. If your app uses Claude for every user interaction and gets
shared widely, those fractions of a penny add up. A rough guide: 1,000 users each making 10
requests is 10,000 API calls — likely a few pounds/dollars at most, but worth checking your
usage in the Anthropic console if you start sharing the app publicly. You can also set a
spending limit in your Anthropic account settings so there are no surprises.
