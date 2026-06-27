=======================
Video Format Comparison
=======================

In determining which :doc:`format to use for my videos <video>` I evaluated the pros and cons of several formats to compare quality, compatibility, and file size.

(If you want to see what settings I use to convert videos, check out the :doc:`Handbrake <../software/convert/handbrake>` page.)

**More current information can be found on Wikipedia.**

- `Comparison of container formats <https://en.wikipedia.org/wiki/Comparison_of_container_formats>`_
- `List of audio and video codecs <https://en.wikipedia.org/wiki/List_of_codecs>`_

Individual Video Format Comparison Chart
========================================

When comparing video formats, you have to start with the container and then dive into the supported audio and video formats that are allowed in that container.

From a compatibility perspective, a device or player needs to not only support the container format, but also the codec for the stuff inside.

It makes for quite a compatibility matrix issue. I have a lot of sympathy for device hardware and player software manufacturers, trying to be compatible with all of the various cross-connected containers and content formats.

I picked these formats as the initial set to compare given my own personal familiarity with the media I already had and the devices I was trying to use.

+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Criteria                       | Windows Media Video                                            | MPEG                                          | MP4                                                                                 | MKV                                             |
+================================+================================================================+===============================================+=====================================================================================+=================================================+
| Reference Link                 | `ASF <https://en.wikipedia.org/wiki/Advanced_Systems_Format>`_ | `MPG <https://en.wikipedia.org/wiki/MPEG-2>`_ | `MP4 <https://en.wikipedia.org/wiki/MPEG-4_Part_14>`_                               | `MKV <https://en.wikipedia.org/wiki/Matroska>`_ |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| File Extension                 | .wmv                                                           | .mpg                                          | .mp4, .m4v                                                                          | .mkv                                            |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Audio Formats                  | Windows Media Audio                                            | MPEG-1 Layers I, II, III (MP3)                | MPEG-2/4 (HE)-AAC, MPEG-1/2 Layers I, II, III (MP3), AC-3, Apple Lossless, ALS, SLS | Anything                                        |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Video Formats                  | Windows Media Video                                            | MPEG-1, MPEG-2, MPEG-4 Part 2, VC-1, H.264    | MPEG-2 Part 2, MPEG-4 ASP, H.264, H.263, VC-1, Dirac                                | Anything                                        |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Allows Multiple Tracks         | Yes                                                            | Yes                                           | Yes                                                                                 | Yes                                             |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Native iPod/iPad Compatible    | No                                                             | Yes                                           | Yes                                                                                 | No                                              |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Native Android Compatible      | No                                                             | Yes                                           | Yes                                                                                 | No                                              |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+
| Plex Compatible                | Yes                                                            | Yes                                           | Yes                                                                                 | Yes                                             |
+--------------------------------+----------------------------------------------------------------+-----------------------------------------------+-------------------------------------------------------------------------------------+-------------------------------------------------+

**Initially I went for MP4/M4V as my target format** because it was compatible with all of my devices and supported the audio and video formats I wanted to use.

**Currently I am using MKV** because, since the original solution, technology has changed and my use cases have updated - I mostly stream through Plex-enabled devices and those devices work with newer formats.

You can see where I landed on the :doc:`video formats <video>` page: **MKV container / H.265 video / AAC + Passthrough audio**.

The :doc:`Handbrake <../software/convert/handbrake>` page goes into more detail about my specific encoding settings.

Audio in the Video Files
========================
I always have a simpler mixdown track in AAC format as the first track in every file. This allows for better general compatibility (like watching a show without the full home theater surround sound on) without requiring transcoding.

Beyond that, I include the original audio (e.g., DTS-HD, Dolby TrueHD, etc.) as a passthrough track so when I do have the full setup running, I can select that track.

AAC has a surround sound (multichannel) spec but it's not very well supported, so going with a Dolby ProLogic 2 mixdown in AAC as primary is better for compatibility. `At 320kbps, AAC is considered transparent <https://en.wikipedia.org/wiki/Advanced_Audio_Coding>`_; I set the mixdown to 256kbps.

:doc:`Handbrake <../software/convert/handbrake>` has a `surround sound guide <https://trac.handbrake.fr/wiki/SurroundSoundGuide>`_ that explains in more detail how to properly handle multiple tracks.

Subtitles
=========
Subtitles are an area where MKV as a container is far and away superior to MP4. In MKV, you can have multiple subtitle tracks (different languages) that can optionally be displayed by the player as needed, just like with a Blu-ray or DVD player.

With MP4, you get one subtitle track and it gets permanently "turned on" by being "burned" into the video image directly. No special player needed, but far less flexibility.

I include "forced subtitles" in my MKV files by default, plus the primary English track.

Full Disc Images - ISO vs. VIDEO_TS
===================================
My original :doc:`requirements <../requirements>` around media center stuff for discs was to try and keep the disc contents stock/unmodified so I could always burn a new copy if my disc went bad. I also wanted to keep the menus, extras, and so on when watching the movie.

ISO is the most faithful disc image format, but it has a lot more compatibility challenges.

Assuming you're using :doc:`Windows Media Center <../software/deprecated/windowsmediacenter>`, both `MediaPortal <https://www.team-mediaportal.com/>`_ and `My Movies for Media Center <https://www.mymovies.name/>`_ will support ISO playback using Daemon Tools. However, ISO doesn't work for Media Center Extenders like the Xbox 360.

Ideally you'd just store one copy of the movie, but with ISO not working, saving ISO would mean having to save two versions of it - the ISO and a MCE-compatible version. That's way too much space to use up for a single movie.

My Movies has a document talking about `which format to store movies in <https://www.mymovies.name/documentation/whatdvdformattochoose.aspx>`_ in which they recommend VIDEO_TS over ISO. You can also use things like `Transcode360 <https://runtime360.com/projects/transcode-360/>`_ to transcode the VIDEO_TS content for media center extenders.

If you go with VIDEO_TS, you can also use :doc:`XBMC <../software/deprecated/xbmc>` for your front end without a special transcoder. VIDEO_TS opens a lot of doors over ISO.

However, **from an overall compatibility perspective, full disc images lose out over individual movie file formats**, so when :doc:`my goals <../requirements>` changed, I moved away from both ISO and VIDEO_TS.

Device Compatibility References
===============================

- `Xbox 360 <https://support.xbox.com/support/en/us/nxe/gamesandmedia/movies/videofaq/viewvideoplaybackfaq.aspx>`_
- `iPod Classic <https://www.apple.com/ipodclassic/specs.html>`_
- `Playstation 3 <https://manuals.playstation.net/document/en/ps3/current/video/filetypes.html>`_
- `PSP <https://manuals.playstation.net/document/en/psp/current/video/filetypes.html>`_
- `Windows 7 <https://social.technet.microsoft.com/Forums/en-US/w7itpromedia/thread/fbdf8df9-b38c-4419-8a5d-19ee7ed0ef08>`_
- `Container comparisons <https://en.wikipedia.org/wiki/Comparison_of_container_formats>`_
- `Audio codec comparisons <https://en.wikipedia.org/wiki/Comparison_of_audio_codecs>`_
- `Video codec comparisons <https://en.wikipedia.org/wiki/Comparison_of_video_codecs>`_
