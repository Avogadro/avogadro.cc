---
layout: single
title: Release Checklist
categories: Developer
---



-   Create a draft of the [release notes](Releases "wikilink") on the wiki.
-   Grab the latest i18n files from [Launchpad](https://translations.launchpad.net/avogadro/+translations) translations.
-   Make sure to update CMakeLists.txt and Doxyfile version numbers - somewhat improved...
-   If it is a major release (e.g., version x.y.0), create a branch for the bug-fix minor releases.
-   Tag the release source.
-   Create a source release:
    -   Copy the source to a new directory -- avogadro-x.y.z
    -   Run the \`python scripts/gitlog2changelog.py\` to generate a ChangeLog.
    -   Run the scripts/distclean.sh script -- this will remove any un-needed files from the release.
    -   Change the default build type in CMakeLists.txt to Release.
    -   Tar the source directory: \`tar cvjf avogadro-x.y.z.tar.bz2 avogadro-x.y.z\`.
    -   Tar the source directory: \`tar cvzf avogadro-x.y.z.tar.gz avogadro-x.y.z\` - this makes Debian happy.

<!-- -->

-   Add a new release to the SourceForge "File Releases" for Avogadro.
-   Make sure the release is "hidden" at first.
-   Upload the source and any binary packages to SourceForge.
-   Once all files are included in the SourceForge release, mark the release as "Active."
-   Update the SourceForge platform download pages to point to the new release and binaries.

<!-- -->

-   Add News to the SourceForge project page with the release announcement.
-   Add the news announcement to the [Main Page](Main Page "wikilink").
-   Update the [:Category:Releases](:Category:Releases "wikilink") and [Get Avogadro](Get Avogadro "wikilink") pages to mention the new release.
-   Send out an e-mail to all mailing lists.



-   Freshmeat.net
-   Qt-apps.org
-   KDE-apps.org
-   Download.com



-   File writing tests:
    -   Check whether the file is saved.
    -   Does it have the correct suffix?
    -   Is it the molecule you saved?
    -   Any extra temporary files that might have been left behind?
    -   Try at least CML, XYZ and PDB.
        -   New file to a location.
        -   Saving over an old file.
-   File reading tests:
    -   Does the file open successfully?
    -   Is the molecule correct?
    -   Try opening a fragment directly from the shared directory.
    -   Try opening old files -- CML, XYZ, PDB, cube etc.
    -   Try pasting a URL, direct download of a PDB.
-   Check display types and ensure each one renders as expected.
-   Draw a new molecule and perform a geometry optimization.
-   Check each of the tools to ensure correct functionality.
-   Check the extensions for basic functionality.
-   Generally stress test the installed binary to check for any abnormalities.
-   Check that i18n works - French and Chinese are good to try.
-   Ideally check the binaries on one or two other systems.



