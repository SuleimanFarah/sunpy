We expect to receive, as we did last year, lots of high quality applications.
So please do give your application some thought!


Follow Google’s outline exactly: https://google.github.io/gsocguides/student/writing-a-proposal
The “deliverables” section is most important!
A clear understanding of the problem we need solved.
A clear plan of action. What are you going to actually do?
Milestones should be achievable and realistic.
Things happen! We can’t foresee every problem! We are happy to see proposals that say “I will do A and B. If there is time, I will do C.”
Read about our grading criteria for proposals.
We are happy to read your proposal and give you feedback. Please allow for a few days for us to get back to you – don’t wait until the last minute!


Student proposal grading criteria
Criteria
Once proposals have been finalised, student proposals will be graded based on the following criteria:

Understanding
Does the proposal accurately address the project area?
Nice bonus features in addition to the main project = good, ONLY unrelated ‘bonus’ features = bad.
Clear evidence of communication skills
Plan
Does the proposal have a realistic timeline?
Bonus for “what if things go wrong planning”, e.g. bonus features towards the end of the plan that can be removed if/when the bugs strike.
Resourcefulness
Can the student carry out tasks on their own over a three month period?
Lower points for gross overcommunication (“what should I name this variable?”), better if they quietly and competently get the job done but interact at appropriate times, e.g. InterMine bugs, sensible progress reports.
Is the student capable of following existing guidelines and instructions where appropriate?
Experience
Does the student have reasonable evidence they’ve competently done something relevant to this before? e.g. one or more of
a GitHub profile,
pull requests on InterMine’s repos
published applications
code from a uni assignment?
Note: we don’t require a PR to an intermine project. It’s handy as a source of evidence, but any of the others should do just fine.
Absolutely no work available - not even a published app, some work experience, or code from a class assignment, is a red flag.
How the ranking process works
All students with a finalised proposal will have their proposals reviewed by one or more mentors in the organisation, and ranked out of 10 based on the criteria above. This score will also be averaged to provide a mean result. These scores are not the final acceptance criteria - so a 9.1 won’t automatically win over an 8.6 - but they do help provide general guidelines for the mentors who are choosing from a large body of qualified students.

Accepted students
Students will be notified of their acceptance by Google when all accepted students are announced, and will not be notified of their internal grades. Please note that we usually have more highly qualified applicants than slots available for the organisation, so sometimes proposals that are genuinely very good have to be rejected. We genuinely wish we could take you all!

Here are some criteria that we consider when reviewing applications. We suggest that you think about these when writing your application.

Has the student interacted with the Mixxx community before submitting their application?
Does the student understand the purpose of their project? Do they understand what impact their project will have on users?
Has the student demonstrated that they have the ability to work with Mixxx's code? The best way to do this is by submitting pull requests and getting them merged. It can also be okay if a student works on a bug but is unable to solve it before the application deadline if they demonstrate competence working with the Mixxx code. Students must have submitted a pull request to Mixxx or provide links to code they have written before in their application (ideally both).
Has the student demonstrated that they can work independently and solve problems on their own without asking for help every step of the way?
Does the student understand the design and technical details of what will be required to implement their proposal?
Is the proposed timeline realistic considering any other obligations the student may have during GSOC?

Be sure to read through all the advice on the wiki and the links we suggested first!
You should include the following information in your proposal:


# Pull Request requirement

In addition to the written proposal, we require every GSoC applicant to have opened a pull request to SunPy.
Note it does not need to be merged to be considered.

Please note that we take your pull requests to SunPy into strong consideration when reviewing your proposal.
This is your best opportunity to prove to us that you are capable of doing what is in your proposal.

To do this:

* Set up your platform to develop with SunPy (install git, clone https://github.com/sunpy/sunpy.git, execute tests).
  The page on our [Developer's guide](http://docs.sunpy.org/en/latest/dev_guide/newcomers.html) will walk you through setting up git and lays out our preferred way of development.

* Create an account at GitHub and fork SunPy (https://github.com/sunpy/sunpy).

* Find something in SunPy that doesn't work or needs improvement.
  If you need inspiration, feel free to fix any issue from our [Package Novice fix issues list](https://github.com/sunpy/sunpy/issues?q=is%3Aissue+is%3Aopen+label%3A%22Package+Novice%22).
  Aside from the issues, search for `FIXME` or `TODO` in the code.
  You can grep from the command line with `git grep "TODO"`.
  You could also search for NotImplementedErrors, maybe).
  You could also play with SunPy and find something that needs fixing or that could be implemented, and do it.

* Your pull request must be code-related, not documentation.
  While we do not want to discourage documentation pull requests as they are very useful.
  This shows us that you know Python and that you are able to interact with the community.
  If your project will use a language other than Python (e.g., C), you should submit patches that use that language as well, so that we know that you know you are proficient in that language.
  **However, for the pull request requirement to be fulfilled, you must have at least one pull request open or in SunPy itself.**

* Note that because we may be slow to review the pull requests, you do not
  have to have your request merged by the application deadline.
  But you do need to at least have one submitted by then.
  We will give priority to reviewing requests that are needed to satisfy GSoC requirements.
  It is up to you to respond to our feedback in a timely enough manner so that your patch gets merged before the acceptance deadline.
