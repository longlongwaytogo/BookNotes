# UBT

Unreal Build System

[UE4构建系统分析 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/441320307)

点击Build之后的基本流程描述：

- 扫描所有Module，如果当前扫描模块没有代码修改，则跳过此模块

- 如果代码有修改，需要编译，检查模块中所有class中是否包含“*.generated.h"头文件以及UCLASS宏

- 有责调用UHT进行额外C++代码生成，以支持UE的反射特性，如果没有则跳过

- UBT开始构建C++代码（宏展开，编译），从而得到二进制文件

  

每个工具都会处理自己的具体工作，下面将会依次介绍Header Tool、Build Tool、Modules等内容





[UE Build System：Target and Module | 循迹研究室 (imzlp.com)](https://imzlp.com/posts/16643/)

[UE4 源码剖析 - 1.1.2 类型系统构建 - 编译系统(UBT之Build) - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/159330024)







[从源码编译UE4,加快Setup.bat下载文件的环节 - Ken_An - 博客园 (cnblogs.com)](https://www.cnblogs.com/AnKen/p/6964465.html)

之前很傻，每次运行这个setup.bat都要等很久很久才能把4g多的东西下载完成，知道有一天突然发现了世外桃源……

从命令行运行setup.bat -help，可以看到参数的说明（没错，参数可选，之前一直以为bat都是拿来双击的……）:

```
Usage:
   GitDependencies [options]

Options:
   --all                         Sync all folders
   --include=<X>                 Include binaries in folders called <X>
   --exclude=<X>                 Exclude binaries in folders called <X>
   --prompt                      Prompt before overwriting modified files
   --force                       Always overwrite modified files
   --root=<PATH>                 Set the repository directory to be sync
   --threads=<N>                 Use N threads when downloading new files
   --dry-run                     Print a list of outdated files and exit
   --max-retries                 Override maximum number of retries per file
   --proxy=<user:password@url>   Sets the HTTP proxy address and credentials
   --cache=<PATH>                Specifies a custom path for the download cache
   --cache-size-multiplier=<N>   Cache size as multiplier of current download
   --cache-days=<N>              Number of days to keep entries in the cache
   --no-cache                    Disable caching of downloaded files

Detected settings:
   Excluded folders: Mac, Android, Linux
   Proxy server: none
   Download cache: disabled

Default arguments can be set through the UE4_GITDEPS_ARGS environment variable.
Installing prerequisites...
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

我们的优化都是围绕这些参数来的：

1. --exclude=<XXX> (这些选项前的双横线也可以用单横线）
   非常有用，减少不必要的文件下载。可以排除掉自己不需要的平台和VS版本，例如： setup.bat -exclude=Linux -exclude=IOS -exclude=HTML5  -exclude=Android -exclude=VS2013
   平台可选的参数:**Win32**, **Win64**, **osx32,osx64**, **Linux**, **Android**, **IOS**, **HTML5**
   VS版本可选参数:VS2012,VS2013,VS2015
   警告： 不要排除Win32 和 VS2012, 不然后期编译会遇到问题
2. --threads=<N>
   可以多线程下载，速度倍增。例如：setup.bat --threads=20
3. --cache=<PATH>
   可以把下载的内容缓存在指定的目录，这样如果有多人需要，就可以只下载一次，然后分享给大家，例如：setup.bat --cache=D:\Temp
4. --proxy=<user:password@url>
   可以使用代理下载





[(138条消息) UE5.1使用VS2022Pro编译时,为什么VS2022只使用单线程编译？-游戏-CSDN问答](https://ask.csdn.net/questions/7871990)

1. Determining max actions to execute in parallel (4 physical cores, 8 logical cores)
2. 1>  Executing up to 4 processes, one per physical core
3. 1>  Requested 1.5 GB free memory per action, 1.12 GB available: limiting max parallel actions to 1
4. 1>Building 5394 actions with 1 process.
5. 



## 编译详细参数说明：

[将虚幻引擎构建为库 | 虚幻引擎5.2文档 (unrealengine.com)](https://docs.unrealengine.com/5.2/zh-CN/building-unreal-engine-as-a-library/)

https://github.com/Allar/compiling-unreal



# UE加速编译

[ClxS/FASTBuild-UE4: Contains all the steps and code required to get FASTBuild working with UnrealEngine 4.13 (github.com)](https://github.com/ClxS/FASTBuild-UE4)

[(138条消息) 使用FASTBuild加速Unreal Engine编译_Vicent_Chen的博客-CSDN博客](https://blog.csdn.net/cjw_soledad/article/details/117362397)

[保姆式教你使用FASTBuild对UE4进行联机编译 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/158400394)





# UE 项目编译配置项

[wiki.unrealengine.com (michaeljcole.github.io)](https://michaeljcole.github.io/wiki.unrealengine.com/Understanding_Unreal's_Build_System/)



## Editor Builds

- Development Editor
- DebugGame Editor

加载UE4Editor.exe后，它会附加到Development Editor[UE4Editor-YourGame.dll]。如果此.dll不存在，它将提供构建它。加载编辑器后，您可以通过从Visual Studio重新编译为开发编辑器版本来更新它。您也可以从Visual Studio重新编译为DebugGame Editor构建[UE4Editor-YourGame-Win64-DebugGame.dll]。

在继续之前值得注意的是，如果您关闭编辑器并重新加载它，它将使用最后一个良好的开发编辑器构建。因此，如果您使用的是调试游戏编辑器构建，则可能看起来像您丢失了工作。只需重建调试游戏编辑器，它就会热加载到编辑器中。

###  Executable Builds

- Development
- DebugGame
- Shipping



### Command Line

- Development Editor

- DebugGame Editor

  

Either listed build type can be used when launching the your game from command line. using switch "-game" will launch your game using [UE4Editor-YourGame.dll]. And using switches "-game -debug" will launch your game using [UE4Editor-YourGame-Win64-DebugGame.dll].

### Compile in Editor

he editor contains a Compile button on the main shelf. When this button is pushed, the unreal build tools create a new Development Editor build and hot links it back to the editor.

This introduction should be expanded as more is learned, but I hope this helps!





# 项目生成设置：

## 生成cmake项目

```cmake
UnrealBuildTool.exe -CMakefile -project="H:\code\UE5\projects\LearningUE\UE5\Start1\Start1.uproject" -game -engine -progress
```

## 生成vs项目

```cmd
>UnrealBuildTool.exe  -projectfiles -project="H:\code\UE5\projects\LearningUE\UE5\Start1\Start1.uproject" -Mode=GenerateProjectFiles -game -engine -progress
```



-game：表示不包含工具项目

-engine： 包含工具项目

-2019: 表示使用vs2019编译器

-2022 :

-Platforms=Mac
-TargetTypes=Game
-TargetConfigurations=Shipping
 -Platforms=Win64+XboxOne+UWP64 ： 项目平台

只有-game，生成engine和project的solution

-game 和-engine生成：engine/project/program的solution



## 使用GenerateFiles.bat 生成项目

[如何为IDE生成虚幻引擎项目文件 | 虚幻引擎5.2文档 (unrealengine.com)](https://docs.unrealengine.com/5.2/zh-CN/how-to-generate-unreal-engine-project-files-for-your-ide/)

[UnrealBuildTool生成ProjectFiles | Dear John](https://john.js.org/2022/11/02/UnrealBuildTool-ProjectFiles/)

```cmd
GenerateProjectFiles.bat ShooterGame.uproject -Game
```



## 控制默认的生成选项，如右键中，生成项目于使用的默认配置：

%appdata%/Roaming\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml

如需要设置默认使用vs2019编译器，可以添加：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration xmlns="https://www.unrealengine.com/BuildConfiguration">
  <ProjectFileGenerator>
    <Format>VisualStudio2019</Format>
  </ProjectFileGenerator>
</Configuration>

```

referenced: [(138条消息) UE 编译配置BuildConfiguration.xml文件说明_ue4 编译配置_封狼居胥_COU的博客-CSDN博客](https://blog.csdn.net/qq_16123279/article/details/127013321)

## 生成引擎的独立安装包

[Using an Installed Build of Unreal Engine | Unreal Engine 5.2 Documentation](https://docs.unrealengine.com/5.2/en-US/using-an-installed-build-of-unreal-engine/)

[How To build the Unreal Editor (GitHub) | Epic Developer Community (epicgames.com)](https://dev.epicgames.com/community/learning/tutorials/k8Ve/unreal-engine-how-to-build-the-unreal-editor-github)

```cmd
C:\EpicSource\UE_5.0\UnrealEngine-5.0\Engine\Build\BatchFiles\RunUAT.bat BuildGraph -target="Make Installed Build [PLATFORM]" -script="Engine/Build/InstalledEngineBuild.xml" -clean

    C:\EpicSource\UE_5.0\UnrealEngine-5.0\Engine\Build\BatchFiles\RunUAT.bat BuildGraph -target="Make Installed Build [PLATFORM]" -script="Engine/Build/InstalledEngineBuild.xml" -set:WithWin64=true -set:WithMac=false -set:WithTVOS=false -set:WithLinux=false -set:WithHTML5=true

```



## 将引擎构建为独立lib库

[将虚幻引擎构建为库 | 虚幻引擎5.2文档 (unrealengine.com)](https://docs.unrealengine.com/5.2/zh-CN/building-unreal-engine-as-a-library/)

## 模块链接模式

[UE Build System：Target and Module | 循迹研究室 (imzlp.com)](https://imzlp.com/posts/16643/)



# 编译monolithic的UnrealEditor.exe

```cmd
set buildTool=E:\UE5\UnrealEngine\Engine\Binaries\DotNET\UnrealBuildTool\UnrealBuildTool.exe
%buildTool%  -Target="UnrealEditor Win64 Development" -WaitMutex -FromMsBuild -2019  -Monolithic
```

