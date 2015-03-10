===================
DVDFab HD Decrypter
===================

Fixing Folder Structure
=======================

When DVDFab HD Decrypter rips a folder, it leaves a crazy two-level-deep folder structure. Here's a batch file to fix that.

.. sourcecode:: bat

    @echo off
    if .%1. == .. goto :help
    pushd %1
    pushd FullDisc
    for /d %%s in (*) do pushd %%s
    for /d %%s in (*) do move "%%s" ..\..\
    for %%s in (*) do move "%%s" ..\..\
    popd
    popd
    rmdir /s /q FullDisc
    popd
    goto :eof

    :help
    echo This script fixes up DVDFab rip folder structures.
    echo fixmovie [moviefolder]
    goto :eof