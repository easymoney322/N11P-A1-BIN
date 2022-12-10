# N11P-A1-BIN
Statically-linked & stripped binary files for ASUS N11P A1 with 2.6.36 GNU/Linux Kernel (Last Firmware Update from 2017 - 3.0.0.4.380_7378)

Asus N11P A1 has MediaTek MT7620N CPU (32bit MIPS-EL 24kec), which resolves into little-endian MIPS32 rel2 v1 by GCC. Terminal is vt100.

Cross compiled with GlibC (--enable-kernel=2.6.36) and Mipsel-linux-gnu-gcc (-EL -march=24kec -static -Os -s -Wl,-Bstatic -static-libgcc) for target mipsel-unknown-linux-gnu, by using crosstools-ng

## Sources: 
- TCPDUMP - https://github.com/the-tcpdump-group/tcpdump (It was requiring [libpcap](https://github.com/the-tcpdump-group/libpcap) )
- NetCat 0.7.1 - https://netcat.sourceforge.net/download.php 
- File 5.32 from lib magic - https://packages.ubuntu.com/bionic/file **!You need to specify magic.mgc database file with -m option. E.g. ./filemagic -m magic.mgc /etc/icon.ico !**
- VIM 9.0 Tiny - https://github.com/vim/vim (With [ncurses](https://github.com/mirror/ncurses) ) . **Binaries are in vimtiny folder**
- DOOM ASCII :feelsgood: - https://github.com/wojciech-graj/doom-ascii (Requires a wad file to play. You want to play with window size, and the "-scaling n" argument) 
- CURL 7.58.0 (**http only** for now) - https://salsa.debian.org/debian/curl.git (Compiled with -static-libgcc --start-group -lc -lnss_dns -lresolv -Wl,--end-group; glibc was recompiled with --enable-static-nss for this one)


## How to use Binaries
To use a binary, simply transfer it to router memory. Change the binary permissions to 777, and execute by ./%file_name_here% .
I usually do it by using wget from telnet session. Keep in mind, that the read-write areas of router are usually tmpfs, and they will be erased after reloading the router.


## How to Play DOOM :feelsgood:
Put the binary and the wad file in the same folder, add read-write-execute perrmissions for them, execute the doom_ascii.

WAD files have to be for ?1.9? version or above.

If you want to take WAD files from Steam's release of Doom 1993, the original doom wad file is over 10MB, so it probably won't fit in the router's memory. 

**You need to configure your terminal's window size, font and font size to meet the "-scaling n" argument. Passing a negative value as a scaling parameter will cause segmentation fault** You might want to see dev's recomendations on this.

Fire key isn't working by default, since the "use" action is binded to space instead, and the shooting is control (I assume). 

So you need to rebind it by creating and editing ".default.cfg" file in doom_ascii folder. Don't forget to add the permissions for new file too.

The syntax for this file is "key_fire %decimal_id_of_the_key_you_want_to_use_in_scancode_format%", separated by a single space. E.g., if you want to bind fire for "H" key:key_fire 35). Scancodes can be found here https://www.millisecond.com/support/docs/current/html/language/scancodes.htm 
