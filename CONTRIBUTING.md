# Contributing to Kode's repositories

This file applies to every public repository of Kode that has no `CONTRIBUTING.md` of its own. Read it before you open a pull request.

## Before you write code

**Open an issue first.** Say what is wrong or what is missing, and on which board and which version. A fix for a typo does not need an issue. Anything bigger does: a maintainer may already work on it, or may know why it is the way it is.

One issue is one problem. Two problems are two issues.

## Branches

The repositories work with git flow:

- `main` holds the releases. Every merge into it is a version, with its tag.
- `develop` holds the next version. Pull requests go here.
- `release/x.y.z` starts from `develop` while a version is prepared, and takes only fixes. It ends in `main`, with the tag, and goes back into `develop`.
- `hotfix/x.y.z` starts from `main` to fix a release. It ends in `main`, with a new tag, and goes back into `develop`.

A pull request into `develop` is merged as one commit, titled with the pull request's title, so give the title the commit format below. `main` takes merge commits only, and a check refuses a pull request into it from any branch but `release/…` or `hotfix/…`. When a release or a hotfix reaches `main`, a workflow opens the pull request that takes it back into `develop`.

## Your pull request

- **From `develop`, into `develop`.** Start your branch from `develop` and open the pull request against it. `main` takes only the release and hotfix branches.
- **One change per pull request.** A fix and a clean-up are two pull requests.
- **A branch named for the change:** `fix/…`, `feat/…`, `docs/…`, `refactor/…`, `test/…`, `ci/…` or `chore/…`, then a few words, for example `fix/sd-card-detect`. In kode-apps an app's branch is `app/<name>`.
- **Commit subjects in the Conventional Commits format:** `type(scope): Summary`. The type is one of the words above. The scope is the component you touched, in lower case (`kdrv`, `kaos`, `kgui`…). The summary is in the imperative, starts with a capital letter, has no final period, and the whole subject fits in 72 characters:

  ```
  fix(kdrv): Read the card-detect line after the pull-up settles
  ```

- **A body that says why**, in a few short sentences, after a blank line. The diff already says what. If the commit closes an issue, end the body with `Closes #N`.
- **Everything in English:** code, comments, commit messages and documentation.

## The checks

Run the repository's own checks before you push, and say in the pull request that they pass. The README of each repository lists them under *Take part*:

| Repository | Checks |
|---|---|
| KodeOS | `tools/host_tests.sh`, `tools/check_layers.sh`, `tools/tool_tests.sh` |
| kode-sdk | `tools/host_tests.sh`, `tools/check_layers.sh` |
| kode_slave_c5 | `test/run.sh` |
| kode-app-template | `idf.py build` |
| kode-apps | `tools/run_tests.sh` |

A change that a person can see on the screen needs a screenshot of each screen it touches. A change to a driver needs a test on a Kode Dot: say which board and what you ran.

No checks run on GitHub: Kode keeps GitHub Actions off, so your own run of the checks is the one that counts, and the reviewer runs them again. When `develop` moves, press **Update branch** and run them once more.

## The code

The C code follows the style of the SDK:

- MISRA C, with a Doxygen comment (`@brief`, `@param`, `@return`) on every public function.
- No magic numbers: a number that means something is a named `#define` with a one-line comment.
- No ternary operator (`a ? b : c`): write the `if`.
- The constant on the left of a comparison, and braces on their own lines.
- One owner for each device. Other code asks the owner with an event and never calls the driver. The SDK's README explains why.

## Review

A maintainer of Kode reviews every pull request. The branches `main` and `develop` are protected: a pull request needs one approval before it is merged. A new push after an approval asks for the review again.

## Licence

You keep the copyright of what you write. By opening a pull request you agree that your contribution is under the licence of the part it changes, as the repository's `NOTICE.md` gives it:

| Where | Licence of your contribution |
|---|---|
| kode-sdk, KodeOS, kode-app-template | GNU General Public License, version 3 or later, **with the additional permission under section 7** that the repository's `NOTICE.md` gives for RFAL |
| kode-apps | GNU General Public License, version 3 or later |
| kode_slave_c5 | Apache License, version 2.0 |
| the drawings and animations of Kody | Creative Commons Attribution-ShareAlike 4.0 |

The additional permission matters: kodeOS links RFAL, the NFC library of STMicroelectronics, which is not under the GPL. Without that permission on your code, nobody could distribute a kodeOS that holds it. A pull request that does not accept it cannot be merged.

Submit only what you have the right to submit. Code copied from another project keeps its owner and its licence: say where it comes from in the pull request, and in a comment in the file.

Your contribution does not give you rights to the names Kode, Kode Dot, kodeOS and Kody: [TRADEMARKS.md](TRADEMARKS.md) says how you can use them.

## Conduct

Everyone who takes part follows the [code of conduct](CODE_OF_CONDUCT.md).
