# "Sunpy Website Improvements"

## Organization: OpenAstronomy

## Sub-organization: SunPy

## About Me

* Name: Sourav Kumar
* IRC/Matrix nick: **@numal**
* Github username: [souravc4](https://github.com/souravc4)
* Email: souravkumarc4@gmail.com
* Time zone: IST(UTC+5:30)
* University: [BITS Pilani Goa](http://www.bits-pilani.ac.in/Goa/)
* Academic Year: 2nd

### Brief Bio:-

My name is Sourav Kumar, a sophomore at BITS Pilani Goa. I love Web Development, I have been practising it for over a year now and am proficient in both front-end and back-end. To list the languages, i am proficient in `HTML`/`CSS`, `Bootstrap`, `JavaScript`, `PHP` and `MySQL`. My favourites are `JavaScript` and front-end development with `Bootstrap`.

I have put up some of my work on Github as **live** websites. To demonstrate a few :-

* [_project](https://souravc4.github.io/my_demo/)
* [_hh](https://souravc4.github.io/hh_demo/)
* [_place](https://souravc4.github.io/ray_demo/)

***

## My contributions

I have been working on the Sunpy's website Github repository over the past few weeks, during this time I have figured out the overall structure of the website, built using the static site generator _Jekyll_, and how it facilitates code(HTML/CSS/JavaScript) sharing with the use of specialized folders like `_layouts` and `_includes` to turn content into static pages with predefined templates. I have worked on issues and improvements to the website with the understanding of the model and design of Jekyll and its way to implement them. Having this knowledge, I've already suggested several changes to the website with most of them being _structural_ in nature. They are from the _merged_ pull [#70](https://github.com/sunpy/sunpy.github.io/pull/70).

* commit [84a0a0f](https://github.com/sunpy/sunpy.github.io/pull/70/commits/84a0a0f969a7ce2c955e7e752cffcb050053ceb9) : This pertains to the issue [Too big headings on Mobile #13](https://github.com/sunpy/sunpy.github.io/issues/13)
* commit [aabb509](https://github.com/sunpy/sunpy.github.io/pull/70/commits/aabb5091b1250459e2461d64932db85c18ac111b) : This removes extra padding around `h1[id]` tags in _Contribute_ and _About_ sections of the website and makes the posts look neater/concise.
* commit [e5c0dbe](https://github.com/sunpy/sunpy.github.io/pull/70/commits/e5c0dbe0c4611c91ac57127f8867cfd61dba67d9) : This commit is about the lists on the `navbar` of _Contribute_ and _About_ not syncing with their corresponding posts.
* commit [bf0ff96](https://github.com/sunpy/sunpy.github.io/pull/70/commits/bf0ff96d49607969f817d002a54eb02175efc040) : Credit for this idea goes to @Cadair, who suggested that instead to hard-coding the version number of the current stable in the home page of the site, find a way to fetch it automatically from _PyPI_. So I used a made a `jQuery` that uses a `JSON` request to the Python Package Index to get the version number automatically. Thus there's no need to update it manually.

With the grasp of the current code base(_the above structural changes may depict it_), I believe it'll be convenient for me to get started with revamp of the website as soon as coding starts.

***

# Project Proposal

### "SunPy Website Improvements"

So why does Sunpy need a quality website? The answer is twofold:

1. The website [Sunpy.org](http://sunpy.org) acts as a medium for people interested in (_SunPy_) for scientific analysis/research to get to know the installation/setup of not only the package but also the necessary python environment for its functioning.
2. Since it is an open-source scientific product for conducting solar data analysis, it should act as both, a forum for conducting advice/discussion on using SunPy (to perform solar data research) and also to provide documentation on using SunPy and its components properly. It should be a community knowledge resource for performing solar research.

But the current website is ineffective on both parameters. The overall look of the website is very unappealing, it appears outdated and uninteresting. The need has come to give it a modern look viz. crisp design, larger font sizes, bright colours and overall catchy/attractive outlook. I'll combine it with distinctive javascript effects/animations to make a consistent professional theme.

The home page is lacking in essential components like a _Installation_ section on the home page itself, proper weight is not given to _Documentation_ and _Blog_ sections which are a necessity for community sourced products.

Through my proposal, I want to layout a comprehensive plan to revamp the website to not only make the UI user-friendly and attractive but also professional looking and scalable across devices. Therefore I propose to not only revamp the original components but also add some features which I think will make the website fruitful.

## Featured Components and their Implementation

### Blog Section

The Blog section provides a place for posting relevant updates related to SunPy and its research, this can also be the place to post and discuss scientific work or anything that the scientific community finds intriguing and worth sharing with the community.

* So I would implement a _comments mechanism_ for blog posts. My initial suggestion is to use _Disqus_- it's a popular comment hosting service which is easily implemented and can also be customised.
* Next on my agenda will be to feature in Blog _author attributes_ alongside posts which is currently lacking. This helps in providing a quick referral to the author- providing a Github link can be one good way. It can also be easily implemented by either storing author's information in `.yml` file and linking details to post.html or having the same information in a `JSON` file and parsing it in compile time. I would rather go with the previous method since the use of _liquid_ plugin might create issues if we use Github hosting.
* Other structural changes to Blog section will be implementing _categorization of posts_-it'll help in easy browsing of posts if we create _custom_ post types, and finally division of blog directory into _sub-directories_ will help in maintenance.
* _A sample live demo of the Blog page which I made is [Blog Demo](https://souravc4.github.io/blog_demo/)_.
* screenshots of above demo are![blog screenshot](https://github.com/souravc4/sunpy_screenshots/blob/master/blog1.png?raw=true)![screenshot 2](https://github.com/souravc4/sunpy_screenshots/blob/master/blog2.png?raw=true)

### About Section

Besides detailing information about the SunPy project, the organization and various channels to interact with the community, I want to:-

* Set-up a _registry of SunPy affiliated packages_ and put it up on the _About_ section of the website. This section will list procedures for requesting affiliated package status and steps to install them. The fresh feature that i will bring to this section is that after a package has been granted affiliate status, the administrator will just need to mention them in a file and all the package related information(package-name, latest stable, repo. address, maintainer etc.) will be fetched from _Python Package Index_ with use of _javascript/jQuery by a JSON request_. Thus, it eliminates manual updating of information and consequently needs negligible maintenance. I have already implemented a similar feature in my commit [bf0ff96](https://github.com/sunpy/sunpy.github.io/pull/70/commits/bf0ff96d49607969f817d002a54eb02175efc040) which updates SunPy version number automatically on the home page, and I hope to take it to the next level in About section.
* _About_ section will also contain information about the SunPy organization, channels to interact with the community and acknowledgements or citations for work.
* _A live implementation of dynamic package information fetching using `AngularJS` and `jQuery`_ :-> [About Demo](https://souravc4.github.io/about_demo/).
* screenshot of above is ![about demo](https://github.com/souravc4/sunpy_screenshots/blob/master/about1.png?raw=true)

### Back-end

Since I believe that the intent of the website should be to require _minimal maintenance_, I don't think the use of server-side languages/frameworks like PHP/MySQL would be a good idea. Jekyll requires very less maintenance since there's no database to maintain and the framework takes it upon itself to do the heavy lifting of rendering blogs/posts in desired way, you just need to follow the proper conventions and even things like the custom organization of posts can be done with ease. Moreover, since Github provides _static_ site hosting, server-side scripting languages like PHP won't work.

* That said I am still open to using dedicated server-side frameworks in making the backend of the website. I have decent understanding and practice in both _PHP_ and _MySQL_. Another option will be to use _Django_ -(Python based back-end framework). It has a very strong community to support it and its library support and update policies makes it an excellent choice. Although I haven't made a web-app with Django before, I'll love to learn it and make the best use of it.
* Similar is the case with the backend regarding _comments_ functionality that I propose to have in a _Blog_ section of the website, although _Disqus_ provides proper comment hosting feature, using login/register _OAuth 2.0_ will certainly provide _robust_ administration of comment system like deleting comments, banning users etc. It must be noted that all these features will come with a tad bit of maintenance, so before making any decision about it, I will take advice from mentors/community.
* Once these things are setup, I'll work towards making the _Documentation_ with _Sphinx_ which is a documentation generator built on python. It provides a convenient way to create good-looking documentation by converting `RST` files into _HTML_ pages.
I'll build the documentation theme corresponding to the main website, the focus will be on giving it a professional effect with proper color-scheming to look attractive as well. This theme can be reused by SunPy's affiliated packages in future.

### Overall UI

* Special emphasis will be given to improving the website design with effective color-scheming to give the website a much _appealing_ outlook. The UI is incomplete without proper javascript as event handlers to make the UI dynamic in nature. Therefore I am confident of making a much attractive theme as front-end web development comes first on my skill set. I will certainly take views of not only the mentors but also the SunPy community as taste of people varies significantly on design overlook of sites. Once finalised this theme will be used across all the pages to give the website a homogeneous theme.
* To make the website _responsive_(scalable) Bootstrap will be used which has built-in responsive features. I am quite proficient in Bootstrap and will employ the best of my knowledge to make an excellent front-end.
* A flaw in the home page of the site is the absence of weight given to components based on their priority. Therefore I have selected three sections which require maximum attention on the home page – “_Installation_”, “_Documentation_”, and “_Contribute_”. These are based on my discretion and I am open to changes in consultation with mentors.
* Also there is no mention of installation procedure(s) on the home page itself which I think is a big downside as currently users are directed to [docs.sunpy.org](http://docs.sunpy.org/) which is not convenient at all.
* A _search bar_ will be implemented which will be available across all the pages is the navigation bar section. But its functionality will be limited to searching within the _documentation_.
* _A live demo of the home page which I have designed is_:-> [Home Demo](https://souravc4.github.io/home_demo/).
* screenshot of above is ![home demo](https://github.com/souravc4/sunpy_screenshots/blob/master/home1.png?raw=true)

### Documentation

The current _Read the Docs_ theme is dull to say the least, moreover, it does not match the theme of the main website.
After creating a striking theme for the main website, I will replicate it for the _Documentation_ using Sphinx by designing an analogous theme.

### Extensions to project :-

1. **Implement a registry of SunPy affiliated packages on the website:**
An affiliated package will a python package that is not part of the SunPy core package, but has requested to be included as part of the SunPy's project's community. As I have already stated, I would like to work on this project and I have my method cut out for this. After getting approval from the appropriate authority, the name of the affiliated package will just need to be put up on the website and all relevant information and links to the package will be automatically fetched from _PyPI_ and displayed on the website, thus eliminating the need for manual updating. I have already elaborated on the system to that above.

2. **Move away from _Jekyll_ to a Python-based static site generator:**
The motivation behind having a python based static-site generator is to use the same ecosystem as SunPy itself, moreover, Jekyll(a ruby gem) runs into trouble sometimes while testing locally if version mismatch of gems occur, as I have experienced it first-hand.
 (a) _Nikola_ is an excellent choice as it being a python package, has strong community support and has efficient update/bug fixing mechanism. Moreover, it has out-of-box support for _comments_ system and has some interesting features like _author-pages_. Also, there is a CLI interface for anyone interested. It comes with decent front-end components and has support for Github page deployment.
 (b) Although _Nikola_ is my first preference, I will take the suggestion from mentors about which generator they feel will suit their needs.

3. **Creating Question and Answer Forum:** _(Optional)_
If time permits I propose to make a Q&A section. I believe it will be a welcome addition to the website as it will help to address common queries. I have thought of the following two systems to implement it:-
(a) Creating a set of predefined questions and answers and implementing _Disqus_ as comment mechanism to have further discussion on any particular topic. As you can see it will be a very minimal version of a Q&A section but on the other hand will require least intervention/maintenance.
(b) Although I prefer the previous method, if the mentors are of the view to go for a full-fledged system, _AskBot_ (a Django) package can be implemented. [https://askbot.com/](https://askbot.com/) | [Github repo](https://github.com/ASKBOT/askbot-devel)

## Timeline

* **5th May - 30th May**: _Community bonding Period_ : I will have detailed interactions with my mentors and community
regarding following points:- **1.** Whether the backend be designed with current Jekyll or Django. **2.** Whether implementation register/login modality be feasible in the sense that- will they be maintained in future? **3.** Since I prefer _Nikola_ as the newer static-site generator as part of the project, I'll get their views on the same. I have my semester exams from 1st to 13th May, therefore I would be less available during this time.

***

* **1st June - 13th June**:_Coding officially begins_ :  **1.** Create and finalise the new design/UI of the website. **2.** Added _author-attributes_ and _post-categorization_ features to the _Blog_ section of the website.

***

* **14th June - 26th June**: _Till first phase evaluation_ : **1.** Take feedback on the new look of the website from mentors/community. **2.** Begin rigorous testing of the new website for cross-browser and cross-device issues **3.** Added _comments mechanism_ by implementing _Disqus_ into the _Blog_ section.

***

* **27th June - 13th July**:  **1.** Create the new documentation theme using _Sphinx_ **2.** Make PRs for changes to the website(_not documentation_). **3.** Begin work on porting the _Jekyll_ website to _Nikola_.

***

* **14th July - 24th July**: _Till second phase evaluation_ :  **1.** Complete new website based on _Nikola_ and PRs for the same **2.** Take another feedback on the latest website based on _Nikola_, with the newer theme, from mentors and community. **3.** Begin work on making the Q&A forum section.

***

* **25th July - 29th August**: _Final Submission_ : **1.** Complete the Q&A forum section **2.** Check for bugs/issues in new website through proper testing. **3.** Provide completed website for submission .

## Commitments

* I have not participated in GSOC before.
* I am not applying to any other organization or project.
* I have no other work/internship during the vacations.
* For any other query /clarification contact me at souravkumarc4@gmail.com
