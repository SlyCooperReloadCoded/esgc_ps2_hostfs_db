# Rolling (SLES-51906)

This patch separate's the game's data archive (roll_p.wad) as well as the IRX modules from the disc image, but still requires the rest to be read from the original disc image.

The result is MUCH faster loading times, as well as potential for future modding.

Disc loading times:

https://github.com/user-attachments/assets/5f169c00-4cb0-4073-9cad-8206fd5710d4

Host Filesystem loading times:

https://github.com/user-attachments/assets/39817700-5ac0-4009-86d9-4319583d1b32

