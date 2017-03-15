- [ ] Update RELEASE.md (major releases only)
- [ ] Run the tests (on both Python 2 and Python 3):
```
python setup.py test
```

- [ ] Update version number in `setup.py` (in both branches) [don't commit yet]
- [ ] Build the source distribution:
```
python setup.py sdist
```
- [ ] Test that the sdist installs:
```
conda create -n sunpy-install python=3.6 numpy scipy astropy matplotlib pandas requests beautiful-soup scikit-image suds-jurko pytest sqlalchemy glymur

source activate sunpy-install

cd dist
tar -xvf sunpy-0.7.tar.gz
cd sunpy-0.7/
pip install .
cd ..
```

- [ ] Check that the `sunpy.__version__` number is correct.
- [ ] Run `sunpy.self_test()` to check that installed tests work

```
pip uninstall sunpy
deactivate
```

- [ ] Commit the changes: 
```
git add .git commit -m "Release 0.1.1"
```

- [ ] Push to the release branch on SunPy (the version number branch).

```
git push
< PR to release branch and merge >
```

- [ ] Test that RTD is building the documentation correctly on release branch (and the version is correct).
- [ ] Check that Travis is passing
- [ ] Check that appveyor passes
- [ ] Update the version for build numbers on Appveyor

- [ ] Release on PyPI:
```
# Make sdist
python setup.py sdist
cd dist
# sign sdist
gpg --armor --detach-sign sunpy-0.7.2.tar.gz
# verify it was signed with the correct signature
gpg --verify sunpy-0.7.2.tar.gz.asc sunpy-0.7.2.tar.gz

# Upload Release
twine upload dist/sunpy-0.7.2.tar.gz dist/sunpy-0.7.2.tar.gz.asc
```

- [ ] Test that it pip installs:
```
cd ~
workon pipsunpy
pip uninstall sunpy
pip install sunpy
```

- [ ] Check sunpy imports, version is correct and `self_test()` passes

```
pip uninstall sunpy
deactivate
```

- [ ] Make a PR to the sunpy-feedstock repo with the updated recipe.

- [ ] Release on GitHub (Tag should be full version number preceeded by a `v`.)
      Add changelog to release description.
```
git checkout 0.7
git tag -s v0.7.2
git push --follow-tags upstream v0.7.2
```
  Then go to GitHub releases > Draft new release then type in the name of the tag. You should see "Exisiting Tag".
  Download the tarball and sign, then edit release and upload signature. (https://wiki.debian.org/Creating%20signed%20GitHub%20releases)



- [ ] Update and make sure all builds of the sunpy/conda-package-build repo are complete, and the binaries are in binstar.

- [ ] Enable the tag on RTD and disable the branch.
- [ ] Push the code to the stable branch via PR

- [ ] Update CHANGELOG.md (Add a new heading for the next release)

- [ ] Send release announcement to mailing lists
- [ ] Post release announcement on social media sites


- [ ] Drink Beer.