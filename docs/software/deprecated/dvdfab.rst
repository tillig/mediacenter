===================
DVDFab HD Decrypter
===================

`DVDFab HD Decrypter <https://www.dvdfab.cn/hd-decrypter.htm>`_ is a great free tool for ripping DVD and Blu-ray content. It can do a lot of stuff if you opt in to the paid version, including movie conversion like :doc:`Handbrake <../convert/handbrake>`.

I used this for a while when I was still ripping VIDEO_TS format. This wasn't sustainable as I moved to more Blu-ray movies, so I stopped using it.

:doc:`MakeMKV <../rip/makemkv>` is great at grabbing individual MKV files based on disc titles, but DVDFab HD Decrypter is sometimes easier to use when it comes to complex copy protection and more one-click operation.

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
