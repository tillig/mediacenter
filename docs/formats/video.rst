=============
Video Formats
=============

In choosing a video format, I went through a :doc:`video format comparison and evaluation <videocompare>` process to figure out what was best for me.

Below is the current video format information; if you're interested in why I chose them, :doc:`check out the video format comparison <videocompare>`.

H.264 Video / AAC + AC3 Passthrough Audio / MP4 Container
=========================================================
As part of my switch to :doc:`Plex <../software/plex>` for my media center server software, I also switched away from ``VIDEO_TS`` video format to individual movie files using:

- H.264 video codec
- AAC audio for the primary track codec
- Native (AC3, DTS, etc.) audio for a secondary passthrough track
- MP4 (with an ``.m4v`` extension) container

I chose this format for three reasons:

- **High compatibility**: The MP4 container with H.264 video and AAC audio can be played by pretty much all of my devices.
- **Video quality vs. file size balance**: H.264 video has good compression for the quality it retains and, based on your settings, you can get a file half the size of the MPEG-2 equivalent but with comparable quality.
- **Audio quality**: While the MP4 container format doesn't really specify support for anything beyond AAC audio, you can embed additional tracks and many popular players (including :doc:`Plex <../software/plex>`) know how to deal with it. This allows you to put in a primary AAC stereo track for compatibility with mobile devices and standard players; and a secondary "passthrough" track with the original, unchanged audio for full surround.

I use :doc:`DVDFab HD Decrypter <../software/dvdfab>` and :doc:`MakeMKV <../software/makemkv>` for ripping content from discs.

I use :doc:`Handbrake <../software/handbrake>` to convert the ripped disc content into the target format. The :doc:`Handbrake page <../software/handbrake>` shows the custom settings I use for video conversion.

VIDEO_TS Disc Image
===================
``VIDEO_TS`` isn't really a "format" in the classic sense.

When you use a tool like :doc:`DVDFab HD Decrypter <../software/dvdfab>` to rip the content from a disc onto a hard drive and you want a full disc image - no compression or conversion - you have two choices. You can either get a literal byte-for-byte image in ``.iso`` format or you can get the *files* from the disc in their native directory structure.

If you choose the files in their directory structure, the directory that comes out is called ``VIDEO_TS``. Inside that are a bunch of files with the extension ``.vob`` that are, basically, MPEG-2 video files.

I used ``VIDEO_TS`` format originally in combination with :doc:`XBMC <../software/deprecated/xbmc>` to both back up my movies and serve them at their original, unchanged fidelity.

However, MPEG-2 video is poor compression and eats up space. Also, you have to use a smarter media front-end like :doc:`XBMC <../software/deprecated/xbmc>` to play a disc image in ``VIDEO_TS`` format because it means the front-end must emulate a DVD player. Thus - it's far less portable than other formats.

When my :doc:`media center goals <../requirements>` changed to go for more portability, I moved away from ``VIDEO_TS``.