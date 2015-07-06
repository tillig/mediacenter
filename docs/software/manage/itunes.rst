======
iTunes
======

I, like many, use iTunes to organize my music.

What I like:

* It's one place I can go to deal with my collection and sync up devices.
* It keeps the music files organized on disk.
* It has a passable metadata editing interface.
* It has a programming interface that lets me write scripts to help automate tasks in music management.

What I don't like:

* It is slower than any other program I use. Startup/shutdown is ridiculous. Switching views, especially if it's to something requiring network activity (like the iTunes store) is laughable.
* It locks up whenever it has to do a network I/O call. I keep all of my music on a shared network drive. If I copy a new file into the library, the UI literally locks up during the whole file copy operation. This gets really bad if it's downloading podcasts - every podcast it saves locks up the UI unexpectedly as it writes the file to the network share.
* It tries to do too much. I don't need an integrated store and an app management system and and and and. I want it to manage my music. I want it to sync my music to my devices. That's it. Do your thing and do it well. Instead, it does 1000 things and it half-asses every one.

I've considered alternatives like `MediaMonkey <http://www.mediamonkey.com/>`_ but I just haven't bitten the bullet yet. I have a few (very few) iTunes DRM-wrapped tracks and videos and without iTunes, I'm not sure if that'd work too well.

Windows Media Center Integration
--------------------------------

At one point, before getting :doc:`Asset UPnP <../serve/asset>`, I tried integrating iTunes music directly into :doc:`Windows Media Center <../deprecated/windowsmediacenter>`. You can read my notes and rough plan on the :doc:`Windows Media Center <../deprecated/windowsmediacenter>` page, but **I never did get it working.**

Advanced Searching
------------------

Sometimes while working with my collection I find I need to do some searching to locate tracks in my library that meet a certain criteria (like the ones that don't have artwork or maybe a regex match on an artist name). The smart playlists work well much of the time, but for when I need a more powerful approach, I wrote this script to help me out.

You need to know about the iTunes COM SDK to know what fields are available to search over, so, YMMV with this.

.. sourcecode:: js

    /* jshint eqnull:true */
    // ComplexSearchTemplate.js
    // A template for doing a search over tracks
    // using some complex logic. Output is in tab-delimited format.
    // Run cscript.exe //U to get Unicode output in Windows.

    // Return true to include the track in the output;
    // false to skip the track.
    function predicate(track) {
      if (track.URL != null || track.Podcast || track.Location == null) {
        // Filter out of non-music.
        return false;
      }

      // Do the search here and return true if the track matches the criteria.
      return true;
    }


    // Get the set of all tracks from the library.
    var iTunesApp = WScript.CreateObject("iTunes.Application");
    var allTracks = iTunesApp.LibraryPlaylist.Tracks;
    if (allTracks === null) {
      WScript.Echo("Unable to get list of library tracks!");
      WScript.Quit();
    }

    // Process the tracks.
    var numTracks = allTracks.Count;
    for (var i = 1; i <= numTracks; i++) {
      var currentTrack = allTracks.Item(i);
      if (!predicate(currentTrack)) {
        continue;
      }

      try {
        WScript.Echo(currentTrack.Location + "\t" + currentTrack.Artist + "\t" + currentTrack.AlbumArtist + "\t" + currentTrack.Album + "\t" + currentTrack.Name);
      } catch (ex) {
        WScript.Echo("Error processing " + currentTrack.Artist + " - " + currentTrack.Name + ": " + ex.message);
      }
    }