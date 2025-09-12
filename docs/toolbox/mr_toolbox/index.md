# 我的 MR 收藏夹

> 这里是我个人用来收藏和分享优秀 MRI 教程和源码的地方。
> 特别感谢所有贡献者！🥳

## 📚 教程

### 1. \[Stanford] RAD 229：超棒的 MRI 信号与序列设计课程

> 斯坦福大学的课程（授课老师：Dr. Daniel Ennis & Dr. Brian Hargreaves）。内容涵盖从 MRI 信号形成的基础，到高级序列设计。提供公开的视频、课件和代码，非常适合系统学习。

* 链接：\[[主页](https://web.stanford.edu/class/rad229/index.html)] \[[YouTube 视频](https://www.youtube.com/channel/UCJgAoFeFMKQ-f1XVPrFBslQ)] \[[课件](https://web.stanford.edu/class/rad229/Notes.html)] \[[GitHub 仓库](https://github.com/mribri999/MRSignalsSeqs)] \[[我的更新版本](https://github.com/ZihanNing/MRSignalsSeqs/tree/ZN_testing)]
* 精彩之处：MR 信号仿真（Bloch/EPG）+ 常用序列的特性讲解非常到位。

### 2. 互动电子书：MRI 原理

> 一本带有交互演示和源码的电子书，用来解释 MRI 物理原理。非常适合喜欢阅读而不是看视频的同学。

* 链接：\[[主页](https://larsonlab.github.io/MRI-education-resources/Introduction.html)] \[[README 的一些建议](https://github.com/larsonlab/MRI-education-resources)]

### 3. MRI 问与答

> 可能是 MRI 领域最出名的 Q\&A 网站了，几乎是 MRI 知识的“字典”。

* 链接：\[[主页](https://www.mriquestions.com/index.html)]

### 4. \[UCSF] BI 201：MRI 原理

> UCSF 的 BI 201 课程（授课老师：Dr. Peder Larson）。内容完整，适合入门，还带了一些基础重建教程。

* 链接：\[[YouTube 播放列表](https://www.youtube.com/playlist?list=PLjBt5Iq93BT9eXMsgevVTXKVv4BgVLB1X)] \[[Larson Lab GitHub](https://github.com/LarsonLab)]

### 5. 视频系列：*Introducing MRI*

> 来自 Albert Einstein College of Medicine 的短视频系列，每个视频聚焦一个问题，简明易懂。

* 链接：\[[YouTube 播放列表](https://www.youtube.com/playlist?list=PLPcImQzEnTpz-5TzxyyoYSbiAa9xdd89l)]

### 6. 两本 NMR & MRI 经典电子书

> Dr. Joseph P. Hornak 的经典著作，学习 NMR 和 MRI 基础必读。

* 链接：\[[NMR 基础](https://www.cis.rit.edu/htbooks/nmr/)] \[[MRI 基础](https://www.cis.rit.edu/htbooks/mri/)]

---

## 🛠️ 我最常用的工具箱 / 软件

### 1. ITK-SNAP

> 免费开源的医学图像分割软件，支持 3D 和 4D 图像。**我几乎每天都用它快速查看 NIfTI 图像。**

* 链接：\[[主页](https://www.itksnap.org/pmwiki/pmwiki.php)]

### 2. elastix

> 开源的刚性和非刚性图像配准工具箱。**我在脑和肾脏的图像配准任务里经常用到它。**

* 链接：\[[主页](https://elastix.dev)] \[[用户手册](https://elastix.dev/download.php)] \[[模型库](https://lkeb.ml/modelzoo/)]

### 3. SPM12

> 用于建模和检验功能成像数据统计假设的工具箱。
> **我常用它做脑分割、配准，以及作为 NIfTI 文件读写的后端，很多我自写的工具都依赖它，对 MATLAB 用户来说几乎是必装工具。**

* 链接：\[[主页](https://www.fil.ion.ucl.ac.uk/spm/)]

### 4. 3D Slicer

> 免费开源的医学图像处理和可视化平台，支持配准、分割、统计分析等。**非常适合需要手动操作的流程，而且社区一直在贡献新的模块。**

* 链接：\[[主页](https://www.slicer.org)]

---

## 💻 开源代码 / 软件

### 1. Stanford SLR RF 脉冲设计代码

> John Pauly 编写的 MATLAB 例程，用于基于 Shinnar-Le Roux 算法设计 RF 脉冲。

* 链接：\[[主页](https://rsl.stanford.edu/research/software.html)] \[[使用手册](https://rsl.stanford.edu/download/pauly/rftools-manual.pdf)]

---

## 🌐 收藏集

### 1. Dr. Mark Chiew 的主页

> 一个非常好的科研主页示例，包含开源代码、教学幻灯片和重建工具。

* 链接：\[[主页](https://mchiew.github.io/index.html)] \[[按论文分类的代码](https://mchiew.github.io/Research.html)] \[[教学幻灯片](https://mchiew.github.io/Teaching.html)] \[[MR 重建 MATLAB 代码](https://mchiew.github.io/Tools.html)]
* 推荐仓库：

  * **[recon-tools-matlab](https://github.com/mchiew/recon-tools-matlab)** — 包含 ADMM、CG、字典学习、去噪等常用重建工具（MATLAB）。

### 2. MR-Hub：ISMRM 开源工具合集

> 由 **ISMRM Reproducibility Research Study Group** 维护，收录经过社区验证的 MR 工具。

* 链接：\[[主页](https://ismrm.github.io/mrhub/)]
* 我常用的工具：

  * **[MRtrix3](https://www.mrtrix.org)** — 高级 DWI 分析工具，我用它做 Gibbs 去环伪影。
  * **[BART](http://mrirecon.github.io/bart/)** — 重建工具箱，用它做 ESPIRiT coil sensitivity 估计。
  * **[Gadgetron](http://gadgetron.github.io)** + **[ISMRMRD](https://ismrmrd.github.io/apidocs/1.5.0/)** — 在线重建平台和数据格式，我的很多重建都基于它们实现。\[[我的 Practical Inline Recon Framework](https://github.com/ZihanNing/Practical_Inline_Recon_Framework-public.git)]
  * **[KomaMRI](https://github.com/JuliaHealth/KomaMRI.jl)** — 灵活的信号仿真与 k 空间轨迹绘制工具。
  * **[gpuNUFFT](https://github.com/andyschwarzl/gpuNUFFT)** — GPU 加速的 NUFFT 算法，可直接在 MATLAB 调用，我用它做钠成像的径向重建。

### 3. NYU 开源数据和代码合集

> 由 NYU CAI2R 提供的 MRI 数据集、重建代码、RF 仿真工具和图像分析软件。

* 链接：\[[主页](https://cai2r.net/resources/#reconstruction-code)]
* 精选内容：

  * **[fastMRI](https://cai2r.net/resources/fastmri-dataset/)** — 大规模原始 k 空间数据集，适合机器学习研究。
  * **[AGILE](https://cai2r.net/resources/agile-gpu-image-reconstruction-library/)** — GPU 加速的线性 / 非线性重建环境。
  * **[MPPCA](https://cai2r.net/resources/denoising-using-marchenko-pastur-principal-component-analysis/)** — 扩散成像去噪方法。
  * **[gpuNUFFT](https://cai2r.net/resources/gpunufft-an-open-source-gpu-library-for-3d-gridding-with-direct-matlab-interface/)** — 快速非笛卡尔 NUFFT。
  * **[GRASP / RACER-GRASP / XD-GRASP](https://cai2r.net/resources/)** — 常用的呼吸运动校正解决方案。
  * **[k-t sparse sense](https://cai2r.net/resources/k-t-sparse-sense-matlab-code/)** — 适用于动态成像的重建方法。
  * **[L+S Recon](https://cai2r.net/resources/ls-reconstruction-matlab-code/)** — 低秩+稀疏动态重建（MATLAB）。

### 4. Michigan Image Reconstruction Toolbox (MIRT)

> Jeff Fessler 开发的 MATLAB 图像重建和 RF 脉冲设计工具合集。

* 链接：\[[主页](https://web.eecs.umich.edu/~fessler/code/index.html)] \[[下载](http://web.eecs.umich.edu/~fessler/irt/fessler.tgz)] \[[GitHub](https://github.com/JeffFessler/mirt)]
* 精选内容：

  * **[Image Reconstruction Toolbox](https://web.eecs.umich.edu/~fessler/code/mri.htm)** — 支持 GPU 的 NUFFT、SENSE（笛卡尔和非笛卡尔）、场图估计、压缩感知重建。
  * **RF Pulse Design** — 频谱-空间脉冲设计和相位预补偿切片选择。

### 5. ISMRM 资源链接

> 几乎囊括了所有 MR 相关的社区、期刊、网站、教程和软件。

* 链接：\[[主页](https://www.ismrm.org/resources/mr-sites/)]
