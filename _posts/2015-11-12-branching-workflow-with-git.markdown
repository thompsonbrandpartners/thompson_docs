---
layout: post
title:  "Branching workflow with Git"
date:   2015-11-12 12:58:54
categories: git, rules, workflow
---
**The following information explains our branching mechanism for Git. This follows the [Git Flow][gitflow] methodology closely and should be the system that we use on *all* projects.**

#### On this page:

* [Branches](#branches)
* [File setup and initial commits](#setup)
* [Feature branches](#features)
* [Collaborative feature branches](#collab-features)
* [Merging into the development branch](#merge-dev)
* [Merging into the staging branch](#merge-stag)
* [Merging into the master branch](#merge-mast)
* [Tagging](#tagging)
* ['Hot fixing'](#hot-fix)
* ['Floating features'](#floating)

{:#branches}
### Branches

Each Git project starts with a `master` branch. Once a project has been created on [Github][github] and synced locally, we should create two additional local branches from the `master`, and Publish them to the remote repository before the project begins. These should be called `development` and `staging`.

[Read more information on creating branches in Tower.][tower-branches]

The purpose of these should be quite clear, but to clarify: 

* `development` should contain all 'in-development' changes and features that are ready for testing and *work*. This branch should not contain anything that would cause another developer issues if they were to 'branch-off' and begin developing a new feature.
* `staging` should contain all changes and features that have been tested and are ready to be deployed to our staging server. In most cases, a `merge` into, or `push` onto this branch will trigger **auto deployment**, so we must be certain that we are happy before doing so. These are changes that we are happy for clients to review.
* `master` should contain **only changes and features that are fully tested, signed off, and that we are happy to deploy to the LIVE server**. 

{:#setup}
### File setup and initial commits

Files should never appear on the `master` branch until they are ready to 'go live', therefore, throughout the course of a new build or re-development project, this branch should remain empty until the go-live date.

Initial project setup (presuming only a single developer is responsible) should happen directly on the `development` branch.

As soon as a project is stable enough for specific 'features' to be developed, changes should no longer be made directly on the `development` branch, and should instead be made on a `feature-branch`.

{:#features}
### Feature branches

A local 'feature branch' should be created for each new feature that we develop for a project. This could be anything from a new widget, to a new page, to an entirely new checkout system.

The branch that you choose to 'branch off' to create your feature branch will depend on the stage of the project. Most of the time it would be advisable to branch off the `master`, as this is the most stable and up-to-date version of the project. If, however, there is another feature residing on the `development` or `staging` branches that is beneficial to the development of your new feature, you may wish to branch off this instead.

*Be aware that if you pick up in-development changes in your new branch, and you wish to put your changes live, you will have to merge **both** sets of changes into the `master` branch and will be responsible for ensuring that all changes are stable and ready to be deployed.*

In [Tower][tower], you can create a 'features' folder by naming your branch `features/new-feature`.

{:#collab-features}
### Collaborative feature branches

If your feature is to be worked on by multiple developers, you must 'Publish' your feature to [Github][github] so that it is available as a remote branch. You **should not** merge any incomplete changes into `development` or any other branch if the sole purpose is to give access to another developer.

Always remember to delete both local *and* remote feature branches when a feature is completed.

{:#merge-dev}
### Merging into the development branch

When a feature is complete and you wish to initiate the go-live process, you should `merge` it into your local `development` branch, and then `push` the changes to the remote [Github][github] repository for review. **Do not squash commits** as this will make the commit history very difficult to review at a later date. If other changes have been pushed to the remote since you began development, you may see an error and have to `pull` before you are able to `push`. Pulling at this point will merge any remote changes into your local branch, thus updating your files with other features that have been developed simultaneously.

{:#merge-stag}
### Merging into the staging branch

When features have been made available and fully tested on the `development` branch they should be merged into the `staging` branch. **Do not squash commits** as this will make the commit history very difficult to review at a later date. In most cases, this branch will be set to auto-deploy to the staging server and changes will be available for review by the team and clients who have access to the server almost immediately. 

Before merging into `staging` it is important to review the commit history to ensure that incorrect files are not uploaded to the server. The date of the previous `merge` on the `staging` branch should indicate how far back you need to check committed files. If you need to speak to another developer about their work to ensure that they are happy for it to be deployed to `staging`, **please do**.

{:#merge-mast}
### Merging into the master branch

When features have been fully tested and signed off on the `staging` branch and we are ready to go-live, the `staging` branch should be merged into `master`. This branch should not auto-deploy as it is important that files are reviewed before being made publically available. This branch should never auto-deploy as we should review all file changes manually beforehand. This reduces the likelihood of an incorrect file being modified/added/removed from the live environment.

{:#tagging}
### Tagging

Tagging allows us to quickly skip between 'major releases'. Whenever a major update takes place on a project, you should tag the merge commit with 'release notes'. A 'major update' might consist of serveral large features being deployed at once, a rebuild or redesign of a section, core file or plugin updates etc.

{:#hot-fix}
### 'Hot fixing'

A 'hotfix' is a small bug fix or tiny feature that may have been missed in testing prior to deployment. We should follow the standard procedure of creating a `feature-branch` from the `master`, however this may be merged directly into `master` when complete. Once merged into `master` it should also be merged back into `development` and `staging` before being deleted in order to ensure the update is not lost in future updates.

{:#floating}
### 'Floating features'

Sometimes it is necessary to make a larger update separately to other features that are in development. These 'floating features' must remain on separate branches as they may need to be deployed onto `staging` or `master` without picking up other 'in-development' features from the `development` branch.

Rather than follow the standard 'Git Flow' workflow, these features should be tested locally and Published to the remote repository for review. At this point they should be merged into `staging` for client sign-off, and then into `master` for live deployment. The main difference is when we're ready to go-live, rather than merging `staging` into `master`, we should merge our floating feature directly from it's `feature-branch` into `master`.

[github]: http://www.github.com
[tower]: http://www.git-tower.com
[tower-branches]:    http://www.git-tower.com/help/mac/branches-and-tags/overview
[gitflow]:  https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
