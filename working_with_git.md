---
layout: default
title: Working With Git
---

# Working With Git

In December 2008 Avogadro moved its version control system over to [Git](http://git.or.cz/), hosted at [GitHub](http://github.com/cryos/avogadro/). Git is quite different to traditional, centralized version control systems. It is a [DVCS](http://en.wikipedia.org/wiki/Distributed_revision_control) (Distrubuted Version Control System). It was coded by Linus Torvalds and others primarily to handle the Linux kernel's very distributed development model.

There are lots of [guides](http://git.or.cz/#documentation) around that help you to work with Git. A good quick start guide is [everyday Git](http://www.kernel.org/pub/software/scm/git/docs/everyday.html). In a normal workflow we recommend that you sign up for a GitHub account, go to the [Avogadro GitHub](http://github.com/cryos/avogadro/) page and fork Avogadro. You will then get your own copy of the Git repository. You can keep this up to date using the web interface or Git, and can make pull requests when your changes are ready for integration.

Configuring Git
---------------

The first thing you will want to do is tell Git who you are. This will be used in commit messages and attributions.

    git config --global user.name "Your Name"
    git config --global user.email "you@yourdomain.com"

If you are like me you may also want to add some color to the Git output.

    git config --global color.branch true
    git config --global color.diff true
    git config --global color.interactive true
    git config --global color.pager true
    git config --global color.status true

One or Two Patches
------------------

If you just have one or two patches you would like to submit you probably just want to clone our repository.

    git clone git://github.com/cryos/avogadro.git

Make any changes you like, commit them to your local repository and then use git format-patch to make a patch. When the patch is applied it goes into Git just like any other commit and you get full credit. For this reason you should ensure you set up your name and email correctly before committing anything.

Contributing to Avogadro
------------------------

If you would like to get more involved with Avogadro, and begin making contributions to our code on a longer term basis, you should take the following steps:

-   Create an account on [GitHub](http://github.com/).
-   Go to the [Avogadro repository](http://github.com/cryos/avogadro/) and click on the fork button.
-   Clone your forked repository to your local machine.
-   It is often convenient to make a topic branch for individual features or fixes, `git checkout -b newfeaturebranch master`.
-   Make any changes you want to make, commit them and do a `git push`.
-   Make a pull request to cryos, see the [GitHub guide to pull requests](http://github.com/guides/pull-requests).

While getting used to Git there are several guides such as [the Git cheat sheet](http://github.com/guides/git-cheat-sheet), [forking and submitting modifications](http://github.com/guides/fork-a-project-and-submit-your-modifications), and [keeping a git fork in sync with upstream](http://github.com/guides/keeping-a-git-fork-in-sync-with-the-forked-repo). You can also ask questions on IRC or our mailing list.

Managing Multiple Remotes, Integrating
--------------------------------------

In order to integrate the changes of other developers we can either use the [fork queue](http://github.com/cryos/avogadro/forkqueue) or manage things on the command line. The command line is often quicker once you get the hang of it, but it can take a little getting used to. Once you have your clone of the repository you can add multiple remotes and fetch their data.

    git remote add timvdm git://github.com/timvdm/avogadro.git
    git fetch

Once a developer makes some commits and requests that they are pulled into the repository you first need to update your copy of their repository, merge the changes and push to the master.

    git checkout master
    git fetch timvdm
    git merge timvdm/master
    git log -p
    git push

You can also use `git cherry-pick` to pick off individual commits to apply. Never rebase anything that has been pushed as this will break history for other people's checkouts. When using private feature/topic branches rebasing is preferable, but not in public branches. This also applies to commits which you later decide are not appropriate - once they have been pushed they must be reverted rather than edited.

Using multiple branches
-----------------------

In Git it is very easy to have several branches. Usually, you keep one branch per feature, so called "Topic Branches".

Because git tracks merges, output from "git log master..$topic" gives all you need to know about $topic. The command lists changes that are still not merged to master on the $topic branch. If the list is empty, $topic is already merged fully to master.

For more details refer to one of the linked tutorials.

Further information
===================

There are lots of guides on using Git, the [everyday Git](http://www.kernel.org/pub/software/scm/git/docs/everyday.html) guide is a very good summary covering different roles you might take.

[Git Wizardy](http://habrahabr.ru/blogs/Git/60347/) - very thorough guide in Russian

<Category:Developer>

