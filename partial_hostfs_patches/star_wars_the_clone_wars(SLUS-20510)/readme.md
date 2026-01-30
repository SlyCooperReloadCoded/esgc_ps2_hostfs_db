# Star Wars: The Clone Wars (SLUS-20510)

This patch separates the "SP", "multi", "sampdata", and "IRX" folders from the disc image, potentially separating the "Addon" folder too, although my testing has been inconclusive. A native HostFS flag exists at 0x36ED00, however this only loads the IRX modules from HostFS, the rest of the data still loading from disc.
