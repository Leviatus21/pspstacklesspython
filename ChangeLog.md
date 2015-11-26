The release information will be put in this page with the newest release on top.

## Version 2.5.2 ##

### Release 1 ###

  * Updated to Stackless Python 2.5.2 from http://svn.python.org/projects/stackless/branches/release25-maint [revision 61023](https://code.google.com/p/pspstacklesspython/source/detail?r=61023).
  * Fix for [Issue #1](https://code.google.com/p/pspstacklesspython/issues/detail?id=#1) where the default build requires the OpenSSL lib to compile hashlib module. Now the module is built only if the flag WITH\_SSL is enabled in Makefile.
  * Updated to latest libs revision from svn://www.fraca7.net/python/trunk/python [revision 172](https://code.google.com/p/pspstacklesspython/source/detail?r=172).
  * Added pach from MagerValp to fix some issues on pspos, psp2d, pspnet.
  * Added support for large memory on PSP Slim and changed memory allocation.
  * Changed release method to support all python library from a Zip file.
  * Log now is placed inside Python own dir instead of MS root.
  * Some fixes to Makefile.base that prevented "make release" to run on some platforms.
  * Not setting clockspeed on main.c anymore.

## Version 2.5.1 ##

### Release 1 ###

  * Application have been made User Mode
  * Almost all modules from Python 2.5.1 supported
  * SSL support removed due non working
  * MP3 and OGG support
  * time and datetime modules now displays the correct date and time
  * WPA support for pspnet module