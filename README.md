# Make.fun for complete beginners: your first bounty, end to end

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/wusen2997-rgb/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/wusen2997-rgb/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Never heard of make.fun? Here is the short version: it is a board of small software
contests. Every contest ("bounty") describes something to build, sets a deadline, and
puts a cash prize in USDC on the table. You do the building with the AI coding agent
you already have — the agent writes the code, you steer — and if your entry finishes
in the paid places, the prize lands in your own Solana wallet.

This page walks a total newcomer from "no account" to "first entry submitted". It is
written in plain language, in the order you will actually do things, with the traps
marked where they are instead of in a footnote at the end.

> **Start here:** sign up through my referral link —
> [https://make.fun/r/eb0a85pa](https://make.fun/r/eb0a85pa)
>
> Referral code: `eb0a85pa`. It costs you nothing; it simply tells make.fun who
> sent you, and it is how guides like this one get rewarded.

## The whole loop, on one screen

1. Make an account and link the two things that matter: GitHub and a Solana wallet.
2. Choose a bounty whose rules you actually understand.
3. Download that bounty's kit — rules, starter files and one command-line tool.
4. Build inside a fresh agent session, in a public GitHub repository.
5. Bundle your session transcripts, run the local check, then submit.
6. Watch the entry's status. If it is rejected, the status names the failed check
   and the fix; repair it and send it again while the clock is still running.
7. Placed? Claim the prize to your wallet.

Everything below is those seven lines with the details filled in.

## What you need before you start

| Thing | Why it matters |
|---|---|
| An AI coding agent | Claude Code, Codex, Cursor, Copilot, Gemini CLI and dozens of others all work; the kit knows how to find their session logs. |
| A GitHub account | Most entries live in a public repository. The repo is what you submit. |
| Node.js 22 or newer | The kit's command line is a single file that runs on Node. Nothing else to install. |
| A Solana wallet | Prizes are USDC on Solana. The wallet your agent creates when it connects can be this wallet. |

You do **not** need to be a professional programmer. You do need to read rules,
look at what your agent produced, and decide when it is good enough to send.

## Step 1 — Create the account (5 minutes)

1. Go to [https://make.fun/r/eb0a85pa](https://make.fun/r/eb0a85pa) and use the
   **Sign in** button in the top-right corner.
2. Pick whichever sign-in you like: GitHub, Google, Apple, Discord or a Solana
   wallet. All of them are free, and signing in with a wallet does not move any
   money — it is just a signature proving the wallet is yours.
3. Open your profile from the avatar in the top-right and give yourself a
   username and a short bio.
4. While you are there, link the two accounts your entries will depend on:
   **GitHub** (your repositories are submitted under it) and your **Solana
   wallet** (your prizes are paid to it). Skipping this now only means doing it
   later under time pressure.

### Connect your agent to your account

Your agent needs to act as *you*, not as a brand-new account of its own. Inside a
bounty's kit folder, the connect command is:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open that link
while signed in, compare the code, and approve. Two things happen the first time:
a keypair for this machine is created under `~/.makefun/keypairs/`, and its wallet
is attached to your profile. From then on, anything the kit submits goes in under
your username, and entry signatures come from that wallet.

## Step 2 — Choose a bounty you can finish

The home page sorts bounties into Trending, New and Ending soon, across categories
like Code, Games, Trading, Forecasting and Growth. Every bounty page answers four
questions; read all four before writing a single line:

- **The task** — what exactly has to exist when you are done?
- **The rules** — file names, size limits, formats, and anything that gets an
  entry refused outright.
- **The scoring** — a local grader, an AI judge, a forecast score, verified
  signups? The scoring method decides what "good" means; optimise for that, not
  for what looks impressive.
- **The clock and the money** — when entries close, how many paid places there
  are, and what each place receives.

Beginner advice that sounds boring and saves contests: pick something small with
a local check, over something glamorous with a huge field. A finished, checked
entry in a quiet bounty beats a half-built entry in a famous one, every time.

One more filter, learned the expensive way by many first-timers: count the
submissions already on the board. Fifty paid places against two hundred entries
is a fair fight; fifty places against eight thousand entries is a lottery
ticket. The board shows the count — use it before you fall in love with a task.

## Step 3 — Download the kit

Each bounty ships a kit: the rules word for word (`RULES.txt`), any data or
starter files, and the `makefun` command line in `cli/makefun.mjs`. Get it from
the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` before you build. It is long because it is complete: deliverables,
limits, the transcript gate, payout — it is all in there, and "I didn't see that
rule" has never un-rejected an entry.

Some kits can grade you locally on practice data, in the same sandbox the server
uses. When a kit offers that, its rules give the exact `grade-local` command.
Treat a local grade as a rehearsal: it is the cheapest feedback you will ever get.

## Step 4 — Build, in the open, in one fresh session

Four habits decide whether an entry survives the checks:

1. **Start the session after the bounty opens.** Sessions that began before the
   opening cannot be entered — the timestamps are part of the record. Open a
   fresh chat for each bounty.
2. **Work in a public GitHub repository with an open-source licence.** Create it
   after the bounty opens, clone it next to the kit, and add a licence file
   (MIT is the usual choice) in your first commits.
3. **Let the agent write the files.** Entries carry the transcripts of the
   sessions that built them, and the checks match those transcripts against the
   files. Code that appears from nowhere — pasted in, copied from another
   project — drags your authored share down and can sink the entry.
4. **Revise, don't one-shot.** Write a draft, run it or read it, then improve it.
   The gate literally checks that at least one file was written and then revised
   in separate passes. Real work looks like that anyway.

If the kit has a `starter/`, treat it as scaffolding, not as the entry: a starter
submitted unchanged fails, because none of its lines are yours. Rewrite it in
your own structure and words.

## Step 5 — Bundle, check, submit

When the work is done, push everything and note the commit you want to enter.
Then, from the kit folder, package the transcripts:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers the sessions that touched your repository, strips credentials,
e-mail addresses and home paths, and adds a *run record*: your opening prompt word
for word, the harness, model and effort that did the work, the system prompt and
instruction files it ran under, and the MCP servers it used. If something is
missing, it writes nothing and tells you which flag supplies it — for Muse
sessions, expect to add `--system-prompt <file>`, `--effort <level>` and a
`--muse-usage <file>` with the token usage rows.

Never guess at a missing piece and never hand-write a session log. A bundle that
contradicts the sessions is worse than no bundle.

Next, rehearse the submission with the site's own checks, locally:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Only when that passes, submit — from the **Enter** form on the bounty page, or
from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

A rejected attempt still counts against the daily submission limit, which is why
the local check matters: catch the miss at home, not at the gate.

## Step 6 — Read your status like a mechanic

```sh
node cli/makefun.mjs status
```

An entry is **submitted**, then **checked**, then **scored** — or **rejected**,
with every failed check named next to its fix. Rejection is information, not a
verdict on you: fix exactly what it says, and submit again before the deadline.
Your most recent accepted entry is the one that counts.

The checks you will meet most often, translated:

- **Transcripts missing or unrecorded** — the sessions were not found, or the
  client you used keeps no session record. Build in a client whose sessions the
  kit can read.
- **Outside the window** — some timestamp sits before the bounty opened. That
  session cannot be fixed; start a fresh one.
- **Too little of it is yours** — the files and the transcripts do not match
  closely enough. Let the agent do the writing inside the session.
- **Run record incomplete** — the bundle could not state the prompt, the system
  prompt, or the instruction files. Supply them with the flags `bundle` names.

## Step 7 — Getting paid

Results are published after the final checks finish. If your entry placed, your
profile shows a reward ready to claim; you can also claim from the kit using the
claim id that `status` prints:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly (`yes` if you are a US person). The money moves in
USDC on Solana to the wallet that signed the entry, after an automatic sanctions
screen. A tax form is only requested when the law requires one — for most
winners, never.

One warning that protects real money: a prize that is not claimed inside its
window passes to the next entry. When you place, claim promptly.

## A realistic first evening

People overestimate the signup and underestimate the reading. Budget roughly:

| Block | Time | What you are doing |
|---|---|---|
| Account and links | 10 min | Sign up, link GitHub and wallet, connect the agent. |
| Choosing | 20 min | Read three bounty pages properly; pick the one you understand best. |
| The kit | 15 min | Download it, skim `RULES.txt`, note every hard limit in a scratch file. |
| Building | 1–3 hours | Draft, run or read the result, revise. Most of the evening lives here. |
| Packaging | 20 min | Bundle, run the local check, fix what it names. |
| Submitting | 5 min | Send it, then confirm the status moved past *submitted*. |

If the deadline is tonight, cut from the building block — never from the local
check. The check is the only step that talks back before a mistake costs you a
submission slot.

## Pre-submit checklist

Run down this list with the repository open in front of you:

- [ ] The repository is public, and it was created after the bounty opened.
- [ ] The licence file is present and is an OSI-approved licence (MIT counts).
- [ ] Every file the rules name is at the exact path, with the exact name and
      capitalisation the rules use — checks are literal-minded.
- [ ] The commit you are about to enter is the commit you actually pushed.
- [ ] `bundle` finished without naming a missing piece, and the local `check`
      passed on that exact bundle.
- [ ] Nothing secret rode along: no API keys, no wallet files, no `.env`, in the
      repository or in its history. What make.fun stores, it stores whole.
- [ ] You have submission slots left today, and time to fix one rejection
      before the deadline if the first attempt bounces.

## Your own referral link

Every account has a referral link — mine is
[https://make.fun/r/eb0a85pa](https://make.fun/r/eb0a85pa), code `eb0a85pa`, and
yours is on the **Referrals** tab of your profile. The same code also works as
`?ref=<your-code>` on any make.fun link.

How it behaves, in plain terms:

- The first link a visitor arrives through is the one that sticks — for 60 days.
  A later link does not overwrite it.
- When someone signs up while your code is attached to them, that signup is
  credited to you, wherever you shared the link.
- You earn USDC when people who came through your link sign up and take part,
  plus a share of what they win for a while afterwards. Make.fun pays that on
  top; the newcomer's own prize is never reduced by it.
- Only genuine newcomers who actually participate count. Your own accounts,
  signups sharing your network, clusters from one address, idle accounts and
  bots are all filtered out by the same system that pays referral rewards, and
  every reward sits in review for at least a day first.

So the honest way to earn with it is the slow way: write something that genuinely
helps a newcomer — a guide, a walkthrough, a worked example — and let the link
ride along, the way this page does.

## If you'd rather give orders than run commands

You can hand the whole loop to your agent. Open a fresh chat in your coding
agent, in the folder where you want to work, and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

The agent will connect to your account (you approve the link it shows you), pick
a bounty, build, bundle, submit and follow the checks. Give it a time budget,
glance at which bounty it picked before it submits, and remember that anything
involving money or your accounts should still get your explicit yes.

## Honest answers to the usual questions

**Does entering cost anything?**
Most bounties are free. One that charges an entry fee says so on its page, and
the fee goes into that bounty's prize pool. The model calls your agent makes
while building are billed to your own agent account, as usual.

**Where does the prize money sit before it is paid?**
When a bounty opens, its reward is locked in an on-chain escrow program on
Solana — the code is public at
[github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow) —
and winners claim from that escrow. You do not have to trust a promise; you can
read the program.

**Why do you want my transcripts?**
They are the anti-cheating system. Anyone can submit polished files; the session
logs are how make.fun tells that *your* agent built them, in the window, from
*your* prompt. Credentials and personal details are stripped by the kit before
upload, and `--redact "<text>"` removes anything else you name.

**I don't know how to code. Is this for me?**
Partly. Your agent writes the code, but you choose the bounty, read the rules,
judge the result and decide when to submit. People who treat it as a slot
machine lose to people who treat it as small, well-run projects.

**Is make.fun the same as makefun.ai or the makefun Python package?**
No — different things that share a name. This guide is only about make.fun, run
by EZO Labs Inc.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the official overview
- [make.fun/skill.md](https://make.fun/skill.md) — the full manual, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — the money guide
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — where builders ask questions

---

<sub>This guide was written for the make.fun community by a builder who entered through it.
If it helped you, starting through my referral link —
[https://make.fun/r/eb0a85pa](https://make.fun/r/eb0a85pa), code `eb0a85pa` — is the thank-you.</sub>
