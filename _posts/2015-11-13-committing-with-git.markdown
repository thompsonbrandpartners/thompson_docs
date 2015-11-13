---
layout: post
title:  "Committing with Git"
date:   2015-11-13 13:52:54
categories: databases, rules
---

**The following information comprises some guidelines and best practices for committing code using Git. For the purposes of our internal workflow, we will assume the use of [Github][github] for storing remote repositories, and the [Tower][tower] application for managing your changes. However, most of these rules are also applicable when using Terminal or other desktop applications.**

#### On this page:

* [Commit regularly](#regularly)
* [Don’t bundle multiple updates into one commit](#dont-bundle)
* [Be descriptive with commit messages, and be neat with capitalisation and grammar](#descriptive)
* [Always use the present tense for commit messages, not past](#present)
* [If an issue exists, always reference the issue number in your commit message](#issue-exists)
* [Ignoring files](#ignore)
* [Excluding files](#exclude)
* [Testing and issue tracking](#testing)

{:#regularly}
### Commit regularly

You should commit small chunks of code regularly. 

Consider you’re working on new features that require several different elements to make them work. If we commit all of those elements together and discover an issue later down the line, we’re only able to Revert ALL of those elements at once. If we commit each element separately then we are able to ‘undo’ very specific changes later down the line. 

If you’re working for a long period and forget to commit regularly, [Tower app][tower] allows us to Stage ‘chunks’ of code within a single file, thus enabling us to make those smaller commits at any time.

For other developers working on the project, this also makes the change history much clearer when reviewing the work that has come before.

{:#dont-bundle}
### Don’t bundle multiple updates into one commit

Expanding on the point above, no matter how small a change is, you must not commit more than one update or fix in a single commit.

{:#descriptive}
### Be descriptive with commit messages, and be neat with capitalisation and grammar

Always consider the possibility of another developer being brought onto a project when you aren't there to explain what has happened so far. Your commit history / messages should paint a clear picure of all the progress on a project so far. If 50 characters isn't enough to explain what you've done, utilise the 'Commit description' to elaborate on your work.

In addition to this, be neat with your commit messages by constructing them with sensible capitalisation. We would recommend using sentence-case.

{:#present}
### Always use the present tense for commit messages, not past

For example use `“Fix issue ABC”` rather than `“Fixed bug ABC”`. A commit is not referencing what the person who made the change *did*, it is referencing what the new change *does*.

{:#issue-exists}
### If an issue exists, always reference the issue number in your commit message

[Github][github] has a great feature whereby if you include an issue number in your commit message, it will reference that commit on the issue comments. This can be very useful if you need to reference the code that fixes a specific issue.

You reference the issue by adding a hash infront of the number, for example `"Fix shopping cart issue #123"`.

In addition to this, if you wish to automatically close an issue at the same time as commiting your code, you can do so by simply using the word "Fix". For example `"Fix #123"`. However, unless this issue has been raised by yourself, you should not do this. Reference the information on Testing and issue tracking below.

{:#ignore}
### Ignoring files

There are various files that should never appear in a remote repository, but which are necessary for a project to work. These are controlled by the `.gitignore` file.

Examples of these are:

* css directory (if the server is running SASS)
* sublime-project and sublime-workspace files
* Temporary files such as .DS_Store
* Config files (that are different to the live environment)

**Please note**

Only *untracked* files will be ignored. If a file has already been committed to the repository you will have to manually remove / untrack them before the `.gitignore` takes effect.

{:#exclude}
### Excluding files

If you find yourself needing to 'ignore' a file locally to get your project working as you want, but you know for a fact that the file is needed in the Live environment and won't necessarily need to be ignored for everyone on the project, **do not** add it to the `.gitignore` file. Instead use 'Exclude'.

**Please note**

Only *untracked* files will be excluded. If a file has already been committed to the repository you will have to manually remove / untrack them before the `.gitignore` takes effect.

[Read more about ignoring and excluding files in Tower][tower-ignore]

{:#testing}
### Testing and issue tracking

During the testing phase of any project it is likely that issues will arise. We track these through the [Issues section of Github][githubissues]. Any new issue should include a descriptive title and immediately be assigned to the person best suited to fixing that issue. If necessary the issue should include a more detailed description containing information such as the error message, browser or device version, screen grabs, etc. If the project is to be released in stages, a milestones label should be applied.

Once an issue has been fixed it should be assigned back to the creator for final testing. If the issue is solved it can be closed, if not then it is assigned back to the developer responsible with further comments on the issue.

[tower]:    http://www.git-tower.com/
[tower-ignore]:    http://www.git-tower.com/help/mac/working-copy/ignore-files
[github]:   https://github.com/
[githubissues]: https://github.com/issues
