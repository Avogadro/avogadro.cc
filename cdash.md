---
layout: default
title: CDash
---

# CDash

The Avogadro project has a CDash [http://www.cdash.org/CDashPublic/index.php?project=Avogadro CDash dashboard](http://www.cdash.org/CDashPublic/index.php?project=Avogadro CDash dashboard "wikilink"), kindly hosted by Kitware. This allows all of our developers to see any configuration and/or compilation errors on the platforms we support. As we add more tests it also allows developers to see the outcome of unit tests.

At a minimum I would like to see daily builds for Linux x86\_64, Linux x86, Mac PPC, Mac x86, Windows x86. Currently Python reports a large number of compilation warnings and so I find it useful to run ctest with and without Python support enabled. On Linux I use ccache to speed up the daily builds quite sigificantly.

As CTest does not currently support Git a script is necessary to perform the update before the tests are run.

Linux
-----

A short script such as the one below should be enough. This box always has an X server running, but it was necessary to set the display variable as it is not set in cron. This runs at 8am EST every day and builds Avogadro with and without Python support.

    export DISPLAY=:0
    cd /home/mhanwell/src/avogadro-anon
    git pull origin master
    ctest -S site.cmake
    ctest -S pythonsite.cmake

The site.cmake I use for the build with Python support is shown below.

    SET (CTEST_SOURCE_DIRECTORY "/home/mhanwell/src/avogadro-anon")
    SET (CTEST_BINARY_DIRECTORY "/home/mhanwell/build/avogadro-ctest")

    SET (CTEST_UPDATE_COMMAND "/usr/bin/git")
    SET (CTEST_CVS_UPDATE_OPTIONS "pull")
    #SET (CTEST_CVS_CHECKOUT "${CTEST_CVS_COMMAND} clone git://github.com/cryos/avogadro.git \"${CTEST_SOURCE_DIRECTORY}\"")

    # which ctest command to use for running the dashboard
    SET (CTEST_COMMAND
            "/usr/bin/ctest -D Experimental"
    )

    # what cmake command to use for configuring this dashboard
    SET (CTEST_CMAKE_COMMAND
            "/usr/bin/cmake"
    )

    ####################################################################
    # The values in this section are optional you can either
    # have them or leave them commented out
    ####################################################################

    # should ctest wipe the binary tree before running
    SET (CTEST_START_WITH_EMPTY_BINARY_DIRECTORY TRUE)

    # this is the initial cache to use for the binary tree, be careful to escape
    # any quotes inside of this string if you use it
    SET (CTEST_INITIAL_CACHE "ENABLE_TESTS:BOOL=ON
    ENABLE_GLSL:BOOL=ON
    ENABLE_PYTHON:BOOL=ON
    BUILDNAME:STRING=Gentoo Linux x86_64 GCC 4.3.3 with Python support
    SITE:STRING=IRIDIUM.cryos
    CVSCOMMAND:FILEPATH=/usr/bin/git
    MAKECOMMAND:STRING=make -j5
    ")
    # set any extra envionment varibles here
    SET (CTEST_ENVIRONMENT
    )

Windows
-------

This was perhaps the most difficult to set up. The main issue is setting up the environment so that the compiler can be found, and all necessary DLLs. Below is the script I use to run the test suite on a Windows XP virtual machine. The paths will need to be adjusted for your particular set up.

    @echo off

    echo "Setting up environment..."
    @call "C:\Program Files\Microsoft Visual Studio 9.0\VC\vcvarsall.bat"

    @set PATH=C:\qt\4.5.0\bin;C:\src\openbabel-2-2-x\build\bin;C:\src\openbabel-2-2-x\windows-vc2005;"C:\Program 
    Files\Git\bin";%PATH%

    cd C:\src\avogadro
    git.exe pull origin master
    echo "Attempting to run ctest..."
    ctest.exe -V -S site.cmake

Scheduled tasks can be set up to run the above script if you save it with the .bat file extension. It seems that you can only set up a scheduled task on Windows XP if you have set a password for the user. Other than that the above script works. The site.cmake used on my Windows VM is pasted below, again paths need to be adjusted for your set up.

    SET (CTEST_SOURCE_DIRECTORY "C:/src/avogadro")
    SET (CTEST_BINARY_DIRECTORY "C:/src/avogadro-ctest")

    SET (CTEST_CVS_COMMAND "/usr/bin/git")
    SET (CTEST_CVS_CHECKOUT "${CTEST_CVS_COMMAND} clone git://github.com/cryos/avogadro.git \"${CTEST_SOURCE_DIRECTORY}\"")

    # which ctest command to use for running the dashboard
    SET (CTEST_COMMAND
        "C:/Program Files/CMake 2.6/bin/ctest -D Experimental"
    )

    # what cmake command to use for configuring this dashboard
    SET (CTEST_CMAKE_COMMAND
        "C:/Program Files/CMake 2.6/bin/cmake"
    )

    ####################################################################
    # The values in this section are optional you can either
    # have them or leave them commented out
    ####################################################################

    # should ctest wipe the binary tree before running
    SET (CTEST_START_WITH_EMPTY_BINARY_DIRECTORY TRUE)

    # this is the initial cache to use for the binary tree, be careful to escape
    # any quotes inside of this string if you use it
    SET (CTEST_INITIAL_CACHE "ENABLE_TESTS:BOOL=ON
    ENABLE_GLSL:BOOL=OFF
    ENABLE_PYTHON:BOOL=OFF
    OPENBABEL2_INCLUDE_DIR:PATH=C:/src/openbabel-2-2-x/include
    OPENBABEL2_LIBRARIES:PATH=C:/src/openbabel-2-2-x/build/src/openbabel-2.lib
    EIGEN2_INCLUDE_DIR:PATH=C:/src/eigen2
    MAKECOMMAND:STRING=nmake -i
    CMAKE_MAKE_PROGRAM:FILEPATH=nmake
    CMAKE_BUILD_TYPE:INTERNAL=Release
    CMAKE_GENERATOR:INTERNAL=NMake Makefiles
    BUILDNAME:STRING=Windows XP x86_32 Visual C++ 2008
    SITE:STRING=WINXP.cryos
    CVSCOMMAND:FILEPATH=/usr/bin/git
    ")
    # set any extra envionment varibles here
    SET (CTEST_ENVIRONMENT
    )

