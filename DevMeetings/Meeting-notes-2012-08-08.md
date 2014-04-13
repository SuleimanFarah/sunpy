
**Telecon minutes: 8th August 2012**

**Present: Steven, Keith, Jack, David, Florian, Matt**

***

### Framework
Tk: Distributes easily but a little antiquated. David suggested that PyQt distribution is not as painful as it may have been in the past, which pushes us further away from Tk. Matt suggested that PySide may distribute a little easier and will ask mailing list to test on various platforms (particularly OS X etc).

### Chaco
Not quite as mature as matplotlib in some respects although its approach to data could be useful to as at some point. As we are currently entrenched in matplotlib, we will continue pursue it for the gui. The matplotlib animation functionality is relatively new and should only improve. Chaco and the other enthought tools might be a side project for someone on mailing list.

### Tabs
Initially focus on single plots but certainly plan for tab support down the line. This should not pose significant challenges.

### Overlays
Photoshop style palate, but modified for our purposes. Support adding overlays “From Tab...” (for files already open in plotman) or “From File...”. May need to advance SunPy classes to ease overlay support, GUI development should drive where we go in that regard.

### Spectrogram Plot
One should be able to toggle the lightcurves between representing data from entire plot and showing data from a selection made using crosshairs. Jack suggested that a “funnel” from the selections to the lightcurve plots would make this clear to the user.

The lightcurve selection boxes should be made by box style selection but should also have the ability to be manually resize and independently locked.

Florian suggested that the selection box colours should be coordinated with the lightcurve plot colours for clarity.

### Other Business
Consider a global figure manager to enable the user to import pre-existing plots into plotman (using the globals builtin?).

Along the same lines, try and link console objects with the GUI such that modifications in the console are reflected in the gui (and vice versa?). Possibly include a REPL as part of the GUI? This will come later, regardless.

First steps for Matt are to get basic map manipulations in place (to some extent refactoring existing code in the gui module) and then start work on the features shown in the spectrogram mockup.