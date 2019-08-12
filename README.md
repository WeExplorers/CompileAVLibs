# Compile Audio/Video Libraries on MacOS
Introduce how to compile the essential audio, video third libraries, here including lame, fad-aac and x264.

## [lame](http://lame.sourceforge.net/download.php)

Today, LAME is considered the best MP3 encoder at mid-high bitrates and at VBR, mostly thanks to the dedicated work of its developers and the open source licensing model that allowed the project to tap into engineering resources from all around the world. Both quality and speed improvements are still happening, probably making LAME the only MP3 encoder still being actively developed.

#### Build lame  

1. Enter **lame-3.100** folder, `cd lame-3.100`.
2. Change shell rights, `sudo chmod 777 build-lame.sh`.
3. Run build shell, `sudo sh ./build-lame.sh` 

You can also refer [lame shell usage](lame-3.100/README.md).


## [fdk-aac](https://sourceforge.net/projects/opencore-amr/files/fdk-aac/)

The Fraunhofer FDK AAC is a high-quality open-source AAC encoder library developed by Fraunhofer IIS. It was officially released for Android, but has been ported to other platforms. The licensed Fraunhofer AAC codec included in Winamp (often called FhG AAC) is not the same as the FDK AAC codec.

#### Build fdk-aac  

1. Enter **fdk-aac-2.0.0** folder, `fdk-aac-2.0.0`.
2. Change shell rights, `sudo chmod 777 build-fdk-aac.sh`.
3. Run build shell, `sudo sh ./build-fdk-aac.sh` 

You can also refer [fdk-aac shell usage](fdk-aac-2.0.0/README.md).

## [x264](https://www.videolan.org/developers/x264.html)

x264 is a free and open-source software library and a command-line utility developed by VideoLAN for encoding video streams into the H.264/MPEG-4 AVC format. It is released under the terms of the GNU General Public License.

#### Build x264  

1. Enter **x264-20190809-2245** folder, `x264-20190809-2245`.
2. Change shell rights, `sudo chmod 777 build-x264.sh`.
3. Run build shell, `sudo sh ./build-x264.sh` 

You can also refer [x264 shell usage](x264-20190809-2245/README.md).


## Possible Issues

- `No working C compiler found`.  
  Maybe it's a problem of Xcode, so run `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer/`
  
- `Found no assembler, Minimum version is nasm-x.x.x or yasm-x.x.x`.  
  It says your assembler version is too low, just update:  
  `brew install nasm` or `brew install yasm`.
  
- Compile for i386 platform, encounters `No working C compiler found`.  
  You can resolve it by any one of below two ways:
  1. Remove `i386` from `ARCHS="x86_64 i386 arm64e arm64 armv7s"` in build shell .
  2. Run `sudo sh ./build-xxx.sh arm64e arm64 x86_64 armv7s`.

  
## Reference

- https://www.jianshu.com/p/b7881a4467db

