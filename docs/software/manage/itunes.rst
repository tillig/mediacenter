======
iTunes
======

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

      // TODO: Do the search here.
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