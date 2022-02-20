# Fuzz-typechecker-for-Z---Ubuntu
Installation of Fuzz typechecker for Z in Ubuntu 20.04

## Do the following commands before starting with Fuzz


```

- Download ![image](https://user-images.githubusercontent.com/63869574/154747372-4e92fff8-9eb3-4477-b40f-2ce43bf834ba.png) from 
https://tug.org/texlive/acquire-netinstall.html
Then (https://www.tug.org/texlive/doc/texlive-en/texlive-en.html#cygwin):
- Unzip and go to folder Then:
```sudo perl /install-tl
sudo apt-get install tcl
```

-Clone Fuzz, install Bison, gawk, gcc, flex (https://spivey.oriel.ox.ac.uk/corner/Fuzz_typechecker_for_Z#Installation)
```
git clone https://github.com/Spivoxity/fuzz.git
cd fuzz/
sudo apt install autoconf
autoconf
./configure
make
```
If this does not work, try modify file src\Makefile.in, line 34 to ```libdir = ./src```, or  to:
```
#
# src/Makefile.in
#
# This file is part of fuzz2000
# Copyright (c) 1982--2006 J. M. Spivey
# All rights reserved
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# 1. Redistributions of source code must retain the above copyright notice,
#    this list of conditions and the following disclaimer.
# 2. Redistributions in binary form must reproduce the above copyright notice,
#    this list of conditions and the following disclaimer in the documentation
#    and/or other materials provided with the distribution.
# 3. The name of the author may not be used to endorse or promote products
#    derived from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
# IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES
# OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.
# IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
# PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
# OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
# WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
# OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
# ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#

# Config stuff
prefix = @prefix@
exec_prefix = @exec_prefix@
libdir = ./src
VERSION = @PACKAGE_VERSION@
AWK = @AWK@
# End of config

all: fuzz fuzzlib

FUZZ = zparse.o zscan.o main.o spec.o type.o frame.o dict.o \
	sched.o pretty.o error.o expr.o alloc.o unify.o schema.o dump.o
GEN = y.output zparse.c symbol.h absyn.h zscan.c

LFLAGS = -s
CC= clang
CPP=cpp
DEFINES = -DDEBUG -DANSI -DASSUME

main.o : DEFINES += -DLIBDIR=\"$(libdir)\" -Dfuzz_version=\"$(VERSION)\"
zscan.o : DEFINES += -DYY_NO_UNPUT -DYY_NO_INPUT

fuzz: $(FUZZ)
	$(CC) $(CFLAGS) -o fuzz $(FUZZ)

clean:
	rm -f *.o $(GEN)

distclean: clean
	rm -f fuzz fuzzlib minilib

realclean: distclean

zparse.c zparse.h : zparse.y
	bison -dv -y zparse.y -o zparse.c

zscan.c : zscan.l
	flex -o$@ $< 

absyn.h: absyn.x absyn.k
	$(AWK) -f absyn.k absyn.x >absyn.h

fuzzlib: symdef.x fuzzlib.k fuzzlib.x minilib.x opdef.x zparse.h
	$(CPP) $(DEFINES) symdef.x >symdef.i
	$(AWK) -f fuzzlib.k output=fuzzlib fuzzlib.x >fuzzlib
	$(AWK) -f fuzzlib.k output=minilib minilib.x >minilib
	rm symdef.i

$(FUZZ): fuzz.h proto.h zparse.h absyn.h

%.o : %.c
	$(CC) $(CFLAGS) -Wall -c $(DEFINES) $<

.DELETE_ON_ERROR:

force:
```
Then do 
```
sudo apt-get install llvm
sudo apt-get install clang
./configure
make clean
make
```

# Run
From the fuzz folder you can run the example in tex folder via:

![image](https://user-images.githubusercontent.com/63869574/154824140-7059c932-9c07-441f-a0d5-9c0fb8c177f6.png)

Or create environmental variable.




## Side notes

Install Cygmin dependencies (not sure if this step is neccesary, https://www.tug.org/texlive/quickinstall.html , http://www.delorie.com/howto/cygwin/fuzz-for-z-install-use-cygwin.html)
```sudo apt-get update -y
sudo apt-get install -y fontconfig-config
sudo apt install ghostscript
sudo apt-get install -y libxaw7-dev
sudo apt-get install libncurses5-dev libncursesw5-dev
```

Also
```
sudo -i // to get to root
apt-get dist-upgrade
apt-get install bison -y
sudo apt-get install gawk
apt-get clean
sudo apt install build-essential  // to install gcc
gcc --version
sudo apt-get clean
```
