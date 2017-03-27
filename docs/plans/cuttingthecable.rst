=================
Cutting the Cable
=================

Starting around January 2015 I started looking at ways to save some money by cutting cable from the :doc:`Comcast <../network/providers/comcast>` "triple-play" internet/phone/cable down to just internet service. I didn't want to lose features or content (if possible) so this is the plan I went through to try and replace those items. **We executed this plan in July 2015.**

.. contents::
  :local:

Features
========
The full system currently has:

- DVR/recording capability. We don't watch TV on a schedule, so the ability to time-shift is important.
- Local programming. Not just stuff that gets relayed through online services, but local news and such.
- Wide variety of content. Standard broadcast and cable networks.
- Ability to watch content from different devices. Most of the time it's on one of the TVs in the house but sometimes we want some mobile abilities.

Hardware
========

We'll be losing the cable boxes, but we need to make sure we can get content to the various TVs in the house. In order to do that, we'll need to invest in some hardware. Which hardware depends on which features we want.

Antenna
-------
The antenna will be required to get access to the local content and some national broadcast content.

There is a choice between indoor and outdoor antennas. `There is a great article on Crutchfield talking about how to choose a good antenna. <http://wwv.crutchfield.com/learn/learningcenter/home/antenna.html>`_ The short version is that outdoor antennas will perform better than the best of indoor antennas because the size and amplification power. You can mount an outdoor antenna on the side of your house (like where the satellite dish used to be) or in the attic (crawlspace above our room).

AntennaWeb.org shows you what channels are available and recommends antenna types (by some sort of a color-code). `Here's the recommendation for us: mostly "yellow" color channels. <http://www.antennaweb.org/Stations.aspx?Address=&City=Hillsboro&State=OR&ZIP=97124&Housing=S&Accuracy=4&Height=6&Obstructed=False&StationList=&Lat=45.5442824&Lon=-122.9521023>`_ This indicates a "small, multi-directional antenna" should work for us. Everything seems to be within ~12 miles.

Picking an Antenna
~~~~~~~~~~~~~~~~~~
If you go with an outdoor antenna, you can hook it up to the same place where the cable comes into the house and it serves the whole house. Indoor antennas have to be per-TV because they are not very strong. **We should go with an outdoor antenna.**

These antennas are "omni-directional" so you don't have to point it in a given direction to adjust for signal. There are some motorized directional antennas for about the same price; and there are directional antennas you can go aim on the roof that are closer to the $30 - $50 range.

- `Winegard FL6550A FlatWave Air Outdoor HDTV Antenna <http://www.amazon.com/dp/B00E5Z3R6A?tag=mhsvortex>`_ ($78)
- `AmazonBasics 60-mile range antenna <http://www.amazon.com/dp/B00MFXNQBU?tag=mhsvortex>`_ ($120)
- `Spectrum2 DTV Motorized Outdoor Indoor TV Antenna SP213 <http://www.spectrumantenna.com/ProductDetails.asp?ProductCode=SP2&Click=564>`_ ($65)
- `ChannelMaster CM 3000 SMARTenna <http://www.amazon.com/dp/B000BSKO84?tag=mhsvortex>`_ ($52)

Wiring the Antenna
~~~~~~~~~~~~~~~~~~
The :doc:`Comcast <../network/providers/comcast>` cable enters the house at one point from the outside. The coax on the inside of the house only carries Comcast signal. The cable modem is hooked to one of these coax outlets and converts that signal to internet. With cable boxes, the other TVs are hooked to other coax outlets and the cable box converts the same signal into TV.

There's a junction box on the side of the house where the Comcast cable feed connects to a splitter and makes it to the rest of the house. I ran a separate coax feed directly from that junction box into the office. When it's time to cut over to the antenna, the Comcast feed will tie directly into that dedicated office coax and the antenna will connect to the splitter.

The initial plan doesn't include an amplifier at the antenna but may need to be put in later.

Initial Result: ChannelMaster CM 3000 SMARTenna
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The flat antennas look nice, like a small satellite. :doc:`The ChannelMaster CM 3000 SMARTenna seems as good as any for the requirements we have. <../hardware/deprecated/cm3000>` A good balance of cost and power.

