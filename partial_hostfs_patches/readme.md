# Partial Host Filesystem Patches

These patches mostly separate a game from its original disc image, but still need access to it or a different disc image in order to work properly.

Create a folder in your PCSX2 install directory and name it "hostfs_games", then put the original disc image in there. This will ensure that the original disc image is not scanned by the games list and won't show up there:

<img width="918" height="439" alt="Capture" src="https://github.com/user-attachments/assets/9f43c4ac-3c2f-4832-85cd-5428a2ee4353" />

In the HostFS-patched game's custom configuration, set the Disc Path to the original disc image which you stored in the "hostfs_games" folder:

<img width="1457" height="559" alt="Capture2" src="https://github.com/user-attachments/assets/db0799b6-5255-4d59-8349-0151496cd9a4" />

This will result in the game reading from the patched paths where applicable, but it'll still be able to read from a disc image where it needs to. This will also achieve the same effect as the setup for Full Host Filesystem Patches, letting PCSX2 detect the game's actual title and region info, making it a valid RetroAchievements title as well as applying the right automatic rendering fixes.
