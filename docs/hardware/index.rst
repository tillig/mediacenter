==================
Hardware / Devices
==================

There's a lot of hardware that goes into my media center. While some of it provides multiple functions, all of it plays a role on some level.

Here's a photo of my current server rack in my office. Most of these are discussed on the :doc:`server <server/index>` page, but there's some :doc:`network <network/index>` hardware in there as well as :doc:`a UPS <power/index>`.

.. image:: servers_small.jpg

:download:`Click for a larger view. <servers.jpg>`

From top to bottom, left to right, you see...

- :doc:`Synology DS1010+ <server/synologyds1010>`, which provides all storage.
- A `Lutron hub <https://www.casetawireless.com/>`_, an `Akita <https://www.akita.cloud/>`_, and a `SmartThings hub <https://www.smartthings.com/products/smartthings-hub>`_ for home automation/IoT work.
- :doc:`Tablo <server/tablo>`, which handles over-the-air DVR services.
- :doc:`Ubiquiti UniFi Security Gateway <network/ubiquiti>` (the white square with the blue light) as the main firewall/entry from the outside for internet.
- :doc:`CyberPower CP1500AVRLCD <power/index>`, the UPS that most (but not all) of this is plugged into.
- A USB hard drive where :doc:`Megaplex <server/megaplex>` gets backed up.
- :doc:`HP ProCurve 2810-24G switch <network/switches>`, connecting these together and linking back to the main network.
- :doc:`Megaplex <server/megaplex>`, my custom dedicated Plex server.

For more detail on any of these things or items in the system that aren't pictured, dig in here.

.. toctree::
    :maxdepth: 2

    frontend/index.rst
    server/index.rst
    network/index.rst
    tv/index.rst
    receiver/index.rst
    speakers/index.rst
    power/index.rst
    deprecated/index.rst