Antenna Follow-Up
~~~~~~~~~~~~~~~~~
After installing a ChannelMaster CM 3000 SMARTenna, I found that the signal in our area is pretty good on clear days but inteference appears in any poor weather conditions. Other folks in my general area have had lots of luck with this and smaller antennas, but I think living somewhat close to an airport adds to my interference levels.

I ended up switching to a :doc:`ClearStream 2V HDTV antenna <../hardware/network/clearstream2v>` mounted in my attic and it produces a much better signal.

Home Network
------------
Other than live TV, all content will get to TVs via a networked device (e.g., :doc:`Chromecast <../hardware/frontend/chromecast>` or :doc:`Xbox <../hardware/frontend/xbox>`). We'll want a good home network connection in all the rooms to ensure good signal.

**Wired network is always better than wireless** because you don't fight interference, but not all devices are wired. Phones, tablets, and Google Chromecast do not have wires, so improving the wireless network may be beneficial even if all the TV devices (Xbox, PS3) do have wires.

Improving Wireless
~~~~~~~~~~~~~~~~~~
To improve the wireless signal we need to add a wireless access point upstairs. From most research this appears to be a simple thing to do.

I tried a second wireless access point (using a :doc:`DAP-1522 <../hardware/deprecated/dap1522>`) to the house upstairs so we should have better wifi all around. I'm using the same SSID and password/encryption so wireless roaming is in effect.

That worked well for some time, but I found the wireless roaming caused weird issues sometimes on mobile devices when you were standing in certain areas of the house where the device had a hard time picking an access point. I ended up upgrading to a :doc:`a Netgear Nighthawk X6 AC3200 tri-band router (model R8000) <../hardware/network/netgearr8000>` to solve my range issues.

At some later time I may consider putting in a more powerful access point to just serve the whole house from one location. The `Ubiquiti Networks UniFi AP Enterprise WiFi System ($67) <http://www.amazon.com/dp/B004XXMUCQ?tag=mhsvortex>`_ is a highly rated, very powerful access point that could solve the signal/range issues. It's also an extensible system so if we want, we can link more than one to the network later and really crank it up.

Improving Wired
~~~~~~~~~~~~~~~
The ideal solution to getting wires to each room is to actually run wires through the house. That's expensive and a pain. Technically we could also run wires out the crawlspace, up the side of the outside of the house, and back in. That's what Comcast did when they installed the extra TV jack in the family room. It's a common solution.

Barring that, to get wires into rooms we'd use :doc:`powerline adapters <../hardware/network/powerline>`. These plug into electrical outlets and broadcast signals through the power system. It's slightly slower than running real wires, but it's fairly easy.

I started off with a set of NetGear Powerline (XAVB1201) 200Mbps adapters ($45/pair) but upgraded the upstairs/downstairs primary set to the XAVB5101 ($80/pair) version which runs at 500Mbps and better handles HD video. These are what served the :doc:`DAP-1522 <../hardware/deprecated/dap1522>` access point upstairs when I had that running.

I did find that the XAVB5101 and XAVB1201 adapters, while they're supposed to work together, don't really work together well at all. After adding the 500Mbps versions, the 200Mbps adapters basically just stopped connecting to the network.

Recommendations
~~~~~~~~~~~~~~~
While not requiring any additional wireless hardware, the XAVB5101 :doc:`powerline adapters <../hardware/network/powerline>` are needed to get wired signal upstairs.

DVR
---
To satisfy the ability to watch/record/pause live TV, we wanted a DVR solution for recording over-the-air (OTA) signals.

DVR boxes generally come in one of three flavors:

