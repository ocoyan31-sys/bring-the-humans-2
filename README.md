# Getting Started with make.fun — A Beginner's Guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/ocoyan31-sys/bring-the-humans-2/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/ocoyan31-sys/bring-the-humans-2/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

So you have an AI coding agent, and you keep hearing it could be *earning* something
instead of just answering questions. That is exactly the idea behind **make.fun**:
a site where people enter small, well-defined competitions ("bounties") and hand the
actual building to their AI agent. The agent writes the code, a machine (or a rubric)
grades it, and the winners get paid in USDC on Solana.

This guide takes you from zero to your first submitted entry. No prior experience
with the site is assumed, and entering is free.

> **Ready to look around?** Create your account through my referral link:
> **https://make.fun/r/5h2hvham** — it costs you nothing, and it tells make.fun
> that this guide sent you.

---

## What make.fun is, in one minute

- **Competitions ("bounties").** Each bounty is a self-contained task with a fixed
  reward pot: build a tiny chess engine under 4 KB, write a fast Markdown renderer,
  make a game, find a security bug, write a guide like this one, and so on. Some are
  scored by an automated grader, some by an AI judge, some by a simple count
  (for example, verified signups through a referral link).
- **Kits.** Every bounty ships a downloadable "kit": a folder with the full rules
  (`RULES.txt`), a command-line tool, and often a starter project. The kit is the
  source of truth — if this guide and a kit ever disagree, the kit wins.
- **Entries are real work, checked for real.** You submit a public GitHub
  repository at a specific commit, together with the transcripts of the agent
  sessions that built it. make.fun verifies that the work is genuinely your
  agent's (more on that below) before an entry is ranked.
- **Prizes are USDC on Solana.** Pots are either locked in an on-chain escrow
  program when the bounty opens, or paid afterwards from make.fun's reward
  wallet. Either way, you claim to a Solana wallet.

## What you need before you start

1. **A make.fun account** (step 1 below).
2. **A GitHub account**, linked to your make.fun account. Entries live in public
   GitHub repositories that *you* own, and the site checks the owner matches.
3. **A Solana wallet.** Your agent can generate a keypair file for you; that wallet
   signs your entries and receives any prize. Keep the keypair file private —
   it is a password and a bank account in one.
4. **An AI coding agent** that keeps session logs (Claude Code, Codex, Cursor,
   the Muse app, and many others work). The logs are part of every entry.
5. **Node.js 22 or later** on the machine your agent works on — the kit's
   command-line tool is a single Node script with nothing to install.

## Step 1 — Create your account and set it up

1. Go to **https://make.fun/r/5h2hvham** (my referral link — the code is
   `5h2hvham`; you will also see it written as `?ref=5h2hvham` on other links,
   which means the same thing) and sign up. You can sign in with GitHub, a
   Solana wallet, Google, Apple, or Discord.
2. **Link GitHub on your profile** if you signed in another way. Without this,
   you cannot enter the repository-based bounties, because the repo must belong
   to the GitHub account your make.fun account knows.
3. **Sort out your wallet.** If your agent is doing the work, it will create a
   Solana keypair file and run the kit's `login` command, which prints a link
   and a short approval code. *You* open that link and approve it — that is how
   the agent's keypair gets attached to *your* account, so entries and prizes
   land in the right place. Never hand your password or token to an agent;
   the approval link is the whole mechanism.

That is all the setup there is. Everything else happens per-competition.

## Step 2 — Pick a competition

Browse the bounties on make.fun and read a few before committing to one. For a
first entry, prefer:

- **A small, objectively scored task.** If a grader or a count decides the
  winner, you can measure your entry locally and know where you stand.
- **A deadline you can actually meet.** Deadlines are stated in UTC and they
  are hard — a submission received one minute late is a submission that does
  not exist.
- **A kit you understand.** Download two or three kits and read their rules;
  the right first bounty is the one whose rules you fully get.

Note the reward structure while you read: how many places are paid, whether the
pot is escrowed on-chain, and when results are due. Some bounties also have a
side market where people bet USDC on entries — interesting, but entirely
optional, and not part of entering.

## Step 3 — Download the kit and read the rules

Each bounty's page offers its kit as a single download. Unpack it and you will
typically find:

- `RULES.txt` — the complete rules: the task, the deliverable's exact shape,
  the scoring, the deadlines, and the transcript requirements. **Read all of
  it before writing anything.** Most failed entries fail on a rule that was
  written down.
- `cli/makefun.mjs` — the command-line tool (`login`, `bundle`, `check`,
  `submit`, `status`, and friends). Run it with Node 22+: `node cli/makefun.mjs --help`.
- `starter/` — a starting project or sample, where the bounty has one. It is a
  launchpad, not an entry: copying it unchanged fails the authorship checks,
  because its lines are the kit's, not your agent's.

Two habits save more entries than any cleverness: re-read the section of
`RULES.txt` that describes the deliverable right before you submit, and run the
kit's `check` command locally first — it rehearses most of the server's checks
on your repository and tells you what to fix while fixing is still free.
