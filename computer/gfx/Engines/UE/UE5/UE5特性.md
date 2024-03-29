# UE5 特性

## 从设计可视化和电影体验，到PC、主机、移动设备、VR和AR上的高质量游戏，虚幻引擎为你提供了启动、发布、成长和脱颖而出所需的一切。



## 01 Pipeline integration
### FBX, USD, and Alembic support
连接到媒体制作管道，支持 FBX、USD 和 Alembic 等行业标准。一流的 USD 支持使用户能够更好地与团队成员协作并并行工作。虚幻引擎可以从磁盘上的任何位置读取USD文件，而无需耗时的完全导入，并将更改写回为覆盖;重新加载 USD 有效负载会立即更新上游其他用户所做的更改。
### python script
将虚幻引擎集成到你的管线中，并在虚幻编辑器中完全支持行业标准的Python脚本，实现工作流程自动化。你可以构建资产管理管线，自动化数据准备工作流程，在关卡中按程序布局内容，以及创建自定义UI来控制虚幻编辑器。
### Datasmith
使用 Datasmith 以高保真度转换整个场景（包括动画和元数据），从 3ds Max、Revit、SketchUp Pro、Cinema 4D、Rhino、SolidWorks、Catia 以及大量其他 DCC、CAD 和 BIM 格式转换。非破坏性重新导入意味着您可以继续在源包中进行迭代，而不会丢失下游更改。对元数据的访问为通过 Python 脚本或可视化数据准备的自动化数据准备打开了大门。
### Visual Dataprep
使用简化的可视化工具轻松自动执行数据准备工作流，即使您不是程序员，该工具可让您创建过滤器和运算符的“配方”，您可以在其他场景或项目中保存和重复使用。根据类、名称、元数据标签或大小等因素创建 LOD、设置 Lightmap UV、替换材质以及删除或合并对象。
### ShotGrid 集成
虚幻引擎中的ShotGrid集成提供了与美术师在其他应用程序（如Maya）中创建的上游3D资产数据的简化连接，以及需要由ShotGrid中的主管和导演审查的下游图像数据。
### LiDAR point cloud support（激光雷达点云支持）
聚合并使用从现实世界捕获的庞大数据集，并能够直接在虚幻引擎中导入、可视化、编辑从激光扫描设备获取的点云并与之交互。点云可用于可视化位置并为新设计的元素提供准确的上下文。

## 02 World building
### 虚幻编辑器
虚幻引擎包括虚幻编辑器，这是一个在Linux、macOS和Windows上可用的集成开发环境，用于内容创作和游戏关卡开发。由于支持多用户编辑，美术师、设计师和开发人员可以安全可靠地同时对同一个虚幻引擎项目进行更改，而能够在VR模式下运行完整的虚幻编辑器意味着你可以在所见即所得的环境中进行构建。
###  建模、UV 和烘焙
虚幻引擎内置了一个广泛的网格体创建和编辑工具集，包括细分操作、动态雕刻工具和几何体脚本。此外，还有一套强大的UV创建和编辑工具，以及用于烘焙纹理和传输网格属性的有用工具选择。总之，这些工具使您能够在资产的最终上下文中优化和迭代资产，而无需往返到 DCC 包。
### 世界分区
世界分区通过自动将世界划分为网格并仅流式传输必要的单元格，使开放世界的创建更快、更容易。借助每个Actor一个文件（OFPA）系统，团队成员可以同时在同一世界的同一区域工作，而不会互相踩到脚趾，而使用数据层，您可以创建同一世界的不同变体作为存在于同一空间中的图层。
### 景观和地形工具
使用地形系统创建包含山脉、山谷甚至洞穴的大规模开放世界环境和地形。添加多个高度贴图和绘制图层，并相互独立地雕刻和绘制它们。用户还可以使用为样条保留的图层无损地编辑地形，并在蓝图中创建独特的自定义画笔，并使用它们根据其他元素调整地形。
### 可扩展的树叶
使用草工具自动用不同类型的草、花、小石头或您选择的网格覆盖您巨大的户外环境，并使用模拟森林多年来生长的程序化植物工具创建充满许多不同种类的树木和灌木的广阔森林。

