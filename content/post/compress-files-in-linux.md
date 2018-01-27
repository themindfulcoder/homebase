---
title: "Compress Files in Linux"
date: 2017-11-10
draft: false
---

# Compress files in Linux

There are many different ways to compress files, however, in my experience the options I am about to share with you are the most common.

### TAR.GZ

**tar** is an acronym for tape-archive. It is an archiving tool by default, which really means creating a single file from a collection of files. It has a wealth of options, some of which will allow you to compress the archive.

``` bash
tar cfz /path/to/my-compressed-file.tar.gz /path/to/my-folder-to-compress
```

`c` Create a new archive.

`f` Specify the name of the compressed file.

`z` Use gzip compression on the archived file.

### ZIP

**zip** is more commonly known than **tar** across operating systems and available on most distributions by default. It does both archiving and compression as a singular feat.

``` bash
zip -r /path/to/my-compressed-file.zip /path/to/my-folder-to-compress
```

`r` Recursively add items in the source folder.

### 7Z

**7z** is the swiss army knife of archiving and compression tools. The package name is p7zip. **7z** is an open standard compression, it features many alternative compression options including **gzip** and **zip** used above.

``` bash
7z a /path/to/my-compressed-file.7z /path/to/my-folder-to-compress
```

`a` Include all files, including already archived files.

### Conclusion

Hopefully you are aware of some of the options available to you when you wish to compress files in linux.