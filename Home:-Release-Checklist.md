**Before major releases only:**

- [ ] Ensure What's New have been finalised at feature freeze time.
- [ ] Do a conda-forge build for at least one of the release candidates.

**Before release candidate releases:**

- [Feature Freeze Checklist](https://github.com/sunpy/sunpy/wiki/Home%3A-Feature-Freeze-Checklist)

**All of the following assumes that you are on the release branch and not main (`X.Y` e.g `1.0`)**

**Before release:**

- [ ] Update the changelog using [towncrier](https://pypi.org/project/towncrier/) (not for rc releases):

```
towncrier build --version X.Y.Z
```

**if it's a rc release do not do this**, the changelog is only rendered automatically in the documentation for pre-releases.

- [ ] Commit the changes

```
git add .
git commit -m "Release vX.Y.Z"
```

- [ ] Push directly to the release branch on SunPy

```
git push upstream X.Y
```

- [ ] Check that the CI passes on last commit on the branch (including the wheel builds).
- [ ] Test that RTD is building the documentation correctly on the branch.

If you need to fix anything do so on the branch and forward port to main as need be (to reduce the CI builds).

- [ ] Tag on and push (tag should be full version number preceded by a `v`)

```
git checkout X.Y
git tag -a vX.Y.Z -m "Releasing version vX.Y.Z"
git push --follow-tags upstream vX.Y.Z
```

This triggers the GitHub Actions release pipeline which will build and test the wheels and dist then upload them to PyPi for you.

If there is an issue at this step, the fix will be to update the config in the [github actions workflows repo](https://github.com/OpenAstronomy/github-actions-workflows), a patch to this repository should only happen if somehow the inputs to the template need to be changed.
Since we use tags, you will to update the tag and force push it.
This should (re)start the tag job on [GitHub Actions](https://github.com/sunpy/sunpy/actions)

- [ ] Update the conda forge [sunpy-feedstock repo](https://github.com/conda-forge/sunpy-feedstock), the bot will do it (normally) but can be slow.

**After Release:**

- [ ] Make sure all builds of sunpy are complete and uploaded (conda-forge and wheels)
- [ ] Create the release on GitHub releases, copy the changelog into the description. The following pandoc command will convert it to markdown: `pandoc --wrap=none -t markdown_strict CHANGELOG.rst`.
- [ ] Ensure the tag has built on read the docs and the "stable" marker has been updated. **Ensure that all the gallery examples have built correctly, restart the build if not**.

*For a major release:*

- [ ] Commit the final rendered changelog to main. (The fragments should have been removed at feature freeze time)
- [ ] Update the index.rst file in sunpy.org repo to point to the new whats new and update the version number.

**Announcements:**

- [ ] Post release announcement on social media sites
- [ ] Send release announcement to mailing lists (sunpy@googlegroups.com and sunpy-dev@googlegroups.com)

```
Email Template
-----

Dear all,

The SunPy developers present to you the latest release of SunPy <version>.
In this update the headline fixes are <fill in>

The full changelog is:

<fill in>

To update you can run these following commands:

Pip users:

pip install -U sunpy

Conda Users:

conda update sunpy

GitHub Users:

git pull <local upstream name> <version>

Please enjoy,
The SunPy Developers
```
