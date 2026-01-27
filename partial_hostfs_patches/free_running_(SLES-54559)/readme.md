# Free Running (SLES-54559)

This patch nearly completely separates the game from its disc image. It also disables a lot of the game's nasty post-processing effects, making it look a lot less blurry and misaligned. However, for some reason it still needs to access the SYSTEM.CNF file from the cdrom0 device, and this check doesn't seem to be easily patched out. Additionally, this game has a full pnach cheat in PCSX2's games database that needs to be applied or else you'll repeatedly fall through the floor. For this reason, you'll need a few more files than usual.

Included is a PCSX2 pnach cheat file with the game's automatic gamefixes as well as the optional widescreen and 50 FPS patches. You'll need to move this cheat file to PCSX2's "cheats" directory and enable at least the Automatic Gamefixes cheat.

Also included is a tiny 5 KB CHD-compressed disc image containing a SYSTEM.CNF file and a massive padding file containing nothing but zeroes:

<img width="1835" height="986" alt="Capture" src="https://github.com/user-attachments/assets/3f237ebc-7aef-4cf9-bfbd-445883204f6d" />

This is enough for the game's SYSTEM.CNF check, so it's safe to distribute as it contains no copyrighted code. Put this into your "hostfs_games" folder rather than the original disc image.

You'll also need to set the game's automatic rendering fixes manually. Use these screenshots as a guide:

<img width="1431" height="724" alt="Capture" src="https://github.com/user-attachments/assets/241ca368-8d2c-4ed9-8017-e9b3d04791ad" />
<img width="1476" height="1115" alt="Capture" src="https://github.com/user-attachments/assets/c82c7159-78e0-4536-8b95-2efd29f6acba" />
<img width="1781" height="1616" alt="Capture3" src="https://github.com/user-attachments/assets/21eb7fce-23bc-47e6-a0de-7d9af87fdf2e" />