### 资产优化
准备和优化复杂模型以获得更好的实时性能可能是一种乏味且耗时的体验，通常涉及多次往返。虚幻引擎提供了自动生成LOD（细节层次）等工具;代理几何工具，该工具将多个网格及其材料组合成单个网格和材料;以及许多用于简化网格和消除隐藏多边形的建模工具。
### 天空、云和环境光照
创作和渲染逼真或风格化的天空、云和其他大气效果，具有完全的艺术自由，体积云组件可以与天空大气、天空光照和最多两个定向光源进行交互。组件可以动态照明和阴影，实时符合时间更新。
### 水系
使用水系统在您的景观中创建可信的水体，使您能够使用样条线定义海洋、湖泊、河流和岛屿。内置流体模拟使角色和物体能够逼真地与水互动;流体也会对地形做出反应，例如反射岸边的涟漪，并对河流流图做出反应。

## 03 Characters and animation
### 动画蓝图
使用动画蓝图创建和控制复杂的动画行为。动画蓝图是控制骨架网格体动画的专用蓝图。图形在动画蓝图编辑器中编辑，您可以在其中执行动画混合，直接控制骨架的骨骼，或设置逻辑，最终定义骨架网格体每帧使用的最终动画姿势。
### 机器学习变形器
机器学习（ML）变形器通过使用自定义Maya插件训练机器学习模型来生成非线性变形器、复杂专有装备或任何任意变形的高保真近似值，而机器学习模型又在虚幻引擎中实时运行。这使您能够模拟胶片质量的变形，例如弯曲的肌肉、凸出的静脉和滑动的皮肤。
### 角色动画创作
使用“控制装备”等美术师友好型工具快速轻松地创建装备并在多个角色之间共享它们，然后在 Sequencer 中摆出姿势并为其制作动画。完全自定义角色并使用状态机等强大功能制作可信的运动;混合空间;以及正向、反向和全身反向运动学 （FBIK）。您甚至可以利用物理驱动的动画来实现布娃娃效果。
### 实时链接数据流
Live Link插件使你能够将来自外部源的实时数据流连接到虚幻引擎。您可以从 DCC 工具（如 Maya 或 Motionbuilder）或动作捕捉或表演捕捉系统（包括 Apple 的 ARKit 面部跟踪）流式传输角色动画、摄像机、灯光和其他数据，以便从 iPhone 捕捉面部表演。Live Link设计为可通过虚幻插件进行扩展，使第三方能够添加对新源的支持。
### 拍摄记录器
通过 Take Recorder，您可以录制链接到场景中角色的动作捕捉动画和 Live Link 数据中的动画，以便将来播放，因此您可以快速迭代表演录制，并轻松查看以前的镜头。通过将Actor录制到子序列中并通过获取元数据组织它们，您可以更轻松地管理复杂的制作。
### 字符重定向
虚幻引擎的美术师友好型重定向工具集包括轻松重用现有动画的功能，甚至可以跨具有不同骨架和比例的角色（例如人和狼）重复使用。此外，您还可以以交互方式创建求解器和目标，为骨架网格体执行姿势编辑，例如，在保持现有动画的同时累加调整角色，例如使移动角色始终查看目标。
### 序列器非线性编辑和动画
Sequencer 由电影和电视专业人士设计，通过专为协作而构建的完全非线性实时电影编辑和动画工具释放您的创作潜力。定义和修改每个镜头的照明、摄像机遮挡、角色和布景。美术师团队可以以前所未有的方式同时处理整个序列。您甚至可以通过混合动画剪辑来创建新动画。
### 运行时动画工具
使用虚幻引擎，你可以在运行时扩充创作的动画序列，以补偿不同的游戏场景。使用运动变形动态调整角色的根运动以与不同的目标对齐，例如，跳过不同高度的墙壁。此外，使用距离匹配来控制动画的播放速率，和/或姿势变形来动态调整姿势，以更好地匹配游戏中角色的动作。
## 04 Rendering,lighting,and materials
### Nanite & Virtual Shadow Maps
使用 Nanite 虚拟化微多边形几何系统和虚拟阴影贴图 （VSM） 创建具有大量几何细节的游戏和体验。Nanite 和 VSM 仅智能地流式传输和处理您可以感知的细节，使您能够导入由数百万个多边形组成的电影级源艺术资源并放置它们数百万次，同时保持实时帧速率，并且不会有任何明显的保真度损失。

