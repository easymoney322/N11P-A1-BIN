# N11P-A1-BIN
Statically-linked & stripped binary files for ASUS N11P A1 with 2.6.36 GNU/Linux Kernel (Last Firmware Update from 2017 - 3.0.0.4.380_7378)

Asus N11P A1 has MediaTek MT7620N CPU (32bit MIPS-EL 24kec), which resolves into little-endian MIPS32 rel2 v1 by GCC. Terminal is vt100.

Cross compiled with GlibC (--enable-kernel=2.6.36) and Mipsel-linux-gnu-gcc (-EL -march=24kec -static -Os -s -Wl,-Bstatic -static-libgcc) for target mipsel-unknown-linux-gnu, by using crosstools-ng on i686-pc-linux-gnu system.

<<<<<<< HEAD
Sources: 
- TCPDUMP - https://github.com/the-tcpdump-group/tcpdump (required [libpcap](https://github.com/the-tcpdump-group/libpcap) )
- VIM tiny - https://github.com/vim/vim (Required [ncurses] (https://github.com/mirror/ncurses) ) !HIGHLY UNSTABLE, requires termcap! It won't the recognize terminal otherwise. (compiled with variablesvim_cv_memcpy_handles_overlap=set vim_cv_bcopy_handles_overlap=set vim_cv_memmove_handles_overlap=set vim_cv_stat_ignores_slash=set vim_cv_timer_create=set vim_cv_getcwd_broken=set vim_cv_toupper_broken="set" vim_cv_terminfo="set" vim_cv_tgetent=zero ./configure --host=arm-apple-darwin11 --with-tlib=ncurses)

=======
## Sources:
TCPDUMP - https://github.com/the-tcpdump-group/tcpdump (required libpcap - https://github.com/the-tcpdump-group/libpcap )
>>>>>>> efec5b3b9bccdedefff5ad0edc470777b61e7e09


## How to use binaries:
To use a binary, simply transfer it to router memory. Change the binary permissions to 777, and execute by ./%file_name_here% .
I usually do it by using wget from telnet session. Keep in mind, that the read-write areas of router are usually tmpfs, and they will be erased after reloading the router.
