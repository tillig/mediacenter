=============
Media Formats
=============

Containers vs. Codecs
=====================

Something that was unclear to me when I started my media server project is the difference between a *container* and a *codec*.

A **container** is a file format, a file that can hold audio and/or video data. It's like a bucket - you might have a round bucket or a square bucket, but it's still just a holder for the stuff that goes inside.

A **codec** is the format of the audio or video data that goes in the **container**.

This is an important distinction, because when someone says, "My computer won't play this `MKV <http://en.wikipedia.org/wiki/Matroska>`_ movie," you have to realize that "MKV" is a *container* so the problem may be that the computer doesn't understand how to *look in the container* or it may not understand how to *play the stuff that's in the container*. Those are two different problems.

Some containers have limits on what sort of stuff you can put in them. That's also important to understand.

`Wikipedia has a great comparison of containers and what can go in them. <http://en.wikipedia.org/wiki/Comparison_of_container_formats>`_

.. toctree::

    video.rst
    audio.rst