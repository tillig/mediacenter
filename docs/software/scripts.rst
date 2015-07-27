================
Scripts and Tips
================

I sometimes come up with scripts or things I need to remember that don't really fall under any other category. Normally I'll post scripts and tips in the relevant place, but if I can't figure out where else to track it, here's a dump of the "extra stuff."

Disable Thumbs.db on Windows
============================

The ``Thumbs.db`` file in Windows hasn't been needed since before Windows Vista but they keep it around for legacy app compatibility. The system creates the files whenever it generates thumbnails for files in a folder (like in a pictures folder) but then it locks the file and makes it so you can't delete the folder. Windows Media Player will also generate these things if it plays any of the media in a folder, so if iTunes is managing your music you'll end up with a bunch of empty folders that just have ``Thumbs.db`` in there.

Ugh.

`You can tell Windows to stop generating Thumbs.db <http://www.sitepoint.com/switch-off-thumbs-db-in-windows/>`_. Do that. It will save a lot of pain and heartache.


Clean Up Empty iTunes Music Folders
===================================

I manage my music collection with :doc:`iTunes <manage/itunes>` but sometimes Windows leaves file system cruft in there, like if I quickly play a song it'll sometimes download the album art and stick it in the folder.

I wrote this little PowerShell script to recurse through my music folders and nuke any folder that only has images or the ``Thumbs.db`` file in it. Set the ``$location`` at the top and run the script. It will prompt you before deleting anything, but it does delete stuff, so, you, know, you're totally on your own if you mess something up. Make sure you have backups.

There's a weird bug where if a folder has square brackets ``[]`` in the name then it can't delete the folder. I don't have too many of those so I didn't bother debugging it to make it perfect. Just be aware.

.. sourcecode:: powershell

        $location = "\\ILLIGHOMESERVER\Music"

        function Get-FoldersToDelete
        {
            param([string]$folder)
            Begin
            {
                $blacklist = @(".jpg", ".gif", ".ini", ".db")
            }
            Process
            {
                if($folder.StartsWith($location + "\Movies\"))
                {
                    return
                }
                $childDirs = Get-ChildItem $folder -Directory
                if($childDirs.Count -gt 0)
                {
                    return
                }

                $files = Get-ChildItem $folder -File -Force
                if($files.Count -eq 0)
                {
                    Write-Host "$folder is EMPTY."
                    Remove-Item $folder -Confirm
                    return
                }

                $groups = $files | Group-Object -Property Extension
                $delete = $true
                $groups.Name | ForEach-Object { if($blacklist -inotcontains $_) { $delete = $false } }
                if($delete)
                {
                    Write-Host "$folder only has blacklist files:"
                    $files | Select-Object -ExpandProperty Name | Format-List
                    Remove-Item $folder -Confirm -Force -Recurse
                }
            }
        }

        $folders = Get-ChildItem $location -Recurse -Directory | Select-Object -ExpandProperty FullName | Sort-Object -Descending -Property Length
        $folders | ForEach-Object { Get-FoldersToDelete $_ }

Edit Chapters in MKV
====================

On one TV series I have, the TV episodes were all combined into one title on the disc. When you wanted to watch a single episode, the player would play for a certain time rather than playing a single title.

Unfortunately, :doc:`Handbrake <convert/handbrake>` doesn't let you convert based on time - it wants chapters in the title. To accommodate for that, I had to manually create chapters of the correct length in the MKV file ripped by :doc:`MakeMKV <rip/makemkv>`.

`MKVToolNix <https://www.bunkus.org/videotools/mkvtoolnix/>`_ is a set of tools that can modify MKV files. You can use that to edit the MKV file to have the correct chapters so Handbrake sees them and can properly convert.