# SunPy Meeting Notes - August 20th 2012

Present: Steven Christe, Keith Hughitt, Jack Ireland, Albert Shih, Florian Mayer, Matt Earnshaw, Jose Ivan Campos

## Recent Progress

### Matt’s update
Basic GUI structure in place, to be pushed in next couple of days
Import existing plot functionality working, uses globals() to find existing Maps. Keith suggested a custom “manager” should be considered in the future to give better control.

### Florian’s update
Callisto class implemented
Conditional dispatch implemented, and used in LightCurves, Callisto etc. Will be useful for other modules.
Mac virtualenv is working, contains all the dependencies. Steven reported it to be working well after some modifications. This will greatly simplify Mac distribution and further testing is to be carried out at Trinity.

## 0.3 Release
Keith suggested we aim for around the time of AGU.

## Solar Probe and Solar Orbiter
In order for SunPy to be considered by the Solar Probe team, Steven suggests we replicate IDL SWAVES and TPlot tool, Steven to file steps to this as issues on GitHub. This will take some time, but potentially crucial to the future of the project. David has started work on the SWavesSpectrogram. Peter will push the discussion on IDL vs Python at the Solar Orbiter workshop. Ideally we can get a dev to meeting to demonstrate SunPy’s capabilities.

## SIPWork
Jack reports that SunPy demos and Keith's talks were well received. There were concerns about the current state of SolarSoft, there is general dissatisfaction, SunPy should answer this. Some talk of moving SSW to modern version control.

## Naming conventions
Florian raised the issue of what our naming conventions should be, should they agree with SSW or create a bespoke more Pythonic SunPy naming convention for classes, methods etc? It was agreed that it’s better to create our own names as SSW frequently poorly named.

## lab module
Florian suggest a sunpy.lab module to prevent unnecessary imports during interactive use. Unresolved, to be discussed again in future meetings.

## Module focus
Keith suggested a "module focus" scheme whereby a "each week or couple weeks we could choose a different module in SunPy. During that time, all of us would spend some time trying to use the module to do what it was designed for, and record notes about what worked well, what didn’t work well, bugs, feature-requests, missing docs, and confusing or ambiguous syntax, etc. Then each of the items should be filed as an issue on GH so that they can be tracked in the future. If more extensive problems exist (e.g. architecture or interface needs to be changed) then a proposal for the changes (diagram, outline, pseudo-code etc) should be submitted to the mailing list and discussed until agreement is reached.". It was agreed that is an excellent idea and **the current focus module is VSO**.

## Future meeting times
Future meetings, tentatively set for 5pm BST to allow those on the West Coast to participate.