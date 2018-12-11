**For major releases only:**
- [ ] Update RELEASE.rst

**Branching:**
- [ ] Create and change onto a new release branch from master labeled with the release number ```X.Y```.

**All of the following assumes that you are on the release branch and not master**

**Pre-release:**
- [ ] Update version number in `setup.cfg`
- [ ] Update the changelog using [towncrier](https://pypi.org/project/towncrier/)
- [ ] Commit the changes
```
git add .
git commit -m "Release vX.Y.Z"
```
- [ ] Push directly to the release branch on SunPy
```
git push upstream X.Y
```
- [ ] Check that the CI passes on release commit
- [ ] Test that RTD is building the documentation correctly on the release branch (and the version is correct)
- [ ] Release on GitHub (tag should be full version number preceded by a `v`)
```
git checkout X.Y
git tag vX.Y.Z
git push --follow-tags upstream vX.Y.Z
```

**Once all the checks are clear: Release**
- [ ] Release on PyPI (using [twine](https://pypi.org/project/twine/)):
```
# Make sdist
python setup.py sdist
cd dist
# Upload Release
twine upload dist/sunpy-X.Y.Z.tar.gz
```
- [ ] Update sunpy-wheels repo to build wheels for the release version
- [ ] Update the sunpy-feedstock repo, ideally a bot should do it for you
- [ ] Update astropy/ci-helpers stable sunpy version number (Three places: `test_env.py`, `travis/setup_dependencies_common.sh`, `appveyor/install-miniconda.ps1`)

**Post Release:**
- [ ] Make sure all builds of sunpy are complete and uploaded (conda-forge and wheels)
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