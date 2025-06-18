

#ixaya-swf

Ixaya ("opening your eyes" in Nahuatl) is a library for parsing/loading FLASH SWF files. It can be used as a basis for the development of tools that consume, modify, or produce SWF files.

#Licence

LGPLv2.1, see LICENSE file

#Origin

Published on 01/Mar/2014.

This library was initially developed by Marcos Ortega from the document "SWF FILE FORMAT SPECIFICATION" published by Adobe in: http://www.adobe.com


#Use


This library was developed with the aim of extracting data from SWF files.

Ixaya-swf does not yet extract all objects within a SWF. The current version extracts shapes (vector graphics), binary assets (jpeg images and others), sounds (mp3s and PCM), lossless (PNG bitmaps), and movie clips.


#Code Features

Ixaya-swf was conceived and developed prioritising the ease of integration into other projects, characterised by:

- It consists of only two files ("ixaya-swf.h" and "ixaya-swf.c").
- It is mandatory that only these include "stdio.h" and "string.h".
- Optionally depends on these includes "stdlib.h" and "assert.h".
- Allows personalised memory management.

Thanks to its current structure, Ixaya-swf can be integrated into most native code projects to:

- Windows
- Linux
- Mac
- iOS
- Android
- Blackberry 10
- etc..


#ZLIB Dependency


Ixaya-swf depends on a function that performs content decompression in ZLIB format. The project where Ixaya-swf is to be integrated must provide a callback to decompress ZLIB. See demos and invocations to the "ixaSwfLoadFile" method.

#Example Code


```c
#include "ixaya-swf.h"

...

IxaBOOL uncompressSwfZlib(IxaUI8* ptrDest, const IxaUI32 destLen, const IxaUI8* ptrSrc, const IxaUI32 srcLen);

...

int main(...){
   STIXA_SwfFile swfFile;
   ixaSwfFileInit(&swfFile);
   if(ixaSwfLoadFile(&swfFile, "/swfPath.swf", uncompressSwfZlib)){
      /*
        Explore the STIXA_SwfFile structure:
        movie clips, sounds, shapes, lossless, bits, etc...
      */
   } 
   ixaSwfFileFinalize(&swfFile);
}

```
