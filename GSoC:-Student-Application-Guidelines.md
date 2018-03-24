Be sure to read through all the advice on the wiki and the links we suggested first!
We expect to receive, as we did last year, lots of high quality applications.
So please do give your application some thought!

## Pull Request requirement

In addition to the written proposal, we require every GSoC applicant to have opened a pull request to SunPy.
Note it does not need to be merged to be considered.

Please note that we take your pull requests to SunPy into strong consideration when reviewing your proposal.
This is your best opportunity to prove to us that you are capable of doing what is in your proposal.

To do this:

* Set up your platform to develop with SunPy (install git, clone https://github.com/sunpy/sunpy.git, execute tests).
  Our [Developer's guide](http://docs.sunpy.org/en/latest/dev_guide/newcomers.html) will walk you through setting up git and lays out our preferred way of development.

* Create an account at GitHub and fork SunPy (https://github.com/sunpy/sunpy).

* Find something in SunPy that doesn't work or needs improvement.
  If you need inspiration, feel free to fix any issue from our [Package Novice fix issues list](https://github.com/sunpy/sunpy/issues?q=is%3Aissue+is%3Aopen+label%3A%22Package+Novice%22).
  Aside from the issues, search for `FIXME` or `TODO` in the code.
  You can grep from the command line with `git grep -i "TODO"`.
  You could also search for NotImplementedErrors, maybe).
  You could also play with SunPy and find something that needs fixing or that could be implemented, and do it.

* Your pull request must be code-related, not documentation.
  While we do not want to discourage documentation pull requests as they are very useful.
  This shows us that you know Python and that you are able to interact with the community.
  If your project will use a language other than Python (e.g., C), you should submit patches that use that language as well, so that we know that you know you are proficient in that language.
  **However, for the pull request requirement to be fulfilled, you must have created at least one pull request in SunPy.**

* Note that because we may be slow to review the pull requests, you do not
  have to have your request merged by the application deadline.
  But you do need to at least have one submitted by then.
  We will give priority to reviewing requests that are needed to satisfy GSoC requirements.
  It is up to you to respond to our feedback in a timely enough manner so that your patch gets merged before the acceptance deadline.

## Student Grading Criteria

Once proposals have been finalized, student proposals will be graded.
Here are some criteria that we consider when reviewing applications.
We suggest that you think about these when writing your application.

0. **Has the student interacted with the SunPy community before submitting their application?**

    We do not accept or even look at any hit-or-run applications.

1. **Does the proposal accurately address the project?**

    Is the student capable of following existing guidelines and instructions where appropriate?
    Nice bonus features in addition to the main project are good, **only** unrelated features are bad.
    Clear evidence of communication skills.
    Does the student understand the design and technical details of what will be required to implement their proposal?
    Do they understand what impact their project will have on users?

2. **Plan**

    Is the proposed timeline realistic considering any other obligations the student may have during GSOC?
    Bonus for "what if things go wrong planning", e.g. features towards the end of the plan that can be removed if/when the bugs strike.

3. **Resourcefulness**

    Can the student carry out tasks on their own over a three month period i.e., has the student demonstrated that they can work independently and solve problems on their own without asking for help every step of the way?
    Lower points for gross over-communication ("what should I name this variable?"), better if they quietly and competently get the job done but interact at appropriate times, e.g., sensible progress reports.

4. **Experience**

    Has the student demonstrated that they have the ability to work with SunPy's code?

    Does the student have reasonable evidence they’ve competently done something relevant to this before?

    For example:

    - A GitHub profile,
    - Pull requests on SunPy's repository
    - Published applications
    - Code from a uni assignment

    Absolutely no work available - not even a published app, some work experience, or code from a class assignment, is a red flag.
    Students must have submitted a pull request to SunPy and provide links to code they have written before in their application.
    Try to select your most proud work, we do not want a link to everything you have ever done.


## Interview

One of the parts of GSoC that isn't very common to other packages is that we try to "interview" the students.
This is generally very informal, much closer to a chat than anything else.
We use this to try and get everyone (all the mentors) who will be involved with the project to have spoken beforehand.
**Please note, if you don't get an interview, it does not mean you have been rejected.**
**Sometimes it is impossible to interview everyone due to time constraints.**

## How the ranking process works

All students with a finalized proposal will have their proposals reviewed by all of the project mentors in the organization, and ranked out of 5 based on the criteria above.
This score will also be averaged to provide a mean result.
These scores are not the final acceptance criteria - so a 4.1 won’t automatically win over an 3.6 - but they do help provide general guidelines for the mentors who are choosing from a large body of qualified students.

## Accepted students

Students will be notified of their acceptance by Google when all accepted students are announced, and will not be notified of their internal grades.
Please note that we usually have more highly qualified applicants than slots available for the organization, so sometimes proposals that are genuinely very good have to be rejected.
We genuinely wish we could take you all!