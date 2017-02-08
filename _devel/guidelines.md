---
layout: single
title: Developer:Guidelines
categories: Devel
---



Developer Guidelines
--------------------

These are general guidelines for new developers contributing to the Avogadro project. They are suggestions and in general should always be used along with common sense.

The first thing to ask before you commit your code is does it compile and work as expected? If you are unsure then it would be a good idea to post the output of \`svn diff\` to the avagadro-devel list and ask for comments. Commits should never break trunk and if you are making large changes to Avogadro they should be discussed in advance.

You can quickly check which files have been modified using the \`svn stat\` command. To see a more detailed breakdown of your change set you can use the \`svn diff\` command which can also be used to produce patches.

In general it is always better to submit very large changes piece by piece as you work on it. Your commit messages should provide a short summary of what the committed code has fixed/improved/changed. The ChangeLog should also be updated with details of what has changed.

