**For major releases only:**
- [ ] Update RELEASE.rst
- [ ] Remove the files under the developer's guide except for `index.rst`, `stability.rst` and `sunpy_stability.yaml`. Then change the `index.rst` file to read:

```
.. _dev_guide:

Developer's Guide
=================

Please go `here <https://docs.sunpy.org/en/latest/dev_guide/index.html>`_ for our up to date developer's guide.

.. toctree::
   :maxdepth: 2

   stability
```

**Branching:**
- [ ] Create and change onto a new release branch from master labeled with the release number ```X.Y```.

**All of the following assumes that you are on the release branch and not master**

**Pre-release:**
- [ ] Update the changelog using [towncrier](https://pypi.org/project/towncrier/): `towncrier --version vX.Y.Z`
- [ ] Commit the changes
```
git add .
git commit -m "Release vX.Y.Z"
```
- [ ] Push directly to the release branch on SunPy
```
git push upstream X.Y
```
- [ ] Check that the CI passes on last commit on the branch
- [ ] Test that RTD is building the documentation correctly on the release branch

If you need to fix anything do so on the branch and forward port as need be.

- [ ] Tag on GitHub (tag should be full version number preceded by a `v`)
```
git checkout X.Y
git tag -a vX.Y.Z -m "Releasing version vX.Y.Z"
git push --follow-tags upstream vX.Y.Z
```
This triggers the Azure release pipeline which will build and test the wheels and dist then upload them to PyPi for you.

If there is an issue at this step, the fix will be to update the config on the [azure template repo](https://github.com/sunpy/azure-pipelines-template) and start a new tag job on [azure pipelines](https://dev.azure.com/sunpy/sunpy/_build?definitionId=4).

- [ ] Update the conda forge sunpy-feedstock repo, ideally a bot should do it for you
- [ ] Push the update to the stable branch

**Post Release:**
- [ ] Make sure all builds of sunpy are complete and uploaded (conda-forge and wheels)
- [ ] Create the release on GitHub releases, copy the changelog into the description.
- [ ] Enable the tag on Read the Docs

**Announcements:**
- [ ] Post release announcement on social media sites
- [ ] Send release announcement to mailing lists
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