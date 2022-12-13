# ffmpegcompileqsvav1
A quick personal script for making ffmpeg on Ubuntu 22.04 LTS on a machine with a Intel Arc card for use with AV1 encoding/decoding

This is a condensed version of the guide that FFmpeg has at: https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

The big difference from that guide is that libvpl-dev is installed during the package installations and --enable-libvpl flag is added to the flags when compiling FFmpeg.

Use at your own risk!
