===============
Home Automation
===============

In July 2017 I picked up a Google Home and started looking into home automation. While turning lights on and off doesn't have much to do with my home media center, there is a lot that goes into integrating media center functionality into a home automation solution. This document has a bunch of my notes in figuring out how to connect everything.


.. contents::
  :local:

Requirements
============

A good place to start is figuring out what I actually want out of home automation... and what I don't really need.

- I want...

  - Voice commands: The ability to turn things on or off, perform actions using voice commands and not just my phone.
  - Light control: Both table/floor lamps as well as overhead lights and fixtures.
  - Temperature control: I have a nice Trane zoned HVAC system that has some automation capabilities I want to tie in.
  - Simple media control: Turn the system on/off, volume control, input control. Maybe "scenes" like "watch a movie."
  - Kid friendly: My media-related remotes can't become useless. Control only through mobile devices or tablets isn't going to work.
  - Blinds/awning: I have a Somfy-based awning that I'd eventually like to tie in.
  - Multiple users: It needs to know the difference between me, my wife, and my kid.

- I don't want...

  - State maintenance: If I turn something on with my voice and turn it off with the remote, I don't want the whole system to go kaput.
  - Big delays: If I ask something to happen, it can't happen three minutes from now.

- I could take or leave...

  - Purchasing ability: When I buy something online I generally want to read reviews and do some price checking. I don't reorder much on a schedule.
  - Shopping lists: We have a phone app called "Mighty Grocery" that is very flexible and we've used it for years. If it integrates with that, great. If it doesn't, that's fine, but I'm not looking to switch to a new shopping list app with fewer options.

Picking an Assistant
====================

There are basically two home assitants out there: Amazon Alexa and Google Home. I didn't consider Cortana because at the time of my research the Harman Kardon Invoke was the only Cortana speaker on the market and it was very new.

Amazon Alexa
------------

Alexa has a slightly nicer set of speakers and an ability to work with multiple Alexa devices across the home. The speakers in the Echo are really nice and have a rich sound - great if you use it to listen to music. The multi-user support is still pretty entry-level. The big sell for Alexa is the ability to easily order things from Amazon.

Now, we do order a lot from Amazon but like I mentioned in the requirements I don't really reorder things much. The stuff I do order, I want to research and see, so voice ordering isn't something I need.

Alexa seems to have a larger set of "skills" or "integrations" than Google Home. It's easier to find Alexa compatible devices than Google Home compatible devices. That may or may not be a good thing; a giant marketplace also sometimes means a flood of mediocre things and difficulty finding things that are good and consistently work. Sort of like app store curation - it's hard to find the good apps amidst a flood of garbage.

Google Home
-----------

Google Home seems to want to be a single device that sits in your home rather than one Google Home in each room. This is getting better with time and you can see that when you have an Android phone - if you say, "OK Google" then the phone recognizes that the Google Home is answering you.

The voice recognition in the Google Home is slightly better than the Alexa. This ties into the multi-user support - it switches users based on voice recognition. This is a big winner for me.

Google Home does make the assumption that many of your things are tied into the Google set of applications - Google Calendar, GMail, etc. That's fine, because both my wife and I are Google users. We have Android phones. We're all in.

Various reviews show that from a general question-asking standpoint, Google Home is also slightly smarter than Alexa. That makes sense because Google is a search company, so searching and returning good results is key.

My Choice: Google Home
----------------------

Despite the reduced set of integrations, we went with the Google Home. The tight integration with Google apps plus the easy multi-user support made it a pretty convincing package.

Automating HVAC
===============

I have a Trane zoned system with a `ComfortLink II XL950 thermostat <https://www.trane.com/residential/en/products/thermostats-and-controls/connected-controls/comfortlink_ii.html>`_. I considered an ecobee or similar replacement for the more robust automation ability but it's not compatible. My HVAC system not only has the zoning, but it also has communication between the heat pump, the furnace, and the air filter. All the components work together to be more efficient. If I wanted the ecobee I'd need to bypass all of the communication... which isn't something I want.

The ComfortLink II XL950 *is* somewhat automated, in that it can connec to `Nexia <http://www.nexiahome.com/>`_. When I first bought the thermostat Nexia wanted $10/month for automation services but has since made it so if you *only* connect the thermostat it's free.

