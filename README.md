# TV-DCP: Total Variation Regularized Dark Channel Prior for Image Dehazing

## 简介

基于全变分与暗通道联合优化的图像去雾算法，通过TV正则化改进传统暗通道先验方法，有效消除块效应并保持边缘细节。
<img width="1028" height="569" alt="image" src="https://github.com/user-attachments/assets/576d065a-11f2-4c14-a344-6781b280de77" />


## 环境依赖

```bash
pip install torch torchvision numpy opencv-python matplotlib scikit-image pandas tqdm
```

## 数据集

支持 [O-HAZE](https://data.vision.ee.ethz.ch/cvl/ntire17//) 数据集:https://data.vision.ee.ethz.ch/cvl/ntire17/
目录结构：

```
./data/O-HAZE/
├── hazy/       # 有雾图像
└── GT/         # 真实参考图像
```

若无数据集，程序自动生成合成测试图像。

![Uploading image.png…]()


## 实验内容

| 实验 | 说明 |
|------|------|
| 消融实验 | TV正则化、引导滤波各模块贡献分析 |
| 参数敏感性 | λ_tv 对 PSNR/SSIM 的影响 |
| 可视化对比 | 局部放大、透射率图、强度曲线 |

## 参数说明

| 参数 | 默认值 | 说明 |
|------|--------|------|
| `patch_size` | 15 | 暗通道窗口大小 |
| `omega` | 0.95 | 去雾强度 |
| `lambda_tv` | 0.01 | TV正则化权重 |
| `t0` | 0.1 | 透射率下限 |

## 输出结果

- `./tvdcp_visual_comparison/` - 可视化对比图
- `./tvdcp_results/ablation/` - 消融实验结果
- `sensitivity_lambda_tv.png` - 参数敏感性曲线
