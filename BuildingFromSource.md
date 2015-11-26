To compile PSP Stackless Python yourself and create the EBOOT.PBP, there are some steps involved to get the final app.

## Requirements ##

You will need an up-to-date PSPToolchain. I use Cygwin on Windows so download it then get the toolchain using the svn tool from: svn://svn.ps2dev.org/psp/trunk/psptoolchain
The toolchain is known to build on other platforms (Linux, MacOS).

### Libraries ###

Download all via SVN. For each one, follow the steps for building and installing in its README or README.psp. Usually, it follows the "configure , make, make install".

  * mikmodlib - svn://svn.ps2dev.org/psp/trunk/mikmodlib
  * libpng - svn://svn.ps2dev.org/psp/trunk/libpng
  * jpeg - svn://svn.ps2dev.org/psp/trunk/jpeg
  * zlib - svn://svn.ps2dev.org/psp/trunk/zlib
  * bzip2 - svn://svn.ps2dev.org/psp/trunk/bzip2
  * libmad(MP3) - svn://svn.ps2dev.org/psp/trunk/libmad
  * libTremor(OGG) - svn://svn.ps2dev.org/psp/trunk/libTremor
  * SQLite - svn://svn.ps2dev.org/psp/trunk/sqlite

Download cpplibs, imaging and pymaging libraries and have them in the same directory where you will place the PSP Stackless sources.

  * cpplibs - http://pspstacklesspython.googlecode.com/svn/cpplibs
  * imaging - http://pspstacklesspython.googlecode.com/svn/imaging
  * pymaging - http://pspstacklesspython.googlecode.com/svn/pymaging

Build cpplibs in its directory and imaging in build-psp dir (both using 'make'). No need to "make install".

## Building ##

Download the PSP Stackless Python using SVN to the chosen directory. Select the latest release from the tags directory or download directly from the maintenance branch.

  * http://pspstacklesspython.googlecode.com/svn/branches/pspstackless-25-maint
for maintenance branch or

  * http://pspstacklesspython.googlecode.com/svn/tags/PSPStacklessPython2.5.2_R1
for Stackless Python 2.5.2 Release 1

You will have a structure like this:

```
~/PSP
   |-StacklessPSP-src
       |-Python/
       |-Include/
       |-Lib
       |-PSP/
       |- many more....
   |-cpplibs
       |-libpsp2d/
       |-libpspsnd/
       |-others....
   |-imaging
       |-build-psp/
       |-src/
       |-others...
   |-pymaging
       |-Makefile
       |-color.h
       |-others...
```


Enter the StacklessPSP-src/PSP/ directory and type 'make'. If nothing went wrong, you should have a EBOOT.PBP file inside this directory after some time.

The Python libraries are a copy of StacklessPSP-src/Lib. Remember to remove the .svn,  plat-**, Lib/test directories since they will waste you memory stick space.**

For convenience, you can type 'make release' to have the EBOOT and the Python libraries packed in a zip file in a directory named StacklessPSP-[version](version.md) in inside your main PSP development directory (the one having imaging, cpplibs, etc).