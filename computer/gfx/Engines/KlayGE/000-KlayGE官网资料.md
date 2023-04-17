# KlayGE官网资料：

以下内容来自官网，只因官网经常性打不开，这里作为搬运工。

[官网地址](http://www.klayge.org)

[英文wiki地址](http://www.klayge.org/wiki/index.php/Main_Page)

[中文地址wiki](http://www.klayge.org/wiki/index.php/%E9%A6%96%E9%A1%B5)

## 1. 入门必读

### 1.1 协议

**开放源代码协议：General Public License (GPL)**

KlayGE的默认协议是[GNU General Public License](http://www.gnu.org/copyleft/gpl.html) 2.0。换句话说，任何人都可以使用它，而且可以访问到它全部的源代码，但使用KlayGE的项目也必须以GPL 2.0的协议发布。协议的全文请见[gplv2.txt](http://www.gnu.org/licenses/gpl-2.0.txt)。

开放源代码是一种很强大的开发方式，它鼓励分发、合作开发和用户的自由。开放源代码软件的源代码是100%可见的，不会暗藏流氓软件，间谍软件和病毒。

**封闭协议：KlayGE Proprietary License (KPL)**

由于某些原因，有些用户无法使用、或者不希望使用GPL的条款。比如，他们希望使用KlayGE，但不能公开发布源代码。

为了让有那些情况的用户仍考虑使用KlayGE，从4.0开始，在缴纳授权费的情况下，可以启用另一个协议，称为KlayGE Proprietary License（KPL）。因此对于需要避开GPL条款的用户，也有机会为项目购买另一个协议的KlayGE。

**如果你对此封闭协议有兴趣，可以[联系我们](mailto:sales@klayge.org)以获取更多细节。**

### 1.2 下载

## 发布版本

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的发布版本可以从[这里](http://www.klayge.org/downloads/)下载

## 开发版本

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的源代码存放在git分布式版本控制系统中，目前有四个repository，分别是：：

- git clone https://github.com/gongminmin/KlayGE.git klayge-git
- git clone http://bitbucket.org/gongminmin/klayge.git klayge-git
- git clone http://git.code.sf.net/p/klayge/git klayge-git
- git clone https://gongminmin.visualstudio.com/DefaultCollection/_git/KlayGE klayge-git

### 1.3 系统需求

原则上说，[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的目标平台是引擎发布当年的出现的最高端硬件到上一年出现的最低端硬件。目前的具体定义为：

**最低需求**

- Windows 7, macOS或Linux
- 2.0GHz以上的多核CPU
- 4GB内存
- 兼容Shader Model 5.0的显卡

**推荐用于开发的配置**

- Windows 10
- Intel i7或AMD Ryzen
- 8GB内存
- NVIDIA GTX 600系列以上
- 大量硬盘空间
- Visual Studio 2015或2017，并安装了最新的更新
- [Python](http://www.python.org/) 3.4

### 1.4 安装

 **通用**

在编译[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)之前，必须先安装Python 2.7+和CMake 3.4+。然后就可以执行build_external.py来编译和安装[第三方库和工具](http://www.klayge.org/wiki/index.php/第三方库和工具)。[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)在这些[编译器](http://www.klayge.org/wiki/index.php/经过测试的编译器)上通过了测试。

从[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.12.0开始，工程文件里都设置好了include和lib路径，解压后打开Build目录下的相应工程文件就可以直接编译[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)本身。或者执行build_all.py编译[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)、[例子程序](http://www.klayge.org/wiki/index.php/例子程序)和[工具集](http://www.klayge.org/wiki/index.php/工具集)。

从[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.1.0开始，工程文件改用cmake，并且包含有几个python的一站式编译脚本。build_glloader.py用来编译[glloader](http://www.klayge.org/wiki/index.php/Glloader)，build_kfont.py用来编译[kfont](http://www.klayge.org/wiki/index.php/Kfont)，build_KlayGE.py用来编译[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)、[例子程序](http://www.klayge.org/wiki/index.php/例子程序)、[工具集](http://www.klayge.org/wiki/index.php/工具集)和[教程](http://www.klayge.org/wiki/index.php/教程)。build_all.py则可以编译上述所有的东西。这几个.py都有两个可选的命令行参数，第一个表示编译器名，第二个表示配置名。比如："build_all.py vc10 x64"表示用vc10的x64配置来编译。目前支持的编译器名有vc8、vc9、vc10、vc11、vc12、mingw和gcc，支持的配置名有x86、x64、x86_app和arm_app。如果不带参数，那么就会选用存在cfg_build.py中的默认参数。

从[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.4.0开始，第三方库也都采用cmake作工程文件。只需要执行build_external.py就可以完成编译，不需要用到第三方库本身提供的工程文件。

从[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.5.0开始，Android和WinRT版本也采用同样的cmake作工程文件。需要先编译出Windows版的工具集，才能正常编译Android和WinRT版本。具体参见[构建Android版本的方法](http://www.klayge.org/wiki/index.php/构建Android版本的方法)。

编译中如果提示v110_xp工具集找不到，请安装Visual Studio 2012 Update（目前的版本是[Update 4](http://www.microsoft.com/en-us/download/details.aspx?id=39305)）。

**在Win8之前的系统上使用VS2012的用户请注意**

如果安装了DX SDK，VS2012的include/lib目录可能会包含DX SDK的include/lib，这会和VS2012自带的Windows SDK冲突。表现是找不到D3D_FEATURE_LEVEL_11_1等。解决方法是把include/lib目录设置里的DX SDK相关目录去掉。

**MinGW用户请注意**

由于新版本Windows SDK，DirectX SDK和MinGW存在一些不兼容，在默认情况下编译DSound插件的时候，编译器会报告找不到sal.h。这时候需要把VC的sal.h拷到MinGW/include下。然后打开MinGW/lib/gcc/mingw32/4.4.1/include/stddef.h，找到"#define NULL __null"，改成"#define NULL 0"。因为sal.h会把__null定义成别的东西。

**Linux平台**

这里以Ubuntu为例。需要安装wine和相关依赖库。

```
sudo apt-get install wine wine-dev libc6-dev-i386 g++-4.8-multilib libx11-dev libgl1-mesa-dev libglu1-mesa-dev libopenal-dev build-essential
```

有了wine之后，还需要强制wine进入32位模式，因为64位的wine基本没法工作。

```
export WINEARCH=win32
winetricks
```

**OSX平台**

如果没有安装brew.sh，就先运行

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

OSX也需要先安装wine。

```
brew cask install xquartz
brew install wine --without-win64
```


### 1.5 第三方库和工具

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的代码依赖于以下的第三方库和工具。从KlayGE 3.12开始，除了OpenGL ES的SDK，其他库和工具的代码将都包含在KlayGE中。用户可以通过调用build_external.py来编译和安装它们。当然，在执行编译脚本前需要事先安装[Python](http://www.python.org/) 2.7+和[CMake](http://www.cmake.org/) 3.4+。

# 列表

这是4.15版中External目录下包含库的完整列表。

|                             名字                             |                             版本                             | 提供了CMake  | 需要编译 |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------: | :------: |
|                   [7z](http://7-zip.org/)                    |          Forked git（修正了UWP和Android的编译问题）          |      否      |    是    |
| [android_native_app_glue](https://developer.android.com/ndk/downloads/index.html) |                         修正过的16B                          |      否      |    否    |
|          [assimp](https://github.com/assimp/assimp)          |                             git                              |      是      |    是    |
|                [boost](http://www.boost.org/)                | 精简的1.70.0，[只用到了一部分](http://www.klayge.org/wiki/index.php/使用到的boost库) | 是，但没用到 |    是    |
|       [cxxopts](https://github.com/jarro2783/cxxopts)        |                             git                              |      是      |    否    |
|                         d3dcompiler                          |                             N/A                              |      No      |    No    |
|     [FreeImage](https://github.com/gongminmin/FreeImage)     |      Forked git（修正了C++17、MinGW和ARM上的编译问题）       |      否      |    是    |
|            [freetype](https://www.freetype.org/)             |                             git                              |      是      |    是    |
|      [googletest](https://github.com/google/googletest)      |                             git                              |      是      |    是    |
|            [libogg](https://github.com/xiph/ogg)             |                             git                              |      是      |    是    |
|         [libvorbis](https://github.com/xiph/vorbis)          |                             git                              |      是      |    是    |
|       [nanosvg](https://github.com/memononen/nanosvg)        |                             git                              |      否      |    否    |
|      [openal-soft](https://github.com/kcat/openal-soft)      |                             git                              |      是      |    是    |
|         [Python](https://github.com/python/cpython)          |           Forked git（修正了UWP和MinGW的编译问题）           |      否      |    是    |
| [python-cmake-buildsystem](https://github.com/python-cmake-buildsystem/python-cmake-buildsystem) | Forked git（修正了Android、iOS、Python 3.7和MinGW的编译问题） |      是      |    是    |
|      [rapidjson](https://github.com/Tencent/rapidjson)       |                             git                              |      是      |    否    |
|       [rapidxml](https://github.com/valnoel/rapidxml)        |                             git                              |      否      |    否    |
| [UniversalDXSDK](https://github.com/gongminmin/UniversalDXSDK) |                              否                              |      否      |          |
|  [wpftoolkit](https://github.com/xceedsoftware/wpftoolkit)   |              Forked git （修改了输出目录结构）               |      否      |    是    |
|            [zlib](https://github.com/madler/zlib)            |                             git                              |     Yes      |   Yes    |

除此之外，你还需要安装一个OpenGL ES SDK才能编译glloader_es和OpenGLES渲染系统。推荐使用[Google ANGLE](http://code.google.com/p/angleproject/)。

### 1.6发展历程

http://www.klayge.org/wiki/index.php/%E5%8F%91%E5%B1%95%E5%8E%86%E7%A8%8B

### 1.7 常见问题和解答

#### 问：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)是什么？

答：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)是一个开放源代码、跨平台的游戏引擎。它是用C++开发的，并使用Python作脚本语言。[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)在[GPL](http://en.wikipedia.org/wiki/GPL)协议下发行。

#### 问：为什么说[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)是最先进的开源游戏引擎？

答：在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的研发过程中，参考了大量最新最前沿的技术，比如实时GI、虚拟纹理、任意放缩字体、基于物理的渲染等，通过很多努力使其实用化。在效果上和效率上远远超越其他流行的开源游戏引擎，甚至可以比肩绝大多数顶级封闭游戏引擎。同时仍然保持了轻量灵活的优点，也强于某些笨重臃肿的封闭引擎。

####  问：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)是你一个人开发的吗？

答：是也不是。几乎所有的开发都是我一个人完成的。但在这个过程中使用了一些[第三方的代码](http://www.klayge.org/wiki/index.php/第三方库和工具)，比如7zip的解码部分。不少朋友也在开发的过程中给予了不可或缺的帮助。从3.12开始，很多功能是由开发团队的其他成员完成的。详见[发展历程](http://www.klayge.org/wiki/index.php/发展历程)。

#### 问：哪里能找到[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的文档？

答：目前[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的文档仅限于本wiki上的内容。文档缺乏的原因主要是我没有足够的时间去写，另外我更希望用代码本身来自我诠释。

#### 问：为什么选择了GPL？

答：在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 2.7之前使用的是[LGPL](http://en.wikipedia.org/wiki/LGPL)协议，但后来为了保护它不被某些专有软件吞并，所以换成了[GPL](http://en.wikipedia.org/wiki/GPL)。

#### 问：为什么用Python而不是LUA？

答：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 2.0之前（当时还叫作Clay! Engine），LUA是首选的脚本语言。LUA的优点是速度快，缺点是在C++中的调用极其麻烦，而且语言本身能力较弱。Python速度不如LUA， 但是语言能力强大得多，也不必写成栈式的调用方式，简洁得多。在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)中，脚本不是为了效率而存在的，所以Python成了不二之选。

#### 问：为什么必须要有Shader Model 2.0及以上？

答：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)是一款面向高端的引擎，所以在一定程度上要用较高的配置，以满足先进技术的需要。另一方面，Shader Model 2.0并不算一个很高的要求，市面上的新显卡几乎都是支持Shader Model 3.0的。对于游戏开发者来说，如果现在还在使用不支持Shader Model 2.0的硬件，那只能说实在落后得太多了。

#### 问：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的网络部分如何？

 ：[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)中的网络是弱项，甚至可以说几乎无法使用。所以需要重新开发，或者使用别的网络库。

#### 问：编译例子的时候出现像这样的连接错误信息：“libcmtd.lib(dbgheap.obj) : error LNK2005: __CrtSetDbgFlag 已经在MSVCRTD.lib(MSVCR80D.dll) 中定义”，请问如何解决？

答：由于[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)在VC下使用的运行库是多线程的DLL，所以需要把所有连接到exe的lib的运行库改为 多线程DLL（Project- >Properties->Configuration Properties->C/C++->Code Generation->RuntimeLibrary，选择Multi-threaded Debug DLL/Multi-threaded DLL）。

#### 问：Boost编译的时候应该用什么参数？

答：Boost 1.36的编译参数可以通过bjam的命令行参数来设置，可以写一个批处理文件，内容是：

```
SET BZIP2_SOURCE="D:/bzip2-1.0.5"
SET ZLIB_SOURCE="D:/zlib-1.2.3"
SET ICU_PATH="D:/icu4c-3_6"
bjam --toolset=msvc-9.0 --stagedir=./lib_vc9_x86 --builddir=./ address-model=32 link=shared runtime-link=shared threading=multi cxxflags=-wd4819 
 cxxflags=-wd4910 define=_CRT_SECURE_NO_DEPRECATE define=_SCL_SECURE_NO_DEPRECATE define=_SECURE_SCL=0 stage debug release
bjam --toolset=msvc-9.0 --stagedir=./lib_vc9_x64 --builddir=./ address-model=64 link=shared runtime-link=shared threading=multi cxxflags=-wd4819 
 cxxflags=-wd4910 define=_CRT_SECURE_NO_DEPRECATE define=_SCL_SECURE_NO_DEPRECATE define=_SECURE_SCL=0 stage debug release
```

直接在boost的目录下运行这个批处理就可以编译出dll版本的boost库。

#### 问：为什么在Visual Studio里运行例子的时候ResLoader::Load出现assert failed？

答：需要在Visual Studio中把工程的Working Directory设置成$(OutDir)。此问题在KlayGE 3.10中不再出现。

#### 问：在编译的时候提示”‘yasm’ is not recognized as an internal or external command, operable program or batch file.”，如何解决？

答：根据设置，Visual Studio的编译工具必须能调用yasm才能编译.asm的文件。解决方法之一是把下载下来的yasm-X.X.X-winYY.exe（X表示版本 号，YY表示32或64）改名成yasm.exe，并拷贝到VC的bin目录下，比如”C:\Program Files\Microsoft Visual Studio 9.0\VC\bin”。（注：这个问题实际上不该出现在本FAQ中，因为这其实是个命令行调用的问题，谁都该会的。可悲于国内“开发者”的素质，竟然有 不少人都问了我该问题，使得我不得不将它写在这里。）此问题将在KlayGE 3.11中避免。

#### 问：为什么KlayGE要抛弃D3D9？

答：KlayGE从3.11开始删除了D3D9插件。实际上目前D3D9存在的唯一理由是Win XP用户。但其中大部分人都是有D3D10的GPU，而因为XP被限制在了D3D9上。其实XP下的OpenGL驱动也是与时俱进的，可以给XP带来原本属于D3D10/11的新GPU能力。相比D3D9，OpenGL在XP上有更多的功能和更高的性能。因此KlayGE坚决地去掉了D3D9，让OpenGL接手D3D9在XP上的任务。

#### 问：为什么KlayGE要抛弃D3D10？

答：KlayGE从3.11开始删除了D3D10插件，由D3D11来取代它。D3D11并不一定要D3D11的GPU，在D3D10的GPU上，D3D11的功能相当于原有D3D10的，加上compute shader 4.0，以及可能有multi-threading。其性能取决于厂商驱动，目前来说性能可以做到和D3D10完全一致。D3D11在早期硬件上执行，只会带来好处，没有损失。D3D10已经完全没有存在的必要。

### 1.8 编程指南

#### 1.8.1 Contents

 [[hide](http://www.klayge.org/wiki/index.php/编程指南#)] 

- [1 总体](http://www.klayge.org/wiki/index.php/编程指南#.E6.80.BB.E4.BD.93)
- [2 渲染系统](http://www.klayge.org/wiki/index.php/编程指南#.E6.B8.B2.E6.9F.93.E7.B3.BB.E7.BB.9F)
- [3 打包系统](http://www.klayge.org/wiki/index.php/编程指南#.E6.89.93.E5.8C.85.E7.B3.BB.E7.BB.9F)
- [4 工具](http://www.klayge.org/wiki/index.php/编程指南#.E5.B7.A5.E5.85.B7)

#### 1.8.2  总体

- ##### 1.8.2.1 [第三方库和工具](http://www.klayge.org/wiki/index.php/第三方库和工具)
- ##### 1.8.2.2 [目录结构](http://www.klayge.org/wiki/index.php/目录结构)

下面是关于完整的[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)目录的主要描述。

```
\bin
    存放编译后的DLL和EXE

\Build
    工程文件

\Core
    内核文件

    \Include
        内核头文件

    \Src
        内核源文件

        \Audio
            音频引擎内核的源文件
        \Input
            输入引擎内核的源文件
        \Kernel
            核心源文件
        \Net
            网络引擎的源文件
        \Pack
            文件打包系统的源文件
        \Render
            渲染系统内核的源文件
        \Scene
            场景管理器内核的源文件
        \Script
            脚本引擎的源文件
        \Show
            播放引擎内核的源文件

\Doc
    文档

\Exporters
    \3DSMax
        \MeshML
            3ds max的导出插件
    \Maya
            Maya的导出插件

\media
    资源文件

    \Fonts
        字体文件
    \Models
        模型文件
    \PostProcessors
        后处理脚本
    \RenderFX
        渲染特效脚本
    \Textures
        纹理文件

\Plugins
    插件文件

    \Include
        插件头文件

    \Src
        插件源代码

        \Audio
            音频引擎插件的源文件
        \AudioDataSource
            音频数据源插件的源文件
        \Input
            输入引擎插件的源文件
        \Render
            渲染系统插件的源文件
        \Scene
            场景管理器插件的源文件
        \Show
            播放引擎插件的源文件

\Samples
    例子

\Tools
    工具文件

    \Bin
        编译生成的工具文件
    \DistanceMapCreator
        从height map建立distance map的工具
    \ForceTexSRGB
        强制把纹理转换为sRGB格式的工具
    \FXML2Shader
        从FXML提取shader的工具
    \GLCompatibility
        OpenGL兼容性测试工具
    \HDRCompressor
        HDR纹理压缩器
    \KFontGen
        字库转换工具
    \NormalMapCompressor
        Normal map压缩器
    \NormalMapGen
        从height map建立normal map的工具

\lib
    存放编译后的静态连接库
```

- ##### 1.8.2.3 [经过测试的编译器](http://www.klayge.org/wiki/index.php/经过测试的编译器)

###### 经过测试的编译器

**KlayGE 4.11**

下列编译器是经过测试的，可以用来编译[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)：

- Microsoft Visual C++ 14.0 Update 3，Microsoft Visual C++ 14.1。
- Windows平台上的MinGW-w64 GCC 5.1和6.3。
- Android NDK r12

还有一些编译器应该也支持，但没有经过测试：

- Windows平台上的MinGW GCC 5.2-6.2。

**KlayGE开发版本**

下列编译器是经过测试的，可以用来编译[KlayGE的开发版本](http://www.klayge.org/wiki/index.php/下载#.E5.BC.80.E5.8F.91.E7.89.88.E6.9C.AC)：

- Microsoft Visual C++ 14.0 Update 3，Microsoft Visual C++ 14.1。
- Windows平台上的MinGW-w64 GCC 5.1和6.3。
- Android NDK r12

还有一些编译器应该也支持，但没有经过测试：

- Windows平台上的MinGW GCC 5.2-6.2。

- ##### 1.8.2.4  [C++代码风格指南](http://www.klayge.org/wiki/index.php/C%2B%2B代码风格指南)

##### C++代码风格指南

**当前页面的内容正在依照[C++ style guide](http://www.klayge.org/wiki/index.php/C%2B%2B_style_guide)的内容进行翻译。**如果您熟知页面内容并擅长翻译，欢迎协助[改善或校对此页面](http://www.klayge.org/wiki/index.php?title=C%2B%2B代码风格指南&action=edit)。
C++是KlayGE使用的主要编程语言。每个C++程序员都知道，这个语言有着很多强大的特性，但强大的同时也带来了各种复杂性。结果就是更容易出bug，并且难以阅读和维护。

本指南将详细描述各种在写C++代码的过程中该做和不该做的事情，以达到控制复杂性的目的。这些规则一方面让代码库便于管理，另一方面允许开发者高效地使用C++的语言特性。

风格，也称为可读性，是掌控我们C++代码的规则。风格这个术语也许有些不当，因为这些规则远远超过了源代码格式的范畴。

我们管理代码库的一种方式是强制保持一致性。让任何开发者可以很快地看懂和明白其他人的代码非常重要。维护一个统一的风格并遵循规则，意味着我们可以更容易地使用“模式匹配”来推断各种符号是什么意思，以及有哪些不变性。建立一个通用的、必需的范式和模式会让代码容易理解得多。在某些情况下，可能会有很好的理由需要改变一些风格的规则，但为了保证一致性，我们仍然需要保持规则不变。

本指南要解决的另一个问题是应对C++的特性膨胀。C++是一个巨大的语言，有着许多先进特性。有些时候我们约束、甚至禁止使用一些特性。我们这么做可以保持代码简单易懂，并避免那些特性可能带来的多种常见错误和问题。本指南列出了这些特性，并解释为什么要限制使用他们。

注意，本指南不是个C++教程。我们假设读者熟悉这门语言。
http://www.klayge.org/wiki/index.php/C%2B%2B%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC%E6%8C%87%E5%8D%97

- ##### 1.8.2.5 [平台](http://www.klayge.org/wiki/index.php/平台)

##### 开发平台

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)可以在下列平台上没有任何限制地进行开发。

- Windows桌面
- MacOSX
- Linux

##### 运行平台

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)可以在下列平台上部署和执行。其中一些平台并不能支持所有功能。下面的表中会列出具体细节。

###### Windows桌面

| 架构 | Core |          Rendering          |     Audio     | Audio format |  Input   | Scene Management | Script | Show  |
| :--: | :--: | :-------------------------: | :-----------: | :----------: | :------: | :--------------: | :----: | :---: |
| x64  |  是  | D3D12/D3D11/OpenGL/OpenGLES | DSound/OpenAL |  OggVorbis   | MsgInput |      Octree      | Python | DShow |
| x86  |  是  | D3D12/D3D11/OpenGL/OpenGLES | DSound/OpenAL |  OggVorbis   | MsgInput |      Octree      | Python | DShow |

##### Windows商店

| 架构 | Core |  Rendering  | Audio | Audio format |  Input   | Scene Management | Script | Show |
| :--: | :--: | :---------: | :---: | :----------: | :------: | :--------------: | :----: | :--: |
| arm  |  是  | D3D12/D3D11 |  否   |      否      | MsgInput |      Octree      |   否   |  否  |
| x64  |  是  | D3D12/D3D11 |  否   |      否      | MsgInput |      Octree      | Python |  否  |
| x86  |  是  | D3D12/D3D11 |  否   |      否      | MsgInput |      Octree      | Python |  否  |

##### Android

|    架构     | Core | Rendering | Audio | Audio format |  Input   | Scene Management | Script | Show |
| :---------: | :--: | :-------: | :---: | :----------: | :------: | :--------------: | :----: | :--: |
|   armeabi   |  是  | OpenGLES  |  否   |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |
| armeabi-v7a |  是  | OpenGLES  |  否   |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |
|  arm64-v8a  |  是  | OpenGLES  |  否   |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |
|     x86     |  是  | OpenGLES  |  否   |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |
|   x86_64    |  是  | OpenGLES  |  否   |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |

##### Linux

|  架构  | Core | Rendering | Audio  | Audio format | Input | Scene Management | Script | Show |
| :----: | :--: | :-------: | :----: | :----------: | :---: | :--------------: | :----: | :--: |
|  x86   |  是  |  OpenGL   | OpenAL |  OggVorbis   |  否   |      Octree      | Python |  否  |
| x86-64 |  是  |  OpenGL   | OpenAL |  OggVorbis   |  否   |      Octree      | Python |  否  |

##### macOS

|  架构  | Core | Rendering | Audio  | Audio format |  Input   | Scene Management | Script | Show |
| :----: | :--: | :-------: | :----: | :----------: | :------: | :--------------: | :----: | :--: |
| x86-64 |  是  |  OpenGL   | OpenAL |  OggVorbis   | MsgInput |      Octree      | Python |  否  |

##### iOS

| 架构 | Core | Rendering | Audio  | Audio format |  Input   | Scene Management | Script | Show |
| :--: | :--: | :-------: | :----: | :----------: | :------: | :--------------: | :----: | :--: |
| x86  |  是  |  OpenGL   | OpenAL |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |
| arm  |  是  |  OpenGL   | OpenAL |  OggVorbis   | MsgInput |      Octree      |   否   |  否  |

##### 参见

[Regression testing](http://www.klayge.org/wiki/index.php/Regression_testing)

[Platform deployer](http://www.klayge.org/wiki/index.php/Platform_deployer)

[OpenGL插件对不同驱动的特殊处理](http://www.klayge.org/wiki/index.php/OpenGL插件对不同驱动的特殊处理)

[OpenGLES插件对不同驱动的特殊处理](http://www.klayge.org/wiki/index.php/OpenGLES插件对不同驱动的特殊处理)

#### 1.8.3 渲染系统

- [渲染系统](http://www.klayge.org/wiki/index.php/渲染系统)架构

[![KlayGE Render System Arch.png](http://www.klayge.org/wiki/images/a/aa/KlayGE_Render_System_Arch.png)](http://www.klayge.org/wiki/index.php/File:KlayGE_Render_System_Arch.png)

## 延迟渲染

在基本的渲染系统之上，还有一个[延迟渲染](http://www.klayge.org/wiki/index.php/延迟渲染)层。

- [延迟渲染](http://www.klayge.org/wiki/index.php/延迟渲染)
- [材质系统](http://www.klayge.org/wiki/index.php/材质系统)

###### 用于[延迟渲染](http://www.klayge.org/wiki/index.php/延迟渲染)的材质系统

[![KlayGE Material.png](http://www.klayge.org/wiki/images/1/1a/KlayGE_Material.png)](http://www.klayge.org/wiki/index.php/File:KlayGE_Material.png)

##### Stencil的分配

- bit 7：不接受lighting
- bit 6：支持反射

#### 1.8.4  打包系统

- [文件打包系统](http://www.klayge.org/wiki/index.php/文件打包系统)

从[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.6开始，打包系统使用了7zip作为打包格式。在使用打包系统之前，需要确保系统中有7zip的7z.dll。



[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)打包系统可以统一地通过[ResLoader](http://www.klayge.org/wiki/index.php?title=ResLoader&action=edit&redlink=1)来调用。命名规则是用“//”来区分压缩包路径和包内路径。如果压缩包有密码，则可以在它的 路径之后加上“|”和密码。例如，有一个folder/example.7z的压缩包，它的密码是abcd，包中有文件ex1/ex2 /test.cpp，那么它的全路径就是：

```
folder/example.7z|abcd//ex1/ex2/test.cpp
```

[ResLoader](http://www.klayge.org/wiki/index.php?title=ResLoader&action=edit&redlink=1)通过这个路径就可以把该文件从压缩包中载入一个[ResIdentifier](http://www.klayge.org/wiki/index.php?title=ResIdentifier&action=edit&redlink=1)中。

#### 1.8.5  工具

- [工具集](http://www.klayge.org/wiki/index.php/工具集)

### 1.9知识库

http://www.klayge.org/wiki/index.php/Category:%E7%9F%A5%E8%AF%86%E5%BA%93

## 2. 特色技术

这些是[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)原创的特色技术

- [特效系统](http://www.klayge.org/wiki/index.php?title=特效系统&action=edit&redlink=1)：跨平台的渲染特效系统，可以高效地包装各种特效。
- [Juda texture](http://www.klayge.org/wiki/index.php/Juda_texture)：可以存储和动态读取1T个像素的虚拟纹理系统。
- [字体系统](http://www.klayge.org/wiki/index.php/字体系统)：兼有矢量和点阵字体的双重优点。
- [glloader](http://www.klayge.org/wiki/index.php/Glloader)：自动载入所有支持的OpenGL扩展，并可以修补一些老驱动带来的兼容问题。
- [HDR压缩](http://www.klayge.org/wiki/index.php?title=HDR压缩&action=edit&redlink=1)：18bpp，高质量的HDR压缩方法，能用于几乎所有显卡。
- 

## 3. 例子

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)包含了多个[例子程序](http://www.klayge.org/wiki/index.php/例子程序)，用于演示引擎的各种特性。

##  4. 工具集

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)有一些用于辅助开发或数据处理的[工具集](http://www.klayge.org/wiki/index.php/工具集)。

###  4.1 美术工具链

[![KlayGE Toolchain.png](http://www.klayge.org/wiki/images/2/23/KlayGE_Toolchain.png)](http://www.klayge.org/wiki/index.php/File:KlayGE_Toolchain.png)

###  4.2 其他辅助工具

- 法线图生成器，可以从高度图生成法线图
- 距离图生成器，可以从高度图或3D纹理生成距离图
- OpenGL兼容性检测工具
- HDR压缩器，支持cubemap和2D HDR纹理的压缩
- Normalmap压缩器，2:1或4:1的压缩率
- 基于distance的[字体](http://www.klayge.org/wiki/index.php/字体系统)生成器，可以把矢量字体转换成引擎使用的字体格式
- FXML2Shader工具，把[FXML](http://www.klayge.org/wiki/index.php?title=FXML&action=edit&redlink=1)的特效脚本转换成HLSL或Cg
- [Juda texture](http://www.klayge.org/wiki/index.php/Juda_texture)打包工具，把多张普通纹理打包成一个Juda Texture
- Color Grading纹理生成工具
- Normals Fitting生成器
- Normal map到height map的生成工具
- Bump2Normal，把早期表示纹理坐标扰动的bump map转成尽量接近的normal map
- Mipmapper，对任意纹理建立mipmap
- [Platform deployer](http://www.klayge.org/wiki/index.php/Platform_deployer)，把纹理和模型对不同平台转成不同格式
- Tex2JTML，把多张纹理拼到一个[Juda texture](http://www.klayge.org/wiki/index.php/Juda_texture)中
- TexCompressor，BC1-5纹理压缩器

## 5. 未来

#  愿望列表

这里列出了一些希望以后能加入[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的功能。

**愿望列表**可以用来激励未来的工作。其中有些是很明确的做法，有些只是飘渺的想法，大部分则介于两者之间。同样，实现这些条目的工作量从对现有接口的小修改到大的研究项目都有。

## Contents

 [[hide](http://www.klayge.org/wiki/index.php/愿望列表#)] 

- 1 愿望列表
  - [1.1 矢量纹理](http://www.klayge.org/wiki/index.php/愿望列表#.E7.9F.A2.E9.87.8F.E7.BA.B9.E7.90.86)
  - [1.2 软件渲染插件](http://www.klayge.org/wiki/index.php/愿望列表#.E8.BD.AF.E4.BB.B6.E6.B8.B2.E6.9F.93.E6.8F.92.E4.BB.B6)
  - [1.3 基于HTML5的UI](http://www.klayge.org/wiki/index.php/愿望列表#.E5.9F.BA.E4.BA.8EHTML5.E7.9A.84UI)
  - [1.4 去除DirectShow](http://www.klayge.org/wiki/index.php/愿望列表#.E5.8E.BB.E9.99.A4DirectShow)
  - [1.5 GPU上进行物理和数学计算](http://www.klayge.org/wiki/index.php/愿望列表#GPU.E4.B8.8A.E8.BF.9B.E8.A1.8C.E7.89.A9.E7.90.86.E5.92.8C.E6.95.B0.E5.AD.A6.E8.AE.A1.E7.AE.97)
  - [1.6 强大的内存管理器](http://www.klayge.org/wiki/index.php/愿望列表#.E5.BC.BA.E5.A4.A7.E7.9A.84.E5.86.85.E5.AD.98.E7.AE.A1.E7.90.86.E5.99.A8)
  - [1.7 GPU音频处理](http://www.klayge.org/wiki/index.php/愿望列表#GPU.E9.9F.B3.E9.A2.91.E5.A4.84.E7.90.86)
  - [1.8 Command buffer的记录和重放](http://www.klayge.org/wiki/index.php/愿望列表#Command_buffer.E7.9A.84.E8.AE.B0.E5.BD.95.E5.92.8C.E9.87.8D.E6.94.BE)
  - [1.9 实时Catmull-Clark细分](http://www.klayge.org/wiki/index.php/愿望列表#.E5.AE.9E.E6.97.B6Catmull-Clark.E7.BB.86.E5.88.86)
- 2 正在做的
  - [2.1 基于GPU的细分](http://www.klayge.org/wiki/index.php/愿望列表#.E5.9F.BA.E4.BA.8EGPU.E7.9A.84.E7.BB.86.E5.88.86)
  - [2.2 实时全局光照](http://www.klayge.org/wiki/index.php/愿望列表#.E5.AE.9E.E6.97.B6.E5.85.A8.E5.B1.80.E5.85.89.E7.85.A7)
- 3 已经完成
  - [3.1 延迟着色](http://www.klayge.org/wiki/index.php/愿望列表#.E5.BB.B6.E8.BF.9F.E7.9D.80.E8.89.B2)
  - [3.2 深度剥离](http://www.klayge.org/wiki/index.php/愿望列表#.E6.B7.B1.E5.BA.A6.E5.89.A5.E7.A6.BB)
  - [3.3 屏幕空间环境遮挡](http://www.klayge.org/wiki/index.php/愿望列表#.E5.B1.8F.E5.B9.95.E7.A9.BA.E9.97.B4.E7.8E.AF.E5.A2.83.E9.81.AE.E6.8C.A1)
  - [3.4 移动平台支持](http://www.klayge.org/wiki/index.php/愿望列表#.E7.A7.BB.E5.8A.A8.E5.B9.B3.E5.8F.B0.E6.94.AF.E6.8C.81)
  - [3.5 地形渲染](http://www.klayge.org/wiki/index.php/愿望列表#.E5.9C.B0.E5.BD.A2.E6.B8.B2.E6.9F.93)

## 愿望列表

### 矢量纹理

直接在texel上存储矢量参数，[字体系统](http://www.klayge.org/wiki/index.php/字体系统)也可以建立在其之上。

### 软件渲染插件

类似于D3D10的软件渲染插件，用纯软件支持D3D10+的所有功能。

### 基于HTML5的UI

集成HTML5渲染器，可以直接用HTML5来作为UI的表达方式。

### 去除DirectShow

不使用DirectShow来播放视频和音频。备选方案之一是用.ogm作为容器格式，Theora作为视频编码，Vorbis作为音频编码，同时也支持字幕。

### GPU上进行物理和数学计算

**提出人：吴野**

GPGPU的物理模拟和线性代数计算。

### 强大的内存管理器

支持跨越DLL边界的内存分配/清除、泄露检测和内存池。最好能Lock-free或Wait-free。

### GPU音频处理

通过GPU处理音频（3D、特效），然后传给声卡播放。

### Command buffer的记录和重放

把所有的DX/OGL API调用都在一个线程里捕捉，并可以在其它线程里重放。

### 实时Catmull-Clark细分

**提出人：周波**

实现[Approximating Catmull-Clark Subdivision Surfaces with Bicubic Patches](http://faculty.cs.tamu.edu/schaefer/research/acc.pdf)的GPU细分算法

## 正在做的

### 基于GPU的细分

在D3D11/D3D10（ATI）上支持硬件的[细分](http://www.klayge.org/wiki/index.php?title=细分&action=edit&redlink=1)，在D3D9/OpenGL上支持基于shader的细分。（D3D11的细分已经支持了）

### 实时全局光照

**提出人：吴野**

实时计算[全局光照](http://www.klayge.org/wiki/index.php/全局光照)。支持阴影、折射、反射、半透明和多次散射。（阴影、单次散射已经完成，折射、反射和半透明分别在不同的框架中完成）

## 已经完成

### 延迟着色

[延迟着色](http://www.klayge.org/wiki/index.php/延迟渲染)的渲染系统，支持抗锯齿和透明。（作为[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.8.0的一个[例子](http://www.klayge.org/wiki/index.php/例子程序#Deferred_Rendering)）

### 深度剥离

顺序无关的透明。（作为[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.7.0的一个[例子](http://www.klayge.org/wiki/index.php/例子程序#Depth_peeling)）

### 屏幕空间环境遮挡

用SSAO来增加暗处的细节。（作为[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.8.0的一个[例子](http://www.klayge.org/wiki/index.php/例子程序#Deferred_Rendering)）

### 移动平台支持

OpenGL ES 2.0插件和D3D mobile插件。

### 地形渲染

大规模地形渲染。

对[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)的未来有什么愿望？可以到[愿望列表](http://www.klayge.org/wiki/index.php/愿望列表)提出来。

## 6.子项目

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)有一些独立子项目，可以在不包含[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)本身的情况下单独使用。

- [DXBC2GLSL](http://www.klayge.org/wiki/index.php?title=DXBC2GLSL&action=edit&redlink=1)
- [glloader](http://www.klayge.org/wiki/index.php/Glloader)
- [KFL](http://www.klayge.org/wiki/index.php?title=KFL&action=edit&redlink=1)
- [kfont](http://www.klayge.org/wiki/index.php/Kfont)
- [MeshMLLib](http://www.klayge.org/wiki/index.php/MeshMLLib)

## 7. Array的入门教程

- [Tutor1 - 构建自己的应用程序框架](http://www.klayge.org/wiki/index.php/Tutor1_-_构建自己的应用程序框架)
- [Tutor2 - 渲染几何体数据](http://www.klayge.org/wiki/index.php/Tutor2_-_渲染几何体数据)



