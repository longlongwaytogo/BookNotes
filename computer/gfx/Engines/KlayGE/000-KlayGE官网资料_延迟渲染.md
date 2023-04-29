延迟渲染

http://www.klayge.org/wiki/index.php/%E5%BB%B6%E8%BF%9F%E6%B8%B2%E6%9F%93#Deferred_Lighting.E7.9A.84.E6.A1.86.E6.9E.B6



本文讲述的是[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)中使用的延迟渲染方法。

## Contents

 [[hide](http://www.klayge.org/wiki/index.php/延迟渲染#)] 

- [1 Deferred Lighting的框架](http://www.klayge.org/wiki/index.php/延迟渲染#Deferred_Lighting.E7.9A.84.E6.A1.86.E6.9E.B6)
- [2 Lighting pass](http://www.klayge.org/wiki/index.php/延迟渲染#Lighting_pass)
- [3 G-Buffer的分配](http://www.klayge.org/wiki/index.php/延迟渲染#G-Buffer.E7.9A.84.E5.88.86.E9.85.8D)
- [4 Shading Pass](http://www.klayge.org/wiki/index.php/延迟渲染#Shading_Pass)
- 5 Light volume
  - [5.1 优化1：视锥检测](http://www.klayge.org/wiki/index.php/延迟渲染#.E4.BC.98.E5.8C.961.EF.BC.9A.E8.A7.86.E9.94.A5.E6.A3.80.E6.B5.8B)
  - [5.2 优化2：Conditional Rendering](http://www.klayge.org/wiki/index.php/延迟渲染#.E4.BC.98.E5.8C.962.EF.BC.9AConditional_Rendering)
  - [5.3 优化3：Stencil Buffer](http://www.klayge.org/wiki/index.php/延迟渲染#.E4.BC.98.E5.8C.963.EF.BC.9AStencil_Buffer)
  - [5.4 优化4：Shadowing pass](http://www.klayge.org/wiki/index.php/延迟渲染#.E4.BC.98.E5.8C.964.EF.BC.9AShadowing_pass)
- 6 Anti-Alias
  - [6.1 Edge AA](http://www.klayge.org/wiki/index.php/延迟渲染#Edge_AA)
  - [6.2 利用硬件MSAA作边缘检测](http://www.klayge.org/wiki/index.php/延迟渲染#.E5.88.A9.E7.94.A8.E7.A1.AC.E4.BB.B6MSAA.E4.BD.9C.E8.BE.B9.E7.BC.98.E6.A3.80.E6.B5.8B)
  - [6.3 能不能就用MSAA？](http://www.klayge.org/wiki/index.php/延迟渲染#.E8.83.BD.E4.B8.8D.E8.83.BD.E5.B0.B1.E7.94.A8MSAA.EF.BC.9F)
- 7 展望未来
  - [7.1 shading pass再次渲染物体的改进](http://www.klayge.org/wiki/index.php/延迟渲染#shading_pass.E5.86.8D.E6.AC.A1.E6.B8.B2.E6.9F.93.E7.89.A9.E4.BD.93.E7.9A.84.E6.94.B9.E8.BF.9B)
  - [7.2 彩色的specular](http://www.klayge.org/wiki/index.php/延迟渲染#.E5.BD.A9.E8.89.B2.E7.9A.84specular)
  - [7.3 inferred lighting](http://www.klayge.org/wiki/index.php/延迟渲染#inferred_lighting)
  - [7.4 Anti-alias](http://www.klayge.org/wiki/index.php/延迟渲染#Anti-alias_2)
  - [7.5 各向异性BRDF](http://www.klayge.org/wiki/index.php/延迟渲染#.E5.90.84.E5.90.91.E5.BC.82.E6.80.A7BRDF)
- 8 KlayGE 4.0中的改进
  - [8.1 流水线](http://www.klayge.org/wiki/index.php/延迟渲染#.E6.B5.81.E6.B0.B4.E7.BA.BF)
  - [8.2 G-Buffer布局](http://www.klayge.org/wiki/index.php/延迟渲染#G-Buffer.E5.B8.83.E5.B1.80)
  - [8.3 透明物体](http://www.klayge.org/wiki/index.php/延迟渲染#.E9.80.8F.E6.98.8E.E7.89.A9.E4.BD.93)
  - [8.4 实时全动态GI](http://www.klayge.org/wiki/index.php/延迟渲染#.E5.AE.9E.E6.97.B6.E5.85.A8.E5.8A.A8.E6.80.81GI)
  - 8.5 Post process
    - [8.5.1 HDR](http://www.klayge.org/wiki/index.php/延迟渲染#HDR)
    - [8.5.2 AA](http://www.klayge.org/wiki/index.php/延迟渲染#AA)
    - [8.5.3 Color grading](http://www.klayge.org/wiki/index.php/延迟渲染#Color_grading)
  - [8.6 总结](http://www.klayge.org/wiki/index.php/延迟渲染#.E6.80.BB.E7.BB.93)
- 9 KlayGE 4.3中的改进
  - [9.1 GI和Deferred的分离](http://www.klayge.org/wiki/index.php/延迟渲染#GI.E5.92.8CDeferred.E7.9A.84.E5.88.86.E7.A6.BB)
  - [9.2 未来](http://www.klayge.org/wiki/index.php/延迟渲染#.E6.9C.AA.E6.9D.A5)
- [10 多视口的改进](http://www.klayge.org/wiki/index.php/延迟渲染#.E5.A4.9A.E8.A7.86.E5.8F.A3.E7.9A.84.E6.94.B9.E8.BF.9B)
- [11 重构Update](http://www.klayge.org/wiki/index.php/延迟渲染#.E9.87.8D.E6.9E.84Update)
- [12 透明物体和Deep G-Buffer](http://www.klayge.org/wiki/index.php/延迟渲染#.E9.80.8F.E6.98.8E.E7.89.A9.E4.BD.93.E5.92.8CDeep_G-Buffer)

## Deferred Lighting的框架

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.11的例子已经从Deferred Shading改成了更节省带宽的Deferred Lighting。这里先对Deferred Lighting作一个简要的介绍，并假设读者已经了解了Deferred Shading。

Deferred Lighting的渲染架构可以分为三个阶段：

```
1. for each object
   {
      填充G-Buffer
   }
2. for each light
   {
      Lighting pass
   }
3. for each object
   {
     执行shading
   }
```

与Deferred Shading不同的是，shading（也就是和材质相关）的计算仅仅发生在最后一个阶段。所以，G-Buffer中需要保存的信息得到极大地减小，甚至不再需要MRT。

## Lighting pass

Lighting pass在Deferred Lighting框架处于核心地位，在这里我打算先把lighting pass解析清楚。一旦lighting pass表达好了，G-Buffer所需要保存的信息，以及shading pass能得到的信息也都清楚了。

[基于物理的BRDF](http://www.klayge.org/wiki/index.php/基于物理的BRDF)推出了渲染模型总公式：
$$
L_{o}(\mathbf{v})=\pi\rho(\mathbf{l_c}, \mathbf{v})\otimes \mathbf{c}_{light} (\mathbf{n} \cdot \mathbf{l_c})=(\mathbf{c}_{diff} + \frac {\alpha + 2} {8}(\mathbf{n} \cdot \mathbf{h})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_c},\mathbf{h})) \otimes \mathbf{c}_{light} (\mathbf{n} \cdot \mathbf{l_c})
$$

再有N个光源的情况下，每个像素的光照响应就是

$$
L_{o}(\mathbf{v})=\pi\rho(\mathbf{l_{c1}}, \mathbf{v})\otimes \mathbf{c}_{light1} (\mathbf{n} \cdot \mathbf{l_{c1}})+\pi\rho(\mathbf{l_{c2}}, \mathbf{v})\otimes \mathbf{c}_{light2} (\mathbf{n} \cdot \mathbf{l_{c2}})
$$


![LaTeX:  + \ldots](http://www.forkosh.com/mathtex.cgi?%20%2B%20%5Cldots)

![LaTeX: +\pi\rho(\mathbf{l_cN}, \mathbf{v})\otimes \mathbf{c}_{lightN} (\mathbf{n} \cdot \mathbf{l_{cN}})](http://www.forkosh.com/mathtex.cgi?%2B%5Cpi%5Crho%28%5Cmathbf%7Bl_cN%7D%2C%20%5Cmathbf%7Bv%7D%29%5Cotimes%20%5Cmathbf%7Bc%7D_%7BlightN%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7BcN%7D%7D%29)

对于Deferred shading来说，每一个shading pass就是执行一个

![LaTeX: \pi\rho(\mathbf{l_cn}, \mathbf{v})\otimes \mathbf{c}_{lightn} (\mathbf{n} \cdot \mathbf{l_cn})](http://www.forkosh.com/mathtex.cgi?%5Cpi%5Crho%28%5Cmathbf%7Bl_cn%7D%2C%20%5Cmathbf%7Bv%7D%29%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blightn%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_cn%7D%29)

而对于Deferred lighting来说，公式需要重新整理一下：

![LaTeX: L_{o}(\mathbf{v})=(\mathbf{c}_{diff} + \frac {\alpha + 2} {8}(\mathbf{n} \cdot \mathbf{h_1})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{c1}},\mathbf{h_1})) \otimes \mathbf{c}_{light1} (\mathbf{n} \cdot \mathbf{l_{c1}})](http://www.forkosh.com/mathtex.cgi?L_%7Bo%7D%28%5Cmathbf%7Bv%7D%29%3D%28%5Cmathbf%7Bc%7D_%7Bdiff%7D%20%2B%20%5Cfrac%20%7B%5Calpha%20%2B%202%7D%20%7B8%7D%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_1%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bc1%7D%7D%2C%5Cmathbf%7Bh_1%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blight1%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc1%7D%7D%29)

![LaTeX: +(\mathbf{c}_{diff} + \frac {\alpha + 2} {8}(\mathbf{n} \cdot \mathbf{h_2})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{c2}},\mathbf{h_2})) \otimes \mathbf{c}_{light2} (\mathbf{n} \cdot \mathbf{l_{c2}})](http://www.forkosh.com/mathtex.cgi?%2B%28%5Cmathbf%7Bc%7D_%7Bdiff%7D%20%2B%20%5Cfrac%20%7B%5Calpha%20%2B%202%7D%20%7B8%7D%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_2%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bc2%7D%7D%2C%5Cmathbf%7Bh_2%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blight2%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc2%7D%7D%29)

![LaTeX: +\ldots](http://www.forkosh.com/mathtex.cgi?%2B%5Cldots)

![LaTeX: +(\mathbf{c}_{diff} + \frac {\alpha + 2} {8}(\mathbf{n} \cdot \mathbf{h_N})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{cN}},\mathbf{h_N})) \otimes \mathbf{c}_{lightN} (\mathbf{n} \cdot \mathbf{l_{cN}})](http://www.forkosh.com/mathtex.cgi?%2B%28%5Cmathbf%7Bc%7D_%7Bdiff%7D%20%2B%20%5Cfrac%20%7B%5Calpha%20%2B%202%7D%20%7B8%7D%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_N%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7BcN%7D%7D%2C%5Cmathbf%7Bh_N%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7BlightN%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7BcN%7D%7D%29)

![LaTeX: =\mathbf{c}_{diff}\otimes (\mathbf{c}_{light1} (\mathbf{n} \cdot \mathbf{l_{c1}}) + \mathbf{c}_{light2} (\mathbf{n} \cdot \mathbf{l_{c2}}) + \ldots + \mathbf{c}_{lightN} (\mathbf{n} \cdot \mathbf{l_{cN}}))](http://www.forkosh.com/mathtex.cgi?%3D%5Cmathbf%7Bc%7D_%7Bdiff%7D%5Cotimes%20%28%5Cmathbf%7Bc%7D_%7Blight1%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc1%7D%7D%29%20%2B%20%5Cmathbf%7Bc%7D_%7Blight2%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc2%7D%7D%29%20%2B%20%5Cldots%20%2B%20%5Cmathbf%7Bc%7D_%7BlightN%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7BcN%7D%7D%29%29)

![LaTeX: + \frac {\alpha + 2} {8}(((\mathbf{n} \cdot \mathbf{h_1})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{c1}},\mathbf{h_1})) \otimes \mathbf{c}_{light1} (\mathbf{n} \cdot \mathbf{l_{c1}})](http://www.forkosh.com/mathtex.cgi?%2B%20%5Cfrac%20%7B%5Calpha%20%2B%202%7D%20%7B8%7D%28%28%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_1%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bc1%7D%7D%2C%5Cmathbf%7Bh_1%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blight1%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc1%7D%7D%29)

![LaTeX: + ((\mathbf{n} \cdot \mathbf{h_2})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{c2}},\mathbf{h_2})) \otimes \mathbf{c}_{light2} (\mathbf{n} \cdot \mathbf{l_{c2}})](http://www.forkosh.com/mathtex.cgi?%2B%20%28%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_2%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bc2%7D%7D%2C%5Cmathbf%7Bh_2%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blight2%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bc2%7D%7D%29)

![LaTeX: + \ldots](http://www.forkosh.com/mathtex.cgi?%2B%20%5Cldots)

![LaTeX: + ((\mathbf{n} \cdot \mathbf{h_N})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{cN}},\mathbf{h_N})) \otimes \mathbf{c}_{lightN} (\mathbf{n} \cdot \mathbf{l_{cN}}))](http://www.forkosh.com/mathtex.cgi?%2B%20%28%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_N%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7BcN%7D%7D%2C%5Cmathbf%7Bh_N%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7BlightN%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7BcN%7D%7D%29%29)

由于**cdiff**是到最后的shading pass才计算，所以在每一个light pass里面，diffuse和specular必须分开才能保证结果正确：

![LaTeX: Diffuse: \mathbf{c}_{lightn} (\mathbf{n} \cdot \mathbf{l_{cn}})](http://www.forkosh.com/mathtex.cgi?Diffuse%3A%20%5Cmathbf%7Bc%7D_%7Blightn%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bcn%7D%7D%29)

![LaTeX: Specular: ((\mathbf{n} \cdot \mathbf{h_n})^{\alpha} F(\mathbf{c}_{spec}, \mathbf{l_{cn}},\mathbf{h_n})) \otimes \mathbf{c}_{lightn} (\mathbf{n} \cdot \mathbf{l_{cn}})](http://www.forkosh.com/mathtex.cgi?Specular%3A%20%28%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_n%7D%29%5E%7B%5Calpha%7D%20F%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bcn%7D%7D%2C%5Cmathbf%7Bh_n%7D%29%29%20%5Cotimes%20%5Cmathbf%7Bc%7D_%7Blightn%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bcn%7D%7D%29)

为了把diffuse和specular放入4个通道的buffer中，就只能牺牲specular的颜色，只剩下亮度，同时**cspec**也简化成一个标量。所以，lighting pass的计算成了：

![LaTeX: float4(1, 1, 1, (\mathbf{n} \cdot \mathbf{h_n})^{\alpha} F(c_{spec}, \mathbf{l_{cn}},\mathbf{h_n})) \times \mathbf{c}_{lightn} (\mathbf{n} \cdot \mathbf{l_{cn}})](http://www.forkosh.com/mathtex.cgi?float4%281%2C%201%2C%201%2C%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_n%7D%29%5E%7B%5Calpha%7D%20F%28c_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bcn%7D%7D%2C%5Cmathbf%7Bh_n%7D%29%29%20%5Ctimes%20%5Cmathbf%7Bc%7D_%7Blightn%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bcn%7D%7D%29)

## G-Buffer的分配

在Deferred框架中，不管是Deferred Shading还是Deferred Lighting，G-Buffer的分配都是非常关键的。前面得出的lighting pass公式如下：

![LaTeX: float4(1, 1, 1, (\mathbf{n} \cdot \mathbf{h_n})^{\alpha} F(c_{spec}, \mathbf{l_{cn}},\mathbf{h_n})) \times \mathbf{c}_{lightn} (\mathbf{n} \cdot \mathbf{l_{cn}})](http://www.forkosh.com/mathtex.cgi?float4%281%2C%201%2C%201%2C%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bh_n%7D%29%5E%7B%5Calpha%7D%20F%28c_%7Bspec%7D%2C%20%5Cmathbf%7Bl_%7Bcn%7D%7D%2C%5Cmathbf%7Bh_n%7D%29%29%20%5Ctimes%20%5Cmathbf%7Bc%7D_%7Blightn%7D%20%28%5Cmathbf%7Bn%7D%20%5Ccdot%20%5Cmathbf%7Bl_%7Bcn%7D%7D%29)

从公式可以看出，在light pass里需要的量有**n**，**h**，alpha，cspec，**lc**。因为**h** = (**v** + **lc**) / 2（见[基于物理的BRDF](http://www.klayge.org/wiki/index.php/基于物理的BRDF)），而**lc** = normalize(**l** - **p**)（**l**是光源位置，**p**是要计算的点位置），所以最终需要G-Buffer提供的量有：**n**，**p**，alpha和cspec。要完整的保存这些量，一共需要8个通道，normal占3个，position占3个，alpha和cspec分别占一个。这样对G-Buffer来说消耗太大了，必须要缩减。

显而易见的是，normal是经过归一化的，只需要保存2个分量。http://aras-p.info/texts/CompactNormalStorage.html比较了多种保存2分量的方法，其中Spheremap transform速度和效果综合起来最佳，Crytek也在用同样的方法，即：

```
float2 encode(float3 normal)
{
   return normalize(normal.xy) * sqrt(normal.z * 0.5 + 0.5);
}
float3 decode(float2 n)
{
   float3 normal;
   normal.z = dot(n, n) * 2 - 1;
   normal.xy = normalize(n) * sqrt(1 - normal.z * normal.z);
   return normal;
}
```

下一步是position。实际上像素所在的位置已经提供了x和y，需要保存的仅仅是z。position何以很好地从z和像素位置计算出来。这里保存的是view space的z除以far plane。在lighting pass，pixel shader里拿到像素在view space的位置之后，做这样的计算：

```
p = view_dir * ((z * far_plane) / view_dir.z);
```

其中，view_dir是在vertex shader中计算之后传到pixel shader。对于把光源的几何体直接作为光源几何的情况（如果你不熟悉这个，请见下篇），那么view_dir就是顶点乘上world * view矩阵之后的结果。对于用全屏的四边形作为光源几何的情况，view_dir就是把view frustum在far plane上的四个点乘上inverse(projection)矩阵之后的结果。z * far_plane就还原出了该点在view space的z，然后根据相似三角形的定理很容易就能推出这个还原公式。现在，position成功地压缩到了1个通道。

剩下的就是alpha和cspec。如果不需要fresnel，可以直接忽略cspec，留到shading pass再做，这里直接存alpha就可以了。否则，就需要把alpha和cspec放入同一个通道。我用的方法是，floor(cspec * 100)作为整数部分，clamp(alpha, 0, 255) / 256座位小数部分。这样的限制是，alpha取值范围为[0, 256)，一般来说够用了。

由此，所有lighting pass需要的信息都被压进4个通道内，G-Buffer只需要1张texture，省去了MRT。

## Shading Pass

shading pass需要把前面所有lighting pass积累出来的光照信息和物体本身的材质信息组合起来，得出最后的着色。物体材质中的cspec已经存在G-Buffer，并在lighting pass中计算了，所以shading pass输入的材质有**cdiff**，**cspec**，**cemit**，alpha。别忘了在前面的公式中，specular号需要乘上归一化系数(alpha + 2) / 8。另一方面，在lighting pass的结果里，rgb存的是积累的diffuse，a存的是积累的specular亮度，如果还有计算AO，那么shading所用的公式就是：

![LaTeX: \mathbf{c}_{emit} + (lighting.rgb * \mathbf{c}_{diff} + \frac{\alpha + 2}{8} * lighting.a) * ao](http://www.forkosh.com/mathtex.cgi?%5Cmathbf%7Bc%7D_%7Bemit%7D%20%2B%20%28lighting.rgb%20%2A%20%5Cmathbf%7Bc%7D_%7Bdiff%7D%20%2B%20%5Cfrac%7B%5Calpha%20%2B%202%7D%7B8%7D%20%2A%20lighting.a%29%20%2A%20ao)

如果在G-Buffer和lighting pass因为不考虑fresnel而至保存了alpha，那么shading pass的公式就变成：

![LaTeX: \mathbf{c}_{emit} + (lighting.rgb * \mathbf{c}_{diff} + \frac{\alpha + 2}{8} * \mathbf{c}_{spec} * lighting.a) * ao](http://www.forkosh.com/mathtex.cgi?%5Cmathbf%7Bc%7D_%7Bemit%7D%20%2B%20%28lighting.rgb%20%2A%20%5Cmathbf%7Bc%7D_%7Bdiff%7D%20%2B%20%5Cfrac%7B%5Calpha%20%2B%202%7D%7B8%7D%20%2A%20%5Cmathbf%7Bc%7D_%7Bspec%7D%20%2A%20lighting.a%29%20%2A%20ao)

## Light volume

在Deferred Rendering中，表示一个光源最简单的方法就是一个全屏的四边形。它能让G-Buffer的每一个pixel都参与计算，在pixel shader中才过滤掉多余的像素。虽然可以保证结果正确，但毕竟多余计算太多，效率不高。这里常用的一个优化就是用一个凸的几何形状来表示光源。该几何 形状覆盖的pixel才计算该光源对它的贡献。显而易见的是，spot light用圆锥，point light用球或者立方体，directional light和ambient light用全屏四边形。下图画了一个spot light的volume：

[![img](http://www.klayge.org/wiki/images/thumb/f/f9/Spot_volume.jpg/400px-Spot_volume.jpg)](http://www.klayge.org/wiki/index.php/File:Spot_volume.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Spot_volume.jpg)

Spot light volume

这样的几何体类似于古老的shadow volume技术所用的几何体，所以我把它叫做light volume。但由于light volume保证是凸几何体，在渲染上比shadow volume简单不少。

### 优化1：视锥检测

有了light volume，就可以把它和视锥做一个相交检测。light volume完全包住了light能覆盖的范围，所以如果一个light volume在视锥之外，这个光源就可以直接忽略。

### 优化2：Conditional Rendering

D3D10及以上的显卡都支持conditional rendering，基本用法是这样的：

```
BeginQuery()
Draw object with simple shader
EndQuery()
...
BeginConditionalRendering()
Draw object with real shader
EndConditionalRendering()
```

如果第一个Draw没有产生可见的像素，那么第二个Draw就会被忽略。与Occlusion query不同的是，在这个过程中不需要把query的结果返回CPU，流水线不会被打断，效率更高。用这种方法，就可以直接忽略掉不照亮任何一个pixel的光源。

### 优化3：Stencil Buffer

和shadow volume一样，这里可以用stencil buffer来标记出光源能找到的像素。实际上，在shadow volume上用的优化也可以照搬过来。比如说，双面stencil是最常用的一个方法，在一个pass内就能同时加减正反两面的stencil。同 样，light volume也存在视点进入volume的问题，需要改变depth function，cull mode和back stencil pass。

### 优化4：Shadowing pass

[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)用shadow map渲染阴影。其生成shadow map的过程和普通方法一样，这里就不累赘了。在使用shadow map的时候有两个选择，以前的方法是在lighting pass里计算光照的时候就查询shadow map，同时计算阴影。另一个方法来自Screen space shadow map。在每个lighting pass之前加一个shadowing pass，仅仅查询shadow map和计算阴影本身（结果是个灰度图）。这样的好处是，shadowing可以在更低的分辨率上计算，而不用和lighting pass用同样的分辨率，提高效率。另外，shadowing pass的结果可以像screen space shadow map那样做一次blur，在让lighting pass使用。

## Anti-Alias

从Deferred Shading发明的一天起，anti-alias的问题就一直困扰着所有Deferred的方法。虽然很多无良的游戏厂商直接在Deferred Rendering的游戏里不支持AA，但确实AA对提升画面质量很有帮助。

### Edge AA

在Deferred的框架里，很自然会想到用Edge AA来处理AA。其过程不外乎：

1. 边缘检测，得到每个像素“像边缘的程度”
2. 在shader里根据“像边缘的程度”来控制采样坐标

这本身并不是个复杂的过程，尤其是第二步，非常直截了当了，所以这里集中讨论的是如何进行边缘检测。

GPU Gems 2的“Deferred Shading in STALKER”一文提供了一种边缘检测的方法，通过把周围像素的法线差和深度差的和来判断边缘，由e_barrier这个参数来定义阈值和比例，而这个参数和分辨率有关。GPU Gems 3的“Deferred Shading in Tabula Rasa”改进了这个过程，只判断法线差和深度差最大和最小的两组。由于只是局部的相对量而已，这样就做到了和分辨率无关的边缘检测。KlayGE目前用的也是这种方法，得到的边缘如下：

[![img](http://www.klayge.org/wiki/images/thumb/7/78/Curr_edge.jpg/400px-Curr_edge.jpg)](http://www.klayge.org/wiki/index.php/File:Curr_edge.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Curr_edge.jpg)

Edge

另一个可能用于边缘检测的方法是，前面提到了如何恢复出每个pixel的view space position，每个pixel取得周围4个pixel的位置之后，就可以直接cross得出一个normal，姑且称为screen space normal。如果一个像素是连续的，那么这个normal就会很接近于G-Buffer中保存的normal，否则它们的方向就会差别很大。下图为G- Buffer中的normal：

[![img](http://www.klayge.org/wiki/images/thumb/a/a5/Normal_g_buffer.jpg/400px-Normal_g_buffer.jpg)](http://www.klayge.org/wiki/index.php/File:Normal_g_buffer.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_g_buffer.jpg)

Normal in G-Buffer

这是screen space计算出的normal：

[![img](http://www.klayge.org/wiki/images/thumb/8/8b/Normal_ss.jpg/400px-Normal_ss.jpg)](http://www.klayge.org/wiki/index.php/File:Normal_ss.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_ss.jpg)

Normal in screen space

把这两个normal做一次dot，小于某个阈值的就认为是边缘，得到：

[![img](http://www.klayge.org/wiki/images/thumb/4/45/New_edge.jpg/400px-New_edge.jpg)](http://www.klayge.org/wiki/index.php/File:New_edge.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:New_edge.jpg)

Screen space normal based edge

### 利用硬件MSAA作边缘检测

前面提到的边缘检测结果虽然不错，但其实都是是参数相关的。能否就用硬件的MSAA来做边缘检测呢？在Shader model 3.0以上的GPU，vertex attribute插值的时候可以选择centroid这个modifier。开启了centroid的attribute，会选择覆盖到的sample 中心来插值，而不是像素中心。所以，同一个属性，如果即有centroid又有不带centroid的版本都传给pixel shader，在pixel shader里面判断两者不一致，就表示这个pixel在边缘上。这样的话，边缘的情况就和硬件MSAA完全一致了。但其实MSAA会过渡判断边缘，所有三角形的边缘都会被认出来，即便只是物体内部的。所以谨慎使用。

### 能不能就用MSAA？

前面讨论了那么多都是基于Edge的AA。在Deferred Lighting框架下，难道就不能直接用MSAA？可以！这也是Deferred Lighting比Deferred Shading优秀的方面之一。Deferred Shading不能直接MSAA的本质原因是在G-Buffer之后，物体几何信息全部抛弃了。相比Deferred Lighting，在shading pass，物体会被再次渲染一遍，这个时候还是有几何信息的，如果在shading pass打开了MSAA，就可以像Forward shading那样利用硬件MSAA了。唯一不同的是，光照来自于lighting pass的texture，而不是从光源计算。就算硬件MSAA，也只是每个pixel执行一次pixel shader，在按照覆盖情况写入sample的，所以在这里视觉上几乎和Forward shading一样。

## 展望未来

### shading pass再次渲染物体的改进

Deferred Lighting最受争议的一点应属在shading pass需要再次渲染几何体了。如果物体很多，尤其是有tessellation和GS的，多渲一遍有可能抵消了lighting pass带来的性能提升。改进的方法之一就是在建立G-Buffer阶段，用类似Deferred Shading的fat G-Buffer。除了原先的一张纹理，还需要一张纹理用来存放diffuse信息。但是lighting pass和原来一样，不涉及diffuse。shading pass就变成画一个全屏四边形，从G-Buffer的第二章纹理读取diffuse，进行着色。甚至emit也这么处理。这种方法介于Deferred Shading和Deferred Lighting之间。

### 彩色的specular

在前文提到过，为了把lighting pass中的diffuse和specular都塞到4个通道里，就只能舍弃specular的颜色，只保存亮度。如果要RGB三个通道的specular，近似的方法是通过diffuse积累结果的颜色来计算specular的颜色。这是个很粗糙的近似，虽然不是正确的，不过能骗骗眼睛：

![LaTeX: specular = diffuse(\frac{lum_{spec}}{lum_{diff} + \epsilon})](http://www.forkosh.com/mathtex.cgi?specular%20%3D%20diffuse%28%5Cfrac%7Blum_%7Bspec%7D%7D%7Blum_%7Bdiff%7D%20%2B%20%5Cepsilon%7D%29)

其中lumspec是累积出来的specular亮度，lumdiff是用累积出来的diffuse颜色计算出的亮度。epsilon是为了避免lumdiff为零。 另一种方法是lighting pass用6个通道。但是如果每个通道都是float 16的，也就是96bpp，带宽开销非常大，就不合适了。我的一个想法是把diffuse和specular都转换到YUV空间。这个空间的一个好处是Y 是float 16的，U和V都只要8 bit就可以了。所以可以这么安排MRT：第一张texture格式为G16R16F，保存diffuse和specular的Y；第二张texture 格式为ABGR8，分别保存两者的U和V。这样只有64bpp，但能保存正确的彩色diffuse和specular。由于YUV格式也是可以相加的，这个地方仍可以用原先的lighting pass积累方法。

### inferred lighting

Lighting pass可以借用inferred lighting的核心思想来加速。也就是说，lighting pass不需要全尺寸，只需要在一个比较小的render target上执行即可（比如3/4大小）。G-Buffer仍是全尺寸的，并在G-Buffer生成后作一次边缘检测。Shading pass也是全尺寸的，在采样lighting pass texture的时候，利用边缘检测的结果进行保边缘的插值（一般称为Discontinuity Sensitive Filtering，DSF），得到全尺寸lighting的近似。

[![img](http://www.klayge.org/wiki/images/0/09/Dsf.jpg)](http://www.klayge.org/wiki/index.php/File:Dsf.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Dsf.jpg)

DSF

上图是使用了800×450的lighting直接拉伸到1280×720做shading的结果，关闭DSF，锯齿严重。下图打开了DSF，基本解决了锯齿问题。

### Anti-alias

前面文章讲了很多AA的方法，但那些都是在空间上做AA，比较适合近处物体。对于远处物体来说，空间上AA得到的收益有限，必须在时间上进行AA。结合上MLAA的威力，应该能有很小的代价实现很接近16xMSAA的结果。

### 各向异性BRDF

Crytek的“CryENGINE 3: Reaching the speed of light”里提到了在Deferred Lighting框架下加入各向异性BRDF的方法。它用了Spherical Gaussian（SG）来近似出NDF（来自于SIGGRAPH Asia 2009的All-Frequency Rendering of Dynamic, Spatially-Varying Reflectance），但这个SG只是per-object的。在G-Buffer阶段，不保存normal，而保存SG展开成lobe的系数。而 BRDF的其他几个项，Fresnel term、Geometry term，都留到shading pass才计算。这种方法的好处是，对lighting pass来说一切都是透明的，它照样可以按原来的方法累积光照，因为Microfacet BRDF中除了NDF，其他都作为公因数提取出去了（Microfacet BRDF的详细讲解可以参见“[基于物理的BRDF](http://www.klayge.org/wiki/index.php/基于物理的BRDF)”）。实际上，Fresnel term的系数是**l**和**h**，必须在lighting pass做。这里相信Crytek是用了**n**和**v**来代替，这样不是物理正确的，只有在高光的中心点，dot(**l**, **h**)才等于dot(**n**, **v**)，其他地方dot(**n**, **v**)会更迅速地衰减，到边缘地方就非常明显了。如果不在乎这个，是可以把NDF都用SG来表示，并用统一的方法进行渲染。

保存lobe的G-Buffer是这个样子的：

[![img](http://www.klayge.org/wiki/images/thumb/b/bc/G_buffer_lobe.jpg/400px-G_buffer_lobe.jpg)](http://www.klayge.org/wiki/index.php/File:G_buffer_lobe.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:G_buffer_lobe.jpg)

Lobes in G-Buffer

各向异性BRDF渲染出来的结果：

[![img](http://www.klayge.org/wiki/images/thumb/f/f8/Aniso_brdf.jpg/400px-Aniso_brdf.jpg)](http://www.klayge.org/wiki/index.php/File:Aniso_brdf.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Aniso_brdf.jpg)

Anisotropic BRDF

## KlayGE 4.0中的改进

在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0中，**延迟渲染**进入了渲染系统的核心，可以作为更通用更方便的一个渲染封装来使用。

在功能上，[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0中的**延迟渲染**也有了长足的进步。下文将着重于解析这些新改进。

### 流水线

先来看看**延迟渲染**的流水线。

[![img](http://www.klayge.org/wiki/images/4/41/Deferred_pipeline.png)](http://www.klayge.org/wiki/index.php/File:Deferred_pipeline.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Deferred_pipeline.png)

Pipeline

在流水线方面，第一个比较大的变化是，G-Buffer改成了MRT的，用类似Deferred Shading的fat G-Buffer来避免在shading pass再次渲染一遍物体。新G-Buffer的布局将在下文分解。在shading pass阶段，只需要渲染一个全屏quad，在每个pixel上把材质和光照信息结合就可以了。

其次，G-Buffer内已经没有Depth的通道，直接使用D24S8格式的texture来保存depth。这样就需要做一个depth线性化的步骤，把24-bit非线性的depth转到32-bit float的纹理上，方便后面使用。线性化的方法为：

![LaTeX: q=\frac{far}{far-near}](http://www.forkosh.com/mathtex.cgi?q%3D%5Cfrac%7Bfar%7D%7Bfar-near%7D)

![LaTeX: depth_{linear}=\frac{near \times q}{q-depth_{non-linear}}](http://www.forkosh.com/mathtex.cgi?depth_%7Blinear%7D%3D%5Cfrac%7Bnear%20%5Ctimes%20q%7D%7Bq-depth_%7Bnon-linear%7D%7D)

其中far为远平面，near为近平面。这样一来，就能省出一个通道，同时depth的精度也提高了。对于D3D9，也可以用扩展格式来实现D24S8纹理。

第三个改进是，规范化了stencil的使用。如果stencil的最高位为1，就表示那个pixel不会在lighting pass中计算光照。这样就可以挡掉一些不希望接受光照的特殊物体。

另外，在shading pass之后增加一个special shading pass。标记有special shading属性的物体会在这个阶段再画一次。special shading的本意是渲染带emit的物体，其实可以和stencil mask配合，在这里作任何想做的forward shading效果。透明物体的alpha也可以在special shading中给出，请看后文关于透明物体的渲染一段。

新的**延迟渲染**流水线从G-Buffer上看，像Deferred Shading，而之后的阶段则更像Deferred Lighting。可以算作是两者的结合。

### G-Buffer布局

前面提到了G-Buffer改成了MRT，那么现在就来比较一下新老G-Buffer的区别。老G-Buffer的安排如下：

[![img](http://www.klayge.org/wiki/images/thumb/c/c8/Old_g_buffer.png/400px-Old_g_buffer.png)](http://www.klayge.org/wiki/index.php/File:Old_g_buffer.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Old_g_buffer.png)

Old G-Buffer

老G-Buffer是4个通道、每个通道都是fp16的RGBA16F格式。其中normal用Spheremap Transform的方式映射到2个通道；depth单独存一个通道；specular和shininess挤在一个通道内，整数部分为specular * 100，小数部分为shininess / 256.0f。

这样的G-Buffer需要占据64-bit，IO开销不小，而且depth精度有限。如果按照新的MRT G-Buffer扩展到2个RT，就需要再增加一个32-bit的RT。对于不支持Independent MRT的D3D9硬件来说，甚至要增加一个64-bit的RT，会很影响性能。

最直接的改进就是把depth去掉，同时把specular和shininess分散到两个通道去，就像这样：

[![img](http://www.klayge.org/wiki/images/4/42/New_g_buffer_v1.png)](http://www.klayge.org/wiki/index.php/File:New_g_buffer_v1.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:New_g_buffer_v1.png)

New G-Buffer V1

这么一来，所有的分量都可以存在8-bit之内，2个RT仍用64-bit就能解决，并且空闲了一个通道！但是，由于normal的位数下降了非常多（从原来32-bit变成16-bit），效果也会受到很大影响。例如，原先（2个16-bit通道）的高光是这个样子的：

[![img](http://www.klayge.org/wiki/images/c/c4/Normal_32bit.png)](http://www.klayge.org/wiki/index.php/File:Normal_32bit.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_32bit.png)

Normal 32-bit

改用2个8-bit通道就出现了很明显而且丑陋的梯度：

[![img](http://www.klayge.org/wiki/images/d/d7/Normal_16bit.png)](http://www.klayge.org/wiki/index.php/File:Normal_16bit.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_16bit.png)

Normal 16-bit

所以说2个8-bit通道没有能力表现出光滑的normal过渡，得把剩余的一个通道用上才行。但需要注意的是，和传统Deferred Shading的G-Buffer不同在于，这种MRT G-Buffer的每个lighting pass只需要读取一次RT0，到了shading pass才读一次RT1。如果把lighting pass需要的信息放到了RT1，就会造成lighting pass的IO加倍，失去Deferred Lighting的有效加速。

因此，我只能作出一个艰难的决定：放弃基于物理的fresnel。原先把specular放在RT0的目的就是，在lighting pass可以用它来计算fresnel：

![LaTeX: F_{Schlick}(\mathbf{c}_{spec}, \mathbf{l}, \mathbf{h})=\mathbf{c}_{spec}+(1-\mathbf{c}_{spec})(1-(\mathbf{l} \cdot \mathbf{h})^5)](http://www.forkosh.com/mathtex.cgi?F_%7BSchlick%7D%28%5Cmathbf%7Bc%7D_%7Bspec%7D%2C%20%5Cmathbf%7Bl%7D%2C%20%5Cmathbf%7Bh%7D%29%3D%5Cmathbf%7Bc%7D_%7Bspec%7D%2B%281-%5Cmathbf%7Bc%7D_%7Bspec%7D%29%281-%28%5Cmathbf%7Bl%7D%20%5Ccdot%20%5Cmathbf%7Bh%7D%29%5E5%29)

基于物理的fresnel需要specular颜色（这里简化成只有亮度了）、light方向和halfway方向，必须在lighting pass计算。最常见的近似是用view和normal来代替light和halfway，这样就可以在shading pass才计算fresnel，而且对于所有角度的光源产生的fresnel系数都相同。实际上，这个近似只有在高光的那一个点的地方是相同的，越往边缘去会越暗。但因为fresnel本身比较弱，这个差异可以被直接忽略。因为通道实在不够，在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0中，我也不得不采用这个近似的、不基于物理的fresnel，得到新的G-Buffer布局如下：

[![img](http://www.klayge.org/wiki/images/4/4c/New_g_buffer_v2.png)](http://www.klayge.org/wiki/index.php/File:New_g_buffer_v2.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:New_g_buffer_v2.png)

New G-Buffer V2

specular被挪到了RT1的A通道，RT0的RGB通道就能都用来存放normal了。那么，在24-bit normal下渲染结果又如何呢？

[![img](http://www.klayge.org/wiki/images/b/b8/Normal_24bit.png)](http://www.klayge.org/wiki/index.php/File:Normal_24bit.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_24bit.png)

Normal 24-bit

可以看到，效果比只用16-bit好了许多，但离32-bit的情况还是很有差距的。至少一眼就能看出来梯度的现象。在SIGGRAPH 2010上，Crytek有个讲座叫CryENGINE 3: reaching the speed of light。里面提到了出现这个现象的根本原因在于：normal是被normalize过的！24-bit一共能表达256x256x256 = 16777216个不同的值，但如果仅限于normalizied的，就剩下了大概289880个，仅占了1.73 %。它有效的位数只有17-bit，所以梯度的格子仅比16-bit的时候密了一倍。Crytek的best fit for normals方法能表达16482364个值，也就是98.2 %，提升了几乎两个数量级。用best fit调整过的normal平滑的多了：

[![img](http://www.klayge.org/wiki/images/1/1e/Normal_24bit_bestfit.png)](http://www.klayge.org/wiki/index.php/File:Normal_24bit_bestfit.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Normal_24bit_bestfit.png)

Normal 24-bit with Best Fit

已经看不出和32-bit normal的区别了。关于best fit for normals的具体方法，可以参考Crytek的ppt。这里提供了一个我的程序预计算出来的纹理，用来查询最佳长度。

[normals_fitting.7z](http://www.klayge.org/wp/wp-content/uploads/2011/11/normals_fitting.7z)

和Crytek的方法不同的是，我省掉了它所说的y/x变换，所以从normal计算纹理坐标的时候也得去掉vTexCoord.y /= vTexCoord.x一行。

### 透明物体

游戏中透明物体是不可缺少的，对于**延迟渲染**来说，透明物体一直是痛苦的。常见的做法是在**延迟渲染**的场景之上用forward shading来单独渲染透明物体，但那样就意味着必须单独实现一整套forward shading的流水线。这对于维护和扩展都是很不利的，对性能也很有影响。

在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0里，我用的方法被称为Deep G-Buffer。其基本过程是，把前文篇所描述的**延迟渲染**流水线复制三份，不透明的物体、透明物体的背面、透明物体的正面分别有自己独立的G-Buffer、lighting pass、shading pass和special shading pass。最后会生成三张shading的结果，再把它们按照alpha混合起来就可以了。

首先建立的是不透明物体的G-Buffer，跟原先一样：

[![img](http://www.klayge.org/wiki/images/thumb/1/1a/Opaque_g_buffer.jpg/400px-Opaque_g_buffer.jpg)](http://www.klayge.org/wiki/index.php/File:Opaque_g_buffer.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Opaque_g_buffer.jpg)

Opaque objects's G-Buffer

细致的朋友可以发现，由于用了best fit for normals，G-Buffer里的normal看上去很有趣。

然后用把cull设置为front，只画透明物体的背面，存在第二个G-Buffer中。这里还需要用类似depth peeling的方法clip掉比不透明物体更远的pixel。因为不透明物体挡住了绝大部分pixel，透明物体的背面只剩下很少一部分：

[![img](http://www.klayge.org/wiki/images/thumb/c/c2/Transparent_back_g_buffer.jpg/400px-Transparent_back_g_buffer.jpg)](http://www.klayge.org/wiki/index.php/File:Transparent_back_g_buffer.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Transparent_back_g_buffer.jpg)

Transparent object back face's G-Buffer

同样，我们可以在第三个G-Buffer存透明物体的正面：

[![img](http://www.klayge.org/wiki/images/thumb/2/23/Transparent_front_g_buffer.jpg/400px-Transparent_front_g_buffer.jpg)](http://www.klayge.org/wiki/index.php/File:Transparent_front_g_buffer.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Transparent_front_g_buffer.jpg)

Transparent object front face's G-Buffer

经过lighting pass、shading pass和special shading pass，就得到了不透明物体的shading：

[![img](http://www.klayge.org/wiki/images/thumb/b/b3/Opaque_shading.jpg/400px-Opaque_shading.jpg)](http://www.klayge.org/wiki/index.php/File:Opaque_shading.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Opaque_shading.jpg)

Opaque object's shading

透明物体背面的shading，几乎没有被照亮的：

[![img](http://www.klayge.org/wiki/images/thumb/d/dd/Transparent_back_shading.jpg/400px-Transparent_back_shading.jpg)](http://www.klayge.org/wiki/index.php/File:Transparent_back_shading.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Transparent_back_shading.jpg)

Transparent object back face's shading

以及透明物体正面的shading：

[![img](http://www.klayge.org/wiki/images/thumb/0/08/Transparent_front_shading.jpg/400px-Transparent_front_shading.jpg)](http://www.klayge.org/wiki/index.php/File:Transparent_front_shading.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Transparent_front_shading.jpg)

Transparent object front face's shading

注意透明物体都会在special shading pass给出像素alpha值。接下来只要把它们混合起来，就可以得到我们想要的结果：

[![img](http://www.klayge.org/wiki/images/thumb/1/15/Blend_shading.jpg/400px-Blend_shading.jpg)](http://www.klayge.org/wiki/index.php/File:Blend_shading.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Blend_shading.jpg)

After blending

再来一张侧面图，可以看到由于光照方式一样，透明物体和不透明物体的光照能连续平滑地过渡。

[![img](http://www.klayge.org/wiki/images/thumb/6/60/Side_view.jpg/400px-Side_view.jpg)](http://www.klayge.org/wiki/index.php/File:Side_view.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Side_view.jpg)

Side view

这一节抛砖引玉地提出了在Deferred框架下渲染透明物体的一个方法，它能简单有效地解决问题。缺点是三倍的内存和带宽消耗。如果depth peeling的层数增加，内存和带宽的消耗还会增加。这里其实也可以借鉴其他order independent transparency的方法，来取代depth peeling分离G-Buffer。

### 实时全动态GI



### Post process

在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0的**延迟渲染**中，post process主要有HDR、AA和color grading。下面将分别讲述它们的改进。

#### HDR

在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 3.12用了[filmic tone mapping](http://www.klayge.org/wiki/index.php/色调映射)之后，HDR部分就几乎没有别的改变。这里唯一的变化是最终输出的float4，把亮度存在A通道上。这是为了后面FXAA的需要。

#### AA

在Deferred框架中，无法使用硬件AA曾经是个恼人的问题。随着这些年各种基于post process的AA方法大量出现，Deferred下AA的问题基本被解决了。

团队成员陈顺斌和郭鹏曾为KlayGE 3.12提供了[FXAA](http://www.klayge.org/wiki/index.php/FXAA)。在新版本中，FXAA也升级到了最新的3.11版。从FXAA 3开始，就要求输入纹理是LDR的RGBL格式（L为亮度），所以计算AA的地点也就从HDR之前改到了HDR之后。虽然FXAA 3.11可以用G通道代替L，但效果肯定会受影响。既然让HDR post process输出RGBL轻而易举，我就没有把L改成G。FXAA极快，目前的实现在GTX480上可以达到0.1ms的惊人速度。几乎做到了无性能损失的高质量AA。

#### Color grading

Color grading是这个版本新增的。以前游戏一般不太重视color grading的作用，但在电影业，color grading是流水线非常重要的一步（可以和skinning相提并论的）。这里我实现的color grading是用16x16x16的3D texture作为查找表，用原RGB作为地址去查询，查询出的结果即为调色后的颜色（来自[GPU Gems 2: Chapter 24. Using Lookup Tables to Accelerate Color Transformations](http://developer.nvidia.com/node/43)）。除了runtime的post process之外，还需要一个离线工具，用来生成那个3D texture。这里我用的方法类似CE3，先生成一个摊平的256×16的2D texture：

[![img](http://www.klayge.org/wiki/images/5/57/Color_grading_flatten.png)](http://www.klayge.org/wiki/index.php/File:Color_grading_flatten.png)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:Color_grading_flatten.png)

Color grading flatten

在photoshop里打开一张游戏截图，调整RGB曲线至需要的色调，然后把那个RGB曲线应用到之前生成的2D texture，最终打包成3D texture就得到了我们所需要的查找表。以后可能会根据需要做一个在线调整color grading的工具。

### 总结

这一章节把[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.0中**延迟渲染**的改进逐一介绍了一下，希望能对也在做类似事情的朋友有所帮助。在总结里我也身边展望一下未来，看看在[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.1中，**延迟渲染**部分还会可能出现什么改进。

- 更高的速度。Multiresolution的方法在GI中获得了成功，也许也可以扩展到direct lighting和SSVO中，用于加速整个**延迟渲染**。
- 改进HDR中的bloom filter。学习3DMark11，用FFT的方式在一个pass内完成bloom、lens flare等特效。
- 支持移动平台。精简的Deferred Rendering流水线将会以至到移动平台上。
- 更多例子用**延迟渲染**实现。目前只有3个例子用到了deferred框架，其他还是forward的。以后会有越来越多的例子转到deferred中。

## KlayGE 4.3中的改进

### GI和Deferred的分离

最早提到这个问题的是团队成员陈顺斌。他在去年就提出Deferred rendering layer太过复杂，应该把相对独立的GI拆出去。当时我的想法是，Deferred和[MRSIL GI](http://www.klayge.org/wiki/index.php/全局光照)在逻辑上关联甚大，应该是一体的。后来实现了SSGI，也放在Deferred框架内，复杂度进一步增加。Deferred也成了个带有多种GI方法的怪物，各个组件之间的耦合度很高。

在分析了MRSIL、SSGI以及未来可能支持的SVO等多种GI方法之后，我发现如果定义好一个接口，那么要将两者分离是有可能的。

这个接口包括两方面，第一是GI从Deferred拿到的数据，第二是GI计算的结果返回给Deferred。从目前的实现来看，GI的计算需要G-Buffer和RSM，计算的结果是一个半分辨率的indirect texture。从半分辨率indirect texture得到全分辨率的步骤在Deferred里面做。用这样的抽象接口就能顺利实现GI和Deferred的解耦。最终结果是，写了一个称为IndirectLightingLayer的抽象类，MSRIL和SSGI都从它派生出来。这么一来，Deferred只需要调用接口，提供所需数据，取出计算结果，而不需要考虑GI的具体实现。简单了很多。

[![img](http://www.klayge.org/wiki/images/thumb/6/6f/IndirectLightingLayer.jpg/400px-IndirectLightingLayer.jpg)](http://www.klayge.org/wiki/index.php/File:IndirectLightingLayer.jpg)

[![img](http://www.klayge.org/wiki/skins/common/images/magnify-clip.png)](http://www.klayge.org/wiki/index.php/File:IndirectLightingLayer.jpg)

Indirect Lighting Layer

需要特别说明的是，SSGI目前虽然不需要RSM，但不排除以后能用上。所以在接口中总是把RSM传过去。

### 未来

Multiresolution的框架也许也可以从GI的具体实现中分离出来，使得不同的GI方法，以及SSVO甚至direct lighting都可以使用的加速结构。这件事情要等到以后慢慢尝试了。

## 多视口的改进

多视口的特性是[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE) 4.2引入的。Deferred rendering layer支持通过多个视口生成多个渲染结果，可以用于分屏、反射、缩略图等情景。原先每个视口都是完全独立渲染的，互相不共享任何东西。实际上spot light和point light的shadow map是view independent的，不会因为视点不同而改变，就应该在视口间共享。

于是开发团队成员李渊完成了这个任务，把shadow map的生成提前到所有视口的G-Buffer之前。也就是说，原先的流水线是：

```
for each view port:
   generate g-buffer.

   for each shadowed light:
      generate shadow map or reflective shadow map.

      shadowing from shadow map.
      lighting.

   shading.
```

经过修改的流水线是：

```
for each shadowed light:
   generate shadow map or reflective shadow map.

for each view port:
   generate g-buffer.

   for each shadowed light:
      shadowing from shadow map.
      lighting.

   shading.
```

这么一来，通过在视口间共享shadow map，减少了重复生成shadow map的开销。需要注意的是，cascaded shadow map是view dependent的，需要在G-Buffer之后生成。

## 重构Update

在完成了上述修改后，多名团队成员以及论坛上的lcbiotech都提到了DeferredRenderingLayer::Update函数过长的问题，已经影响到了理解和维护，重构迫在眉睫。经过一番重构，那个函数被分解成了几十个小函数，每个负责做一件事情。Update函数本身则只是定义了流水线，实际执行都是通过调用那些小函数完成的。在对外的接口完全不变的情况下，流程变清晰很多。

## 透明物体和Deep G-Buffer

在[延迟渲染#透明物体](http://www.klayge.org/wiki/index.php/延迟渲染#.E9.80.8F.E6.98.8E.E7.89.A9.E4.BD.93)中，为了用纯Deferred的框架解决透明物体渲染的问题，[KlayGE](http://www.klayge.org/wiki/index.php/KlayGE)引入了Deep G-Buffer的方法。对不透明物体、透明物体的背面、透明物体的正面分为三个G-Buffer layer，分别有一条Deferred流水线，最终通过alpha把三层blend成最终结果。这种方法虽然能简单有效地解决问题，并避免繁琐的forward流水线，但需要三倍的存储和带宽。而且如果depth peeling的层数增加，开销还会进一步加大。最近出现的几种OIT方法，都不兼容于deferred。所以如果不用forward，就得想办法解决这个问题，至少减轻一点算一点。

Deferred的流水线如果考虑了Deep G-Buffer，看起来是这样的：

```
for each shadowed light:
   generate shadow map or reflective shadow map.

for each view port:
   for each G-Buffer layer:
      generate g-buffer.

   for each shadowed light:
      for each G-Buffer layer:
         shadowing from shadow map.
         lighting.

   for each G-Buffer layer:
      shading.

  for each G-Buffer layer:
      merge shading result.
```

在重构Update之前，一团乱麻的代码根本看不出这个结构。重构之后可以清晰地看到，这个流水线应该进一步整理为：

```
for each shadowed light:
   generate shadow map or reflective shadow map.

for each view port:
   for each G-Buffer layer:
      generate g-buffer. 

      for each shadowed light:
         shadowing from shadow map.
         lighting.

      shading.
      merge shading result.
```

也就是说，不同的G-Buffer layer之间可以共享G-Buffer、lighting texture、shading texture等。由于不同的G-Buffer layer已经用stencil把需要计算的pixel标记出来了，这么共享texture不会造成错误的pixel值。只要把最终shading结果alpha blend起来，结果会和使用Deep G-Buffer完全相同。

比较一下这么改进前后的存储开销：

|                             |          改进前           |    改进后     | 不支持透明物体时 |
| :-------------------------: | :-----------------------: | :-----------: | :--------------: |
|          G-Buffer           |         6张RGBA8          |   2张RGBA8    |     2张RGBA8     |
|    Depth stencil buffer     |         3张D24S8          |   1张D24S8    |     1张D24S8     |
|     Linear depth buffer     |          3张D32F          |    1张D32F    |     1张D32F      |
|      Shadowing texture      |         1张RGBA8          |   1张RGBA8    |     1张RGBA8     |
| Lighting accumulate texture |       3张R11G11B10F       | 1张R11G11B10F |  1张R11G11B10F   |
|       Shading texture       | 1张R11G11B10F，2张RGBA16F |  1张RGBA16F   |  1张R11G11B10F   |

很显然改进后所需的存储开销急剧减少，和不支持透明物体的时候，只是shading texture从R11G11B10F变成RGBA16F，其他都没区别了。如果进一步修改special shading，改成手工把shading和emit相加，就能仍然保留R11G11B10F的格式。有时间的话我会试着这么改。由此，我们得到了一个可以在完全不增加显存占用的情况下支持透明物体渲染的方案。而且，就算要用depth peeling增加更多透明层，这个框架仍然不需要增加存储消耗，是完全memory bounded的。

[Category](http://www.klayge.org/wiki/index.php/Special:Categories): 

- [渲染](http://www.klayge.org/wiki/index.php/Category:渲染)