### Virtual Texturing( 虚拟纹理)
虚幻引擎提供了两种方法，通过将非常大的纹理划分为小图块并仅加载可见图块来启用对超大纹理的支持。流式虚拟纹理使用磁盘上转换纹理中的纹素数据，可减少光照贴图和详细的 UDIM UV 艺术家创建的纹理的纹理内存开销。运行时虚拟纹理（其中纹素数据由 GPU 在运行时生成）可提高程序化和分层材质的渲染性能。

### Lumen
Lumen 是一种完全动态的全局照明和反射解决方案，可让您创建可信的场景，其中间接照明会动态适应直接照明或几何体的变化，例如，随一天中的时间改变太阳的角度、打开手电筒或打开外门。使用 Lumen，您不再需要创作光照贴图 UV、等待光照贴图烘焙或放置反射捕获。
### 实时逼真的光线追踪
使用虚幻引擎基于物理的混合光线追踪器，实现开箱即用的好莱坞品质视觉效果。有选择地选择光线追踪反射、阴影、半透明、环境光遮蔽、基于图像的照明和全局照明，同时继续栅格化其他通道，以所需的性能获得微妙、准确的效果。效果包括来自区域光源的动态柔和阴影，以及来自 HDRI 天窗的光线追踪光。
### Temporal Super Resolution(时间超分辨率)
下一代游戏机的玩家期望在高分辨率显示器上的帧速率达到 60 fps 或更高，这给渲染资源带来了巨大的压力。时间超分辨率 （TSR） 是一种内置的、独立于平台的高质量上采样系统，使引擎能够以低得多的分辨率进行渲染，但输出像素保真度与以更高分辨率渲染的帧相似。TSR在虚幻引擎5中默认启用。

### Flexible Material Editor(灵活的材质编辑器)
使用虚幻引擎基于物理的材质编辑器，享受对角色和对象外观的前所未有的控制。使用基于节点的直观工作流程，快速创建各种表面，在仔细检查时保持视觉效果。在像素级别对材质进行分层和微调值，以实现所需的外观。

### Path Tracer(路径追踪器)
路径追踪器是一种 DXR 加速、物理上精确的渐进式渲染模式，无需任何额外设置即可启用。它生成通常仅在离线渲染中看到的最终像素输出，具有物理正确且无妥协的全局照明、物理校正折射、反射和折射中的特征完整材质以及超级采样抗锯齿等功能。

### Sophisticated lighting(精致的照明)
使用各种高级照明工具（包括大气的太阳和天空环境、体积雾、体积光照贴图、预计算的照明场景和网格距离场），在保持实时性能的同时创建逼真的内部和外部照明效果。
### Post-process and screen-space effects(后期处理和屏幕空间效果)
从一系列胶片品质的后期处理效果中进行选择，以调整场景的整体外观，包括 HDR 泛光、色调映射、镜头光晕、景深、色差、渐晕和自动曝光。屏幕空间反射、环境光遮蔽和全局照明使您能够在实现逼真的效果的同时最大限度地降低成本。
### Color-accurate final output(色彩准确的最终输出)
Composure是虚幻引擎的内置合成器，有助于直接在虚幻编辑器中进行实时合成，从而可以在摄像机中交付最终像素输出。还可以输出单个通道以进行离线合成，同时支持Composure中的OpenColorIO，视口，电影渲染队列和nDisplay，以及在遵守ACES标准的同时输出到HDR显示器的功能可确保整个管线中颜色一致。
## 05 Simulation and effects
### 尼亚加拉粒子和视觉效果
使用内置的Niagara视觉效果编辑器中完全可定制的粒子系统，实时创建电影质量的VFX润色水平，用于火，烟，尘和水等效果。使用粒子光影响场景;使用矢量场创建复杂的粒子运动;作者效应，例如植绒和链条与粒子之间的通信;并使用音频波形数据接口让粒子对音乐或其他音频源做出反应。
### 服装工具
使用混沌物理求解器模拟服装和其他面料。直接在虚幻编辑器中设置服装参数，并立即查看结果，以便快速轻松地进行迭代。使用“油漆布工具”直观地选择网格的哪些区域的行为类似于布，以及它们受物理影响的程度。

