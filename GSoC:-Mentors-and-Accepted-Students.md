# Advice for GSoC Mentors

## Before GSoC

If you want to mentor a project, add it the [OpenAstronomy](https://github.com/OpenAstronomy/openastronomy.github.io/) website.

Read (at least skim) the [Google guide for mentors](https://google.github.io/gsocguides/mentor/).
It’s actually very useful.

Mentors should communicate with applicants and help them create relevant applications.

CC any co-mentors when responding to communication from students via email.

## During student selection

Mentors will discuss with their co-mentor(s) to identify promising students.

Be aware that there are often more good students than there are slots the organization can support.
This means we may not be able to take on your favorite student.

## After the start of GSoC

Mentors should make sure they speak to their student at least weekly.

Inform the organization administrators if any issues arise, or seem likely to arise, including:

        Mentor is unable to continue mentoring or experiencing too high workload.
        Student is under performing or non responsive.

Complete all evaluations as early as possible in agreement with their co-mentor and encourage students to complete them early as well.

Coordinate vacation and out-of-office periods to ensure at least one mentor is available to respond to their student at all times.
If both/all mentors are likely to be unavailable at the same time, please speak to an organization administrator to arrange backup.
This is particularly important around evaluation periods!

# Advice for Accepted Students

First of all, welcome to SunPy!
We're excited to have you working with us this year.
We’ll try to generally adhere to the Google Manuals to avoid repetition, but here are a few SunPy-specific guidelines for Google Summer of Code.

## Communication

You’ll establish a personal rhythm with your mentors, but please bear the following points in mind:

* Email

    All students and mentors should subscribe to our SunPy public mailing list.
    This is to ensure that we can effectively share announcements.

* Chat

    You can come hang at our IM room [here](https://app.element.io/#/room/!unyYitVQrpIQvLQQHQ:cadair.com), and feel free to ask for help.
    If you are using riot you can start a group for the project with all the mentors.
    Remember to make tickets or send emails for any big bugs or design decisions, as chat logs are transient.

* Videoconferencing

    Every week on a wednesday at 16:00 UTC or 17:00 UTC (depending on daylight saving), [we have a developer meeting](https://sunpy.org/jitsi).
    An announcement email is sent to the mailing list.
    We expect all students to show up for these meetings (barring any issues) to discuss what they have done since the last meeting.
    You might have smaller meetings with your mentors often throughout the project life cycle.

* Writing code

    All code must be to a high standard, documented and well-commented, and accompanied by a unit test (where applicable).
    We use GitHub for our source control, with a Git Flow-like branching model.
    New work is done in personal forked repository branches, periodically merged into the upstream master branch when it appears stable.

    You should follow a similar model - treat github.com/sunpy/sunpy as upstream and work on a branch your own fork, i.e. github.com/yourusername/sunpy, merging (or PRing for existing projects) periodically.
    Remember, pushed commits (to your own repository) prove you’re alive and working on the project! ;)

* Project Management

    You do need a work plan!
    Make sure you and your mentor have a good idea of what the deliverables are.
    It’s okay not to use the work plan from your proposal, but you and your mentor(s) will need to agree to any changes.
    You’ll want to schedule regular meetings with your mentor.

* Time commitment / Missed days

    From the Google Manual:

        GSoC needs an investment of about 18 hours a week.

    If you know in advance that you’ll need to take a couple of days of vacation/break during the Summer of Code, you should communicate that with your mentor beforehand and plan to make up for lost days.

* Outreach

    We’d love to host blog posts (which you can do on the SunPy website) about yourself, the work you’re planning to do, or work you have done.
    Equally, if you’re tweeting or blogging on a personal blog and would like us to link to it / mention you / etc., poke your mentor and we’ll give you a shout-out on the SunPy website or Twitter page.

* Final Report

    Each student will write up their project.
    The length and detail vary a great deal from project to project.
    Please coordinate with your mentor.
    We’ve had short blog posts that simply describe the project and provide links to the repository.
    Others have created detailed tutorials to use their software, and we’ve had others who wrote entire papers!
    This final report can be a blog post or a standalone site on GitHub.
