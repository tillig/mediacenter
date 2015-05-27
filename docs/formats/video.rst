=============
Video Formats
=============

In choosing a video format, I went through a :doc:`video format comparison and evaluation <videocompare>` process to figure out what was best for me.

(If you want to see what settings I use to convert videos, check out the :doc:`Handbrake <../software/convert/handbrake>` page.)

Below is the current video format information; if you're interested in why I chose them, :doc:`check out the video format comparison <videocompare>`.

H.264 Video / AAC + AC3 Passthrough Audio / MP4 Container
=========================================================
As part of my switch to :doc:`Plex <../software/serve/plex>` for my media center server software, I also switched away from ``VIDEO_TS`` video format to individual movie files using:

- H.264 video codec
- AAC audio for the primary track codec
- Native (AC3, DTS, etc.) audio for a secondary passthrough track
- MP4 (with an ``.m4v`` extension) container

I chose this format for three reasons:

- **High compatibility**: The MP4 container with H.264 video and AAC audio can be played by pretty much all of my devices.
- **Video quality vs. file size balance**: H.264 video has good compression for the quality it retains and, based on your settings, you can get a file half the size of the MPEG-2 equivalent but with comparable quality.
- **Audio quality**: While the MP4 container format doesn't really specify support for anything beyond AAC audio, you can embed additional tracks and many popular players (including :doc:`Plex <../software/serve/plex>`) know how to deal with it. This allows you to put in a primary AAC stereo track for compatibility with mobile devices and standard players; and a secondary "passthrough" track with the original, unchanged audio for full surround.

I use :doc:`DVDFab HD Decrypter <../software/rip/dvdfab>` and :doc:`MakeMKV <../software/rip/makemkv>` for ripping content from discs.

I use :doc:`Handbrake <../software/convert/handbrake>` to convert the ripped disc content into the target format. The :doc:`Handbrake page <../software/convert/handbrake>` shows the custom settings I use for video conversion.

Something I did notice as I moved away from ``VIDEO_TS`` into a new, "standalone file" sort of format, is that audio/video sync sometimes got off somewhere so lip sync was visibly bad. Sometimes this is due to the source material being bad already; other times it had to do with frame rate issues. :doc:`I talk more about lip sync on the Handbrake page. <../software/convert/handbrake>`

I will say that, from a container perspective, subtitles is an area where MKV definitely outshines MP4 - MKV allows multiple subtitle tracks, just like a regular disc; MP4 only gives you one, and whichever one you choose is "permanently turned on." :doc:`I talk more about how I handle subtitles on the Handbrake page. <../software/convert/handbrake>`

I gathered some general statistics after I finished the mass conversion of all of my media using :doc:`Handbrake <../software/convert/handbrake>` that may help you gauge how much space you need. This is using the settings outlined on the :doc:`Handbrake <../software/convert/handbrake>` page.

- Total number of files: 4998
- Total content runtime: 134 days, 8 hours, 56 minutes, 47 seconds
    - SD runtime: 115 days, 12 hours, 25 minutes, 17 seconds
    - HD runtime: 18 days, 20 hours, 31 minutes, 30 seconds
- Total file size: 5182.3GB
    - SD file size: 3042.04GB
    - HD file size: 2140.26GB
- Average MB/minute for SD content: 18.73
- Average MB/minute for HD content: 80.72

VIDEO_TS Disc Image
===================
``VIDEO_TS`` isn't really a "format" in the classic sense.

When you use a tool like :doc:`DVDFab HD Decrypter <../software/rip/dvdfab>` to rip the content from a disc onto a hard drive and you want a full disc image - no compression or conversion - you have two choices. You can either get a literal byte-for-byte image in ``.iso`` format or you can get the *files* from the disc in their native directory structure.

If you choose the files in their directory structure, the directory that comes out is called ``VIDEO_TS``. Inside that are a bunch of files with the extension ``.vob`` that are, basically, MPEG-2 video files.

I used ``VIDEO_TS`` format originally in combination with :doc:`XBMC <../software/deprecated/xbmc>` to both back up my movies and serve them at their original, unchanged fidelity.

However, MPEG-2 video is poor compression and eats up space. Also, you have to use a smarter media front-end like :doc:`XBMC <../software/deprecated/xbmc>` to play a disc image in ``VIDEO_TS`` format because it means the front-end must emulate a DVD player. Thus - it's far less portable than other formats.

When my :doc:`media center goals <../requirements>` changed to go for more portability, I moved away from ``VIDEO_TS``.

AVCHD / MTS / M2TS
==================
I first encountered this format when I bought an HD camcorder. At that point it was sort of difficult to deal with - not much would play it directly and I spent some time trying to figure out how best to store it as something more compatible.

As it turns out, **this is the same format in which Blu-ray discs are stored**. More things play the format natively now, but I still end up converting these files (from my Blu-ray discs and my camera) into MP4 files. :doc:`Handbrake <../software/convert/handbrake>` is the way to go for conversion here.

For home movie editing in this format, I use `Sony Vegas <http://www.sonycreativesoftware.com/vegassoftware>`_. I save my edited movies as MP4.