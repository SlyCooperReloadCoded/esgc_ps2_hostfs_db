# Full Host Filesystem Patches

These patches completely separate a game from its original disc image. Simply apply the LunarIPS patch to the specified executable, delete the SYSTEM.CNF file, turn on "Enable Host Filesystem" in PCSX2 2.0+, and you're all set!

Note that if you wish to use the game with RetroAchievements, you'll need to keep the original disc image. Create a folder in your PCSX2 install directory and name it "hostfs_games", then put the original disc image in there. This will ensure that the original disc image is not scanned by the games list and won't show up there:

<img width="918" height="439" alt="Capture" src="https://github.com/user-attachments/assets/9f43c4ac-3c2f-4832-85cd-5428a2ee4353" />

In the HostFS-patched game's custom configuration, set the Disc Path to the original disc image which you stored in the "hostfs_games" folder:

<img width="1457" height="559" alt="Capture2" src="https://github.com/user-attachments/assets/db0799b6-5255-4d59-8349-0151496cd9a4" />

This won't make it read from disc since the game has been patched to not do so, however PCSX2 will grab the correct title and version info from it, marking it as a valid RetroAchievements title. This will also make PCSX2 apply the correct automatic rendering fixes, but if there's needed automatic pnach patches, these will NOT be applied, and each game's directory in this repository will include special instructions for this.
