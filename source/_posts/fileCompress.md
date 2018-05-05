title: Summary File Compress
date: 2017-11-14 22:28:06
tags:
- Linux
- Raspberry Pi
- Retropie
- File compress
categories:
- Linux
- Raspberry Pi
- Retropie
---

It is a summary to uncompress different type of files, some there are necesary to compress or extract to run rooms on RetroPi or other linux distribution. I prefer use [tar](https://www.gnu.org/software/tar/manual/tar.html) to compress and uncompress files.

## Tar:

To use tar, the first argument it is mode:
```
-c  create an archive (files to archive, archive from files)
-x  extract an archive (archive to files, files from archive)
```
And the next arguments are options:
```
-f FILE  name of archive - must specify unless using tape drive for archive
-v       be verbose, list all files being archived/extracted
-z       create/extract archive with gzip/gunzip
-j       create/extract archive with bzip2/bunzip2
-J       create/extract archive with XZ
```

For example:

* Compress (gzip) and package (tar) the directory myfiles to create myfiles.tar.gz: `$ tar -czvf myfiles.tar.gz myfiles`
* Uncompress (gzip) and unpack compressed package, extracting contents from myfiles: `$ tar -xzvf myfiles.tar.gz`

## Other File Compression Tools:

* ### .rar:
  - Install: `sudo apt-get install unrar`
  - Extract: `unrar e file.rar`
* ### .ecm:
  - Install: `sudo apt-get install ecm`
  - Extract: `ecm-uncompress file.ecm`
  - Compress: `ecm-compress file`
* ### .mdf (If you need create .cue for playstation):
  - Install: `sudo apt-get install mdf2iso`
  - Extract: `mdf2iso file.mdf`
  - Compress or generate cue or toc files: `mdf2ios --cue file`
* ### .7z:
  - Install: `sudo apt-get install p7zip-full`
  - Extract: `p7zip -d file.7z`

* ### .zip:
  - Install: `sudo apt-get install unzip`
  - Extract: `unzip file.zip`
  - Compress: `zip name.zip ./file_to_compress`
