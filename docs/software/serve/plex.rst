====
Plex
====
`Plex is a media server and associated set of client apps. <https://plex.tv>`_ I switched to use Plex for things due to the ability to access my media in more places. That means no more storage of full DVD image rips, but that's OK because :doc:`the Synology DS1010+ <../../hardware/server/synologyds1010>` was running out of space and we didn't watch the extra features anyway. The added flexibility of the media is awesome.

The Synology DiskStation Manager has a Plex server package but **the physical machine is not powerful enough to transcode HD video**. Trying to watch home movies proved difficult because they're all HD.

For `a standalone server <https://support.plex.tv/hc/en-us/articles/200375666-Stand-Alone-Server>`_ that serves data off the network and can transcode the HD video you need:

- Intel Core 2 Duo 2.4GHz or better (better if you want more than one transcode op to run at once)
- 2+ GB RAM
- `Network resources properly mounted as drives <https://support.plex.tv/hc/en-us/articles/201122318-Mounting-Network-Resources>`_

**Plex doesn't run as a service** - it's interactive (except when run on the Synology). There are various forum posts about how to get Plex to run as a service or otherwise always start up after rebooting but there's no official solution.

I bought a lifetime `Plex Pass subscription <https://plex.tv/subscription/about>`_ in September 2014 for $75 before they doubled the price to $150. This lets me get the latest server packages early and try out new features, plus I'm happy to support the development effort.
