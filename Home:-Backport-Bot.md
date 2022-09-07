# Backport Bot

This page describes how to add the backport bot to a new repo, you will need to
be a repo admin to do this.

If you want to know why and how the backport bot works see the 
[developer guide](https://docs.sunpy.org/en/latest/dev_guide/contents/backports.html).

## Meeseeks

The backport bot we currently use is
[MeeseeksBox](https://github.com/MeeseeksBox/MeeseeksDev/).

### Preparing the Repo

Before unleasing the bot upon the repo you need to setup a few things.

1) Labels

Meeseeks uses the description field of the label to know what branch to
backport to. Therefore you should have at least one label with a description of
the form: `on-merge: backport to <branchname>`

2) CI Configuration

You should exclude backport branches from CI runs. This means that only the
"pull request" will have CI run on it rather than the branch **and** and the
pull request. For GitHub actions this looks like:

```
on:
  push:
    branches:
      - '*'
      - '!*backport*'
```

3) Add the GitHub App to the repo

You can add the bot to a new repo here:
https://github.com/organizations/sunpy/settings/installations/27933228
