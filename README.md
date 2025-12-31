# ESGC PlayStation 2 Host Filesystem Patch Database

This is a collection of Host Filesystem patches for PlayStation 2 games.

This repository contains ***ABSOLUTELY NO ORIGINAL CODE OR COPYRIGHTED MATERIAL***! You are ***LEGALLY REQUIRED*** to dump your own physical copies of video games. Having a friend dump their copy or downloading it from the internet because your physical copy is too damaged to dump ***BOTH STILL COUNT AS SOFTWARE PIRACY***.

## What is Host Filesystem?

The PlayStation 2 console has a lot of devices it can interface with, such as the disc drive (cdrom0), the memory cards (mc0/mc1), and the internal hard drive (hdd), but another one exists referred to internally as "host0". This is the Host Filesystem, and in the context of a devkit, it's a location on the same network that the devkit is connected to, and is where the actual game executable is, such as a Windows computer. This is often used during a game's development, making it easier to switch out files since developers don't need to re-burn a new disc for every change they make.

[PCSX2](https://pcsx2.net/), the PlayStation 2 emulator, has an option which simulates Host Filesystem, marking the directory the executable was launched in as the Host Filesystem, even if it's not literally on a network. Any software capable of reading from Host Filesystem will do so, and ***will not be limited to disc-reading speeds***, instead using the read speeds of the storage medium you have the files on. If your computer has an SSD, then files are read as fast as the software will allow. Wouldn't it be great if normal disc-based games could take advantage of this?

Unfortunately, unlike Dolphin which can extract GameCube games and play them that way or a modded Xbox which can install games to an internal hard drive, the PlayStation 2 has many different types of file access methods, a handful requiring the files be on a disc specifically, and will fail to load certain files ***even if the path to the file is correct***. Some games go beyond this, either hardcoding file reads to a specific method or using custom methods. A select few tend to read data from LBA, or a specific physical sector on the disc, and probably won't be able to do anything with file paths. The first three Sly Cooper games are a prime example of this, as they don't use files, instead reading from a hardcoded list of sectors stored in the game executable. This is why a disc image from any of those games will appear to be mostly empty if loaded in ISO-viewing software.

A surprising amount of games actually have leftover host0 paths in their executable, and potentially even a flag that switches the game between cdrom0 and host0. Some games don't have such a flag, but play nicely if the cdrom0 paths are manually edited to be host0 paths. This repository contains Host Filesystem patches that I and others in the [Extreme Sports Game Collective Discord server](https://discord.gg/aHA8DTyuNZ) have created, since the Discord server is really obscure and it massively reduces the visibility of these patches. Credit will be given in each patch's folder where applicable.

## Installation

These patches are in the form of [LunarIPS](https://www.romhacking.net/utilities/240/) patches. This allows only the changed sectors of files to be shared, solving the issue of needing to distribute entire executables, which is software piracy. Simply apply the patches to the specified executables and/or IRX modules, then rename the executable to something you'll remember and give it the ".elf" file extension.

## FAQ

**Q:** Can every game get a Host Filesystem patch like the ones in this repository?

**A:** No. Lots of games are hardcoded to look for files from a disc location specifically. If you had the source code or a completed decompilation of one of these games, you COULD in theory write custom code to create such a patch, however at that point it would be more wise to port that game to other, more powerful systems that weren't limited in this way.

**Q:** What are some advantages to running games through the Host Filesystem?

**A:** Apart from much faster loading times and seek times no longer being a factor, ease of modding is a big plus. Imagine a game that had a modding community because its game archives could be unpacked and repacked. Now imagine that game could actually read from extracted archives instead of packed archives. It would suck if you had to rebuild the game's ISO for every change you made, but if you were able to run a game from a directory on a blazing-fast storage medium instead of a disc image, that requirement would be gone, and the ability to load from extracted archives would have a valid use. Wouldn't that be the most ideal scenario? One of the patches in this repository is for a game that DOES have a completely loose filesystem with no compressed archives whatsoever, and it does benefit in this way.

**Q:** Did AI create any of these patches? Can AI create these patches? Will AI be able to create these patches?

**A:** Close your browser, clear your mind, and start learning how to do things the morally-correct way: yourself - with your own brain and your own two hands. You'll become infinitely more skilled of a person and you won't regret it.
