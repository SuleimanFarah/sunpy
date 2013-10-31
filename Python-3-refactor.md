Notes on the refactor to 3.3:

`__future__` imports from http://docs.astropy.org/en/latest/development/codeguide.html#welcome-to-the-future

using: 
```
find . -name "*.py" -print | xargs sed -i 's/from __future__ import absolute_import/from __future__ import absolute_import, division, print_function, unicode_literals/g'
```
then run some 2to3:

```
2to3 -f basestring -f dict -f except -f has_key -f idioms -f imports -f itertools -f itertools_imports -f unicode -f xrange
```

like:
```
find sunpy/<submodule> -name "*.py" -exec 2to3 -w -n -f basestring -f dict -f except -f has_key -f idioms -f imports -f itertools -f itertools_imports -f unicode -f xrange {} \;
```