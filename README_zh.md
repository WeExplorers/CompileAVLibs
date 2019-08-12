# 简介
做音视频开发，除了平台提供的SDK外，我们经常会用到一些优秀的第三方开源库，这里我们将介绍下lame, fad-aac, x264的编译及使用。

### [lame](http://lame.sourceforge.net/download.php)
目前，LAME被认为是中高比特率和VBR的最佳MP3编码器，主要得益于其开发人员的专注工作和开源许可模式，使该项目能够利用来自世界各地的工程资源。 质量和速度的提升仍在继续，可能使LAME成为唯一仍在积极开发的MP3编码器。

### [fdk-aac](https://sourceforge.net/projects/opencore-amr/files/fdk-aac/)

Fraunhofer FDK AAC是由Fraunhofer IIS开发的高质量开源AAC编码器库。 它是针对Android正式发布的，但已被移植到其他平台。 Winamp中包含的许可Fraunhofer AAC编解码器（通常称为FhG AAC）与FDK AAC编解码器不同。FDK AAC是一个目前效率很高的aac编解码库。

### [x264](https://www.videolan.org/developers/x264.html)

x264是一个免费的开源软件库和VideoLAN开发的命令行实用程序，用于将视频流编码为H.264 / MPEG-4 AVC格式。 它是根据GNU通用公共许可证条款发布的。

# 编译

lame, fad-aac, x264的编译其实很简单，github上有现成的build shell, 但有些并非在机器上就能跑起来。所以针对一些错误，我对一些build shell做了少许改动力，支持 x86_64, arm64e, arm64, armv7s, armv7架构的编译。

接下来我们就要开始编译了，请先从[这里下载](https://github.com/masterav/CompileAVLibs)编译需要用的代码、脚本和一些说明，下载后，直接进行编译就行，很省时间。

#### Build lame  

1. 进入目录 **lame-3.100** , `cd lame-3.100`.
2. 更改脚本文件的权限, `sudo chmod 777 build-lame.sh`.
3. 运行脚本, `sudo sh ./build-lame.sh` 

你也可以参考脚本使用说明 [lame build guide](lame-3.100/README.md).

#### Build fdk-aac    

1. 进入目录 **fdk-aac-2.0.0** , `cd fdk-aac-2.0.0`.
2. 更改脚本文件的权限, `sudo chmod 777 build-fdk-aac.sh`.
3. 运行脚本, `sudo sh ./build-fdk-aac.sh` 

你也可以参考脚本使用说明 [fdk-aac build guide](fdk-aac-2.0.0/README.md).

#### Build x264  

1. 进入目录 **x264-20190809-2245** , `cd x264-20190809-2245`.
2. 更改脚本文件的权限, `sudo chmod 777 build-x264.sh`.
3. 运行脚本, `sudo sh ./build-x264.sh` 

你也可以参考脚本使用说明 [x264 build guide](x264-20190809-2245/README.md).

#### 编译可能碰到的问题

 - `No working C compiler found.`
    可能是xcode路径问题，终端输入命令：
    sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer/

 - `Found no assembler,Minimum version is nasm-x.x.x` 或
    `Found no assembler,Minimum version is yasm-x.x.x`
     原因是没有安装yasm/nasm或yasm/nasm版本太低，需要重新安装nasm/yasm。
    `brew install nasm` 或 `brew install yasm`.

- 编译i386遇到`No working C compiler found`
  有两种解决办法，任选一种就好：
  1. 可以直接将i386略过编译，将`i386`从编译脚本**ARCHS="arm64 x86_64 i386 armv7 armv7s"** 中删除，然后重新编译
  2. 在终端输入`./build-x264.sh arm64e arm64 x86_64 armv7s`进行编译。


# 参考

- https://www.jianshu.com/p/b7881a4467db
