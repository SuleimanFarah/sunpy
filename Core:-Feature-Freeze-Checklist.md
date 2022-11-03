So it's that time again when it's time to feature freeze and create a new release branch, this checklist is a list of things to do as part of that process. When the checklist is finished you should be able to tag an rc from the newly created release branch.

## Before branching

The following steps are to be taken on the main branch (via PR) prior to branching:

1. Update the `.mailmap` and `.zenodo.json` files. These are metadata files about the authorship of the code.
    1. The `.mailmap` file needs updating manually, to remove any duplicates and where possible to add peoples real names. The best way to do this is to first run `git shortlog -es vX.Ydev..HEAD` where `vX.Y` is the previous release number. Look down this list and check for duplicates and people without real names. Edit the `.mailmap` file until all these are fixed.
    2. Next run the `tools/update_zenodo.py` file, this script uses the output of `git shortlog` to update the `.zenodo.json` file. Check the printed output of the script and the diff for sanity.
1. Update the vendored modules in `/sunpy/extern/` if they need updating, these should be copied from their latest releases on GitHub.
1. Update the stored `sunpy/net/vso/data/attrs.json` and `sunpy/net/jsoc/data/attrs.json` files by running the `tools/update_attrs_json.py` file, commit and PR the changes.
1. Check if the API stability yaml needs updating.
1. Generate the statistics for the what's new with with `./tools/generate_releaserst.xsh X.Y.0 vX.Ydev --pat=<your GH PAT>`, where `X.Y` is the previous major version number.
1. Check license end year and update if needed.

## Branching

The next step is to create the release branch, to do this following series of git commands:

    git remote update
    git fetch upstream
    git switch -c X.Y upstream/main
    git push upstream X.Y

This will add a new branch to the upstream sunpy/sunpy which is level with the main branch. Note the branch names (unlikle tags) are not prefixed with `v`.

## Post-Branching

Once this is done there is a couple of things left to do before the first rc release:

1. On release branches we use the milestone checker in the Giles bot to ensure that all backport PRs are attached to a release. We need to enable this by editing the `pyproject.toml` file. Add the following to this file, somewhere under the `[tool.gilesbot]` heading:

```
  [ tool.gilesbot.milestones ]
    enabled = true
    missing_message_long = "This pull request does not have a milestone assigned to it. Only maintainers can change this, so you don't need to worry about it. :smile:"
```

2. Remove all changelog fragments on the main branch.

1. Commit (and PR) the removed changelog fragments to main.

1. Tag the main branch with the "start of development" tag for the next version. So if you just branched 3.0 you would tag main with `v3.1dev`, which has the pattern `v[next_major].[next_minor]dev`. Push this tag to upstream with `git push upstream v3.1dev`.

1. Enable the new branch on read the docs. Mark it as hidden, so it does not show up on the version picker. This is mainly to ensure that the builds work on that branch.

## Pre-releases

Making a pre-release (normally we just use "release candidate" `rcZ` versions) should follow the normal release procedure: <https://github.com/sunpy/sunpy/wiki/Home:-Release-Checklist>

Unlike a normal release, **DO NOT RENDER THE CHANGELOG**.

Things to remember to test during the pre-release phase are:

1. Open a PR to the conda-forge feedstock testing building the conda package with at least one rc release. **DO NOT MERGE IT**.
2. Ensure all sponsored packages tests pass with the rc (or lastest main if tested regularly), sunpy core versions which break sponsored packages should not be released. Make a new release of the package if needed.
