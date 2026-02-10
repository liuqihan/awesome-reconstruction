# awesome-reconstruction
This repo is build for scenario/scene reconstruction used in autonomous driving, and mainly focus on 3DGS/4DGS 

## 1. Feed-Forward Gaussian:
### 1.1. Omni-Scene: Omni-Gaussian Representation for Ego-Centric Sparse-View Scene Reconstruction
   - papper: https://wswdx.github.io/omniscene/assets/paper.pdf
   - repo:  https://github.com/WU-CVGL/Omni-Scene repo:
   - intro: 用6张环视照片（比如手机原地转一圈拍的图），0.1秒重建整个街道的3D模型。官方Demo里直接重建了整条马路+楼房，连遮挡的车屁股都能补全（终于不用围着车拍200张了）。代码/预训练模型全公开，还给了nuScenes数据集预处理脚本.

### 1.2. EVolSplat4D: Efficient Volume-based Gaussian Splatting for 4D Urban Scene Synthesis
   - project page: https://xdimlab.github.io/EVolSplat4D/
   - papper: https://arxiv.org/pdf/2601.15951
   - repo: https://github.com/Miaosheng1/EVolSplat4D

### 1.3 FastVGGT: Training-Free Acceleration of Visual Geometry Transformer
   - project page: https://mystorm16.github.io/fastvggt/
   - papper: https://arxiv.org/abs/2509.02560
   - repo: https://github.com/mystorm16/FastVGGT

## 2. 3D-Segmentation
### 1.1 Online Segment Any 3D Thing as Instance Tracking
   - papper: https://arxiv.org/abs/2512.07599
   - repo: https://github.com/AutoLab-SAI-SJTU/AutoSeg3D

## 3. 4D-Segmentation
### 1.1 4DLangVGGT: 4D Language Visual Geometry Grounded Transformer
   - papper：https://arxiv.org/abs/2512.05060
   - repo：https://github.com/hustvl/4DLangVGGT
   - into： 可以查找3D序列中的目标物，能直接使用，对自然语言搜索支持度好。

## 4. 数字人
### 1.1 AvatarBrush: Monocular Reconstruction of Gaussian Avatars with Intuitive Local Editing
   - papper：https://arxiv.org/pdf/2511.19189
   - repo： https://github.com/AutoLab-SAI-SJTU/AutoSeg3D

## 5. 重建过程中的相机位姿鲁棒性
### 1.1 PROFusion: Robust and Accurate Dense Reconstruction via Camera Pose Regression and Optimization
   - papper:https://arxiv.org/abs/2509.24236
   - repo: https://github.com/siyandong/PROFusion

### 1.2  Explicit Motion Modeling for High-Quality Street Gaussian Splatting
   - papper: https://arxiv.org/abs/2411.15582
   - repo: https://github.com/qingpowuwu/emd
   - intro: 一个适配场景重建时车速不同的即插即用模块

#### 1.3 CityGaussianV2: Efficient and Geometrically Accurate Reconstruction for Large-Scale Scenes
   - papper：https://arxiv.org/abs/2411.00771
   - repo：https://github.com/Linketic/CityGaussian
   - intro：解决2DGS的显存爆炸问题。
## 6. 3dgs-激光雷达点云
### 1.1. FGGS-LiDAR: Ultra-Fast, GPU-Accelerated Simulation from General 3DGS Models to LiDAR
   - papper：https://arxiv.org/pdf/2509.17390
   - repo：https://github.com/TATP-233/FGGS-LiDAR



## 如何“有效复现”
### 1. 构建自有数据集：破解“数据依赖”困局
开源论文常依赖特定数据集（如nuScenes、COCO），但受限数据会导致复现结果泛化性差。自主采集数据可突破这一限制

#### 1.1. 小规模DIY采集：
使用性价比高的3D扫描仪、手机+LiDAR扫描App（如Polycam）采集物体点云，适配3D重建论文（如Omni-Scene）；运动相机多机位同步拍摄动态场景（如人/车运动），解决动态重建数据缺失问题（如SLAM3R需长序列视频）。用SAM+人工修正生成掩码，替代专业标注工具。
#### 1.2. 合成数据生成：
使用Blender生成带精确深度图的3D物体（适配SPAR3D单图重建）；用UE5引擎构建虚拟街道场景，替代自动驾驶数据集（如CityGaussianV2的1.97km²重建需求。

### 2. 建立多维度Benchmark：超越论文单一指标
#### 2.1. 扩展公开数据集
#### 2.2. 设计压力测试集：
极端条件下低光照/运动模糊数据测试SLAM稳定性（如Hier-SLAM的语义建图）；用艺术画作测试单图3D重建（如Craftsman3D），验证开放场景适应性

### 3. 复现中的关键技术策略
#### 3.1. 模块替换实验：
将BG-Triangle的贝塞尔三角形渲染器替换为传统光栅化，分析边界模糊改善机制；在CityGaussianV2中插入Depth-Anything-V2模块，验证深度估计对重建精度影响。
#### 3.2. 失败归因文档化：
记录复现中出现的显存溢出、数据格式错误等，并提交Pull Request修复（如补充缺失的data_loader.py）
### 4. 知识沉淀：构建可复用的研究资产
#### 4.1. 数据管道标准化：
将自采数据集转换为通用格式（如COCO式标注），发布至Hugging Face Datasets供社区验证；
#### 4.2. 开发最小复现包（MRE）：
剥离论文非核心模块，发布仅含模型+推理脚本的轻量化仓库（如Craftsman3D的法线优化器独立模块）
