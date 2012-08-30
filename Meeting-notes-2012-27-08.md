## Recent Progress
Matt has shown a demo of the animation, and will write a blog post once it is committed.

## Packages
Is SunPy a library or an environment? We are willing to work with developers using SunPy to improve SunPy itself based on their needs, but SunPy should not become an amalgamation of different projects to avoid becoming like the current state of SSW (eg. avoid different versions of fundamental data structures in different missions). In these early stages of development we should work closely with developers as they will inevitably implement things we require. Then where necessary, useful externally developed tools can be merged into SunPy. Russell suggested investigating the scipy kits model.

SSWDB... what do we do with it? All calibration files, response curves... How do we manage them? do we use it? Maybe prep-server is the solution.

## sunpy.lab
Importing one submodule ends up importing a lot of unnecessary other modules which takes time and it cause unrelated ImportErrors. A sunpy.lab module could provide an environment for interactive use, giving some separation from the rest of the implementation. Florian will create some use cases for future discussion.

## VSO mofulr focus
Florian has fixed some issues with VSO. Documentation should more explicitly show that VSO is a submodule of sunpy.net, and internal classes/methods should be removed from the docs where necessary. We will continue to focus on VSO for the time being.

## SWAVES
Currently issues with distribution as a static library, Steven is chasing up source code. Juan Carlos will be invited to future discussions to demo TPlot etc.

## Organisation
How should we structure the organisation to ensure new developers get support / mailing list enquiries get answered / meetings are setup? Keith suggested it may be advantageous to assign a particular developer to these tasks every month or so to ensure someone is always on hand. Steven suggested a calendar for people to add their periods of commitment. More fine grained organisation (maintainers etc.) is slightly too early to consider at this stage due to the small team and should be discussed at a later date. SunPy-dev mailing list to be discussed on main SunPy list, as a way of separating development discussion from announcements and questions. If SunPy dev list to be used then the main SunPy list should be made fully aware of the dev list.