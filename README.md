# MDSF-Det: Modal Specificity Decoupling and Synergistic Dynamic Fusion for Infrared-Visible Object Detection
## 🎯 Key Features

- ✨ Modal Specificity Decoupling Backbone (MSDB)
- 🔥 Modality-aware Synergistic Dynamic Fusion (MSDF)
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
   
   # Install ultralytics
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

## 🔍 Validation

### Model Validation

1. **Validate trained model**
   ```bash
   conda activate c
   cd MDSF-Det
   python val_MDSF-Det.py --weights runs/train/exp/weights/best.pt --data data/config.yaml
   ```

2. **Validation with custom parameters**
   ```bash
   python val_MDSF-Det.py \
       --weights path/to/model.pt \
       --data data/config.yaml \
       --batch-size 32 \
       --imgsz 640 \
       --device 0
   ```

3. **Multi-GPU validation**
   ```bash
   python -m torch.distributed.launch --nproc_per_node=8 val_MDSF-Det.py \
       --weights runs/train/exp/weights/best.pt \
       --data data/config.yaml
   ```

## 🧪 Testing & Inference

### Model Testing

1. **Test on specific dataset**
   ```bash
   conda activate c
   cd MDSF-Det
   python test_MDSF-Det.py --weights runs/train/exp/weights/best.pt --source data/test/images
   ```

2. **Test with custom parameters**
   ```bash
   python test_MDSF-Det.py \
       --weights path/to/model.pt \
       --source data/test/images \
       --conf-thres 0.25 \
       --iou-thres 0.45 \
       --device 0 \
       --save-txt \
       --save-conf
   ```

3. **Batch testing**
   ```bash
   python test_MDSF-Det.py \
       --weights runs/train/exp/weights/best.pt \
       --source data/test \
       --batch-size 16 \
       --imgsz 640
   ```

### Inference Examples

```bash
# Test on single image
python test_MDSF-Det.py --weights best.pt --source image.jpg

# Test on video
python test_MDSF-Det.py --weights best.pt --source video.mp4

# Test on webcam
python test_MDSF-Det.py --weights best.pt --source 0

# Test on image folder
python test_MDSF-Det.py --weights best.pt --source path/to/images/
```

## 📁 Project Structure

```
MDSF-Det/
├── train_MDSF-Det.py          # Main training script
├── val_MDSF-Det.py            # Validation script
├── test_MDSF-Det.py           # Testing/Inference script
├── requirements.txt           # Python dependencies
├── data/                      # Dataset configurations
│   ├── config.yaml           # Dataset config file
│   ├── train/                # Training data
│   ├── val/                  # Validation data
│   └── test/                 # Test data
├── models/                    # Model architectures
├── utils/                     # Utility functions
├── weights/                   # Pre-trained weights
└── runs/                      # Training/validation/test results
    ├── train/                # Training outputs
    ├── val/                  # Validation outputs
    └── detect/               # Detection/test outputs
```

## 🔧 Troubleshooting

### Common Issues

1. **CUDA out of memory**
   ```bash
   # Reduce batch size
   python train_MDSF-Det.py --batch-size 16
   python val_MDSF-Det.py --batch-size 16
   ```

2. **Port already in use**
   ```bash
   # Use different port
   python -m torch.distributed.launch --master_port=29501 --nproc_per_node=8 train_MDSF-Det.py
   ```

3. **Model not found**
   ```bash
   # Check model path
   ls runs/train/exp/weights/
   python val_MDSF-Det.py --weights runs/train/exp/weights/last.pt
   ```

## 🎯 Quick Start

### Complete Workflow

```bash
# Setup
git clone https://github.com/241316435/MDSF-Det.git
cd MDSF-Det
conda create -n c python=3.8
conda activate c
pip install torch torchvision numpy matplotlib polars pyyaml pillow psutil requests scipy seaborn ultralytics

# Training
python -m torch.distributed.launch --nproc_per_node=8 train_MDSF-Det.py

# Validation
python val_MDSF-Det.py --weights runs/train/exp/weights/best.pt --data data/config.yaml

# Testing
python test_MDSF-Det.py --weights runs/train/exp/weights/best.pt --source data/test/images
```

## 📊 Performance

| Dataset | mAP@0.5 | mAP@0.5:0.95 | Parameters | FLOPs |
|---------|---------|--------------|------------|--------|
| M3FD    | -       | -            | -          | -      |
| LLVIP   | -       | -            | -          | -      |

*Performance metrics will be updated upon code release.*

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
