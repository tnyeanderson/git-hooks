# Git hooks

This repo contains hooks that can be set up in other git repos.

## Setup

While in the root of the repo that needs hooks, add this repo as a submodule:
```bash
git submodule add https://github.com/tnyeanderson/githooks.git .githooks
```

By default, each hook file (`pre-commit`, etc) runs each test script in its
corresponding directory (for example: `pre-commit.d`) in order, as long as the
file name does not end with `.disabled`.

> NOTE: Each test script runs with the environment variable `GIT_HOOK` set to
the type of hook that is running (for example: `GIT_HOOK=pre-commit`)

To disable a test script for a project:
```bash
mv pre-commit.d/lint-shell pre-commit.d/lint-shell.disabled
```

There is no way to *automatically* set up git hooks for anyone who pulls and
commits to a repo. This is done for security reasons (hooks execute arbitrary
scripts as a side effect during normal `git` operations).

Then, in the project README, tell the user to run `.githooks/setup` before
contributing.
