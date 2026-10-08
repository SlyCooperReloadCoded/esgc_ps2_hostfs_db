# Star Wars: Starfighter

This patch, created by modeco80, completely separates this game from its disc image. This was a real feat considering it was previously hardcoded to use a set LBA for each file. This one is an xdelta patch rather than a LunarIPS patch, and its source code can be found at the link below:

https://github.com/modeco80/europa-hostfs

To clarify what the "StreamDirs" part of the setup instructions mean, you simply need to open the "LEC.REG" file included with the game (it's a real registry entry, careful not to merge it!) and change this line:

***"StreamDirs"="$STREAMS\DIALOG;$STREAMS\MUSIC;$STREAMS\CINE"***

so it doesn't contain the dollar signs anymore, like this:

***"StreamDirs"="STREAMS\DIALOG;STREAMS\MUSIC;STREAMS\CINE"***

The rest should be self-explanatory. This patch also makes the game print all debug console output to PCSX2's system console, which seems like what the game original did during development, but who can really say? This is groundbreaking because it allows you to finally scroll through long lists that the console can output.
