# UE5工程文件结构

# 01-UE5 vs项目打开包含 

- Engine: 引擎主要代码
- Progams： 引擎所使用的通过用工具集合
- Visualizers： 适用于Visual Studio 的调试内存格式显示映射

# 02- Engine

## 02.1-UE5

- Build :引擎编译相关平台脚本

  - Android
  - BatchFiles
  - Graph
  - IOS
  - Linux
  - Mac
  - Rsync
  - SteamDeck
  - Turnky
  - TVOS
  - Windows
- Config： 不同平台的配置信息

  - Android
  - HoloLens
  - IOS
  - Layouts
  - Linux
  - LinuxArm64
  - Localization
  - Mac
  - TVOS
  - Unix
  - UnrealBuildTool
  - VulkanPC
  - Windows
- Content

  - Editor ： 编辑器的模板创建文档
- PlatForms： 特殊设备平台相关功能模块

  - HoloLens
- Plugins ：插件模块，相对独立的功能集合

  - 2D
  - AI
  - Animation
  - AudioGameplay
  - AudiogamePlayVolume
  - BlueprintFileUtils
  - Bridge
  - Cameras
  - Coposition
  - Compression
  - Developer
  - Editor
  - EnhancedInput
  - Enterprise
  - Experimental
  - FastBuildController
  - FX
  - Importers
  - Interchange
  - JsonBlueprintUtilities
  - LightWeightInstancesEditor
  - Media
  - MeshPainting
  - MoviceScene
  - NetCodeUnitTest
  - Online
  - Performance
  - Portal
  - Protocols
  - RenderGraphInsights
  - Runtime
  - ScriptPlugin
  - Slate
  - Test
  - TraceUtilities
  - VirtualProduction
  - Web
  - XGEController
- Programs：引擎编译使用的工具配置

  - UnrealBuildTool
  - UnrealHeaderTool
- Shaders：shader文件

  - Private
  - Public
  - Shared
  - StandaloneRenderer
- Source 引擎核心代码

  - Developer
- Editor
  - Programs
- Runtime
  - ThirdParty



将Engine\UE5\Source 部分单独分析：

## 02.2-Source 引擎核心代码
### 02-2.1-Developer: 编辑器和引擎公用代码
### 0202.2-Editor： 编辑器代码
 -  ActorPickerMode
-  AddContentDialog
 - AdvancedPreviewScene
 - AIGraph
 - AnimationBlueprintEditor
 - AnimationBlueprintLibrary
 - AnimationEditMode
 - AnimationEditor
 - AnimationModifiers
 - AnimationSettings
 - AnimGraph
 - AssetTagsEditor
 - AudioEditor
 - BehaviorTreeEditor
 - BlueprintEditorLibrary
 - BlueprintGraph
 - Blutility
 - Cascade
 - ClassViewer
 - ClothingSystemEditor
 - ClothingSystemEditorInterface
 - ClothPainter
 - CommonMenuExtensions
 - ComponentVisualizers
 - ConfigEditor
 - ContentBrowser
 - ContentBrowserData
 - CSVtoSVG
 - CurveAssetEditor
 - CurveEditor
 - CurveTableEditor
 - DataLayerEditor
 - DataTableEditor
 - DerivedDataEditor
 - DetailCustomizations
 - DeviceProfileEditor
 - DeviceProfileServices
 - DistCurveEditor
 - Documentation
 - EditorConfig
 - EditorFramework
 - EditorSettingsViewer
 - EditorStyle
 - EditorSubsystem
 - EditorWidgets
 - EnvironmentLightingViewer
 -  Experimental
    -  EditorInteractiveToolsFramework
    -  HordeExecutor
    -  RemoteExecution

 -  FoliageEdit
 -  FontEditor
 -  GameplayTasksEditor
 -  GameProjectGeneration
 -  GraphEditor
 -  HardwareTargeting
 -  HierarchicalLODOutliner
 -  InputBindingEditor
 -  InternationalizationSettings
 -  Kismet
 -  KismetCompiler
 -  KismetWidgets
 -  LandscapeEditor
 -  LandscapeEditorUtilities
 -  Layers
 -  LevelAssetEditor
 -  LevelEditor
 -  LevelInstanceEditor
 -  LocalizationCommandletExecution
 -  LocalizationDashboard
 -  **MainFrame**
 -  MaterialEditor
 -  MergeActors
 -  MeshPaint
 -  MovieSceneCaptureDialog
 -  MovieSceneTools
 -  NaniteTools
 -  NewLevelDialog
 -  OverlayEditor
 -  PackagesDialog
 -  Persona
 -  PhysicsAssetEditor
 -  PIEPreviewDeviceProfileSelector
 -  PIEPreviewDeviceSpecification
 -  PinnedCommandList
 -  PixelInspector
 -  PlacementMode
 -  PListEditor
 -  PluginWarden
 -  ProjectSettingsViewer
 -  ProjectTargetPlatformEditor
 -  PropertyEditor
 -  RewindDebuggerInterface
 -  SceneDepthPickerMode
 -  SceneOutliner
 -  Sequencer
 -  SequencerCore
 -  SequenceRecorder
 -  SequenceRecorderSections
 -  SequencerWidgets
 -  SerializedRecorderInterface
 -  SkeletalMeshEditor
 -  SkeletonEditor
 -  SourceControlWindowExtender
 -  SourceControlWindows
 -  StaticMeshEditor
 -  StatsViewer
 -  StatusBar
 -  StringTableEditor
 -  StructViewer
 -  SubobjectDataInterface
 -  SubobjectEditor
 -  SwarmInterface
 -  TextureEditor
 -  ToolMenusEditor
 -  TranslationEditor
 -  TurnkeySupport
 -  UATHelper
 -  UMGEditor
 -  UndoHistoryEditor
 -  **UnrealEd**
 -  UnrealEdMessages
 -  ViewportInteraction
 -  ViewportSnapping
 -  VirtualizationEditor
 -  VirtualTexturingEditor
 -  VREditor
 -  WorkspaceMenuStructure
 -  WorldBrowser
 -  WorldPartitionEditor





