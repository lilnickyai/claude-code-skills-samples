---
name: first-run-setup
description: Use this skill when setting up an AI coding agent (Claude Code or similar) for the first time, or when helping a beginner get from zero to a safe working setup. Trigger phrases: "set up my agent", "first time using Claude Code", "get started with agents", "configure my agent", "beginner setup".
---

# First-Run Setup

Take a total beginner from zero to a safe, working agent setup in about 20 minutes. Assume no prior knowledge. Explain every term the first time you use it.

## What you are setting up

An AI coding agent is a program that can read files, run commands, and make changes on your computer when you tell it to. Claude Code is one of the most popular ones. This skill gets it installed, configured safely, and proves it works with one small task.

## Step 1: Install check (5 minutes)

1. You need Node.js version 18 or newer. Check by opening a terminal and running: `node --version`
2. If that prints a version number, skip to step 3. If it says "command not found", install Node.js from nodejs.org (download the LTS version, run the installer, restart the terminal).
3. Install Claude Code: `npm install -g @anthropic-ai/claude-code`
4. Start it: `cd` into any folder, then run `claude`
5. Log in with your Anthropic account when prompted.

If any step fails, stop and read the error message out loud to the user in plain language before trying fixes. Do not guess.

## Step 2: Use a practice folder first (2 minutes)

Never point the agent at important files on day one.

1. Make a new folder called `agent-practice` somewhere easy to find.
2. `cd` into it and run `claude` there.
3. Everything the agent does in this session stays inside that folder.

Tell the user: "This is your sandbox. Break things here, not in your real projects."

## Step 3: Write a starter CLAUDE.md (5 minutes)

CLAUDE.md is a file the agent reads automatically every session. Think of it as the agent's permanent instructions about you and your setup.

Create `CLAUDE.md` in the practice folder with this content, filled in for the user:

```markdown
# About me
- Name: [their name]
- Skill level: beginner, explain what you are doing as you go

# Rules
- Always show me what you are about to change before you change it.
- Never delete files. Ask me first, every time.
- Never send emails, messages, or post anything online without my explicit approval for that specific send.
- If you are unsure about something, stop and ask instead of guessing.
- Keep explanations short and plain. No jargon without defining it.
```

Read it back to the user and confirm each rule makes sense to them.

## Step 4: Set safe permissions (3 minutes)

Permissions control what the agent is allowed to do without asking.

1. Keep the default "ask before running commands" setting ON. Do not turn on auto-approve. Ever, for a beginner.
2. Explain the tradeoff in one sentence: "Asking slows things down a little, but it is the one thing standing between you and the agent deleting the wrong folder."

## Step 5: Run one safe first task (5 minutes)

Pick exactly one of these. Do not combine them.

- "Explain what is in this folder in plain language."
- "Create a README.md file that describes this practice project."
- "Write a tiny hello-world script and explain each line."

After it finishes, walk the user through what happened: what the agent did, what it asked permission for, and where to see the result. This builds the mental model everything else depends on.

## What NOT to do on day one

- Do not connect it to email, messaging apps, or social accounts.
- Do not point it at a real project with real data.
- Do not turn on auto-approve for anything.
- Do not run it and walk away. Watch the first five sessions.

## Troubleshooting the common first errors

- "command not found: claude" means the npm install did not finish or the terminal needs a restart. Re-run the install, restart the terminal.
- "login failed" usually means the browser window for auth was blocked. Allow popups for the auth page and try again.
- The agent doing nothing after a prompt usually means the prompt was too vague. Rewrite it as one specific action with a checkable result, for example "list every file in this folder" instead of "look around".

## When this skill is done

The user has: Claude Code installed and logged in, a practice folder, a CLAUDE.md with safety rules, permissions set to ask-first, and one completed safe task they understand. Point them at the `safe-mode-guardrails` skill next if they want the full safety lockdown before touching real projects.
