## Version Info ##

Stackless Python for PSP Version 2.5.2 Release 1

### Installation ###

  * The install pack consists of the EBOOT.PBP and the standard library.
  * Install EBOOT.PBP in your PSP/GAME (if using 3.xx mode) or in PSP/GAME3xx.
  * To install library, place the python.zip file together with the EBOOT.PBP.

### Running your applications (scripts) ###

  * Once EBOOT.PBP and the python library are installed on your Memory Stick, you can run it as any homebrew.
  * When launched, the interpreter will try to find a "script.py" file in its directory and run it
  * If there is none, it will exit to XMB.
  * All output is mapped into a file called pytrace.txt so check this file for any error.

The directory structure is the same as the computer, 3rd party modules goes into ms0://python/site-packages/ directory.