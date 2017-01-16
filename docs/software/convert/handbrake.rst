=========
Handbrake
=========

I use Handbrake to convert my videos into :doc:`MP4 (M4V) format <../../formats/video>`.

SD Settings
===========
My entire ``user_presets.xml`` file is pasted in below, but for readability, I have three SD presets that only differ by the "x264 Tune" setting for Film (most everything), 2D Animation, or Grain.

- Picture

  - Width/Height: nil (let it auto-correct)
  - Anamorphic: Loose
  - Modulus: 2
  - Cropping: Automatic

- Filters

  - Detelecine: Off
  - Decomb: Default
  - Deinterlace: Off
  - Denoise: Off
  - Deblock: Off
  - Grayscale: Unchecked

- Video

  - Video Codec: H.264 (x.264)
  - Framerate FPS: Same as source
  - **Constant Framerate**
  - x264 Preset: Slower
  - x264 Tune: **Film, Animation, or Grain** (depends on the source – I change this per item ripped)
  - H.264 Profile: High
  - H.264 Level: 4.1
  - Fast Decode: Unchecked
  - Extra Options: Empty
  - Quality: **Constant Quality RF 18**

- Audio

  - Track 1:

    - Source: The best AC3 sound track on there with the most channels. (It usually does a good job of auto-detecting.)
    - Codec: **AAC (FDK)**
    - Bitrate: **256**
    - Samplerate: Auto
    - Mixdown: Dolby Pro Logic II
    - DRC: 0.0
    - Gain: 0

  - Track 2:

    - Source: Same as Track 1.
    - Codec: AC3 Passthru

  - Track 3 (depending on source)

    - Source: The DTS track, if there is one.
    - Codec: DTS Passthru

- Subtitles: Generally none, but there are some movies that need them, in which case I'll add one track. High Profile (and my settings) generally don't include this.

  - Source: English (VobSub)
  - Forced Only: Unchecked
  - Burn In: Checked
  - Default: Unchecked
  - Everything else default.

- Chapters: I do select "Create chapter markers" but I let the automatic detection do the naming and timing.

The truly important bits there are **bold** - these are the settings that differ from the "High Profile" preset.

**Using these settings, I calculated SD content for me uses an average of 18.73MB/minute.**

HD Settings
===========
My entire ``user_presets.xml`` file is pasted in below, but for readability, I have three HD presets - one each for Film (most everything), 2D Animation, or Grain.

The settings stem from my SD settings, above, so I'll just put the differences here:

- Video

  - Variable Framerate
  - x264 Tune: Film, Animation, or Grain (depends on the source – I change this per item ripped)
  - Quality:

    - For Film:
    - For Grain: Constant Quality RF 21
    - For Animation:

I started my testing by checking out links like `the Rokoding guide to 1080p encoding <http://www.rokoding.com/settings/0_10_0/0100_1080p_blu-ray_film.html>`_. These give some great guidance and help you know where to begin.

In testing to find the right HD settings, I went through a few different movies. I found the output size was very different based on the movie type and the x264 Tune setting.

=============  ==============  ==============================  ===================  ==========================  =================
Movie          300             Hunger Games: Mockingjay Pt. I  Across the Universe  Alice in Wonderland (2010)  Cinderella (1950)
=============  ==============  ==============================  ===================  ==========================  =================
x264 Tune      Grain           Film                            Film                 Film                        Animation
Original Size  21,530,308,978  21,742,181,655                  26,831,992,958       24,308,963,706              22,461,786,135
RF 18          22,119,901,510  4,240,158,260                   --                   --                          --
RF 19          --              3,595,175,689                   11,076,964,804       12,880,097,076              --
RF 20          16,703,767,507  3,090,776,234                   8,913,678,948        11,083,481,088              3,957,488,389
RF 21          14,317,745,001  2,727,727,566                   7,143,310,360        8,408,253,360               3,801,331,209
RF 22          12,158,064,830  --                              5,741,888,616        7,254,867,569               --
=============  ==============  ==============================  ===================  ==========================  =================

In all cases, just as with the SD presets, I had a stereo mixdown audio track and an original/surround passthrough track. I didn't keep extra tracks like commentary, etc. (For *Cinderella* I had two passthrough tracks - the 5.1 DTS-HD and the original mono DTS-HD.)

