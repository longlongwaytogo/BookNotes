# 001-KlayGE 引擎学习



![](images/logo.png)

## 一、KlayGE引擎介绍



### 软件简介

KlayGE中文译为：粘土游戏引擎，是一个开源、跨平台，基于插件结构的游戏引擎。该引擎从 2003 年开始研发，设计目的是用最先进的技术武装引擎，使游戏的开发、测试、移植得到简化。

该引擎是国人龚敏敏开发！

- 图形
  
  - 基于[延迟渲染](http://www.klayge.org/wiki/index.php/延迟渲染)
  - 支持DirectX 11-12，OpenGL 2.0-4.5，以及OpenGL ES 2.0-3.2
  - 采用[FXML](http://www.klayge.org/wiki/index.php?title=FXML&action=edit&redlink=1)作为可渲染物体的特效脚本，可以直接把美工生成的特效导出使用
  - Python脚本可以在运行期动态解释，所以修改脚本以后不需要重新编译
  - 可以通过高度图来建立地形场景
  - 支持骨骼动画
  - 硬件遮挡裁减
  - 粒子系统
  - 后处理技术
  - 自适应硬件状态缓存和延迟更新机制
  - 支持逐像素光照和渲染技术
  - 基于距离场的[字体系统](http://www.klayge.org/wiki/index.php/字体系统)，兼有矢量字体和点阵字体的优点
  - 支持[过程纹理](http://www.klayge.org/wiki/index.php?title=过程纹理&action=edit&redlink=1)
  - 支持[次表面散射](http://www.klayge.org/wiki/index.php?title=次表面散射&action=edit&redlink=1)，可用于渲染树叶、皮肤、玉器等半透明材质
  - 支持[Phong tessellation](http://www.klayge.org/wiki/index.php?title=Phong_tessellation&action=edit&redlink=1)技术，在运行期自动光滑低模
  - 用于[延迟渲染](http://www.klayge.org/wiki/index.php/延迟渲染)的[材质系统](http://www.klayge.org/wiki/index.php/材质系统)
  - 着色
  
  
  
  - 光照
  
  
  
  ### 音频
  
  - 支持各种平台的音频输出
  - 支持3D声音定位和多普勒效应
  - 输入格式支持Ogg Vorbis
  - 支持流式播放
  
  ### 工具
  
  - 法线图生成器，可以从高度图生成法线图
  - 距离图生成器，可以从高度图或3D纹理生成距离图
  - MeshML导出插件，从3ds Max导出模型
  - OpenGL兼容性检测工具
  - HDR压缩器，支持cubemap和2D HDR纹理的压缩
  - Normalmap压缩器，2:1或4:1的压缩率
  - 基于distance的[字体](http://www.klayge.org/wiki/index.php/字体系统)生成器，可以把矢量字体转换成引擎使用的字体格式
  - FXML2Shader工具，把[FXML](http://www.klayge.org/wiki/index.php?title=FXML&action=edit&redlink=1)的特效脚本转换成HLSL
  - [Juda texture](http://www.klayge.org/wiki/index.php/Juda_texture)打包工具，把多张普通纹理打包成一个Juda texture
  - Color Grading纹理生成工具
  
  ### 程序特性
  
  - **KlayGE**是开放源代码的，包含了100%的引擎、工具的源代码
  - 可扩展的、面向对象的C++引擎，带有用于静态和动态加载代码和资源的软件架构，易于移植和调试
  - 用Python作为脚本语言，提供了对动态数据的自动支持，开发调试方便，并很容易和C++主程序配合工作
  - 在各平台上都是原生代码
  
  ## 外部链接
  
  - [KlayGE网站](http://www.klayge.org/)
  - [KlayGE图集](http://www.klayge.org/gallery/)



# 二、主要模块介绍

KlayGE的设计也比较容易理解，大体分成以下几部分：

- DXBC2GLSL DX-GLSL shader转换工具

- External： 第三方扩展依赖库

  - 7z：压缩
  - assimp： 外部模型导入
  - D3dCompiler: dx HLSL 编译工具
  - fmt：
  - FreeImage：
  - freetype
  - goolgetest： 测试框架
  - libogg： 音频
  - liborbis：
  - openal-soft
  - Python
  - zlib

- glloader： OpenGL API 接口加载

- KFL： 基础公共库

- kfont： 字体库

- KlayGE： 引擎库

  - Engine： 引擎主体

    - Core

      - KlayGE_Core

      - KlayGE_RC

      - TableGen
    - KGEConfig
    - Plugins
      - Audio
        - KlayGE_AudioDataSource_NullAudioDataSource
        - KlayGE_AudioDataSource_OggVorbis
        - KlayGE_AudioEngine_NullAudio
        - KlayGE_AudioEngine_OpenAL
        - KlayGE_AudioEngine_XAudio
      - Devhelper
        - KlayGE_DevHelper
      - Render
      - KlayGE_RenderEngine_D3D11
      - KlayGE_RenderEngine_D3D12
      - KlayGE_RenderEngine_NullRender
      - KlayGE_RenderEngine_OpenGL
      - Input
        - KlayGE_InputEngine_MsgInput
        - KlayGE_InputEngine_NullInput
      - Scene Management
        - KlayGE_Scene_OCTree
      - Script
        - KlayGE_ScriptEngine_NullScript
        - KlayGE_ScriptEngine_Python
      - Show
        - KlayGE_ShowEngine_DShow
        - KlayGE_ShowEngine_MFShow
        - KlayGE_ShowEngine_NullShow
  
   - Samples
  
     - AreaLighting
     - AtmosphericScattering
     - CascadedShadowMap
     - CausticsMap
     - DeepGBuffers
     - DeferredRendering
     - DetailedSurface
     - DetailedSurfaceDR
     - EnvLighting
     - Foliage
     - GPUParticleSystem
     - JudaTexViewer
     - Metalness
     - Metalness
     - MotionBlurDoF
     - Ocean
     - OIT
     - ParticleEditor
     - PostProcessing
     - ProceduralTex
     - Reflection
     - SampleCommon
     - ScenePlayer
     - ShadowCubeMap
     - SkinnedMesh
     - Sound
     - SSSSS
     - SubSurface
     - Text
     - VDMParticle
     - VectorTex
     - VideoTexture
  
   - Tests
  
     - Tests
  
   - Tools
  
     - KGEditor
       - KGEditor
       - KGEditorCore
       - KGEditorCoreWrapper
  
     - MtlEditor
       - MtlEditor
       - MtlEditorCore
       - MtlEditorCoreWrapper
  
     - TexViewer
       - TexViewer
       - TexViewerCore
       - TexViewerCoreWrapper
  
     - ColorGradingTexGen
     - D3DCompilerWrapper
     - DistanceMapCreator
     - FFTLensEffectsGen
     - Fxml2Shader
     - FxmlJit
     - GLCompatibility
     - GLESCompatibility
     - HDRCompressor
     - HWCollect
     - ImposterGen
     - JudaTexPacker
     - KFontGen
     - NoiseTexGen
     - Normal2NaLength
     - PlatformDeployer
     - PrefilterCube
     - Tex2JTML
     - ToolCommon
     - VectorTexGen
  
   - Tutorials
  
     - DistanceMapping
  
     - Fractal
     - InputCaps
     - RasterizationOrder
     - Refract
     - Tessellation
     - Tutor1
     - Tutor2
     - VertexDisplacement
  



链接：

官网地址：

http://www.klayge.org/wiki/index.php

http://www.klayge.org/

[KlayGE学习主目录](https://blog.csdn.net/kasteluo/article/details/130200334)
