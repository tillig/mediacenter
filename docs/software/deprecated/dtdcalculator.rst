==============
DTD Calculator
==============
This is a tool that allows you to set up custom resolutions for Intel graphics chipsets based on VESA timing information. This is key in trying to run the :doc:`Dell Studio Hybrid <../../hardware/dellstudiohybrid>` full screen for :doc:`Windows Media Center <windowsmediacenter>`. After switching away from WMC and changing the TV the Studio Hybrid was attached to, I didn't need to use this tool.

`DTD Calculator is maintained and discussed in AVSForum <http://www.avsforum.com/avs-vb/showthread.php?t=947830>`_. There is a lot of great information there and people will help out if things don't seem to work.

`You can download DTD Calculator from Clever Technologies. <http://www.clevertec.co.uk/productsfree.htm#dtdcalc>`_ There's a `forum here <http://www.mp3car.com/vbulletin/lcd-display/115373-800x480-solution-intel-graphics.html>`_ talking about how you might use it to fix resolution issues.

My usage sounds like:

* Install `MonInfo <http://www.entechtaiwan.com/util/moninfo.shtm>`_.
* Install DTD Calculator.
* Get the EDID info from MonInfo and paste it into DTD Calculator. If it'll do the full res, great; if not, try one of the other modelines.

There is a modeline database at MythTV that `has some Sharp modelines I could try in DTD Calculator <http://www.mythtv.org/wiki/index.php/Modeline_Database#Sharp>`_. There's 1360 x 768, not 1366 x 768, but that might be the way to go. This one is for the LC-40C32U. I have :doc:`LC-37D7U <../../hardware/sharpaquoslc37d7u>`, but it might work.

.. sourcecode:: none

    ## with ubuntu edgy's x.org and the nvidia 8776 drivers, a simple mode of "1360x768" works without
    ## the custom modeline
    #Section "Monitor"
    #        Identifier      "Sharp LC-40C32U"
    #        HorizSync       24-62
    #        VertRefresh     49-76
    #
    #        modelines from the web generator at
    #        http://xtiming.sourceforge.net/cgi-bin/xtiming.pl
    #        Modeline "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807
    #
    #        EDID-derived modelines
    #        ModeLine "1360x768@60" 85.5 1360 1424 1536 1792 768 771 777 795 +hsync +vsync
    #EndSection