Nexia itself doesn't directly integrate with Google Home, but it does integrate well with `IFTTT <https://ifttt.com>`_. I was able to set up some settings in Nexia that can be triggered by IFTTT.

For example, I have a setting where my downstairs zone gets set so it heats to 68 and cools to 72. In Nexia I named this setting "downstairs home." I then set up IFTTT so if I say, "Set downstairs temperature to home" it triggers the Nexia "downstairs home" configuration and the thermostat settings get updated. The thermostat will have the zone set accordingly and behaves like you put a temporary temperature hold in place - on the next setting change via schedule it'll resume normal settings.

Nexia doesn't really have much richer integration beyond "execute this setting" and that's fine. I don't know how you'd do something as complex as zoned temperature control in an intuitive voice system. It does what I need, and that's good enough.

Automating Media
================

This is where things get a little messy.

At a minimum I need:

- Receiver power, volume, and inputs
- TV power and volume

It'd be *nice* to have more, like the Roku or Xbox One, but I'm not going to go overboard.

**The problem with most media automation solutions is the use of infrared.** Using standard IR remotes means the automation system needs to be the *only* thing that turns on and off components in the system. If you use your regular remote to turn something on, the automation system still thinks it's off since there's no feedback to let the system know you turned the thing on manually.

That goes against one of my requirements - I really can't *only* control this with automation and mobile apps.

What that means, indirectly, is the things I need to control have to be controlled through a programmatic network-based interface. Luckily that will work for at least my TV and receiver:

- The :doc:`Samsung UN65KS8000 TV <../hardware/tv/samsungun65ks8000>` has `an API with decent documentation <http://developer.samsung.com/tv/develop/api-references/>`_.
- The :doc:`Marantz SR5010 Receiver <../hardware/receiver/marantzsr5010>` has `an API with not much doc <https://github.com/tillig/MarantzVolumeMonitor/wiki/Marantz-API>`_ but I have some experience with it, having created `a volume monitor with an Arduino <http://www.paraesthesia.com/archive/2017/03/27/arduino-volume-monitor-for-marantz-receiver/>`_.

The question then becomes how to best communicate with the components through the network.

Logitech Harmony Hub
--------------------

This seems to be a pretty common way to integrate media components with home automation. However, I'm not sure if the Harmony Hub will use the APIs to control the components or if it's only going to use an IR blaster. `I've asked a question about this on the support forums. <https://community.logitech.com/s/question/0D55A0000704D1ESAU/does-the-harmony-hub-control-marantz-receivers-andor-samsung-tvs-via-network>`_ The official answer was, "We are sorry to inform you that, currently, we can’t control Marantz receivers and/or Samsung TVs through the IP."

This basically means Harmony Hub is off the table for me at the time being.

Samsung SmartThings
-------------------

The Samsung SmartThings hub is a more general purpose home automation hub than Harmony Hub and definitely has first-class support for my Samsung TV. However, there isn't direct support for the Marantz receiver.

One thing you can do with SmartThings is write a "SmartApp" that is a plugin for automating other things. `There is already a community SmartApp for controlling Denon network receivers <https://community.smartthings.com/t/re-release-denon-network-av-receivers/80834>`_ and Marantz uses the same API. The source for it `is on GitHub <https://github.com/sbdobrescu/DenonAVR>`_. I may need to `follow this tutorial to create my own version of the app <https://www.youtube.com/watch?v=D6rG4mk164M&feature=youtu.be>`_ but I'm not sure.

There is `a Google Home Helper app <http://thingsthataresmart.wiki/index.php?title=Google_Home_Helper>`_ (`source on GitHub <https://github.com/MichaelStruck/SmartThingsPublic/tree/master/smartapps/michaelstruck/google-home-helper.src>`_) that helps to bridge things Google Home doesn't naturally support (e.g., thermostats) using a SmartApp. The interesting thing about this is that it means you can use SmartApps in a similar manner to devices registered with SmartThings. Unfortunately, there's no way to test it out without actually having a SmartThings hub.

Automating Blinds
=================