I've seen in some forum posts and videos that folks want to change the number of reference frames to 4 (``ref=4``) in advanced settings, but the intent is always to *increase* the number of reference frames used. Using :doc:`MediaInfo <mediainfo>` I could see that the default number of reference frames used was 5 (``ref=5``) so I stopped messing with it.

For *300*, the file was very hard to shrink much because of the details in the grainy appearance. Too much more and you start noticing unfortunate artifacting around edges. Only 7% of this file was audio; the rest is all video.

*The Hunger Games: Mockingjay Part I* seemed to create an unusually small file regardless of the RF number. It made me curious why the original was so big. The same thing happened with *Alice in Wonderland*, though it's not as apparent: *Wonderland* has a DTS-HD MA soundtrack that I allowed to pass through (I like having the original audio) and *that track alone took 3GB* - 38% of the file size under RF21.

*Across the Universe* had a larger video size than either *Mockingjay* or *Wonderland*. With only 427MB of the size coming from sound, the majority of that file size truly is video. I'm unclear if this is an anomaly.

*Cinderella* is a pretty decent example of standard, full-frame (4:3) 2D animation, at least from the movies I have (Disney classics). The sound - a stereo mixdown track, a DTS-HD 5.1 track, and a DTS-HD mono track - was about 2.5GB of the file size. The video was closer to 30% with the rest being audio. Visually, honestly, I couldn't really tell the difference between the RF 21 and RF 20 and both looked amazingly clear, so I didn't bother going any further with it. I may have been able to squeeze it more, but given the majority of the file is sound, it would be diminishing returns.

**The HD video "sweet spot" for Grain and Film seems to be RF 21; for 2D animation I like RF 20.** Those numbers seem a good balance between file size and quality and they follow the rough guideline I've seen for 22+/-1 for HD.

HD video done with the Film setting at RF 21 seemed to take my :doc:`Megaplex server <../../hardware/server/megaplex>` around 3 - 4 hours to complete. *300*, on the grainy setting, took closer to 6 - 7 hours. 2D animation ran about 2 hours.

Of course, these end up being "guidelines" rather than "rules." I start here, and after the conversion I'll see if I need to reconvert with different settings. I ended up keeping the RF 18 version of *Mockingjay*.

**Using these settings, I calculated HD content for me uses an average of 80.72MB/minute.**

Subtitles
=========
I learned *a lot* about subtitles in doing video conversion. If you're like me, you never thought much about how they work - the text just comes up on the screen as needed.

`Handbrake has a really good page explaining things from a technical perspective <https://trac.handbrake.fr/wiki/Subtitles>`_ but it breaks down in my world like this:

- Handbrake can read all of the standard subtitle types you'll find on discs.
- If you're using :doc:`the MP4 format <../../formats/video>` like me, you can either permanently "burn in" the subtitles to the video image or you don't get subtitles at all. This is because MP4 doesn't let you keep a separate subtitle track the way MKV does.

Since I am fortunate enough to only need subtitles in non-English-speaking films or in parts during English-speaking films where they switch languages, this is less an issue, but it does require you "flip a switch" in Handbrake to tell it to include the subtitles.

- General Subtitles: This is for a foreign language film where you always want the subtitles on through the whole movie. Think "English speaker watching a Kung Fu movie."
- Forced Subtitles: This is for a native language film where you only need subtitles for the few foreign language parts. Think "Black Widow getting interrogated by the Russians in 'The Avengers'."

Here's how to get subtitles in your movie:

#. First, choose which, if any, kind of subtitles you want.
#. Switch to the "Subtitles" tab in Handbrake.
#. Click "Add Track" to add a subtitle track.
#. For your chosen subtitle type...

    #. For general subtitles, select the language of the subtitles you want and click the "Burn In" checkbox.
    #. For forced subtitles, select "Foreign Audio Scan" as the language and click both the "Forced Only" and "Burn In" checkboxes.

Even though I've added forced subtitles to my ``user_presets.xml`` (below), the default doesn't seem to keep - you need to re-add the forced subtitle track each time.

