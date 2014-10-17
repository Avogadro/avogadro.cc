---
layout: default
title: Working with Gerrit
---

# Working with Gerrit

Avogadro's gerrit server is at [<http://review.avogadro.cc>](http://review.avogadro.cc/). Before submitting a patch, create an account there. You will need to add an SSH key and pick a memorable username.

If you run into problems or have questions, do not hesitate to [contact us](Contact "wikilink") on the mailing list or on IRC.

Initial Configuration
---------------------

We have provided a set up script to guide you through setting up your local development clone for use with Gerrit. To clone Avogadro and set it up for use with Gerrit (skip the first line if you already have a clone):

`git clone `[`git://github.com/cryos/avogadro.git`](git://github.com/cryos/avogadro.git)
`cd avogadro`
`./scripts/setup-for-development.sh`

This will guide you through setting up your clone, adding a remote for Gerrit submission and helpful aliases.

Starting a New Topic Branch
---------------------------

All work should happen on topic branches, nothing directly on your local master (or other integration) branch. To start a new topic based on the latest master branch, assuming origin is a remote referring to the Github/Gitorious repository (substitute if not),

`git fetch origin`
`git checkout -b my-topic-branch origin/master`

You can then work on this topic, make local commits, and submit it for review when ready.

Sending new patch for review
----------------------------

Do some work, make a few commits, then check what you are about to push:

`$ git log origin/master..`

You can substitute origin/1.0 to see commits relative to the 1.0 branch for example. An alias for checking commits relative to master is provided too,

`$ git prepush`

Then push the branch to gerrit:

`$ git push gerrit HEAD:refs/for/master/topic-name`

You can substitute the 1.0 branch if your topic is based on 1.0 instead of master. An alias for submitting changes to the master branch is provided, this will automatically push the name of the local topic branch for you:

`$ git gerrit-push`

Your patch(es) should appear on Gerrit now.

Making changes in the uploaded patch
------------------------------------

If your changes require revisions before they are accepted, the process to submit revised code is:

1. Gather information -- you need the changeset's *Change-Id* (if you used the hook you can skip this).

-   The Change-Id starts with an "I" and is located on the gerrit page for the changeset towards the top of the page. (Read about [ git hook](Working_with_Gerrit#Git_hook_for_Change-Id "wikilink") to learn, how to get it added automatically.)

3. Edit the commit that needed revision with git rebase -i. For example, assuming the commit is two back:

`$ git rebase -i HEAD~2`

An editor will open with:

`pick d10ab29 Commit message from commit needing revision`
`pick ce373fd Commit message from the revision you created in step 1`

To edit the commit, change the first line:

`edit d10ab29 Commit message from commit needing revision`
`pick ce373fd Commit message from the revision you created in step 1`

Write the file and exit the editor. Make the necessary corrections, then add the changes to the index and amend the commit.

`vim file.cxx`
`git add file.cxx`
`git commit --amend`

You will need to add the Change-Id if you didn't use the hooks to do it for you, it must be the last line in the commit message. You should copy and paste the entire Change-Id line from Gerrit's web interface, e.g. 'Change-Id: I187d71bbe6092683645aa7c3d97c2ef9e50d07e3', the short form will not suffice.

`Change-Id:[your Change-Id here]`

Now, continue the rebase. If you did not use the Change-Id hook you will need to edit every commit after the one you change, and add that commits Change-Id too. This is why I would really recommend just using the hook.

4. Push the new commit to gerrit with

`$ git gerrit-push`

Gerrit should now reflect these changes.

Git hook for Change-Id
----------------------

If you plan to contribute frequently, you're probably interested in more convenient procedure for revising of changes. This is done by use of so-called "git hook" - special script, which automagically inserts Change-Id in all new commits. When you modify these commits, you will not need to look for Change-Id in Gerrit and paste it in.

To install hook, run this command in the root of your source tree:

`$ scp -p [your_username]@review.source.kitware.com:hooks/commit-msg .git/hooks/ `

More information about this hook: [1](http://gerrit.googlecode.com/svn/documentation/2.1.2/user-changeid.html)

Merging in accepted changes
---------------------------

Once a change, or a topic branch (series of changes) has been tested, approved and verified you need to merge in those changes. Only those in the correct group have permissions to do this, if you are not in a group someone who is can handle the merges. Assuming you added the Gerrit Git server as a remote named Gerrit, and have been added to the Avogadro group of core developers, you can copy and paste the line Gerrit gives you to download the change, verify it is good and works, then make a topic branch from it, merge into master, check all is well and push.

The following is an example, the first URL is specific to the changes being reviewed, branch name made up.

`$ git fetch `[`http://review.source.kitware.com/p/avogadro`](http://review.source.kitware.com/p/avogadro)` refs/changes/14/14/1 && git checkout FETCH_HEAD`
`$ git checkout -b mac/Qt-4-7-fixes`
`$ git checkout master`
`$ git fetch Gerrit`
`$ git reset --hard Gerrit/master       # This will ensure you have a pristine master branch`
`$ git merge --no-ff mac/Qt-4-7-fixes`
`$ git log Gerrit/master..              # Check what new commits will be pushed - should be reviewed patches + a merge`
`$ git push Gerrit master               # Publish the changes to Gerrit`

Gerrit is set to replicate all changes to both Github and Gitorious. You shouldn't try to push directly to either of these repositories anymore, which is why push access has been removed for now. If you are in the Avogadro group you can bypass code review all together by pushing branches that were not pushed to Gerrit first - please avoid using this unless it is necessary.

<Category:Developer>

