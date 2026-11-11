# Agent instructions

This repo is a practice project for test-driven development (TDD). The person
you're working with may not be a programmer. They say what "correct" means in
plain English; you write the tests and the code, and prove each step. The
project is described in [README.md](README.md).

## Before you start

Check who owns this repo (`gh repo view --json owner`). If the owner isn't
`prism-lca`, tell the person: "This copy is in your personal account, so your
teacher can't see it. You may want to delete it and make a new copy with Owner
set to prism-lca." Then continue if they want to.

## Working on an issue: branch, plan, test, fix

Every issue is built on its own branch, with an approved plan committed first,
and test first: each acceptance criterion gets an automated test that is shown
failing before the code that makes it pass.

Using issue #1 as the example:

1. **Branch.** Show the person the issue's title and description and ask
   whether to start. Once they say yes, tell them you're creating
   `issue-1-branch` and why (each issue gets its own branch), then create it
   from an up-to-date `main`.
2. **Plan before any code.** Read the issue and draft `plans/issue-1-plan.md`
   from the template below. Write each acceptance criterion as an example
   that can be checked yes or no. If anything is unclear, such as how to
   round, ask the person until they agree with every criterion. Don't guess,
   and don't write any code in this step. Show the plan to the person so they
   can edit it. Commit and push it only once they approve it. It is the
   branch's first commit.
3. **Test, then build, one criterion at a time.** For each acceptance
   criterion, in the order the plan lists them:
   - **Red.** Write one test for it. Run all the tests and show the person
     that the new one FAILS, in plain words, e.g. "Rule 1 failed: expected
     40, got 0". Say in one sentence why it fails. Commit the test, e.g.
     `#1: test that 20% off $50 is $40.00`. Never write the code for a
     criterion before its test has been seen failing.
   - **Green.** Write the smallest change that makes the test pass. Run all
     the tests, show the result, and commit, e.g. `#1: take percent off the
     price`.
   - **Tidy.** Clean up the code if needed, keeping every test passing.

   Push as you go, and start each commit message with the issue number.
   - **Tests are the person's agreement.** Never weaken, skip or delete a
     test to make it pass. If a test seems wrong, stop and ask. If the person
     agrees to change it, change the plan first and commit that, then the
     test.
   - For each test, explain in plain English what it checks.
4. **Build the screen.** When every criterion's test passes, build the page
   that uses the tested code. Then ask the person to check each acceptance
   criterion by hand, following the plan's testing steps, and tick the
   criteria they confirm. Passing tests aren't enough on their own: the hand
   check catches a test that checks the wrong thing.
5. **Pull request.** Open a PR from `issue-1-branch` into `main`. The
   description must include `Fixes #1`, a link to the plan, the output of the
   final test run, and a short note on how the person checked it by hand. Ask
   them how they checked it rather than guessing. Don't merge it yourself:
   the person reviews it and merges it.
6. **Clean up.** After the merge, switch to `main`, pull, and delete the local
   branch with `git branch -d issue-1-branch`.

### Plan template

```markdown
# Plan for issue #1: <issue title>
Branch: issue-1-branch · Owner: …

## Goal
(one or two sentences: what we want, and why)

## Acceptance criteria
(from the issue: things someone can check yes or no)
- [ ] …
- [ ] …

## What will change
(a short, plain-language summary of the files that will be added or changed)

## Tests
(one automated test per acceptance criterion, in the same order, each
named in plain words; each is shown failing before its code is written)
1. …
2. …

## Testing steps
(numbered steps a person follows by hand to check each acceptance criterion)
```

Write the plan in plain language: the person and reviewers may not be
programmers.

## Running tests

Use what's already installed. Don't add a test framework or a `package.json`.

- Keep the calculation in its own file, `sale.js`, so it can be tested
  without a browser. `index.html` loads it with
  `<script src="sale.js"></script>`. End `sale.js` with
  `if (typeof module !== "undefined") module.exports = { salePrice };`
  (listing its own functions) so both the page and the tests can use it.
- Put the tests in `sale.test.js`, using Node's built-in test runner
  (`node:test` and `node:assert`). Name each test after the rule it checks,
  e.g. `test("20% off $50 is $40.00", ...)`.
- Run all the tests with `node --test`.
- The page itself is checked by hand, by opening `index.html` in a browser.
  In a codespace, run `python3 -m http.server 8000` and open the forwarded
  port.
