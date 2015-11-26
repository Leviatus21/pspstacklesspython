## Music Support ##

Currently, beyond the pspsnd audio support provided by python-psp, there are currently OGG and MP3 support built in PSP Stackless Python. Below you find some information on module usage:
Information

### OGG Vorbis support ###

  * I have added a basic OGG Vorbis support for the port. The API is based on oggplayer from PSPMediaCenter. The problem is that i loads the entire file into memory and playbacks it from there. On MP3 this doesnt happens.. more below.
  * The API for the OGG is very simple, a sample application follows.

### MP3 Support ###

  * With the great help from Ghoti (thanks Rein) the MP3 streaming playback is now available transparently. What streaming means? Your application wont load the entire file into memory for playback. The application creates a buffer and loads small chunks from disk as needed. This leaves a lot of memory to the interpreter and you play with. In my tests, my interpreter have around 18Mb RAM available.

## Samples ##

### OGG ###

Inside your PSP/GAME/Stackless (or PSP/GAME3XX/Stackless) dir, create a script.py file containing the following code, also place your OGG file and change its name in the "load" function.
```
import pspogg, psp2d

pspogg.init(2)
pspogg.load('REALTEST.OGG')

pspogg.play()

while 1:
    pad = psp2d.Controller()
    if pspogg.endofstream() == 1 or pad.cross:
        print pspogg.getsec()
        print "end of stream"
        pspogg.end()
        break

print "exit"
```

### MP3 ###

Inside your PSP/GAME/Stackless (or PSP/GAME3XX/Stackless) dir, create a script.py file containing the following code, also place your MP3 file and change its name in the "load" function.

```
import pspmp3, psp2d

pspmp3.init(1)
pspmp3.load('test.mp3')
pspmp3.play()

while 1:
    global lastPad
    pad = psp2d.Controller()
    if pspmp3.endofstream() == 1 or pad.cross:
        print pspmp3.gettime()
        pspmp3.end()
       break

print "exit"
```

## Module API ##

The modules have the following API:

### pspogg ###

  * pspogg.init(ch) Initializes the OGGVorbis subsystem.
  * pspogg.load(file) Loads an OGG file.
  * pspogg.stop() Stop OGG playback.
  * pspogg.pause() Pauses OGG playback, call again to unpause.
  * pspogg.play() Play a loaded OGG file.
  * pspogg.endofstream() Returns 1 if stream has ended.
  * pspogg.getsec() Returns the stream play time in seconds.
  * pspogg.getmin() Returns the stream play time in minutes.
  * pspogg.gethour() Returns the stream play time in hours.
  * pspogg.volume(vol) Sets the OGG subsystem volume.
  * pspogg.end() Stops playback and free up used memory.

### pspmp3 ###

  * pspmp3.init(ch) Initializes the MP3 subsystem.
  * pspmp3.load(file) Loads a MP3 file.
  * pspmp3.stop() Stop MP3 playback.
  * pspmp3.pause() Pauses MP3 playback, call again to unpause.
  * pspmp3.play() Play a loaded MP3 file.
  * pspmp3.endofstream() Returns 1 if stream has ended.
  * pspmp3.gettime() Returns the stream play time in format HH:MM:SS.
  * pspmp3.freetune() Free up used memory and releases MP3 subsystem.
  * pspmp3.end() Stops playback and calls freetune.