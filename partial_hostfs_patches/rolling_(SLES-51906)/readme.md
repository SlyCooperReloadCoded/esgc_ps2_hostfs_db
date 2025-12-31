# Rolling (SLES-51906)

This patch separates the game's data archive (roll_p.wad) as well as the IRX modules from its disc image, but still requires it to be present for it to properly read everything else.

The result is MUCH faster loading times, as well as potential for future modding.

Disc loading times:

https://github.com/user-attachments/assets/5f169c00-4cb0-4073-9cad-8206fd5710d4

Host Filesystem loading times:

https://github.com/user-attachments/assets/39817700-5ac0-4009-86d9-4319583d1b32


