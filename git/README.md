## Git workflow

### Commits

Individual commits should be atomic changes to the codebase. Specifically:

* A commit should not leave the code in a broken state waiting on a later
  commit to fix it.
* Changes that aren't related should be split into separate commits. This
  must be taken with the previous rule in mind to help determine what's
  related or not.  Bugfixes that are prerequisites to your change but not
  the main point of the change should be made in separate commits that come
  first.


### Commit Messages

Follow the [git commit message standard](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html):

* Capitalized, short (50 chars or less) summary.
* More detailed explanatory text, if necessary (in the body)
* The blank line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.
* Wrap it to about 72 characters or so.
* Always include the isssue reference in the body (e.j. #ALU-534) plus the issue title to provide context easily and link it to JIRA.
* Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.


It's a good idea to include the rationale for a change in the explanatory
text for non-trivial changes.  When in doubt, think about what would be
useful three years down the line when blaming a weird line of code.


### Make sure changes are rebased on latest master.

Ensure your code is up-to-date to prevent merge conflicts and make testing
easier.
