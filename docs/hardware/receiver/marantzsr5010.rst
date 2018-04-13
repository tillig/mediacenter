==============
Marantz SR5010
==============

The Marantz SR5010 was `picked up from Amazon for about $900 <http://www.amazon.com/dp/B010FH2J9W?tag=mhsvortex>`_ in March 2016 as a replacement for the :doc:`Yamaha RX-V777BT <../deprecated/yamaharxv777bt>`.

.. image:: marantzsr5010.jpg

General Overview
================

This is my first Marantz receiver and while I admittedly wasn't initially fond of the look of the unit, the setup and on-screen menu system is by far one of the easiest and most straightforward I've encountered.

This is the second unit I've had that's had the HDMI passthrough feature allowing you to use the receiver as a video switcher without keeping the unit turned on. I'm guessing this is a common feature now, but it's the little things like this that make it.

It's a native DLNA receiver so Bluetooth connectivity is less interesting than just "playing to" the receiver. You can cast audio or video at it without issue. (You can connect to it with Bluetooth if you want, however.)

One thing I've noticed is that when it displays 4K content no on-screen display comes up. This includes the volume/source overlay information. It's really difficult to see the volume level without that.

Network Control
===============

With the receiver in the cabinet and the 4K on-screen display problem mentioned earlier, I needed a way to see when the receiver was on, which source it was tuned to, and the volume level.

To that end, I `created an Arduino-based volume monitor <http://www.paraesthesia.com/archive/2017/03/27/arduino-volume-monitor-for-marantz-receiver/>`_ that uses the HTTP network interface for the receiver.

In April 2018 a firmware update came through that caused the network communication - both HTTP and Telnet based - to be unstable. Even streaming music services don't stream well. The network connection seems to reset periodically. I've opened a support ticket for the issue but it effectively renders the volume monitor useless.