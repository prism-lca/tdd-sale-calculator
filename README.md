# Sale Price Calculator: a test-first practice project

In this project you guide an AI coding agent (Claude Code, Codex or OpenCode)
to build a small web page, **test first**. You don't write any code. You say
what "correct" means, the agent proves it, and you check the result yourself.

## What you're building

A one-page website, `index.html`, that works out sale prices. You type in a
price and a discount, and the page shows the sale price and how much you save.

The page has two parts, and the agent writes both:

- **The screen:** the boxes you type into and the price you see. You check
  this part yourself by using it.
- **The calculation** (`sale.js`): the rules that turn a price and a discount
  into a sale price. This is the part the automated tests (`sale.test.js`)
  check, because a wrong price is the mistake that matters.

## The rules it has to follow

Each rule is an example with a real answer you can check on a phone
calculator. Each one becomes a test.

| # | Example | Correct answer | Why it's here |
| :- | :- | :- | :- |
| 1 | $50 with 20% off | $40.00 | The basic case |
| 2 | $19.99 with 15% off | $16.99 | The raw math gives $16.9915. Prices need whole cents. |
| 3 | A discount of 120% | The message "A discount can't be more than 100%" | A store can't pay you to take an item |

## What's a test?

Think of an answer key, written before anyone does the homework. You grade a
blank sheet first: it should be marked wrong, which proves the key can catch a
mistake. Then the real work is graded against the same key.

A test is that answer key, and the computer grades against it automatically.
**Red** means "wrong answer". **Green** means "matches the key". The rule:
**every rule shows red before it shows green.**

## How to do it

### 1. Make your own copy

Click **Use this template → Create a new repository** at the top of this page.

- **Owner:** choose **prism-lca**, not your own account, so your teacher can
  see your work.
- **Repository name:** `tdd-sale-calculator-<your-name>`, for example
  `tdd-sale-calculator-diana`.
- Click **Create repository**.

### 2. Open it in a codespace

In your new repo, click **Code → Codespaces → Create codespace on main**. The
agents are already installed. Start one in the terminal: `claude`, `codex` or
`opencode`.

### 3. Create your issue

In your new repo, go to **Issues → New issue → Sale Price Calculator** and
click **Create**. The rules are already filled in. It will be issue #1.

### 4. Ask the agent to start

Say to your agent:

> Let's work on issue #1, following AGENTS.md.

### 5. Follow along

1. **Agree on the rules.** The agent shows you the issue and asks questions
   before writing anything, for example "Should $16.9915 round to the nearest
   cent, or always round down?" or "Is a 100% discount allowed?" Answer them:
   these are questions about how the store works, not about code. You can add
   rules of your own too. The agent updates the issue so the list of rules
   always matches what you decided.
2. **Red, then green, for each rule.** In order, the agent:
   - writes the test and shows it **failing** (red), for example
     "Rule 1 failed: expected 40, got 0"
   - writes just enough of the calculation to make it **pass** (green), and
     re-runs all the tests
3. **The page.** When every rule is green, the agent builds the page and
   starts a web server so you can open it. Try it:
   - $50 and 20% → **$40.00**
   - $19.99 and 15% → **$16.99**
   - a discount of 120 → the error message
   - a price from a real receipt of your own
4. **Wrap up.** The agent asks how you checked the page, posts the final test
   results on the issue, and closes it.

## What to watch for

| | |
| :- | :- |
| ✅ Good | Every rule shows red before it shows green. |
| ✅ Good | Failure messages mention your numbers, like "expected 40, got 0". |
| ✅ Good | Every run re-checks all the earlier rules, not just the newest. |
| 🛑 Stop | The agent built something before showing you a failing test. |
| 🛑 Stop | The agent changed a rule or an expected answer to make it pass, without asking you. |
| 🛑 Stop | The agent says "all tests pass" but didn't show you the results. |

If you see a stop sign, say: "Stop. Go back and follow the test-first steps
in AGENTS.md."

## When you're done

Your repo keeps a record of how it went:

- **The issue** shows the rules you agreed on, and ends with a comment holding
  the final test results.
- **The commit history** (click **Commits** on your repo's main page) shows a
  separate commit for each test and each piece of code, so you can see every
  test came first.

Once you're comfortable with red and green, the team's full process adds a
written plan, a branch and a pull request. See AGENTS.md in
[prism-practice-repo](https://github.com/prism-lca/prism-practice-repo).
