====================
Photo Intake Process
====================

This is the process I go through when I pull photos off of phones or cameras to add to my collection. Following this process helps me ensure I keep everything organized and backed up. Plus, with a consistent organization, I can easily find things later.

My photo intake process is very similar to my :doc:`home video intake process <homevideo>` and usually takes place at the same time because the devices with photos usually also have videos.

Photo Organization
==================

I organize my photos by date and logical event. For photos that don't have a particular event associated, I create a "random pictures" folder by month. For example, you might see a layout like this in my pictures folder::

    pictures/
        2012/
        2013/
        2014/
        2015/
            20150101 Random Photos/
                20150103_132230 Crazy Cat Face.jpg
                20150112_165211 Phoenix Dancing.jpg
            20150405 Easter Sunday/
                20150505_094112.jpg
                20150505_101201.jpg
                20150505_104532.jpg

Intake Process
==============

1. Download the photos from the device onto my computer desktop.
2. Use `exiftool <https://www.sno.phy.queensu.ca/~phil/exiftool/>`_ to rename the files to a format like ``YYYYMMDD_HHMMSS.jpg`` (e.g., ``21050611_113812.jpg``) based on the original date/time field in the photo. The command to do this is: ``exiftool "-FileName<DateTimeOriginal" -d "%%Y%%m%%d_%%H%%M%%S%%%%-c.%%%%e" your_image.jpg``.
3. Fix any files that didn't have proper metadata or were otherwise corrupt. This happens with some camera programs or photo editors - sometimes you have to manually tweak the original date/time metadata. I use `Microsoft Pro Photo Tools <https://www.microsoft.com/en-us/download/details.aspx?id=13518>`_ for that - free and pretty easy. After that's fixed, I re-run the ``exiftool`` rename command. Rinse and repeat until all pictures are correctly named.
4. Group photos by logical event. If there are three or more photos associated with a memorable event, I'll put those in a folder with a descriptive name. The folder will be named in a ``YYMMDD`` format with an additional small description, like ``20150405 Easter Sunday``. All the photos will be put in there and no additional work is required.
5. For remaining photos - the ones that are sort of "random" - I add a small description to each photo so we can basically tell what it is, like ``20150103_132230 Crazy Cat Face.jpg``. These photos will get grouped by month into folders with the description "Random Photos" like ``20150101 Random Photos``.

Exiftool Script
===============

For convenience, I created a batch file for `exiftool <https://www.sno.phy.queensu.ca/~phil/exiftool/>`_ called ``picture-rename.bat`` and put it in the same folder as ``exiftool``. I can now run ``picture-rename.bat *.jpg`` and it does all the photos at once.

.. sourcecode:: bat

    %~dp0exiftool "-FileName<DateTimeOriginal" -d "%%Y%%m%%d_%%H%%M%%S%%%%-c.%%%%e" %1