## 06 Gameplay and interactivity authoring
### 强大的多人游戏支持
二十多年来，虚幻引擎的多人游戏框架已经在许多平台和游戏类型中进行了实战测试，产生了一些业界最引人入胜的多人游戏体验。虚幻引擎附带了一个开箱即用的可扩展且经过验证的客户端/服务器架构，为任何项目的多人游戏组件带来即时可行性。
### 高级人工智能 （AI）
让AI控制的角色增强对周围世界的空间感知，使他们能够使用虚幻引擎的游戏框架和人工智能系统（通过蓝图或行为树进行控制）做出更智能的动作。动态导航网格会在您移动对象时实时更新，以始终获得最佳路径，而智能对象使您能够创建有意义的游戏交互。
## 07 Interated media support
### 专业的视频 I/O 支持和回放
虚幻引擎在一系列AJA视频系统和Blackmagic卡上以高位深度和帧速率支持4K UHD视频和音频I/O，从而将AR和CG图形集成到直播传输中。完全支持时间码和同步锁相，确保多个不同的视频馈送和信号处理设备之间的同步。
### 虚幻音频引擎
通过丰富的音频功能集增强项目的音频，这些功能集包括实时合成、动态 DSP 效果、物理音频传播建模、OSC 支持、分层声音并发、用于混音的频谱分析器、烘焙频谱分析曲线和包络的功能、卷积混响处理和声场渲染。
## 08 Virtual Production

### 摄像机内视觉特效编辑器
专用的摄像机内视觉特效编辑器提供了一个简化的UI/UX，用于执行常见的舞台操作任务，无需在大纲视图中搜寻特定对象和控件。它使您能够直观高效地在 nDisplay 墙上直观高效地创建、移动和编辑灯光卡、保存模板以及执行一系列颜色校正操作。

### 远程控制协议和 Web UI 构建器
轻松创建自定义 UI，使用户能够通过拖放式 UI 构建器和完全符合 REST 标准的 API 从托管 Web 浏览器的任何设备（包括移动设备）进行设置，例如，您可以通过 iPad 控制现场 LED 音量的照明。还支持 OSC（开放式声音控制）协议，这是一种易于使用的行业标准，用于各种设备、传感器和音频设备之间的双向通信。
## 09 Content

