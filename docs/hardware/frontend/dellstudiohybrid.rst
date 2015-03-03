==========================
Dell Studio Hybrid
==========================

The Dell Studio Hybrid is a small form factor PC that I use as a media center front end. It's pretty under-powered and is one of those models that came and went quickly. It's hard to find updated drivers for it and has odd HDMI issues occasionally.

Now that there's a :doc:`Plex <../../software/plex>` app for :doc:`Xbox 360 <xbox360>` and :doc:`Playstation 3 <ps3>` I don't really use this anymore. I will probably repurpose it.

Display Resolution
==================

I used to have a display resolution issue when the Dell Studio Hybrid was hooked up to the :doc:`Sharp Aquos TV <../tv/sharpaquoslc37d7u>`. It ran at 1280 x 768, which left a letterbox on each side since the Sharp Aquos TV we have runs at 1366 x 768 natively. This problem went away when I connected it via HDMI to the :doc:`Samsung LN52A750 TV <../tv/samsungln52a750>` we got - now it runs at full 1080p.

* Most TVs don't accept more than 720p through VGA/DVI, which we found while figuring out how to hook up the :doc:`Xbox 360 <xbox360>` (though that may have changed with newer TVs).
* Different resolutions become available when you hook the computer up to the TV using the HDMI connection. I tried this with the Sharp Aquos and found that 1080i became available (though it didn't display nicely - that could have been due to the TV not understanding the input right). That wasn't available through the DVI hookup.
* The Dell Studio Hybrid uses an `Intel X3100 graphics processor on GM965 chipset <http://www.intel.com/products/notebook/chipsets/GM965/GM965-overview.htm>`_. `I tried asking a question on The Green Button <http://thegreenbutton.com/forums/3/297610/ShowThread.aspx>`_ about whether the HD resolution was unavailable because I was using DVI but didn't get any response.
* A tool called :doc:`DTD Calculator <../../software/deprecated/dtdcalculator>` enables easier manipulation of DTD values and doesn't require all the work that is mentioned in the article.

Problem: DVD Causing AppCrash
=============================
I found that the DVDs "`Christmas Vacation <http://www.amazon.com/dp/B000VBIGD6?tag=mhsvortex>`_" and "`A Christmas Story <http://www.amazon.com/dp/B0000AYJUW?tag=mhsvortex>`_" both cause Windows Media Center and Windows Media Player to crash on this machine. `I posted to the Intel forums about the issue <https://communities.intel.com/message/78182#78182>`_ but never received a response.

Problem: Machine Sleep is Unpredictable
=======================================
There are forums upon forums about sleep problems with Windows. With this machine I've had both a problem where the machine *won't* go to sleep and a problem where the machine would go to sleep but wake up for no reason.

I fixed it by turning the amount of time until the machine goes to sleep down to 10 minutes and picking a different screen saver ("Bubbles").

Problem: HDMI Handshake/Signal Loss
===================================
I had been using VGA video, but a new problem appeared once I started HDMI - if the display turns off (or the machine goes to sleep) while the TV is off, the TV will never get the signal again once you wake the computer up. As it turns out, the signal only seems to be lost if :doc:`Windows Media Center <../../software/deprecated/windowsmediacenter>` is running full screen; if it's minimized, I don't see the issue. Some people report this as an "EDID handshake" problem but I'm not thinking it's what I'm seeing.

I tried fixing it by not letting the machine ever sleep, but that doesn't seem to be 100%.

**What fixed it**: `I purchased an HDMI switcher. <http://www.amazon.com/dp/B00B46XUQU?tag=mhsvortex>`_ `This blog entry <http://www.edbott.com/weblog/?p=2480>`_ pointed me to that. Somehow the switcher is able to keep the signal going, and if anything disconnects I can switch the HDMI signal away and back to the PC and it reconnects.

**Things that don't work**:

- Switching the ACPI sleep mode from S3 to S1.
- Changing resolution via command line.  `There is a guy on this forum <http://www.xpmediacentre.com.au/community/vista-media-center-software/20373-vmc-dvi-hdmi-blank-screen-after-tv-power-off-fix.html>`_ who uses "MultiRes" and a batch script to "wake up" the signal. I tried this using the `12noon program Display Changer <http://www.12noon.com/index.htm>`_, previously Resolution Changer, with no luck.
- `Folks in AVSForum <http://www.avsforum.com/avs-vb/showthread.php?t=1013888>`_ have used a thing called `DVI Detective <http://www.amazon.com/dp/B0002CZJ8O?tag=mhsvortex>`_ to get past this, but it seems to have problems in inexplicable ways and reading the product description, doesn't look like it's for me.

There's a guy who wrote `a program "hdmiOn" <http://thydzik.com/hdmion-a-solution-to-loss-of-dvi-video-epid-signal-on-hd-tvs/>`_ that you can assign to a hot key and it turns the monitor off/on - ostensibly that should fix it, but some commenters say it doesn't work. I didn't try that.

I did start a question `in the Microsoft Answer Forums <http://social.answers.microsoft.com/Forums/en-US/vistamedia/thread/2211c68c-d58b-42bd-964d-9694dc761be4>`_ on this. I've also posted the question at `The Green Button forums <http://thegreenbutton.com/forums/4/350763/ShowThread.aspx>`_. On the Microsoft Answer Forums, the tech there said it sounds like a video card driver issue. No updated drivers have fixed it thus far.

Problem: Slow Wireless Speed
============================
The Intel 1505 WLAN wireless G card included in the box is really slow to connect to the network.

There is `some doc on configuring it on the Dell site <http://support.dell.com/support/edocs/network/p70008/EN/props.htm>`_.

I experimented with the settings on the card without luck; eventually I switched to an external wireless-N adapter (and, later, to a wired connection).

Original settings here - I'll make changed settings **bold**.

- 802.11h+d: Loose 11h
- Afterburner: Disabled
- Antenna Diversity: Auto
- AP Compatibility Mode: Higher Performance
- Band Preference: None
- Bandwidth Capability: 11a:20/40;11bg:20MHz
- Bluetooth Collaboration: Enable
- BSS Mode: 802.11n Mode
- Disable Bands: None
- Disable Upon Wired Connect: Disabled
- Fragmentation Threshold: 2346
- IBSS 54g(tm) Protection Mode: Auto
- IBSS Mode: 802.11b Only **802.11 a/b/g/n Auto**
- Locally Administered MAC Address: Not Present
- Location: USA
- Minimum Power Consumption: Enabled
- PLCP Header: Auto (Short/Long)
- Priority & VLAN: Priority & VLAN Disabled
- Rate (802.11a): Best Rate
- Rate (802.11b/g): Best Rate
- Roam Tendency: Moderate
- Roaming Decision: Default
- RTS Threshold: 2347
- Wake-Up Mode: Magic & WakeUp Frame
- WMM: Auto
- WZC IBSS Channel Number: 11(20MHz)
- XPress (TM) Technology: Disabled

Problem: One Pixel Overscan Line
================================
In a continued weirdness with the video driver, every once in a while I see a one pixel "line" along the right side of the TV when watching video. It's not a showstopper, but it sure is distracting. I've started `a forum post on the Green Button <http://thegreenbutton.com/forums/p/81192/403439.aspx#403439>`_ for this. There is `another thread <http://thegreenbutton.com/forums/p/80771/401486.aspx#401486>`_ that talks about `a hotfix for this <http://support.microsoft.com/default.aspx/kb/974324>`_. I didn't try it because, after switching away from :doc:`Windows Media Center <../../software/deprecated/windowsmediacenter>`, the issue went away.