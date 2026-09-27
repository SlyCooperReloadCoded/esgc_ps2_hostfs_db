# ESGC PlayStation 2 Host Filesystem Patch Database

This is a collection of Host Filesystem patches for PlayStation 2 games.

This repository contains ***ABSOLUTELY NO ORIGINAL CODE OR COPYRIGHTED MATERIAL***! You are ***LEGALLY REQUIRED*** to dump your own physical copies of video games. Having a friend dump their copy or downloading it from the internet because your physical copy is too damaged to dump ***BOTH STILL COUNT AS SOFTWARE PIRACY***. Additionally, as these patches are unofficial modifications, please do not submit bug reports to PCSX2 while using them, because they get enough invalid reports already, I'm sure of it.

## What is Host Filesystem?

The PlayStation 2 console has a lot of devices it can interface with, such as the disc drive (cdrom0), the memory cards (mc0/mc1), the internal hard drive (hdd), and inserted USB flass drives (mass), but another one exists referred to internally as "host0". This is the Host Filesystem, and in the context of a devkit, it's a location on the same network that the devkit is connected to, such as a Windows computer, and is where the actual game executable is. This is often used during a game's development, making it easier to switch out files since developers don't need to re-burn a new disc for every change they make unless the game in question requires a disc-only setup.

[PCSX2](https://pcsx2.net/), the PlayStation 2 emulator, has an option which simulates Host Filesystem, marking the directory the executable was launched in as the Host Filesystem, even if it's not literally on a network. Any software capable of reading from Host Filesystem will do so, and ***will not be limited to disc-reading speeds***, instead using the read speeds of the storage medium you have the files on. If your computer has an SSD, then files are read as fast as the software will allow. Wouldn't it be great if normal disc-based games could take advantage of this?

Unfortunately, unlike Dolphin which can extract GameCube games and play them that way or a modded Xbox which can install games to an internal hard drive, the PlayStation 2 has many different types of file access methods, a handful requiring the files be on a disc specifically, and will fail to load certain files ***even if the path to the file is correct***. Some games go beyond this, either hardcoding file reads to a specific method or using custom methods. A select few tend to read data from LBA, or a specific physical sector on the disc, and probably won't be able to do anything with file paths. The first three Sly Cooper games are a prime example of this, as they don't use files, instead reading from a hardcoded list of sectors stored in the game executable. This is why a disc image from any of those games will appear to be mostly empty if loaded in ISO-viewing software.

A surprising amount of games actually have leftover host0 paths in their executable, and potentially even a flag that switches the game between cdrom0 and host0. Some games don't have such a flag, but play nicely if the cdrom0 paths are manually edited to be host0 paths. This repository contains Host Filesystem patches that I and others in the [Extreme Sports Game Collective Discord server](https://discord.gg/aHA8DTyuNZ) have created, since the Discord server is really obscure and it massively reduces the visibility of these patches. Credit will be given in each patch's folder where applicable.

## Installation

Unless otherwise specified, these patches are in the form of [LunarIPS](https://www.romhacking.net/utilities/240/) patches. This allows only the changed sectors of files to be shared, solving the issue of needing to distribute entire executables, which also counts as software piracy.

Partial Host Filesystem patches need the disc image accessible for one reason or another, while Full Host Filesystem patches completely separate all the disc image's contents, letting you run the entire game from a disconnected folder. Keep this in mind going forward.

When extracting a game image for patching, your executable will usually have a name like "SCXX_XXX.XX". If it's an American game, it'll usually be "SCUS_XXX.XX". If it's a European game, it'll usually be "SCES_XXX.XX". If it's a Japanese game, it'll usually be "SCPS_XXX.XX" or "SCJS_XXX.XX". This file is the one you need to patch. After patching it, rename it - file extension included - to the game's actual name or something very similar so you could spot it in a list of names later on, and with the ".elf" file extension. For example, if you're applying the patch to the American release of Jimmy Neutron: Attack of the Twonkies, rename the executable to "JNAoTT.elf", like this:

<img width="1504" height="364" alt="6" src="https://github.com/user-attachments/assets/d9fd96dd-7161-4d8c-90a2-2116a7887d4e" />

Then, in the game's custom config, you can set a name of your own in the "Title" field, and it'll be displayed in the game list as that name.

<img width="1463" height="596" alt="7" src="https://github.com/user-attachments/assets/a275c2e7-126c-4805-ad69-c7eecdb44a8b" />

This way, you won't have "JNAoTT.elf" in the game list anymore. If you want to give your patched game a cover image, rename the cover image to the name you gave the executable. In this case, you'll want to rename the cover image to "JNAoTT.png" or "JNAoTT.jpg", then put it in your "covers" folder like normal. Savestates and GS dumps created from these patched games will also use the executable name, as will the texture replacement system.

Whoa whoa whoa, don't just put the newly-patched game in the games directory you already have set up, you'll need to do some more prep work for this. Create a folder in your PCSX2 install directory named "hostfs_games". Whenever you modify a game to run through Host Filesystem, put it in its own properly-named folder, and move that folder inside the "hostfs_games" folder, like this:

<img width="1218" height="607" alt="1" src="https://github.com/user-attachments/assets/668293b7-bee3-4929-824f-36b2ec30a338" />
<img width="1251" height="995" alt="2" src="https://github.com/user-attachments/assets/7a08785d-bb23-4a89-9180-39c6a316ce4d" />

Then, in PCSX2's "Game List" menu, add each of these games' folders individually and choose to NOT scan recursively, which should look like this:

<img width="1424" height="632" alt="3" src="https://github.com/user-attachments/assets/9ae55363-75ad-47b0-8cc7-b6acc936d037" />

This will both add the games to the emulator while preventing it from manually scanning every subfolder for more games.

After you've done this, go back to PCSX2's install directory and create a new folder named "hostfs_game_images", which can be seen in the same screenshot from earlier. Every time you need to give a game disc access for use with Partial Host Filesystem patches, you don't want the original game image to show up as a game, so instead, put it in your "hostfs_game_images" folder then set the "Disc Path" in the game's custom configuration so it points at the game image, like this:

<img width="1488" height="487" alt="4" src="https://github.com/user-attachments/assets/1a52175e-ecca-47bb-b0d7-1bcac4197722" />
<img width="1465" height="611" alt="5" src="https://github.com/user-attachments/assets/8bbf2d13-da69-4845-8b80-222d1a1447ed" />

This will result in the game reading from the patched paths where applicable, but it'll still be able to read from a disc image where it needs to. This will also let PCSX2 detect the game's actual title and region info, making it a valid RetroAchievements title, as well as applying the correct automatic rendering fixes. Note that this will NOT make the built-in patches appear in the "Patches" submenu, so you'll need to manually find those inside "resources/patches.zip", rename them to the new CRC as seen in the game's custom config, put them into PCSX2's "cheats" directory, and activate them that way. For any games that have automatic gamefixes which include a patch required for the game to function properly, I've included those and any other patches those games have alongside the Host Filesystem patch.

Additionally, you can still give games patched with Full Host Filesystem patches disc access for the extra benefits it provides, or if you're a power user and know what all the advanced settings do (i.e. you're ***NOT*** following a "Best Settings for Performance" YouTube video) you can navigate to "resources/GameIndex.yaml", locate your game in the list, and manually apply all the settings yourself. The choice is entirely up to you.

## FAQ

**Q:** Can every game get a Host Filesystem patch like the ones in this repository?

**A:** No. Lots of games are hardcoded to look for files from a disc location specifically. If you had the source code or a completed decompilation of one of these games, you COULD in theory write custom code to create such a patch, however at that point it would be more wise to port that game to other, more powerful systems that weren't limited in this way.

**Q:** What are some advantages to running games through the Host Filesystem?

**A:** Apart from much faster loading times and seek times no longer being a factor, ease of modding is a big plus. Imagine a game that had a modding community because its data archives could be unpacked and repacked. Now imagine that game could actually read from extracted archives instead of packed archives. It would suck if you had to rebuild the game's ISO for every change you made, but if you were able to run a game from a directory on a blazing-fast storage medium instead of a disc image, that requirement would be gone, and the ability to load from extracted archives would have a valid use. Wouldn't that be the most ideal scenario? Several of the patches in this repository are for a games that have a completely loose filesystems with no compressed archives whatsoever, and they do benefit in this way.

**Q:** Did AI create any of these patches? Can AI create these patches? Will AI be able to create these patches?

**A:** With the rise of Generative AI, people might think that any task can be handled with the various available models. However, despite what most people believe, Generative AI is the "Apple in the Garden of Eden" so to speak. It's very tempting to use for those who haven't used it, because it promises that it can do pretty much anything for you, especially technical and game modding tasks. For those who regularly use it, it acts like a drug, rotting your brain away, making you unable to act or think without relying on it, which some argue is its main purpose. People like this range from asking Grok or ChatGPT what a 3-word sentence means, all the way to to people who throw away their lives to defend the technology, attacking people who say it's not all it's cracked up to be, even [spending tens of thousands of dollars running a 24/7 DDoS attack for over a week straight](https://blog.xkeeper.net/the-cutting-room-floor/tcrf-2026-ddos-postmortem/) targetting a free information source purely because they block users who use Generative AI.

In reality, Generative AI is - factually - a bias machine. You train it on what you want it to do, you tell it what you want it to do, and it does it, claiming both you and it are "100% correct" despite 99.99% of the time both you and it messing up horribly. In regards to models designed to work with game code, most if not all of its output, even from the best models publicly-available, will spit out random functionless gobbledy-goop at worst, or functional but completely unreadable and technically useless code at best. Therefore, you'd be ***INFINITELY MORE PRODUCTIVE*** learning how to do computing and game modding tasks yourself rather than relying on a machine to do it for you. If you ask the machine for the answers, you have a very small chance of getting the answers, and even if you do, only you will be able to arrive at the answer. If you learn how to arrive at the answer, you know how you got there and you can teach other people. The machine will exist forever, but you will not. Wouldn't it be a waste if more people didn't learn how to do this stuff?

In total, no, Generative AI did not create any of these patches. Attempting to use Generative AI to create Host Filesystem patches not only robs you of a real, useful learning experience that helps you and others grow as people, but if it eventually manages to succeed, it takes away the fun of making them from the real people who have been making them all this time. I'm not going to block your access to this repository if you use Generative AI in the same way that "Smoking Kills" ads don't stop you from buying cigarettes if you're a smoker, but smoking is a detriment to society and helps no one, if you get what I mean.