**It's important to look at the output when you expect subtitles.** I found that sometimes there are multiple English tracks and sometimes you get the wrong one. There are tips for troubleshooting on the `Handbrake subtitle page <https://trac.handbrake.fr/wiki/Subtitles>`_.

Additional tips for subtitles:

- `This forced subtitles Google Doc spreadsheet <https://docs.google.com/spreadsheet/ccc?key=0AkGO8UqErL6idDhYYjg1ZXlORnRaM3ZhTks4Z3FrYlE&usp=sharing#gid=20>`_ is an incomplete but ever-growing list of movies that have forced subtitles in them. It can help determine if you need to switch on forced subs.
- `SubtitleEdit <http://www.nikse.dk/SubtitleEdit/>`_ is a tool for inspecting and editing subtitles. I use it to figure out where the subtitles start and end (looking at the source ripped content) so I can narrow down what I should look at in the end conversion.

Lip Sync Issues
===============

I discovered after the first round of scanning movies that there were issues with graininess, cropping, and lip sync on some movies. I rescanned them. After rescan, these still had some issues:

- Buffy the Vampire Slayer (1992) - Possible naturally bad sync. Everything is off by just a couple of frames.
- Christmas Vacation (1989) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Elf (2003) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Eraser (1996) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- GI Jane (1997) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.
- Iron Monkey (1993) - Almost looks like the wrong language, but this is apparently normal for some Cantonese films - they overdub themselves.
- It's a Very Merry Muppet Christmas Movie (2002) - Possible naturally bad sync. Everything is just a little off.
- Jay and Silent Bob Strike Back (2001) - This is a variable frame rate movie and it seems to have naturally bad sync. Switching to constant frame rate makes some of the sections stutter.
- Labyrinth (1986) - Possible naturally bad sync.
- Lethal Weapon (the entire series) - All of these seem to have naturally bad sync.
- Maverick (1994) - Possible naturally bad sync. Some scenes are right on, some are off by a couple of frames.

I stopped tracking the complete list. It kind of sucks, but it is what it is.

Part of the way I fixed this was to start using **constant frame rate** in all my conversions rather than variable frame rate. I noticed that, as a general rule, this reduced or removed many of the lip sync problems I saw.

Remote Queue Monitoring
=======================
Handbrake has a command-line interface and good scripting abilities, but it doesn't have an official way to monitor the status of the queue.

Not that it's super important, but I'm curious to see how things are progressing without having to remote all the way in. The way I solved that was with a PowerShell script and `OneDrive <onedrive.live.com>`_.

Handbrake stores the queue XML in the ``%AppData%\Handbrake`` folder. The files are always named like ``hb_queue_recovery1234.xml``. I set up a scheduled task to generate a small text report of the most recently written queue XML file and dump it in a OneDrive folder. That way I can see the state of the queue from anywhere.

Here's the script I used:

.. sourcecode:: powershell

    $reportFile = "C:\Users\Travis\OneDrive\QueueStatus.txt"
    $handbrakeDir = Join-Path ([Environment]::GetFolderPath("ApplicationData")) -ChildPath "Handbrake"

    [XML]$queue = Get-ChildItem -Path $handbrakeDir -Filter "hb_queue*.xml" |
    Sort-Object -Property LastWriteTime -Descending |
    Select-Object -First 1 |
    Get-Content

    $queue.ArrayOfQueueTask.QueueTask |
    Select-Object -Property @{n='Status';e={$_.Status}},@{n='Source';e={$_.Task.Source}},@{n='Destination';e={$_.Task.Destination}} |
    Format-Table -AutoSize |
    Out-String -Width 4096 |
    Out-File $reportFile -Force

The report output looks like this::

    Status     Source                                                    Destination
    ------     ------                                                    -----------
    InProgress E:\Rip\Enchanted (2007)\Enchanted_t01.mkv                 E:\Rip\Enchanted (2007).m4v
    Waiting    E:\Rip\The Expendables (2010)\The_Expendables_t01.mkv     E:\Rip\The Expendables (2010).m4v
    Waiting    E:\Rip\The Expendables 2 (2012)\The_Expendables_2_t55.mkv E:\Rip\The Expendables 2 (2012).m4v
    Waiting    E:\Rip\Family Guy.s09e18\FAMILY_GUY_IT'S_A_TRAP!_t00.mkv  E:\Rip\Family Guy.s09e18.m4v
    Waiting    E:\Rip\The Fifth Element (1997)\title00.mkv               E:\Rip\The Fifth Element (1997).m4v

