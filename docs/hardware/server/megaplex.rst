=============================
Megaplex - Custom Plex Server
=============================

As part of :doc:`my plan to cut cable <../../plans/cuttingthecable>` I built a custom server specifically for hosting :doc:`Plex <../../software/serve/plex>` and handling hardcore HD video processing/transcoding - something for which the :doc:`Synology <synologyds1010>` isn't quite as well suited.

Research
========

`Plex has some recommendations on what sort of CPU you need to accomplish transcoding <https://support.plex.tv/hc/en-us/articles/201774043-What-kind-of-CPU-do-I-need-for-my-Server-computer->`_. Using a separate server to do the video processing and leaving the content stored on a NAS is something `several folks have working well <https://forums.plex.tv/index.php/topic/124747-pms-on-separate-pc-w-nas-as-media-storage/>`_.

There is a benchmark called "Passmark" that helps guide what sort of CPU might fit the bill. The rough guideline is that if we want HD content, we need to multiply 2000 (the benchmark required for a single stream) by the number of streams we might have (say, 2 or 4). For me, I figured four streams would be enough to future-proof things for a while, so I wanted a CPU with Passmark of ~8000.

**I ended up choosing an AMD FX-8350 processor with a Passmark of 8988** and `a pretty good price-to-performance ratio <http://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-8350+Eight-Core>`_.

Parts
=====

I wanted to stay in a reasonable budget with it - I'm not gaming with it, so a huge video card isn't going to help, for example.

The parts I used to build the server (prices listed as of March 2015):

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

Storage
=======
I originally tried to use the WD Green drives I had tried in my :doc:`Windows Home Server <hpex475>`. **FAIL.** The poor performance on these drives caused any sort of heavy :doc:`Plex <../../software/serve/plex>` library indexing to fail with I/O errors. I ended up having to replace these with different, better-performing drives.

I used a drive I already had for the system drive on the box and added the extra two higher-perf drives I bought as storage for the Plex library and scratch/temp space. They are configured using Windows Storage Spaces as a mirrored cluster for fault tolerance.

Performance
===========
After getting this built, I was very pleased with the performance. Transcoding a 1080p video barely raises the CPU usage to 10%, and a typical 2-hour 1080p movie can be converted with :doc:`Handbrake <../../software/convert/handbrake>` in under three hours.