- Ultra-simple: This is basically a VCR with a hard drive attached. There's no real "guide," there's no integration with your network, and it's not super friendly or flexible. Program a channel and time to record and it goes. `These run about $50 <http://www.amazon.com/dp/B00I2ZBD1U?tag=mhsvortex>`_ and do not include a hard drive to record things.
- DIY: You can build your own DVR using software like MythTV and, depending on what you build, it can be very flexible and integrate into a lot of things. It can get very expensive, though, because you need a reasonably powerful computer that can process multiple video streams; one tuner for each program you want to record simultaneously (~$70 each); the drive to store things; and so on. It also can be very fiddly. This, too, doesn't necessarily include the guide, but there are ways to hack it in there.
- DVR Appliance: This is the TiVo style thing - a product meant for recording. Every one of these has an additional monthly subscription that populates the program guide. This subscription is also what allows you to do things like "record all new episodes of this show."

I chose the "appliance" style box because I wanted more features than the ultra-simple DVRs offered and didn't want to fuss with the homegrown DVR.

Minimum DVR requirements:

- Two tuners, but ideally four (or more).
- Program guide.
- Ability to watch in any room ("whole house").

**The major competitors delivering that are TiVo and Tablo.**

Base Device Costs
~~~~~~~~~~~~~~~~~

===========  ===============  ===================  =========  =============  =============
Feature      TiVo Roamio OTA  TiVo Roamio Plus HD  TiVo Mini  Tablo 2-Tuner  Tablo 4-Tuner
-----------  ---------------  -------------------  ---------  -------------  -------------
Tuners       4                6                    0          2              4
Device Cost  $50              $320                 $130       $190           $270
Storage      500GB (75h HD)   1TB (150h HD)        0          0 (USB HD)     0 (USB HD)
===========  ===============  ===================  =========  =============  =============

You don't attach Tablo to a TV - instead it's *only streaming*. You need some sort of front-end device to display the content. However, Tablo has a Plex channel and apps for Roku, etc. so this won't be too difficult to achieve.

TiVo offers the $50 version of the Roamio that only works with over-the-air signals. This appears to be a Best Buy "exclusive," though you can get it through Amazon with additional "processing time" for the same price. The next step up from the $50 OTA Roamio is the 6-tuner $320 version.

In order to watch TiVo content, you need to have a TiVo Mini at each TV. Yes, the TiVo Mini is more expensive than the Roamio DVR.

Program Guide Service Costs
~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you want the programming guide you have to subscribe. Most TiVo devices lock you into a 1 year contract minimum. Tablo is entirely optional and comes with a 30 day trial when you buy so you can see if you like it.

=========  ====  =====
Cost       TiVo  Tablo
---------  ----  -----
Per Month  $15   $5
Per Year   $150  $50
Lifetime   $500  $150
=========  ====  =====

Feature Comparison
~~~~~~~~~~~~~~~~~~
The difference between TiVo and Tablo primarily is the way you access content.

**TiVo wants to be your set top box** (and it requires you have a box at each TV to access content). If you want to stream to devices, you have to buy an extra "TiVo Stream" box or you have to go with the Roamio Plus HD box ($320).

**Tablo is more interested in working like Plex** - being a recording server that sits out there and lets you access from whatever. There are already apps for Android and iOS; there's a web app for computers; and there's a Plex integration channel so you can watch through Plex. As long as you have one of the network-enabled devices attached to the TV, you get the DVR/live TV functionality.

Cost Comparison
~~~~~~~~~~~~~~~
Assuming we want what we have now:

- Simple TV in our room. Not necessarily DVR access.
- Full TV/DVR access in the game room and living room.
- The programming guide so the thing is usable - one year of service.
- Four tuners (for apples-to-apples on the DVR comparisons).

==============  =====================================  ==============================
Item            TiVo                                   Tablo
--------------  -------------------------------------  ------------------------------
Equipment Cost  Roamio OTA: $50, TiVo Mini (x2): $130  4-Tuner: $270, Hard Drive: $50
Guide Cost      $150                                   $50
Total           $330                                   $370
==============  =====================================  ==============================

At first that looks like it costs more to go Tablo. However, if we want to extend TV into other rooms, the TiVo Mini cost starts impacting things. Even just adding one more TiVo Mini puts Tablo over the edge. And if you start considering the longer-term guide cost, Tablo totally wins out.

Recommendation: Tablo
~~~~~~~~~~~~~~~~~~~~~
The flexibility and features of Tablo plus the cheap cost of the guide means it's probably the best overall solution for us.