### Programs ：引擎和编辑器使用的外部工具
### Runtime： 运行时使用的模块
###  ThirdParty


# 03-Programs

## BuildWorker

## Datasmith

## LowLevelTest

## VirtualProduction

## BenchmarkTool

## BlankProgram

## BootstrapPackagedGame

## BuildPatchTool

## ChaosVisualDebugger

## CrashReportClient

## CrashReportClientEditor

## DotNetPerforceLib

## DsymExporter

## EpicWebhelper

## HeadlessChaosPerf

## InterchangedWrker

## LiveCodingConsole

## ReplicationSystemTest

## ShaderCompilerWorker

## SlateUGS

## SlateViewer

## SwitchboardListener

## SymsLibBDump

## TestPAL

## UnrealAtoS

## UnrealEditorServices

## UnrealFrontend

## UnrealHeaderTool

## UnrealInsights

## UnrealLaunchDaemon

## UnrealLightmass

## UnrealMutiUserServer

## UnrealMultiUserSlateServer

## UnrealObjectPtrTool

## UnrealPackageTool

## UnrealPak

## UnrealRecoverySvc

## UnrealVersionSelector

## UnrealVirtualizationTool

## UnSync

## ZenDashboard

# 04-Visualzers

- Unreal.natvis: 调试模式下，针对UE数据结构的可视化显示映射

  
  
# 05- 工程结构

 ##  Source

**Game** - 游戏项目目录中的源文件按模块分组，一个模块一个目录。每个模块包含以下内容：

   - **Classes** - 包含所有的头文件（`.h`）。
   - **Private** - 包含所有 `.cpp` 文件，包括游戏逻辑类以及各种模块的实现文件。
   - **Public** - 包含模块的头文件。

  UE引擎安装目录的Engine目录和项目目录，两者的通用目录结构：

- Binaries：包含可执行程序或编译期创建的其他文件
- Build：构建引擎或者游戏所需要的文件
- Config：配置文件
- Content：保存游戏资源，如贴图、mesh等资源包
- DerivedDataCache：包含加载时针对引用内容生成的派生数据文件，引用内容没有相应的缓存文件导致加载时间显著延长
- Intermediate：包含构建引擎或游戏生成的临时文件。在游戏目录中，着色器村删除在这里
- Saved：包含自动保存、配置(.ini)和日志。

# 06-reference

  [UE4随笔：目录结构 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/390651930)

[目录结构 | 虚幻引擎文档 (unrealengine.com)](https://docs.unrealengine.com/4.27/zh-CN/Basics/DirectoryStructure/)

  

