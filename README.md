# MDSF-Det: Modal Specificity Decoupling and Synergistic Dynamic Fusion for Infrared-Visible Object Detection

> **🚧 代码即将发布 | Code Coming Soon 🚧**
> 
> 该代码库将在论文被接收后发布完整实现代码。
> 
> This repository will be updated with the complete implementation upon paper acceptance.

## 🎯 Key Features

- ✨ Modal Specificity Decoupling Backbone (MSDB)
- 🔥 Modality-aware Synergistic Dynamic Fusion (MSDF)
- 📊 State-of-the-art performance on M3FD and LLVIP datasets
- 🚀 End-to-end training pipeline

## 🛠️ Environment Setup

### Prerequisites
- Python 3.8+
- CUDA 11.0+
- 8 GPUs for distributed training (recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/241316435/MDSF-Det.git
   cd MDSF-Det
   ```

2. **Create and activate conda environment**
   ```bash
   conda create -n c python=3.8
   conda activate c
   ```

3. **Install dependencies**
   ```bash
   # Install core dependencies first
   pip install torch torchvision numpy matplotlib polars pyyaml pillow psutil requests scipy seaborn 
   
   # Install ultralytics without dependencies
   pip install ultralytics 
   
   # Or use requirements.txt
   pip install -r requirements.txt
   ```

4. **Verify installation**
   ```bash
   python -c "import torch; print(torch.__version__); print(torch.cuda.is_available())"
   ```

## 🚀 Training

### Distributed Training (8 GPUs)

1. **Activate environment and navigate to project**
   ```bash
   conda activate c
   cd MDSF-Det
   ```

2. **Run distributed training**
   ```bash
   # Single command for 8-GPU training
   python -m torch.distributed.launch --nproc_per_node=8 train_MDSF-Det.py
   
   # Alternative using torchrun (PyTorch 1.9+)
   torchrun --nproc_per_node=8 train_MDSF-Det.py
   ```

### Training Configuration

```bash
# Example training command with custom parameters
python -m torch.distributed.launch \
    --nproc_per_node=8 \
    --master_port=29500 \
    train_MDSF-Det.py \
    --batch-size 32 \
    --epochs 300 \
    --data data/config.yaml \
    --weights weights/yolov8n.pt
```

### Single GPU Training
```bash
python train_MDSF-Det.py --device 0
```

## 📁 Project Structure

```
MDSF-Det/
├── train_MDSF-Det.py          # Main training script
├── requirements.txt           # Python dependencies
├── data/                      # Dataset configurations
├── models/                    # Model architectures
├── utils/                     # Utility functions
├── weights/                   # Pre-trained weights
└── runs/                      # Training results
```






## 📧 Contact

如有问题，请联系：[10431240210@stu.qlu.edu.cn](mailto:10431240210@stu.qlu.edu.cn)

⭐ **如果这个项目对您有帮助，请给个星标！**

## 📝 Citation

```bibtex
@article{mdsf-det2024,
  title={MDSF-Det: Modal Specificity Decoupling and Synergistic Dynamic Fusion for Infrared-Visible Object Detection},
  author={Your Name},
  journal={Conference/Journal Name},
  year={2024}
}
```
