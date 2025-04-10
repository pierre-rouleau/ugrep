This directory contains a subset of the LZMA SDK lzma2301/C files

LZMA SDK is available from https://7-zip.org/sdk.html

LZMA SDK is placed in the public domain.

LZMA SDK by Igor Pavlov.

Updated 23.01 to apply YOKOTA Hiroshi's patches:
https://salsa.debian.org/debian/7zip/-/blob/master/debian/patches/0002-Disable-hardware-acceleration-support-on-armel.patch?ref_type=heads

Included in this directory is a new C API written for ugrep to simplify
decompression:

- viizip.h   API declarations, see below (hides implementation details)
- viizip.c   API implementation
- libviiz.a  static library compiled from source

The 7zip decompressor API state with hidden members:
    struct viizip

To create a new 7zip decompressor for the given 7zip file:
    struct viizip *viinew(FILE *file)

To free viizip decompressor state:
    void viifree(struct viizip *viizip)

To get archive part pathname and info, start decompressing:
    int viiget(struct viizip *viizip, char *name, size_t max, time_t *mtime, uint64_t *usize)

To decompress up to len bytes into buf[], return number of bytes decompressed:
    ssize_t viidec(struct viizip *viizip, unsigned char *buf, size_t len)

The viizip files are part of the ugrep project licensed BSD-3.
