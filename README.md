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

## 6. 3dgs-激光雷达点云
### 1.1. FGGS-LiDAR: Ultra-Fast, GPU-Accelerated Simulation from General 3DGS Models to LiDAR
   - papper：https://arxiv.org/pdf/2509.17390
   - repo：https://github.com/TATP-233/FGGS-LiDAR
