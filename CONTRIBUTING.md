# Contributing and Editing the Guide

Any partner within Learners Guild can contribute to the guide. This document explains how.

Depending on the kind of edit, there are different approaches.

If the edit is about formatting, fixing links, or otherwise improving the form of the content, it is a **style edit**. If the edit is about changing, removing, or adding to the information contained within the guide, it is a **content edit**.

Style edits don't need to be approved by anyone - they can be immediately integrated. Content edits should be approved by at least one other partner, since they will affect how we work together.

Before learning about how to make edits, let's review the technology used.

## Getting Started

The Guide is hosted as a [GitHub repository][gh-repo] at https://github.com/LearnersGuild/guide. It follows the [GitBook format][gb-format], allowing it to be rendered as a GitBook site at http://guide.learnersguild.org/.

The content stored in the master branch of the guide repo (https://github.com/LearnersGuild/guide/tree/master) is what the GitBook site pulls from. Any changes made to files and folders in this branch will be reflected in the GitBook site.

**To make edits, you will need a GitBook account and access to the [Guide book][gb-guide] on the LearnersGuild GitBook organization.**

In order to work effectively with the Guide, it is helpful to have a baseline understanding of GitBook and Markdown (the text format used to write all content in the Guide).

To learn about GitBook, start by reading the following documentation:

- [Introduction](http://help.gitbook.com/index.html)
- [Format](http://help.gitbook.com/format/index.html)
- [Output](http://help.gitbook.com/format/output.html)
- [Readme and Introduction](http://help.gitbook.com/format/introduction.html)
- [Chapters and Subchapters](http://help.gitbook.com/format/chapters.html)
- [Markdown](http://help.gitbook.com/format/markdown.html)
- [Editor](http://help.gitbook.com/editor/index.html)

Although not absolutely necessary, it is very helpful to have a working understanding of GitHub as well. Here are some good introductory resources to learn about GitHub:

- Complete the ["Hello World" tutorial on GitHub guides][gh-hello-world] to develop a basic understanding of how git and GitHub work, and how to work with repositories.
- Watch this [video on collaboration with GitHub][gh-collaboration].

Now you're ready to start editing.

## Making Style Edits

To make a style edit (change formatting, edit link, etc.), follow these steps:

1. Go to the Guide GitBook page: https://www.gitbook.com/book/learnersguild/guide/
1. Click the "Edit" button
1. Use the "Table of Contents" or the "Files Tree" to find the file you want to change
1. Click on the desired file to navigate to it
1. Make any changes to the file in the left-hand pane
  - You can either write in Markdown or use the style buttons in the formatting bar at the top of the editor
1. Check your changes in the live-updating rendering of the page on the right-hand pane
1. When you have finished your changes, save the document by clicking on the "Save" button in the upper left-hand corner of the editor
1. Your changes are now saved and should be visible on the live Guide at http://guide.learnersguild.org/
  - If you don't see them right away, wait 10-15 seconds and refresh the page (sometimes it takes a little bit for the server to update)

## Making Content Edits

To edit the content of the Guide, we use [GitHub flow][gh-flow].

Distilled, the process looks like this:

1. Create a new branch to encapsulate the desired changes
2. Make all changes as commits on the new branch
3. When the branch is ready to be merged, open a pull request from your branch to the `master` branch
4. Have at least one another partner review and approve of the changes
5. When the changes are approved, merge the pull request

[gh-repo]:https://help.github.com/articles/github-glossary/#repository
[gb-format]:http://help.gitbook.com/format/index.html
[gh-hello-world]:https://guides.github.com/activities/hello-world/
[gh-collaboration]:https://youtu.be/SCZF6I-Rc4I?list=PLg7s6cbtAD15Das5LK9mXt_g59DLWxKUe
[gb-guide]:https://www.gitbook.com/book/learnersguild/guide/
[gh-flow]:https://guides.github.com/introduction/flow/