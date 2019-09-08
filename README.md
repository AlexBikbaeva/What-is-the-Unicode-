# What is the Unicode?
The moto is simple:
>Unicode provides a unique number for every character,  
>no matter what the platform,  
>no matter what the program,  
>no matter what the language.

The Unicode Standard is the universal character encoding standard used for representation of scripts (characters) for every language in the world and is maintained by [Unicode Consortium](https://www.unicode.org/consortium/utc.html).  Each letter, digit or symbol has a unique numeric value which is called a *code point*, no matter what the platform, device, application or the writing system is. For example, English letter *A* is encoded as *U+0041*, where *U+* is the prefix that all characters have, that basically means “Unicode”, and the other part is a hexadecimal number. 

The design of Unicode Standard is based on ***10 Fundamental Principles***, and not all of them can be satisfied simultaneously (from *The Unicode Standard / the Unicode Consortium ; edited by Julie D. Allen ... [et al.]. — Version 6.0.*):

***1) Universality***  
The Unicode Standard provides a single, universal repertoire.

***2) Efficiency***  
Unicode data is simple to parse and process.

***3) Characters, not glyphs***  
The Unicode Standard encodes characters, but not *glyphs* (*the elements of writing, like ligatures*). 

***4) Semantics***  
Characters’ semantics is well-defined.

***5) Plain text***  
Unicode characters represent plain text.

***6) Logical order***  
Logical order is the default for memory representation.

***7) Unification***  
The Unicode Standard unifies duplicate characters within scripts across languages.

***8) Dynamic composition***  
 Accented forms can be dynamically composed.

***9) Stability***  
Characters, once assigned, cannot be reassigned and key properties are immutable.

***10) Convertibility***  
Accurate convertibility is guaranteed between the Unicode Standard and other accepted encoding standards.

The Unicode standard represents every existing character, like punctuation marks, mathematical symbols, technical symbols, alphabets such as Chinese, Thai or Arabic, whereas *ASCII* (American Standard Code for Information Interchange) supports only a set of 128 basic English characters.  

## Differences between *UTF-8* and *UTF-16*  

***UTF*** stands for _Universal Transformation Format_. It defines an algorithm to map every Unicode *code point* to a unique byte sequence. There are several forms of Unicode encodings: ***UTF-8***, ***UTF-16*** and *UTF-32*. 

***UTF-8*** and ***UTF-16*** are the only two established standards for encoding and both have a variable width. The main difference between the two is in the number of bytes to represent a character in memory. For instance, ***UTF-8*** uses minimum 1 byte or 8 bits to encode the data, while ***UTF-16*** uses 2 bytes or 16 bits. Consequently, this has an impact on the resulting size of the encoded files. ***UTF-8*** uses only one byte to represent common English characters. European (Latin), Hebrew, and Arabic characters are represented with two bytes, while three bytes are used to Chinese, Japanese, Korean, and other Asian characters. Any other additional Unicode characters can be represented with four bytes. ***UTF-16***, however, represents *BMP* (*Basic Multilingual Plane*) characters, including Latin, Cyrillic, most Chinese and most Japanese with 2 bytes, that helps to speed up indexing and calculating *code point* count in case the text does not contain supplementary characters.

***UTF-8*** extends the identity encoding of the *ASCII* character set, which means that an *ASCII* character will be encoded in the same manner by the ***UTF-8*** encoding of Unicode as by the identity encoding of *ASCII*, so the file size will stay the same. It also provides decent backwards compatibility in most cases. But if encoded in ***UTF-16***, the encoded file would be about twice as big as the same file encoded in ***UTF-8***.

Another thing is that ***UTF-8*** is byte oriented (and ***UTF-16*** is not), thus there are no problems with  byte oriented networks or files and *Big Endian / Little Endian issue* (*BE/LE issue*). On the contrary, ***UTF-16*** needs to establish byte order to work with byte oriented networks and files.

If using ***UTF-16*** as a fixed-length encoding in common scenarios (especially in US / EU / countries with Cyrillic alphabets / Israel / Arab countries / Iran and others) it mostly works, but it may also lead to broken support in cases where it does not work.Therefore, the programmers have to be aware of surrogate pairs and handle them properly in cases where it matters.

***UTF-8*** is widely used in email systems and the web. Besides, it is used as the default encoding by many software programs. 

Overall, ***UTF-8*** is good for text files and network protocols (like HTML) as there is *ASCII*-compatibility and no *BE/LE issue*, whereas ***UTF-16*** may be better for in-memory representations BE/LE issue is irrelevant in there and the indexing process is faster.

**To sum up**:  

1) ***UTF-8*** uses **minimum 1 byte** to encode the data, while ***UTF-16*** uses **2 bytes**.  
2) ***UTF-8*** is **backwards compatible with *ASCII***, yet ***UTF-16*** is not.  
3) ***UTF-8*** is **byte oriented and** ***UTF-16*** needs to **establish byte order** to work with byte oriented networks and files.  
4) ***UTF-8*** is more efficient in working with **text files and network protocols**, while ***UTF-16*** is well suited for **in-memory representations**.
