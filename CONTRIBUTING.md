# Contributing

When contributing to this repository, please first discuss the change you wish
to make via an issue.

## Pull Request Process

1. Create an issue. Outlining the fix or feature.
2. Fork the repository to your own github account and clone it locally.
3. Hack on your changes.
4. Update the docs (README.md if there's no `docs` folder) with details of api- or behaviour-changes.
5. Correctly format your commit message see "Commit Message Guidelines" below.
6. Ensure that CI passes. If it fails, fix the failures.
7. Every pull request requires a review from the maintainer.
8. If your pull request consists of more than one commit, please squash your
   commits as described in "Squash Commits"

## Commit Message Guidelines

Well formed commit messages not only help reviewers understand the nature of
the Pull Request, but also assists the release process where commit messages
are used to generate release notes.

1. The first line should:
   * contain a short description of the change (preferably 50 characters or less)
   * be entirely in lowercase with the exception of proper nouns, acronyms, and
   the words that refer to code, like function/variable names
   * be prefixed with the type of the change: (chore, fix, feat, perf, refactor, test, doc, build)

   Examples:
   * `feat: add support for large trees`
   * `fix: fix error in newest chrome version`

2. Keep the second line blank.
3. A longer description of the change (if needed)

4. If your patch fixes an open issue, you can add a reference to it at the end
   of the log. Use the `Fixes:` prefix and the number of the issue. For other
   references use `Refs:`.

   Examples:
   * `Fixes: #1337`
   * `Refs: #3615`

Sample complete commit message:

```txt
type: explain the commit in one line

The body of the commit message should be one or more paragraphs, explaining
things in more detail if this is needed.

Fixes: #1337
```

Note the `Fixes #123` tag: this references the issue raised and allows us to
ensure issues are associated and closed when a pull request is merged.

Please refer to [the Github help page on linking issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
for more information and valid keywords.


## Squash Commits

Should your pull request consist of more than one commit (perhaps due to
a change being requested during the review cycle), please perform a git squash
once a reviewer has approved your pull request.

A squash can be performed as follows. Let's say you have the following commits:

    initial commit
    second commit
    final commit

Run the command below with the number set to the total commits you wish to
squash (in our case 3 commits):

    git rebase -i HEAD~3

You default text editor will then open up and you will see the following::

    pick eb36612 initial commit
    pick 9ac8968 second commit
    pick a760569 final commit

    # Rebase eb1429f..a760569 onto eb1429f (3 commands)

We want to rebase on top of our first commit, so we change the other two commits
to `squash`:

    pick eb36612 initial commit
    squash 9ac8968 second commit
    squash a760569 final commit

After this, should you wish to update your commit message to better summarise
all of your pull request, run:

    git commit --amend

You will then need to force push (assuming your initial commit(s) were posted
to github):

    git push origin your-branch --force

Alternatively, a core member can squash your commits within Github.

## Create a release

1. Check if the CI is green for the current `main` branch.
2. Trigger the `create-release` GitHub Action through the UI with the new version.

## License

By submitting a contribution to this project, you agree to allow the project
owners to license your work as part of this project under the project's license.

## Code of Conduct

Sigstore adheres to and enforces the [Contributor Covenant](http://contributor-covenant.org/version/1/4/) Code of Conduct.
Please take a moment to read our [code of conduct](https://github.com/ckotzbauer/.github/blob/main/CODE_OF_CONDUCT.md) document.
