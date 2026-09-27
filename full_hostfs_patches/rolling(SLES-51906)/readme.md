# Rolling

This patch created by modeco80 is special and very unlike the others. Not only is it an [xdelta patch](https://github.com/marco-calautti/DeltaPatcher/releases) rather than a LunarIPS patch, but it allows the entire game to run from both Host Filesystem AND from an unpacked game data archive, allowing for full game modding potential!

The patch will likely receive updates over time, so the latest version can always be found at this link:

https://github.com/modeco80/rolling-hostfs/releases

For this reason, I recommend keeping a backup copy of the original executable somewhere, maybe with a renamed file extension, so that you can easily re-patch the executable without needing to go find the disc image again. Note that every time you re-patch the executable, PCSX2 will detect a new CRC, so you'll need to update your custom config and any PNACH cheats to the new CRC every time this happens.

Included in this directory is a Python script (Python 3.10+ required) which unpacks the game's "roll_p.wad" data archive. Simply drag and drop the data archive onto the script and it'll unpack it to the directory where the data archive was located. In order for this patch to work properly, you'll need to do the normal steps required for a Host Filesystem patch, but extract the data archive into the root directory. Essentially you patch the executable with the xdelta patch, then follow the rest of the installation instructions, giving you a setup that looks like this:

<img width="1620" height="667" alt="1" src="https://github.com/user-attachments/assets/b480a421-10b4-4a33-a458-b5bc0907c9bf" />

Then, you extract and delete the data archive, leaving you with this:

<img width="1408" height="1922" alt="2" src="https://github.com/user-attachments/assets/248da807-6cf9-46e6-a566-1424185397f1" />

With these modifications, the game should load incredibly fast and be fully open to modding! Note that the extra "sles_519.06" file that gets extracted from the data archive is not used by the game and should not be patched. This game doesn't have any automatic gamefixes in PCSX2, nor does it need any, and it upscales without any visual errors whatsoever.