[市场生态系统](https://www.unrealengine.com/marketplace/en-US/store)

虚幻商城拥有数以千计的高质量资源和插件，可加速制作并为你的工作带来新功能。访问新的环境、角色、动画、纹理、道具、声音和视觉效果、音乐曲目、蓝图、中间件集成插件、附加工具和完整的入门工具包。价值数百万美元的内容在市场上免费提供，还有更多内容可供购买。

[行业特定模板](https://docs.unrealengine.com/en-US/working-with-projects-and-templates-in-unreal-engine/)

为了帮助你找到适合项目的起点，并在尽可能短的时间内实现预期的结果，虚幻引擎允许你从各种有用的模板中进行选择，包括用于桌面和VR设备上协作式多用户设计评审的模板、用于产品设计的带有HDRI背景的演播室光照，以及用于建筑可视化的高度逼真的太阳和天空环境。

[奎克塞尔超级扫描](https://www.unrealengine.com/bridge)

每个虚幻引擎许可证都可以免费访问整个Quixel Megascans库，以便在虚幻引擎中使用。基于真实扫描，这个优质的库包含数千个 3D 和 2D PBR 资产，具有优化的拓扑、UV 和 LOD 以及一致的缩放和分辨率。将Quixel Bridge完全集成到虚幻编辑器中后，您只需将选定的Megascan直接拖放到场景中即可。

[示例项目](https://docs.unrealengine.com/en-US/samples-and-tutorials-for-unreal-engine/)

探索、改编虚幻引擎附带的20多个示例项目并从中学习。从逼真的数字人类，到用于直播的虚拟演播室，再到将汽车配置器像素流式传输到远程设备，您将找到一系列示例，这些示例将帮助您在更短的时间内加快自己的项目进度。

## 10 Developer Tool

### Full access to C++ source code（完全访问C++源代码）
通过免费访问完整的C++源代码，你可以研究、自定义、扩展和调试整个虚幻引擎，并无障碍地完成你的项目。随着我们在自己的主线中开发功能，我们在 GitHub 上的源代码存储库会不断更新，因此您甚至不必等待下一个产品发布即可获得最新的代码。
### Seamless Perforce integration（无缝集成 Perforce]）

虚幻编辑器与Perforce具有深度兼容性，将许多版本控制命令直接引入内容浏览器。使用编辑器中的图标和操作更密切地管理项目并监控资源状态，与其他团队成员共享资源和代码，并随时将更改回滚到早期版本。

### Profiling and performance

虚幻引擎包含大量工具，通过识别和消除瓶颈，帮助你分析、分析和优化项目，实现实时性能。最新新增的虚幻洞察系统可收集、分析和可视化虚幻引擎行为数据，帮助你实时或从预先录制的会话中了解引擎性能。

### C++ API

借助强大的C++API，你可以添加新类来扩展虚幻引擎的功能。然后，设计师可以使用蓝图从这些构建块创建自定义游戏玩法或交互。实时编码使你能够在不关闭虚幻编辑器的情况下编译更改，因此你可以快速测试你的进度。

### Oodle and Bink

由RAD Game Tools创建，现在是Epic Games家族的一部分，[Oodle](https://docs.unrealengine.com/en-US/using-oodle-in-unreal-engine/)压缩套件和[Bink Video](https://docs.unrealengine.com/en-US/bink-video-for-unreal-engine/)编解码器是业内最快，最高效，最受欢迎的压缩和编码工具。Oodle包括用于压缩游戏数据，块压缩BC1-BC7纹理和网络流量的工具，而Bink是性能设计的视频编解码器。Oodle和Bink内置于虚幻引擎5中。

## 11 Platform support

### Multi-platform development

借助虚幻引擎，你可以在各种桌面、控制台和移动平台上交付内容，包括Windows、macOS和Linux PC;PlayStation 4，PlayStation 5，Xbox One，Xbox Series X和Nintendo Switch;以及 iOS 和安卓移动设备。

### Containers

容器是软件包，包含在任何环境（包括云）中运行的所有必要元素。对容器的支持使虚幻引擎能够充当强大的独立基础技术层，促进基于云的开发工作流程和部署策略（如像素流送、CI/CD、AI/ML训练、批处理和渲染以及微服务）以及增强的制作管线。

### [XR（AR、VR 和 MR）支持](https://www.unrealengine.com/xr)

虚幻引擎为创建增强现实（AR）、虚拟现实（VR）和混合现实（MR）体验提供了最高质量的解决方案，这要归功于与最流行的平台（包括Oculus VR、SteamVR、HoloLens 2、PlayStation VR2、ARKit和ARCore）的原生集成。借助对 OpenXR 的支持，您可以针对新设备使应用程序面向未来。

### Pixel Streaming（[像素流送](https://docs.unrealengine.com/en-US/pixel-streaming-in-unreal-engine/)）

创作交互式体验，如产品配置器或培训应用程序，将它们托管在基于云的 GPU 或本地服务器上，并将它们流式传输到世界任何地方的远程 PC、Mac、平板电脑或手机上的 Web 浏览器，而无需额外的软件或移植。像素流送也可以从容器环境运行。