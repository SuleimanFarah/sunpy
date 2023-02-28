# Wiki Maintenance

This is a tricky topic since it is possible for anyone to write to the wiki.
Compounded by the fact that the wiki does not see folder hierarchy.
So as it stands, each subsection has its own series of folders as outlined below.
When files are added to the wiki, GitHub adds it to the main level of the folder tree.
This means that someone has to clone the wiki and manually move it in order to maintain the wiki.

## Directory Tree

### GRANTS

We add grants here as required and link them on the main level `Grant-Applications.md` file.

### GSOC

In the main GSoC folder, there is a year dated file that links to any project ideas or applications.
Then there are folders for each year and in each one of those are the files for applications or ideas.

* GSoC
  * 2013
    * Individual student applications
  * 2014
    * Individual student applications
  * 2015
    * Individual student applications
  * repeat

### ORG

Nothing, all the files are just placed in here.
I could not figure out a good structure so I moved on.

### GSOD

Add applications directly since its a one file per year application.

### SOCIS

This mirrors the GSOC one.

## Sidebar

The wiki sidebar is created via [this package](https://github.com/adriantanasa/github-wiki-sidebar).
Update it if you want more links but you have to add the files to the highest level of the repository.
