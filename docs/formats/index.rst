=============
Media Formats
=============

.. toctree::

    video.rst
    audio.rst
    videocompare.rst

Physical vs. Digital
====================

Obviously in a media center/networked solution you have to stream digital media - you can't really "stream a disc" across a network.

That said, **I usually purchase any media - audio or video - in a physical format.** I do that for several reasons:

- **DRM**: `DRM, or Digital Rights Management <https://en.wikipedia.org/wiki/Digital_rights_management>`_, is the copy protection technology used on digital media to stop piracy. The problem with DRM on digital media is that it causes incompatibility with different devices. For example, if I purchase a movie on iTunes, the DRM on the movie requires me to play the movie on an Apple device - I can't stream it through :doc:`Plex <../software/serve/plex>`. I can't copy it onto my Android phone and play it.
- **Portability**: Some digital-only media sources make the assumption that you'll always have network bandwidth to get your data. You can't download the movie to your device. If you can, you're required to use a specific player to access the movie - DRM, right?
- **Quality**: It wasn't that long ago when most MP3s you could get were 128kbps (medium quality). That's not awesome. I want high quality content. I don't mind if I have to downscale for certain formats, but while I can't tell the difference in quality on my crappy phone speaker, if I'm playing that content on my home stereo, I totally can.
- **Format fluency**: There was a time before H.264 when movies were mostly MPEG-2 format. DVD movies still are. As formats change and improve, if I only have a digital copy of the content I don't have the ability (without loss) to convert from one format to another. If I have the disc, I can re-rip the content at its original quality and convert directly to the new format.

This isn't all-or-nothing. I do have some albums I've bought from Amazon or Google that are MP3 format only. They provide some decent high-quality stuff (256kbps) where I admittedly don't notice the difference between that and a lossless copy. In this case, the only thing I'm really losing is the format fluency. Video services aren't here yet, though, so I don't have any digital-only videos outside of home movies.

I recognize that some folks are probably trying to go for a "digital-only" life with no physical media at all. I don't mind storing discs out of the way if it gives me the freedom to do what I want with my media. If you can live with the restrictions that come with digital-only, more power to you.

Containers vs. Codecs
=====================

Something that was unclear to me when I started my media server project is the difference between a *container* and a *codec*.

A **container** is a file format, a file that can hold audio and/or video data. It's like a bucket - you might have a round bucket or a square bucket, but it's still just a holder for the stuff that goes inside.

A **codec** is the format of the audio or video data that goes in the **container**.

This is an important distinction, because when someone says, "My computer won't play this `MKV <https://en.wikipedia.org/wiki/Matroska>`_ movie," you have to realize that "MKV" is a *container* so the problem may be that the computer doesn't understand how to *look in the container* or it may not understand how to *play the stuff that's in the container*. Those are two different problems.

Some containers have limits on what sort of stuff you can put in them. That's also important to understand.

`Wikipedia has a great comparison of containers and what can go in them. <https://en.wikipedia.org/wiki/Comparison_of_container_formats>`_

`MediaInfo <https://mediaarea.net/en/MediaInfo>`_ is a great piece of software to help you look at media files and figure out what's actually in them.
