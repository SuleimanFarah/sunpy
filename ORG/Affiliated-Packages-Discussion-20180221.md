# Affiliated Packages Discussion 2018 Notes

## Steven Christe's Proposal and Thoughts

The primary purpose of affiliated packages are to foster an eco-system of high-quality and compatible packages for solar physics. To achieve this goal the SunPy project can offer the **affiliated package** designation which can be considered a kind of **seal of approval**. As described in the [original SEP](https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0004.md), the requirements for becoming an affiliated package are based on the quality of the package itself (documentation, tests, etc.) and not necessarily on the usefulness of the package. It should therefore **not** be considered a recommendation on the part of the SunPy project to use the package. For example, if two different developers created similar GUIs interfaces for Fido, as long as they meet our standards, both could become affiliated packages.

### Process for acceptance

The current process as described in the SEP is that registering an affiliated package requires a developer nominate their package to the board and the board votes. I recommend that this process be changed based on the time and effort needed to perform this function. My suggestions is that the lead developer create an evaluation process which is well-documented, clear, and fair for potential applicants. After that evaluation is performed, the lead developer shall provide the results of that evaluation to the board along with a recommendation of acceptance or refusal. The board would then be asked to provide _concurrence_. The board should define this process but potentially it could be as simple as 3 board members approvals similar to how our PRs are currently accepted.

## Provisional Acceptance

Provisional acceptance may be provided to a package that has not yet achieved _release status_ but is managing to meet all of the requirements of an affiliated package during their development process. In order to apply the package must be deemed to provide some useful functionality. On release (as defined by the primary developer), the lead developer shall provide a new recommendation which shall again be submitted for board concurrence. This is to allow the board to review the final usefulness of the package.

### Proposal for Sponsored Affiliated Packages

It may become appropriate for SunPy to go beyond the seal of guarantee that is provided to affiliated packages and provide a recommendation. For example if there are 5 Fido guis in the list of affiliated packages, it may be appropriate for the project to elevate one to a recommended package. I would recommend that only packages which are held inside of the sunpy organization on github can get that privileges. I don't think we should be playing "favorites" but "take on" projects and their developers into the fold (if they agree). All packages under the sunpy org would then be our recommended affiliated packages.