Plex Server
-----------
We currently serve Plex through the :doc:`Synology DS1010+ <../hardware/server/synologyds1010>` NAS in the office. The problem is that, while it works great for SD (standard definition) content, it doesn't have the horsepower to handle HD content. Any time you try to play HD content, the video stutters as the server tries to keep up. This was going to be a stumbling block for putting our HD movies on Plex anyway, but we could have put it off for a bit since getting the HD movies in there isn't a huge priority.

However, given Tablo access will probably be through Plex for some devices, it becomes a bit more pressing.

The CPU power required is for transcoding - which is basically "taking the video stream and converting it into something that looks good on your device." Video processing takes a lot of CPU and the current Synology NAS just doesn't have it. It wasn't meant for that kind of work.

`Plex has some recommendations on what sort of CPU you need to accomplish transcoding <https://support.plex.tv/hc/en-us/articles/201774043-What-kind-of-CPU-do-I-need-for-my-Server-computer->`_. Using a separate server to do the video processing and leaving the content stored on a NAS is something `several folks have working well <https://forums.plex.tv/index.php/topic/124747-pms-on-separate-pc-w-nas-as-media-storage/>`_.

There is a benchmark called "Passmark" that helps guide what sort of CPU might fit the bill. The rough guideline is that if we want HD content, we need to multiply 2000 (the benchmark required for a single stream) by the number of streams we might have (say, 2 or 4). For me, I figured four streams would be enough to future-proof things for a while, so I wanted a CPU with Passmark of ~8000.

**I ended up choosing an AMD FX-8350 processor with a Passmark of 8988** and `a pretty good price-to-performance ratio <http://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-8350+Eight-Core>`_.

**I targeted a server cost of about $500.** Here are the parts I bought to build my :doc:`Megaplex server <../hardware/server/megaplex>`:


- `AMD FD8350FRHKBOX FX-8350 FX-Series 8-Core Black Edition Processor - $169.99 <http://www.amazon.com/dp/B009O7YUF6?tag=mhsvortex>`_
- `Gigabyte AM3+ AMD DDR3 1333 760G HDMI USB 3.0 Micro ATX Motherboard GA-78LMT-USB3 - $58.99 <http://www.amazon.com/dp/B009FC3YJ8?tag=mhsvortex>`_
- `Rosewill Dual Fans MicroATX Mini Tower Computer Case, Black FBM-02 - $29.99 <http://www.amazon.com/dp/B009NJAE4Q?tag=mhsvortex>`_
- `Antec EarthWatts EA-380D Green 380 Watt 80 PLUS BRONZE Power Supply - $40.01 <http://www.amazon.com/dp/B002UOR17Y?tag=mhsvortex>`_
- `Crucial Ballistix Sport 8GB Kit (4GBx2) DDR3 1600 MT/s (PC3-12800) CL9 @1.5V UDIMM 240-Pin Memory BLS2KIT4G3D1609DS1S00 - $59.99 <http://www.amazon.com/dp/B006WAGGUK?tag=mhsvortex>`_
- `LG Electronics 14x Internal BDXL Blu-Ray Burner Rewriter WH14NS40 - Bulk Drive - Black - $56.95 <http://www.amazon.com/dp/B007YWMCA8?tag=mhsvortex>`_
- `5 Pack Monoprice 18-Inch SATA III 6.0 Gbps Cable with Locking Latch and 1 x 90-Degree Plug (108783) - $7.99 <http://www.amazon.com/dp/B00IOS6EAU?tag=mhsvortex>`_
- `StarTech.com 12-Inch LP4 to 2x SATA Power Y Cable Adapter - $3.99 <http://www.amazon.com/dp/B0002GRUV4?tag=mhsvortex>`_
- `JBtek Sleeved PWM Fan Splitter Cable 1 to 2 Converter - $5.99 <http://www.amazon.com/dp/B00OZ10FI2?tag=mhsvortex>`_
- `WD Blue 1TB SATA 6Gb/s 7200rpm Internal Hard Drive - $54.99 (2 of these) <http://www.amazon.com/dp/B0088PUEPK?tag=mhsvortex>`_

