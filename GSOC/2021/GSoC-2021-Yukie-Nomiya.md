# SunPy Scraper rewrite

## About me

My name is Yukie Nomiya and I'm a Computer Science student from Rome, Italy. I will graduate in May with a Bachelor's Degree at Sapienza University of Rome and I will start my Master's Degree next fall.

### My contact information

Timezone: GMT+1

Email: nomiyayukie@gmail.com

Github: <https://github.com/yukienomiya>

Linkedin: <https://www.linkedin.com/in/yukie-nomiya>

Resume: <https://drive.google.com/file/d/1a8ib3fXWy5oYjYRcwgY9WRXeWFGwT88p>

## GSoC experience

I participated in the 2020 edition of Google Summer of Code working on the "Italian translation and i18n improvements" project with the Processing Foundation.
To briefly summarize, I worked on improving and facilitating the internationalization process of the [p5.js website](https://p5js.org/) (p5.js is an open-source JavaScript library for creative coding, one of the most popular libraries maintained by the Processing Foundation). The improvements I made ranged from JS scripts that parsed i18n info, to workflow automation using GitHub actions and even a small web platform created to facilitate the translation work for contributors.
You can read more about my project in the [project wrap-up post](https://github.com/processing/p5.js/blob/main/contributor_docs/project_wrapups/yukienomiya_gsoc_2020.md).

Last summer I learned a lot, developed a great relationship with my mentor and the Community and overall had a really positive GSoC experience that compelled me to apply again this year.

**Are you also applying to other projects?**

I'm not applying to any other projects this year. From the experience of last year, focusing on a single organization allows you to write a better proposal.

**Are you eligible to receive payments from Google?**

Yes, I am.

**How much time do you plan to invest in the project before, during, and after the Summer of Code?**

I plan to spend ~20h per week working on this GSoC program, but I am prepared to put in more hours if the project turns out to be more difficult than anticipated.
The only time I might be a little busy could be during the last weeks of May (due to graduation), but I don't think it's going to interfere much with the Community Bonding Period. As I have already finished my exams, this summer I don't have any other particular commitments that would cause a break from work.

## Programming experience

As part of my Computer Science major at Uni, I completed two programming-focused courses. The first one was centred around the basics of programming and was taught in Python, the second one focused on Object-Oriented Programming and was taught in Java.
I particularly enjoyed the first course and during the semester I tried to do as many exercises as I could (and then uploaded them to this [repository](https://github.com/yukienomiya/fondamenti_nomiya.1744602)).
During the last couple of years, I've also grown an interest in Competitive Programming. Although so far I never took part in official competitions, I like to solve CP problems mostly in Python and C++.
During the application period, I built a simple [link scraper](https://github.com/yukienomiya/link-scraper) from scratch to familiarize myself with the topic and to better understand what I needed to focus on.

I have been using GitHub for a few years now to upload both my personal and academic projects, but prior to my first GSoC I never really contributed with code to a big open source project. Last summer was therefore a great learning experience that allowed me to get more familiar and comfortable with the contribution process, from understanding other people's code to making Pull Requests and discussing ideas and solutions with the Community.

**What are your contributions to SunPy so far?**

While setting up the SunPy project for the first time on my machine I encountered some issues with the conda environment, so I looked for an alternative and I ended up using a virtualbox VM with a Vagrant configuration file that allowed me to set up the work environment with a single command. I decided to make a Pull Request (PR [#5201](https://github.com/sunpy/sunpy/pull/5201)) to propose the alternative as I thought others might find it useful. I will also try to solve the issues that I encountered when installing it on my machine and I'm planning to follow up about this in a separate issue.

I also increased the test coverage of the `sunpy.map.compositemap` class in the PR [#5202](https://github.com/sunpy/sunpy/pull/5202).

## The project

**What do you want to achieve? What excites you about this project? Why did you choose it?**

My goal with this project is to make the design of the Scraper API more robust and to solve the many problems users are facing while using it.
I was drawn to this project because web scraping it's something I don't have much experience with and I'm excited about the possibility of learning from it and growing as a Software Engineer.

**Why are you suited to work on this project?**

Due to my last GSoC experience, I'm pretty familiar with the tools required to work on open source development (git, linting, testing, code reviews, etc...). As I previously mentioned I'm not very experienced with web scraping, but I'm excited to learn more about it and to contribute to SunPy.

**What have other people done on this idea?**

Currently, the `Scraper` class works by receiving in input a string pattern and multiple optional keyword arguments. The pattern is a string that contains one or more datetime format strings (e.g. %Y %m %d) and that may contain placeholders for the keyword arguments. Optionally, the pattern may contain regexs as well but only in the file name and if there are no keyword arguments.
The Scraper then uses the format() function to insert the keywords in the pattern string.

The main function of the Scraper API is the `filelist(timerange)`: it makes a request (using protocols like http, ftp and file) to the "base URL" (the pattern obtained by removing the file's name and extension) substituting in the datetime format string of the pattern every valid date and times that respect the timerange provided.
Then for each file in the directory the filelist function matches its file pattern with the one fetched on the server it returns it if the patterns match.

A lot of issues with the current API have been reported by users. For example:

* If the "base URL" of a pattern contains a regex, the scraper won't find any matches.

![example 1](https://user-images.githubusercontent.com/49163604/114612984-11f80000-9ca3-11eb-9957-ef2ecdde8556.png)

In this example, the class does not visit the file tree so it can't match the subdirectories in `%Y/%m/%d/` and therefore returns an empty list of files.

* The class does not allow to use of both regex and named arguments.

![example 2](https://user-images.githubusercontent.com/49163604/114613347-7d41d200-9ca3-11eb-9a32-6f8ccd9b1a51.png)

This happens because if, for instance, we have the regex `[a-z]{3}` the `{3}` part of the regex has a special meaning for the format function and would break the implementation.
E.G: `r"[a-z]{3}{instrument}".format(instrument='swap')` will raise the exception "IndexError: Replacement index 3 out of range for positional args tuple"

* The scraper breaks when there is a `T` between date and time.

<img src="https://user-images.githubusercontent.com/49163604/114613522-bb3ef600-9ca3-11eb-9f1f-3dd4f4d6a96f.png" alt="example 3" width="500"/>

(Both patterns should work in this case).

* If the pattern contains a regex that includes a dot ('.'), the Scraper won't work properly. This is caused by the fact that the class uses the `split('.')` function on the pattern to separate the name of the searched file from its extension.

**How do you plan to implement the project?**

**If it involves any API changes, how does it affect the user?**

**Does it improve on the current API? If so, how?**

I believe that the API needs to be simplified and the implementation needs to be more robust. Since changing the API means breaking existing users' code, it would be ideal to design the class so that it can be made backwards compatible with the previous syntax (e.g. by writing a wrapper around the new implementation to mimic the old one).

In the following, I will assume that backward compatibility is important, and thus that the new implementation will keep using regex. The solution though is general enough so that changing it to use the parse library format is straightforward.

First I would design a `BaseScraper` class that simply takes a file server (more details below) and starts to walk the file tree partially matching the pattern as it walks the folder.

So for instance if the server root is `http://solarmonitor.org/data/` and the pattern is the regex `\d{4}/\d{2}/\d{2}/fits/\w*/\w*_\d{5}_fd_\d{4}\d{2}\d{2}_\d{2}\d{2}\d{2}\.fts\.gz` the `Scraper` will first matches the regex `\d{4}` among the files inside of `http://solarmonitor.org/data` then for each subfolder it will match `\d{2}` (e.g. folders inside `http://solarmonitor.org/data/2015/`), etc.

Using this kind of directory-level pattern allows us to both discover and match files as we walk the tree (avoiding pre-fetch the entire tree and then matching). This has the advantage of being quite efficient, though has the limitation of not allowing patterns like `.*\.fts\.gz` since we can't partially match them as we walk the tree, and we would need to first visit the whole file server tree and for each leaf (i.e. file) match the regex on the whole path from the root to leaf. This limitation means that we would need to make sure to tell the user that regex are on a per-directory basis and do not span over multiple directories.

Once the simple `BaseScraper` class is implemented, I would create a new class `DatedScraper` that introduces the concept of datetime formats inside paths and that uses the implementation of `BaseScraper` but with the additional logic to filter out paths that are outside the given time range.

The logic that handles the protocol-specific way of discovering files on a server would be abstracted away from the `BaseScraper` class by Implementing 3 separate classes namely `FTPFileTree`, `HTTPFileTree`, `LocalFileTree` all extending an ABC class `FileTree` that provides a unified API to access files on a file server. In this way `BaseScraper` simply takes a `FileTree` in input instead of a string and then uses its APIs to walk the file tree and match the pattern.

Once all this is done, it should be possible to write a wrapper around the new `DatedScraper` class to mimic the old implementation.

## Development Schedule

* **Community Bonding Period** (May 17, 2021 - June 7, 2021)

  In this phase, I will need to discuss the following topics with my assigned mentor/mentors: the project timeline, the meetings schedule, the project priorities and finally, any further research required before the coding period starts.

* **Week 1-2** (June 7, 2021 - June 21, 2021)

  Finalize the API design document.

* **Week 3-4** (June 21, 2021 - July 5, 2021)

  Implement all the *FileTree classes + tests

* **Week 5-6** (July 5, 2021 - July 19, 2021)

  Implement BaseScraper + tests

  _Midpoint Evaluation (July 12, 2021)_

* **Week 7-8** (July 19, 2021 - August 2, 2021)

  Implement DatedScraper + tests

* **Week 9-10** (August 2, 2021 - August 16, 2021)

  Write documentation on how to migrate to the new API/or in case of backward compatible API implementing the wrapper to mimic the old API.

  _Final Evaluation (August 16, 2021)_
