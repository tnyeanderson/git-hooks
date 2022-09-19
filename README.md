# githooks

This repo contains hooks that can be set up in other git repos.

## Add hooks to an existing repo

While in the root of the repo that needs hooks, add this repo as a submodule:
```bash
git submodule add https://github.com/tnyeanderson/githooks.git .githooks
```

Then set up the hooks:
```bash
./githooks/setup
```

> IMPORTANT: A note should be added to contributors in the README to run
`./githooks/setup` before committing to the repo! There is no way to
*automatically* set up git hooks for anyone who pulls and commits to a repo.
This is done for security reasons (hooks execute arbitrary scripts as a side
effect during normal `git` operations).

By default, each hook file (`pre-commit`, etc) runs each test script in its
corresponding directory (for example: `pre-commit.d`) in order. If a file
called `active-hooks` is present at the root of the hooks directory
(`.githooks`), then only the hooks defined in that file will be run. See
`active-hooks.example` for more information.

Each test script runs with the environment variable `GIT_HOOK` set to
the type of hook that is running (for example: `GIT_HOOK=pre-commit`)

## Contributing to this repo

The hooks need to be run for this repo too! Run this before committing:
```bash
git config core.hooksPath hooks
```
