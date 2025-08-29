# MDSF-Det: Modal Specificity Decoupling and Synergistic Dynamic Fusion for Infrared-Visible Object Detection

> **🚧 代码即将发布 | Code Coming Soon 🚧**
> 
> 该代码库将在论文被接收后发布完整实现代码。
> 
> This repository will be updated with the complete implementation upon paper acceptance.

## 📝 Abstract

Red外-可见光目标检测(IVOD)旨在融合可见光图像的结构纹理与红外图像的热辐射线索。然而，现有方法采用共享主干网络和静态拼接，无法解决因不同模态成像物理原理而产生的表示纠缠问题，并且难以在动态场景中合理分配融合权重。为解决这一问题，我们提出了端到端检测器MDSF-Det...

## 🎯 Key Features

- ✨ Modal Specificity Decoupling Backbone (MSDB)
- 🔥 Modality-aware Synergistic Dynamic Fusion (MSDF)
- 📊 State-of-the-art performance on M3FD and LLVIP datasets
- 🚀 End-to-end training pipeline

## 📊 Performance

| Dataset | mAP@50 | mAP@75 | FPS |
|---------|--------|--------|-----|
| M3FD    | **70%** | TBD    | TBD |
| LLVIP   | **80%** | TBD    | TBD |

## 🛠️ Installation

```bash
# Coming soon...
git clone https://github.com/zzyadad/MDSF-Det-2024.git
cd MDSF-Det-2024
pip install -r requirements.txt
```

## 🚀 Quick Start

```python
# Coming soon...
from mdsf_det import MDSFDetector

# Initialize model
model = MDSFDetector(config='configs/mdsf_det.yaml')
model.load_pretrained('checkpoints/mdsf_det.pth')

# Inference
results = model.detect(rgb_image, ir_image)
```

## 📁 Project Structure

```
MDSF-Det-2024/
├── configs/           # Configuration files
├── datasets/          # Dataset handling
├── models/            # Model implementations
│   ├── backbone/      # MSDB implementation
│   ├── fusion/        # MSDF implementation
│   └── detector/      # Full detector
├── tools/             # Training and testing scripts
├── checkpoints/       # Pre-trained models
└── docs/              # Documentation
```

## 📚 Citation

```bibtex
@article{mdsf_det_2024,
  title={MDSF-Det: Modal Specificity Decoupling and Synergistic Dynamic Fusion for Infrared-Visible Object Detection},
  author={Your Name and Co-authors},
  journal={Target Journal/Conference},
  year={2024}
}
```

## 📧 Contact

如有问题，请联系：[your.email@domain.com](mailto:your.email@domain.com)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ **如果这个项目对您有帮助，请给个星标！**
