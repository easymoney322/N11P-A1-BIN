# In case you want to compile it by youself (implying you have all the required libraries installed), these are the commands that I've been using. :finnadie: 
Config log will be located in vim/src/auto/config.log

**Dont forget to change your sysroot , prefix, compiler(s), linker, strip, target (and -march CFLAG), build , host and --with-compiledby= --with-modified-by=**

**When you are recompiling, don't forget to remove old binaries from prefix. System won't be able to overwrite symbolic links otherwise, and the installation will fail**

## Configure 
vim_cv_memcpy_handles_overlap=set vim_cv_bcopy_handles_overlap=set vim_cv_memmove_handles_overlap=set vim_cv_stat_ignores_slash=set vim_cv_getcwd_broken=set vim_cv_tgetent=zero vim_cv_terminfo=set vim_cv_toupper_broken=set CXX=mipsel-linux-gnu-g++ CC=mipsel-linux-gnu-gcc  CFLAGS="-static -march=24kec -Wl,-Bstatic -lc -static-libgcc -lncurses -s -EL -Os --sysroot=/root/x-tools/mipsel-linux-gnu/mipsel-linux-gnu/sysroot" ./configure --build=x86_64-pc-linux-gnu --target=mipsel-unknown-linux-gnu --host=mipsel-unknown-linux-gnu --prefix=/root/x-tools/mipsel-linux-gnu/mipsel-linux-gnu/sysroot --with-tlib=ncurses --with-features=tiny --without-gnome --without-x --disable-selinux --with-compiledby=EasyMoney322 --with-modified-by=EasyMoney322 --disable-gtktest --disable-desktop-database-update LD=mipsel-linux-gnu-ld STRIP=mipsel-linux-gnu-strip LDFLAGS="-static -Wl,-Bstatic -lc -static-libgcc -lncurses"

**Yes, all these vim variables are necessary when cross-compiling. Except, maybe, tgetent.**

## Make 
make -j8 CC=mipsel-linux-gnu-gcc  CFLAGS="-static -march=24kec -Wl,-Bstatic -s -static -lc -static-libgcc -lncurses -EL -Os --sysroot=/root/x-tools/mipsel-linux-gnu/mipsel-linux-gnu/sysroot" CXX=mipsel-linux-gnu-g++ MAKEINFO=false --debug=V -d LD=mipsel-linux-gnu-ld STRIP=mipsel-linux-gnu-strip LDFLAGS="-static -Wl,-Bstatic -lc -lncurses"

## Make install 
make -j8 install CC=mipsel-linux-gnu-gcc  CFLAGS="-static -march=24kec 
-Wl,-Bstatic -s -static -lc -static-libgcc -lncurses -EL -Os 
--sysroot=/root/x-tools/mipsel-linux-gnu/mipsel-linux-gnu/sysroot" 
CXX=mipsel-linux-gnu-g++ MAKEINFO=false 
LD=mipsel-linux-gnu-ld STRIP=mipsel-linux-gnu-strip LDFLAGS="-static 
-Wl,-Bstatic -lc -lncurses"
