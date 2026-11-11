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

## Working on an issue, test first

Work directly on `main`: this repo belongs to one person, so there are no
branches or pull requests. Using issue #1 as the example:

1. **Read the issue.** Show the person the issue's title and acceptance
   criteria, and ask whether to start.
2. **Agree on the rules before any code.** Go through the acceptance
   criteria with the person. Each one must be an example that can be checked
   yes or no, with a real answer. If anything is unclear, such as how to round
   or whether a 100% discount is allowed, ask. Don't guess, and don't write any
   code in this step. When the person adds or changes a rule, update the
   issue's acceptance criteria to match (`gh issue edit 1 --body-file ...`),
   and show them the updated list. Start building only once they say the list
   is right.
3. **Test, then build, one rule at a time.** For each acceptance criterion,
   in the order the issue lists them:
   - **Red.** Write one test for it. Run all the tests and show the person
     that the new one FAILS, in plain words, e.g. "Rule 1 failed: expected
     40, got 0". Say in one sentence why it fails. Commit the test, e.g.
     `#1: test that 20% off $50 is $40.00`. Never write the code for a rule
     before its test has been seen failing.
   - **Green.** Write the smallest change that makes the test pass. Run all
     the tests, show the result, and commit, e.g. `#1: take percent off the
     price`.
   - **Tidy.** Clean up the code if needed, keeping every test passing.

   Push after each commit, and start each commit message with the issue
   number, so the history shows every test committed before its code.
   - **Tests are the person's agreement.** Never weaken, skip or delete a
     test to make it pass. If a test seems wrong, stop and ask. If the person
     agrees to change the rule, update the issue first, then the test.
   - For each test, explain in plain English what it checks.
4. **Build the page.** When every rule's test passes, build the page that
   uses the tested code. Start a web server so the person can open it (see
   "Running tests" below). Ask them to try each rule on the page by hand, and
   to try a price of their own. Passing tests aren't enough on their own: the
   hand check catches a test that checks the wrong thing.
5. **Wrap up.** Post a comment on the issue (`gh issue comment 1`) with:
   - the output of the final test run
   - the commits, in order, showing each test came before its code
   - how the person checked the page by hand (ask them rather than guessing)

   Then tick the acceptance criteria the person confirmed and close the issue.

## Running tests

Use what's already installed. Don't add a test framework or a `package.json`.

- Keep the calculation in its own file, `sale.js`, so it can be tested
  without a browser. `index.html` loads it with
  `<script src="sale.js"></script>`. End `sale.js` with
  `if (typeof module !== "undefined") module.exports = { salePrice };`
  (listing its own functions) so both the page and the tests can use it.
- Put the tests in `sale.test.js`, using Node's built-in test runner
  (`node:test` and `node:assert`). Name each test after the rule it checks,
  e.g. `test("Rule 1: 20% off $50 is $40.00", ...)`.
- Run all the tests with `node --test`.
- To show the page, run `python3 -m http.server 8000` and tell the person to
  open the forwarded port 8000 (in a codespace) or http://localhost:8000.
