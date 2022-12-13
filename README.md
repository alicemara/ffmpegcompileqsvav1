# ffmpegcompileqsvav1
A quick personal script for making ffmpeg on Ubuntu 22.04 LTS on a machine with a Intel Arc card for use with AV1 encoding/decoding and oneVPL.

This is a condensed version of the guide that FFmpeg has at: https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

The big difference from that guide is that libvpl-dev is installed during the package installations and --enable-libvpl flag is added to the flags when compiling FFmpeg. 

(Note that you will get errors if you try to enable both libvpl AND libmfx.) 

If you're just wanting to compile FFmpeg with oneVPL you can follow the guide linked above and run when installing dependencies at the beginning:

`
sudo apt-get install libvpl-dev
`

and add the flag `--enable-libvpl` when at the compiling FFmpeg stage like so:

```
cd ~/ffmpeg_sources && \
wget -O ffmpeg-snapshot.tar.bz2 https://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2 && \
tar xjvf ffmpeg-snapshot.tar.bz2 && \
cd ffmpeg && \
PATH="$HOME/bin:$PATH" PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig" ./configure \
  --prefix="$HOME/ffmpeg_build" \
  --pkg-config-flags="--static" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" \
  --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --extra-libs="-lpthread -lm" \
  --ld="g++" \
  --bindir="$HOME/bin" \
  --enable-gpl \
  --enable-gnutls \
  --enable-libaom \
  --enable-libass \
  --enable-libfdk-aac \
  --enable-libfreetype \
  --enable-libmp3lame \
  --enable-libopus \
  --enable-libsvtav1 \
  --enable-libdav1d \
  --enable-libvorbis \
  --enable-libvpx \
  --enable-libx264 \
  --enable-libx265 \
  --enable-libvpl \
  --enable-nonfree && \
PATH="$HOME/bin:$PATH" make && \
make install && \
hash -r
```


Use at your own risk!
