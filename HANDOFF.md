# Handoff notes (temporary, delete before students start)

Notes from a Claude Code session (Nov 2026) that set up this repo, so another
agent can pick up the work. This file is not part of the student activity.
If you are an agent helping a student, ignore this file and follow AGENTS.md.

## The goal

Teach non-programmer students test-driven development (TDD) with AI coding
agents (Claude Code, Codex, OpenCode). The student says what "correct" means;
the agent writes a test, shows it failing (red), then writes the code that
makes it pass (green), one rule at a time. The student checks the result by
hand. The practice project is a one-page Sale Price Calculator.

## Where things are

| What | Where |
| :- | :- |
| This template repo (public, marked as a template) | https://github.com/prism-lca/tdd-sale-calculator |
| The activity page students follow (GitHub Pages, from `/docs` on `main`) | https://prism-lca.github.io/tdd-sale-calculator/ |
| A shared claude.ai copy of the same page (doesn't auto-update) | https://claude.ai/artifact/EXDEVoKW6hAhFGg743L1VZ |
| The team's full process (issue → branch → plan → test-first → PR) | https://github.com/prism-lca/prism-practice-repo |
| A finished example (Diana's, built with the full process) | prism-practice-repo: `test-driven-development-example/diana/` and `plans/issue-59-plan.md` (issue #59, PR #60) |

## How the activity works now

1. The student opens the activity page.
2. They click **Use this template**, set Owner to **prism-lca**, and name it
   `tdd-sale-calculator-<name>`.
3. They open a codespace and start `claude`, `codex` or `opencode`.
4. They copy the rules message from the activity page and paste it to the
   agent:

   ```
   Let's build the Sale Price Calculator, following AGENTS.md. Here are the rules:
   1. $50 with 20% off → $40.00
   2. $19.99 with 15% off → $16.99 (rounded to the nearest cent)
   3. A discount over 100% → no price, and the message "A discount can't be more than 100%"
   ```
5. `AGENTS.md` drives the agent through these steps:
   1. Check the repo owner is prism-lca, and warn if not.
   2. Read the rules back.
   3. Agree on the rules with the student, with no code yet.
   4. Red/green/tidy for each rule. Commit the test, then the code, and push
      after each commit.
   5. Build `index.html` and serve it with `python3 -m http.server 8000`.
   6. Wrap up in the chat with the final test output, `git log` and how the
      student checked the page by hand.
6. The code is `sale.js` (with the
   `if (typeof module !== "undefined") module.exports = {...}` guard),
   `sale.test.js` (Node's built-in `node:test`, run with `node --test`) and
   `index.html`.

## Decisions the user made (keep these)

- **Rules live only on the activity page.** They are not in the repo, not in
  a RULES.md, and not in an issue. Students paste them to the agent, and the
  tests are the record of the rules.
- **Work directly on `main`.** There are no issues, branches, plan files or
  pull requests. The full process stays in prism-practice-repo.
- **One web page.** It holds both "how it works" and the directions.
  `docs/example.html` just redirects to it.
- **A non-LCA, non-Python example.** It's a web page with a visible UI.
- **Three rules only.** No second discount, and no "break the code on
  purpose" step.
- **The rules table has three columns:** #, Example and Correct answer.
  There's no "Why it's here" column.
- **Students' copies go in the prism-lca org.** Members can create repos
  there and the default permission is write. Copies have no branch
  protection, so students can push to `main`.
- **Leave prism-practice-repo's `main` protection as it is.** Pushes are
  restricted to catiehe and the maintainers team, and that applies to admins
  too. It was briefly removed by mistake and then restored.

## Environment

- The devcontainer uses `ghcr.io/prism-lca/prism-devcontainer:latest`, which
  is public. It includes Claude Code, Codex, OpenCode, Node 24, Python 3 and
  gh. Port 8000 is forwarded.
- Students must sign in to their agent on first use.

## Editing the activity page

`docs/index.html` is the source. Edit it directly and push to `main`, and
GitHub Pages rebuilds within a minute or two. The claude.ai copy (link above)
is a separate snapshot. If you update it, republish it with the Artifact tool
using that URL, or let it go stale.

Watch out: the page uses `.step-num` for the circled step numbers and
`td.num` for the table answer column. Don't reuse `.num` for the circles; that
caused circles to appear around the table answers.

## Open items / ideas

- Nobody has run the full student flow from a fresh copy of this template
  yet. Do one end-to-end test in a codespace before giving it to students.
- Delete this HANDOFF.md before students start, because copies of the
  template get every file in the repo.
- prism-practice-repo's `docs/sale-price-calculator.md` points to this
  template. Check that it still describes things correctly.
