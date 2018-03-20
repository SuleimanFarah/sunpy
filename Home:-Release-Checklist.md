For Major releases only:
- [ ] Update RELEASE.md

Pre-release:
- [ ] Update version number in `setup.py` (the version number branch and don't commit yet)
- [ ] Modify the changelog title (remove `(unreleased)`)
- [ ] Build the source distribution:
```
python setup.py sdist
```
- [ ] Test that the sdist installs (in an enviroment of your choice)
- [ ] Check that the `sunpy.__version__` number is correct
- [ ] Run `sunpy.self_test()` to check that installed tests work
- [ ] Commit the changes: 
```
git add .
git commit -m "Release vX.Y.Z"
```
- [ ] Push to the directly release branch on SunPy (the version number branch)
```
git push upstream X.Y
```
- [ ] Check that Travis passes on release commit
- [ ] Check that AppVeyor passes on release commit
- [ ] Test that RTD is building the documentation correctly on release branch (and the version is correct)
- [ ] Release on GitHub (tag should be full version number preceded by a `v`)
```
git checkout X.Y
git tag -s vX.Y.Z
git push --follow-tags upstream vX.Y.Z
```
- [ ] Update sunpy-wheels repo to test build wheels for the release version
- [ ] Release on PyPI:
```
# Make sdist
python setup.py sdist
cd dist
# sign sdist
gpg --armor --detach-sign sunpy-X.Y.Z.tar.gz
# verify it was signed with the correct signature
gpg --verify sunpy-X.Y.Z.tar.gz.asc sunpy-X.Y.Z.tar.gz

# Upload Release
twine upload dist/sunpy-X.Y.Z.tar.gz dist/sunpy-X.Y.Z.tar.gz.asc
```
- [ ] Make a PR to the sunpy-feedstock repo with the updated recipe and merge once CI is passed
- [ ] Update sunpy-wheels repo to push build wheels for the release version

On Release:
- [ ] Make sure all builds of sunpy are complete (conda-forge, wheels, etc)
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
Post Release:
- [ ] Update CHANGELOG.rst (Add a new heading for the next release)
- [ ] Update astropy/ci-helpers stable sunpy version number (Two places: `test_env.py` and `travis/setup_dependencies_common.sh`)
- [ ] Update sunpy-wheels repo to test build wheels for the release version