**Total price: $543.87**

Set-Top Box
-----------
In the master bedroom there's no gaming console or other device that can get the online content, so we need to solve that. Depending on the solution and what it provides, we may want to put a device even at the TVs that have gaming consoles.

Options
~~~~~~~

- Google :doc:`Chromecast <../hardware/frontend/chromecast>`
- Apple TV
- Amazon Fire TV
- :doc:`Roku 3 <../hardware/frontend/roku>`

`CNet has a great comparison of these devices that matches up with my findings so I won't repeat the whole thing here. <http://www.cnet.com/news/chromecast-vs-apple-tv-vs-roku-3-which-media-streamer-should-you-buy/>`_

We have a :doc:`Chromecast <../hardware/frontend/chromecast>` and I've found two problems with it.

- It never gets a great network signal. Even if it's right next to the access point, it never seems to get over three bars.
- Starting February 2104, it has been getting really flaky, not wanting to connect to the wireless network. Some quick research shows this is not uncommon.

Since I want a wired solution to ensure good connectivity, **Chromecast is out**. Most of our stuff is not in Apple format, so **Apple TV is out**.

`Tablo is both on Amazon Fire TV and Roku 3 <https://www.tablotv.com/blog/sneak-peek-new-roku-channel-amazon-fire-android/>`_. Reading online reviews, while both devices seem reasonable, almost every comparison review (outside of the Amazon web site) points to Roku as a clear winner for having more available content and easier-to-use features. For example, when you search for a title on Amazon Fire TV, it only searches a single app - :doc:`Netflix <../services/netflix>` or :doc:`Amazon Prime <../services/amazon>`. When you search on Roku, you get searches across all the apps, so it'll find the title in Netflix, Amazon, and :doc:`Hulu Plus <../services/hulu>`, then give you a choice which source to use.

Recommendation: Roku 3
~~~~~~~~~~~~~~~~~~~~~~
I got a :doc:`Roku 3 <../hardware/frontend/roku>` for the master bedroom and it turned out amazing. I very shortly thereafter also got one for the main TV. The ease of setup and ease of use really can't be beat.

Content
=======
The content we get through cable right now includes movies (mostly on demand through Showtime, Starz, and Encore) and shows (mostly DVR or on-demand from broadcast networks, though a few from Showtime).

Movies / On-Demand Shows
------------------------
Movies are available on :doc:`Netflix <../services/netflix>`, :doc:`Hulu Plus <../services/hulu>`, :doc:`Amazon Prime <../services/amazon>`, and on our Plex server. I don't think we'll be at a shortage of movies to watch, however, most of these are not new releases.

New releases may require us to use Redbox or rent/buy from Amazon Instant Video or Xbox Video.

CBS has its own on-demand service called "CBS All Access." It only works on computers - there's no app and no integration with anything else.

Channels like TNT, FX, and such (expanded basic channels) mostly do not have on-demand solutions. :doc:`Hulu Plus <../services/hulu>` has a few of these shows, but generally shows from these channels are limited to previous seasons.

Live TV
-------
If we want live programming, we can use over-the-air broadcasts via an antenna.

There are effectively two ways to watch live TV: Directly through the antenna attached to the TV or through a device (like a tuner box).

Just watching live TV is free and works with the antenna. If you want the ability to pause/record live TV or see a program guide, it requires one of the DVR devices I outlined above.

Subscriptions
-------------

==============  =============
Service         Cost Per Year
--------------  -------------
Netflix         $96 ($8/mo)
Hulu Plus       $96 ($8/mo)
Amazon Prime    $99
CBS All Access  $72 ($6/mo)
==============  =============

I didn't really research HBO Now since $15/month for a single channel seems like a bit much.

Shows We Watch
--------------

This grid shows a few of the shows we watch and which provider covers that show. Assuming the show isn't available on live TV to record via DVR, we'd use a provider to get the show.