Somfy
-----
Somfy seems to work on the 433.42 MHz frequency, which is weird as many RF emitters are 433.93 MHz. The non-standard (proprietary?) frequency along with the communication protocol makes it sort of painful to automate. You can get a `MyLink Hub that CNET didn't review highly, saying it's a bit spendy for what you get <https://www.cnet.com/products/somfy-mylink/review/>`_.

We have a Sunsetter motorized awning that uses a Somfy controller. This is something to consider when looking at a solution for blinds but isn't make-it-or-break-it.

ZRTSI Z-Wave Interface
~~~~~~~~~~~~~~~~~~~~~~

There's a `16-channel Z-Wave interface for Somfy blinds <http://amzn.to/2eLtx1A>`_ that, at the time of this writing, is about $300. That's a little spendy for what you get if you only have one or two motors to drive.

DIY Controller
~~~~~~~~~~~~~~

You can `hook a Raspberry Pi or an Arduino to a Somfy remote <http://www.instructables.com/id/RaspberryPi-Web-Curtain-Controller/>`_ with a little work. Hypothetically I could do something like this and create a SmartThings app or an IFTTT integration to call the controller when needed. A single-channel Somfy remote costs around $40 and an Arduino is like $15. For $55 and some leg work that might be a more affordable way to make things happen as long as I only need a single channel to run.

Other projects to look at for DIY on this:

- `blind-control <http://romor.github.io/blind-control/>`_: Raspberry Pi with a five-channel Somfy remote.
- `Somfy_Remote <https://github.com/Nickduino/Somfy_Remote>`_: Emulate a Somfy remote with an Arduino and a 433.42MHz transmitter.

If I actually get full house blinds on a Somfy system I'd need to reconsider the ZRTSI controller.

Serena Shades
-------------

Given I haven't automated my existing blinds yet, a `Serena Shades solution <https://www.serenashades.com/>`_ may be interesting. They're a Lutron company and should work with Google Home via the Caseta hub. `CNET reviews this well <https://www.cnet.com/products/lutron-serena-remote-controlled-shades/review/>`_ but says the price may be high once you consider the hub you need to get. We'll already be getting that for the lights and using the same hub/protocol is a big win.

After-Market Blind Automation
-----------------------------

The problem with after-market automation is that it generally assumes the blinds are driven by a chain pull; that's not always the case for us.

Automating Lights
=================

There are basically two types of lights to automate - lights that can be handled at the *plug* (like a table lamp); and lights that must be handled at the *switch* (like overhead light fixtures).

Plug-In Lights
--------------

There are a lot of "smart plugs" out there. Plug the smart plug in the wall, connect the lamp to the smart plug.

I like the `TP-Link Smart Plug Mini <http://amzn.to/2uGKb6d>`_. I picked it for a few reasons:

- Reasonable price: Between $25 and $30 for a single unit.
- Brand affinity: TP-Link hasn't let me down in the past.
- Takes one outlet: Some adapters cover a little bit of the second plug in the outlet so you can't plug anything else in.
- Works with Google Home: The TP-Link "Kasa" app connects with Google Home through directly supported integration.

Overhead Lights
---------------

I have standard two-way and three-way switches to accommodate. I'd like all the switches to be the same brand so it's not mix-and-match all over the place and integration is consistent.

Three-way switches are a tricky thing. In a standard switch environment it's easy enough to wire up, but in home control pushing one of the switches needs to let the other switch know the state of the lights (so if you push one switch to turn the lights on you can push the other to turn them off).

I originally considered the `GE Z-Wave switches <http://amzn.to/2uGR0oh>`_. They're affordable and I like that the three-way switches don't require remotes or "auxiliary" switches that use batteries - they're powered right off the wired electrical supply.

However, I'm now thinking the `Lutron Caseta <http://www.casetawireless.com>`_ series of switches and dimmers would be better. Based on reading a lot of reviews like `this one on The Wirecutter <http://thewirecutter.com/reviews/best-in-wall-wireless-light-switch-and-dimmer/>`_ it seems a lot of folks are ending at the same conclusion. It does require a hub to work, but Google Home has first-class integration with it, so I'm not too concerned.