Reporting Media Info
====================
I used a script to calculate video media average sizes for my collection, the result of which I posted on the :doc:`video format page <../../formats/video>`. The script I used is here:

.. sourcecode:: powershell

    $mediaShare  = "\\DISKSTATION\video"

    function Get-MediaInfo
    {
        param([Parameter(ValueFromPipeline=$true)] $path)

        Begin
        {
            $shell = New-Object -COMObject Shell.Application
            Write-Progress -Activity "Scanning media info" -Status "Starting scan"
        }

        Process
        {
            Write-Progress -Activity "Scanning media info" -Status $path
            $fileSize = Get-Item $path | Select-Object -ExpandProperty Length

            $folder = Split-Path $path
            $file = Split-Path $path -Leaf
            $shellfolder = $shell.Namespace($folder)
            $shellfile = $shellfolder.ParseName($file)

            # Good stuff! http://powershell.com/cs/blogs/tobias/archive/2011/01/07/organizing-videos-and-music.aspx
            # 27  = Length in H:M:S format
            # 299 = Frame height
            # 301 = Frame width
            [int]$frameWidth = $shellfolder.GetDetailsOf($shellfile, 301)
            [int]$frameHeight = $shellfolder.GetDetailsOf($shellfile, 299)
            $length = [System.TimeSpan]::Parse($shellfolder.GetDetailsOf($shellfile, 27))
            New-Object -TypeName PSObject -Property (@{'Path'=$path;'Size'=$fileSize;'Width'=$frameWidth;'Height'=$frameHeight;'Length'=$length})
        }

        End
        {
            Write-Progress -Activity "Scanning media info" -Status "Done" -Completed
        }
    }

    $allMediaInfo = Get-ChildItem $mediaShare -File -Recurse | Select-Object -ExpandProperty FullName | Get-MediaInfo
    $sdMediaInfo = $allMediaInfo | Where-Object { $_.Width -le 720 }
    $hdMediaInfo = $allMediaInfo | Where-Object { $_.Width -gt 720 }

    $hdLength = [System.TimeSpan]::Zero
    $sdLength = [System.TimeSpan]::Zero
    $hdMediaInfo | ForEach-Object { $hdLength = $hdLength.Add($_.Length) }
    $sdMediaInfo | ForEach-Object { $sdLength = $sdLength.Add($_.Length) }
    $hdSize = $hdMediaInfo | Measure-Object -Sum -Property Size | Select-Object -ExpandProperty Sum
    $sdSize = $sdMediaInfo | Measure-Object -Sum -Property Size | Select-Object -ExpandProperty Sum

    Write-Host "Total files:      " $allMediaInfo.Count
    Write-Host "SD Length:        " $sdLength
    Write-Host "HD Length:        " $hdLength
    Write-Host "Total Length:     " $hdLength.Add($sdLength)
    Write-Host "SD Size:          " ($sdSize / 1GB) "GB"
    Write-Host "HD Size:          " ($hdSize / 1GB) "GB"
    Write-Host "Total Size:       " (($hdSize + $sdSize) / 1GB) "GB"
    Write-Host "SD MB per Minute: " (($sdSize / $sdLength.TotalMinutes) / 1MB) "MB"
    Write-Host "HD MB per Minute: " (($hdSize / $hdLength.TotalMinutes) / 1MB) "MB"

Additional References
=====================

- `Rokoding <http://www.rokoding.com/>`_ has great information on encoding video with particular emphasis on :doc:`Roku <../../hardware/frontend/roku>` compatibility.
- `The Matt Gadient best settings guide for Handbrake 0.9.9 <https://mattgadient.com/2013/06/12/a-best-settings-guide-for-handbrake-0-9-9/>`_ is indispensible. Great side-by-side comparisons for things so you can tell what settings actually do.

User Presets
============

The following is my set of presets. If you put these in ``%AppData%\Handbrake\user_presets.xml`` then you'll see the same settings as me.

<script src="https://gist.github.com/tillig/35949ae52492f2be85f74dea057814bb.js"></script>
