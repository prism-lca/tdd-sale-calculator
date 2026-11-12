# Sale Price Calculator: a test-first practice project

In this project you guide an AI coding agent (Claude Code, Codex or OpenCode)
to build a small web page, **test first**. You don't write any code. You say
what "correct" means, the agent proves it, and you check the result yourself.

## Follow the activity page

**https://prism-lca.github.io/tdd-sale-calculator/**

It explains how test-first work goes, shows the finished calculator working,
walks you through every step, and has the rules to copy and paste to your
agent.

## The short version

1. Click **Use this template → Create a new repository** at the top of this
   page. Set **Owner** to **prism-lca** (not your own account) and name it
   `tdd-sale-calculator-<your-name>`, for example
   `tdd-sale-calculator-diana`.
2. In your new repo, click **Code → Codespaces → Create codespace on main**.
   The agents are already installed. Start one in the terminal: `claude`,
   `codex` or `opencode`.
3. Copy the rules message from the activity page and paste it to your agent.
4. Agree on the rules, then watch each rule's test go **red** (failing)
   before it goes **green** (passing).
5. When every rule is green, the agent builds the page and you try it
   yourself.

## When you're done

Your repo's commit history (click **Commits** on your repo's main page) shows
a separate commit for each test and each piece of code, so you can see every
test came first. The tests in `sale.test.js` are named after your rules.

Once you're comfortable with red and green, the team's full process adds an
issue, a written plan, a branch and a pull request. See AGENTS.md in
[prism-practice-repo](https://github.com/prism-lca/prism-practice-repo).