========================  =======  =========  ======  ==============
Show                      Netflix  Hulu Plus  Amazon  CBS All Access
------------------------  -------  ---------  ------  --------------
NCIS                                                  C,P
CSI                                                   C,P
Doctor Who                P        P          P
Parks and Recreation               C,P        P
Homeland
Sherlock                  P
Big Bang Theory                                       C,P
Agent Carter                       C,P
Agents of SHIELD                   C,P
House of Cards            C,P
Orange/New Black          C,P
American Horror Story     P        P          P
Bob's Burgers                      C,P
The Librarians
Saturday Night Live                C,P
Person of Interest                                    C,P
Grimm                              C,P
Family Guy                         C,P
Glee                               C,P
Archer                    P        P
Nurse Jackie
Jake / Neverland Pirates
Sofia the First
========================  =======  =========  ======  ==============

- C = Current episodes available (sometimes delayed)
- P = Past episodes available

Not counting shows that are broadcast, there are definitely some shows that don't have an online solution at all (e.g., Homeland or anything from Disney Jr.).

We do watch a lot of CBS shows. It's unclear whether it'd be worth $72/year for access online. **A DVR solution would probably be better.** We just couldn't miss any episodes or... well, we'd miss them. No on-demand.

Recommendations
---------------

Based on our viewing habits and the presence of a DVR solution, we're looking at:

- :doc:`Netflix <../services/netflix>`
- :doc:`Hulu Plus <../services/hulu>`
- :doc:`Amazon Prime <../services/amazon>`

Cost Breakdown
==============

Current Cost
------------

Our :doc:`Comcast <../network/providers/comcast>` cable package provides:

- 105Mbps internet
- TV (expanded basic + Starz/Encore)
- Phone

=====================================  ============  ===========  ============
Package                                Monthly Cost  Annual Cost  Savings/Year
-------------------------------------  ------------  -----------  ------------
HD Preferred XF Triple Play (current)  $163.35       $1960.20     --
Internet/Phone only                    $110.90       $1330.80     $629.40
Internet only                          $65.95        $791.40      $1168.80
=====================================  ============  ===========  ============

**The most savings is obviously with internet-only.**  We can use our mobile phones for our primary numbers and wifi calling in the house now enables us to get a good signal and actually receive calls at home. We would lose our landline number unless we choose to do something like the Sprint solution and port the number there, but that's not a huge deal.

Cable Cutting Startup Costs
---------------------------
Given some guesses at which equipment we'd want, here's an equipment + services cost estimate for losing cable.

+--------------------+---------------------------------+-------+
| Live TV                                                      |
+--------------------+---------------------------------+-------+
|                    | ChannelMaster CM 3000 SMARTenna | $52   |
+--------------------+---------------------------------+-------+
|                    | Tablo 4-tuner DVR               | $270  |
+--------------------+---------------------------------+-------+
|                    | 1TB USB HDD for Tablo recording | $100  |
+--------------------+---------------------------------+-------+
|                    | Tablo guide service (1 year)    | $50   |
+--------------------+---------------------------------+-------+
| Network                                                      |
+--------------------+---------------------------------+-------+
|                    | Netgear 500Mbps XAVB5101 (pair) | $80   |
+--------------------+---------------------------------+-------+
| Content Providers                                            |
+--------------------+---------------------------------+-------+
|                    | Netflix (1 year)                | $96   |
+--------------------+---------------------------------+-------+
|                    | Hulu Plus (1 year)              | $96   |
+--------------------+---------------------------------+-------+
|                    | Amazon Prime (1 year)           | $99   |
+--------------------+---------------------------------+-------+
| Plex Server                                                  |
+--------------------+---------------------------------+-------+
|                    | Parts                           | $544  |
+--------------------+---------------------------------+-------+
| **Startup Equipment Costs**                          | $1046 |
+--------------------+---------------------------------+-------+
| **Total Recurring Annual Costs**                     | $341  |
+--------------------+---------------------------------+-------+
| **TOTAL FIRST YEAR COST**                            | $1387 |
+--------------------+---------------------------------+-------+

We already pay for :doc:`Netflix <../services/netflix>` and :doc:`Amazon Prime <../services/amazon>`, and we really wanted the Plex server anyway, so if you subtract those costs from the "startup" cost, **the first year is more like $648**

Notes:

- **There is a chance there is something not being accounted for here.** For example, cables we don't have, or some connector or another to get things hooked up.
- **If we run physical cable instead of using powerline, it would be cheaper.** Of course, it's a ton more work.
- **Hard drive prices change often** so we may come in cheaper on that.
- **We could get the 2-tuner Tablo and save $80**, but we could only record one thing and watch one other thing through it; or record two total things. Kind of like the old cable DVR that we didn't like much.
- **If we want a better wireless access point, this doesn't account for that.** I did end up upgrading our router to improve wireless, but that's not in this budget.
- If we like the Tablo service, **the lifetime $150 cost may be a better long-term investment** with a break-even after three years.

Cost For First Year
-------------------

==========================================  ========
Comcast internet-only                       $791.40
H/W + services (w/o Netflix, Amazon, Plex)  $648.00
Total                                       $1439.40
Savings from current plan                   $520.80
==========================================  ========

Due to the startup hardware costs the savings is not as good in the first year as in subsequent years. If we went to internet/phone, it would be closer to the same price as we already pay - we wouldn't actually save any money the first year.

Cost After First Year
---------------------

==============================  ========
Comcast internet-only           $791.40
Services (w/o Netflix, Amazon)  $146.00
Total                           $937.40
Savings from current plan       $1022.80
==============================  ========

**This subsequent year scenario is where the payoff is.** Once the hardware is in place, you basically only pay for services and the internet connection.

The Migration Plan
==================

1. Prepare for phone replacement.
    a. Ensure cell phones are set up for wifi calling.
    b. Figure out "quiet time" for phones so we can mute them at night but still allow calls through. (`This "Do Not Disturb" app <https://play.google.com/store/apps/details?id=com.cabooze.buzzoff>`_ is a reasonable solution.)
2. Update home network.
    a. Purchase and install upgraded powerline adapters to extend wired network.
    b. Verify strong connectivity upstairs.
    c. Determine if better wireless access point is required upstairs - purchase and install if so.
3. Update Plex server.
    a. Order and assemble parts.
    b. Install Plex server software.
    c. Port the existing library (metadata) to the new :doc:`Megaplex server <../hardware/server/megaplex>`.
4. Prepare for antenna installation - determine how the cables will be hooked up.
    a. Figure out where the cables from the junction box on the side of the house go once they go under through the vent.
    b. Wire up a coax run from the junction box to the office to ensure the Comcast signal still gets there.
5. Install antenna and test.
    a. Order antenna.
    b. Put up the antenna and get the wiring in place.
    c. Temporarily switch to antenna signal with Comcast only running in office.
    d. Verify antenna signal is good - determine if signal amplifier or different antenna placement is required.
    e. Switch back to Comcast inside the house but leave the antenna hooked to the one outlet in the office (the one that will eventually be Comcast). We'll use that to set up Tablo.
6. Set up Tablo.
    a. Order the Tablo box.
    b. Hook up Tablo to the one outlet that has antenna signal. Make sure it powers on and connects to things. Scan for channels but don't program recordings yet.
    c. Install Tablo apps on mobile devices and tablets.
    d. Set up the Plex channel for Tablo and test, particularly with HD signal.
    e. Verify Tablo still gets the channels - maybe re-scan to ensure.
    f. Set up recordings.
7. Pre-cut over.
    a. Finish watching all the shows we have recorded.
    b. Write down all of the things we record - channels, times, etc. so we can set up Tablo or plan things on Hulu.
    c. Start Hulu Plus subscription.
    d. Add Hulu Plus apps to Xbox, Playstation, mobile, tablet.
8. Cut over.
    a. Discontinue TV and phone service with Comcast.
    b. Remove Comcast boxes and wire the TVs directly to the wall coax outlet.
    c. Swap the cables outside - Comcast goes to the single outlet in the office, antenna goes to everything else.
    d. Swap the cable to the Tablo so it gets TV signal.
    e. Swap the cable to the Comast router so it gets Comcast signal.
9. Set up existing TV points.
    a. Update TV input/output to skip cable box input.
    b. Update remote controls as needed to control standard TV channels rather than cable box channels.
