This document describes the procedure that the people in the sunpy-maintainters group must follow when merging a pull request. If in any doubt about merging a pull request, the correct course of action is to contact the Lead Developer / Executive Director and ask.

# Fundamental Components of a Pull Request

Each pull request *must* meet the following criteria before it is considered for merge:

* The code must be PEP 8 compliant and meet the ill-defined SunPy quality standards.
* The PR must contain a CHANGELOG entry.
* The test coverage **ABSOLUTELY** must not decrease, and for new features should be at or very close to 100%.
* All code must be properly documented. Each function and each class must have an associated doc string in the correct format.

# Review Process

Before the 'merge' button is clicked the following criteria must be met:

* All the builds pass (currently Travis CI, Appveyor and Coveralls.
* At least two members (not the author of the PR) of the sunpy-developers group have approved the PR. (Normally via the GitHub [review](https://help.github.com/articles/about-pull-request-reviews/) or by commenting on the PR with either a :+1:(`:+1:`) emoticon or +1).
* All comments posted on the thread must be resolved, a +1 after any comments by the same author indicates that the comments have been satisfactorily resolved. (Note: do not +1 a pull request unless you would be willing for it to be merged in it *current* state.)

It is important that approval for merging the PR is done on the comment thread, as this becomes part of the 'permanent record', this includes in during developer and IRC meetings.

# SunPy GitHub Groups

This document has already referred to two SunPy groups, namely 'developers' and 'maintainers' there is also a third primary SunPy group 'owners'.

## SunPy owners
The SunPy owners group is the group of people who have total control over the SunPy GitHub organisation. The SunPy board have control over who is in this group, it has been decided that generally it will be the Executive Director (Lead Developer) and the SunPy board chair and vice-chair.

## SunPy Maintainers
This is the group of people who have push access to the main SunPy repos. The membership of this group is at the discretion of the Executive Director, but shall generally be made up of people who have demonstrated themselves to be trust worthy and active contributors to the project.

## SunPy Developers
The members of this group have 'read' access to the SunPy orgs repos. As all these repos are open anyway, what this effectively means is that these people can be assigned to issues. The members of this group are people who are involved in the development of SunPy at a good frequency, they are people who's opinions have been demonstrated to be constructive and informative.

# Pull Request Labelling
Like we use labels for sorting issues and pull requests the following tags will be used for sorting Pull Requests. These tags will be applied as issue labels.

* `[Review]` - This PR is 'complete' and in need of a 'final' review.
* `[BugFix]` - This is a lightweight bug-fix PR, generally no more than a few lines, and should be handled rapidly.
* `[DocFix]` - This is a lightweight documentation patch that should also be fast-tracked.

*As an exception to the normal review requirements, only one developer approval (as opposed to two) is required for "BugFix" and "DocFix" PRs.*

# Pull Requests to Feature Branches

From time to time, large feature development work may occur in branches other than `master`, and all maintained releases currently have a branch i.e. `0.6`. When making a PR to one of these branches, please put the name of the branch in square brackets at the beginning of the PR, i.e. `[0.6] My bug fix`. This makes it easier to filter and review these PRs.

