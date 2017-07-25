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