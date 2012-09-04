Present: Steven Christe, Florian Mayer, Stuart Mumford, Nabil Freij, Matt Earnshaw

## Better 3.x forward compatibility (all \_\_future\_\_ imports)
As the next matplotlib release will support 3.x, it makes sense to start improving our 3.x support). Florian suggested that a good way to do this is by including \_\_future\_\_ imports,

\# 1 / 2 → 0.5

from \_\_future\_\_ import division

\# print is a function

from \_\_future\_\_ import print_function

\# no relative imports

from \_\_future\_\_ import absolute_import

\# “foo” is unicode

from \_\_future\_\_ import unicode_literals

SunPy code should be include these imports.

## Unify arguments to .plot. Rethink subplotting.
The current plot method creates figure with a single subplot. Florian will put together an example of a more “correct” way of plotting and overplotting onto an existing plot.

## Coding standards
Steven has started compiling some coding standards. Please take a look at what is currently on the sunpy wiki https://github.com/sunpy/sunpy/wiki/Developer-Standards. Merge existing coding standards with the more comprehensive list above. Everyone should go ahead and add things that are missing.

## Progress report from Matt
Image GUI ready almost ready to be committed for testing.

## Progress report from Florian
Spectrogram object improved, better initialisation. Spectrogram plotting improved. Solar orbiter poster for workshop.

## New logos. 
Check whether fonts are standardized. Please always use logo with the name sunpy.

## Documentation
We need to work on the docs! Need someone to be in charge of it. May be the best way to get a lot of work done on it.

## Other
Any meeting discussion should take place on the Google+ page. We have agreed to use a seperate sunpy-dev list. Meeting notes will be placed on GitHub wiki and a link sent to the mailing list.