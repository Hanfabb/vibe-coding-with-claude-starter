# Vibe Coding with Claude — Starter

Welcome. In this 2-hour session you'll build a small, real, working thing with Claude, and you'll do the building yourself. No experience needed, nothing to install. Everything runs in your browser.

## 1. Open your workspace

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/Im-Hal-9K/vibe-coding-with-claude-starter?quickstart=1)

Click the **Open in GitHub Codespaces** button above (sign in with a free GitHub account if asked). Wait a minute while your workspace builds. A full code editor opens right in your browser, with nothing installed on your own computer.

## 2. Connect to Claude (takes 20 seconds)

Once the editor has finished opening:

1. **Open a terminal:** top menu **Terminal → New Terminal** (or press `` Ctrl+` ``). A panel opens at the bottom, that's where you type commands.
2. **Give Claude the class key.** Type the line below, replacing `PASTE-CLASS-KEY-HERE` with the **key your instructor shows on screen**, then press Enter:
   ```bash
   export ANTHROPIC_API_KEY=PASTE-CLASS-KEY-HERE
   ```
   Nothing visible happens, and that's correct. *(What it does: `export` saves a value for this terminal session; `ANTHROPIC_API_KEY` is the name Claude looks for. You just handed Claude the temporary key it needs.)*
3. **Start Claude.** Type:
   ```bash
   claude
   ```
4. The first time, Claude asks **"Do you want to use this API key?"** Choose **Yes**. (It defaults to *No*, so don't just press Enter.)

You're connected. If you ever close the terminal and open a new one, run the `export` line again.

## 3. Build something

Tell Claude, in plain English, what you want to build. Use a starter idea from [`PROMPTS.md`](PROMPTS.md) or bring your own.

Then run it, look at it, and ask Claude to change something. That loop, **describe → look → refine**, is the whole skill. When your project runs, a **preview opens automatically** in a side tab. Your page replaces `index.html`.

## A few commands worth knowing

You only need a couple. And remember, you can always ask Claude itself, "what does this command do?"

| You type | What it does |
| --- | --- |
| `claude` | Starts Claude in the terminal. |
| `export ANTHROPIC_API_KEY=…` | Gives Claude your class key for this session. |
| `serve .` | Serves your page in the live preview (Claude will usually do this for you). |
| `Ctrl + C` | Stops whatever is currently running in the terminal. |

## What you'll do today

- Meet Claude and see how plain-language requests become working software.
- Build one small thing you'd actually use (a page, a calculator, a tracker, flashcards, a countdown, see `PROMPTS.md`).
- Make it better, fix what breaks, and learn how to keep going on your own.

## If something goes wrong

Tell your instructor. You cannot break anything, and there are no dumb questions. If Codespaces misbehaves, your instructor will point you to claude.ai with Artifacts as a backup.

## Keeping going after class

The key you typed in class is a **temporary class key**. It gets switched off after the session, on purpose. So when you come back later and try to run Claude, it will stop working. That is expected. Nothing is broken and you did not do anything wrong.

To keep building on your own, you need two small changes: your own way of signing in to Claude, and one line removed from this project that was only there for the classroom.

### Step 1: remove the classroom setting

During class, this project quietly pointed Claude at a class server so everyone could share one key. On your own, you need Claude to go straight to Anthropic instead.

1. In your Codespace, open the file `.devcontainer/devcontainer.json`.
2. Find the line that starts with `"ANTHROPIC_BASE_URL"`. Delete that whole line.
3. Rebuild your workspace: press `F1`, type **Rebuild Container**, and pick it. Wait a minute for it to finish.

*(What that line did: it told Claude "send everything through the classroom server." Once it is gone, Claude talks to Anthropic directly, using your own sign-in.)*

If you skip this step, Claude will keep trying the classroom server no matter what key you give it, and it will keep failing. This is the part people get stuck on.

### Step 2: sign in as yourself

Pick whichever fits you. **Option A is the simpler one and has no surprise costs.**

**Option A: use a Claude account (recommended)**

If you have a paid Claude plan, or you get one, Claude can just log you in through your browser.

Open a terminal and type:

```bash
unset ANTHROPIC_API_KEY ANTHROPIC_BASE_URL ANTHROPIC_MODEL
claude
```

Claude will open a browser window and ask you to sign in. Do that once, and you are set.

*(What `unset` does: it clears out the leftover classroom settings for this terminal, so they cannot get in the way.)*

**Option B: use your own API key**

This is pay-as-you-go. You add a payment method and you are charged for what you use, usually cents for small projects, but it is metered, so know that going in.

1. Go to **console.anthropic.com**, make an account, and add a payment method.
2. Create an API key and copy it.
3. In your terminal:

```bash
unset ANTHROPIC_BASE_URL
export ANTHROPIC_API_KEY=paste-your-own-key-here
claude
```

### One thing to remember

The `unset` and `export` lines only last for that one terminal. Close it, open a new one, and they are gone. That is why Step 1 matters: editing the file makes the fix permanent, so you are not retyping commands every time.

If you get stuck, ask Claude itself. "I finished a class and now my key does not work, help me set up my own" is a perfectly good thing to type.

---

*Instructor note: the class key is shown on screen during class, never stored in this repo. The `.devcontainer/` pre-installs the Claude tooling, routes it through the spend-capped class proxy, and pre-answers Claude's setup prompts so students land ready.*
