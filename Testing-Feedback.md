by schriste on 7-Jun-2020
based on experience on PR #???

There are 12 different checks being run on this PR. They are run on Giles, Azure Pipeline and Azure Pipeline(?).

On Giles we run
* changelog
* milestone

On Azure Pipeline we run

* sunny.sunpy: This seems to run the tests.
* sunpy.sunpy (codestyle): This seems to run pycodestyle. If failed it provides the annoying message "##[error]Bash exited with code '1'". Did this fail or did it run into an error? Looking at the output was not useful at all.
* sunpy.sunpy (py38-online [linux]): I assume this runs the test suite but with the online tests enabled. Most new contributors probably don't know that there are online and offline tests.
* sunpy.sunpy (py36 [macos]): Is this the test suite but on a Mac? What is sunpy.sunpy running on then? Is it online or offline?
* sunpy.sunpy (py36-conda [linux]): I assume this installs sunpy with conda but don't all of the tests do this?
* sunpy.sunpy (py36-oldestdeps [linux]): ???
* sunpy.sunpy (py38-32bit [linux32]): ???
* sunpy.sunpy (py38-devdeps [linux]): ???
* sunpy.sunpy (py38-hypothesis [linux]): ???
* sunpy.sunpy (py37 [windows]): Running on windows. Are the tests online or offline?

At a quick glance I can't tell which of these are the building docs tests. 

I received a test failure on the changelog that I was never able to figure out. It said that the number did not match the PR number but I checked it twice but perhaps I made a mistake.


