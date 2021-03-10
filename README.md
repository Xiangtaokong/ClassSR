# ClassSR
(CVPR2021) ClassSR: A General Framework to Accelerate Super-Resolution Networks by Data Characteristic

Authors: Xiangtao Kong, [Hengyuan Zhao](https://github.com/zhaohengyuan1), [Yu Qiao](https://scholar.google.com/citations?user=gFtI-8QAAAAJ&hl=zh-CN), [Chao Dong](https://scholar.google.com.hk/citations?user=OSDCB0UAAAAJ&hl=zh-CN)
[Paper](https://arxiv.org/abs/2103.04039)


## Dependencies

- Python >= 3.6 (Recommend to use [Anaconda](https://www.anaconda.com/download/#linux))
- [PyTorch >= 1.5.0](https://pytorch.org/)
- NVIDIA GPU + [CUDA](https://developer.nvidia.com/cuda-downloads)
- Python packages: `pip install numpy opencv-python lmdb`
- [option] Python packages: [`pip install tensorboardX`](https://github.com/lanpa/tensorboardX), for visualizing curves.

# Codes 
- Our codes version based on [BasicSR](https://github.com/xinntao/BasicSR). 

## How to test a single branch
1. Clone this github repo. 
```
git clone https://github.com/Xiangtaokong/ClassSR.git
cd ClassSR
```
2. Download the testing datasets ([DIV2K_valid](https://data.vision.ee.ethz.ch/cvl/DIV2K/)). 

3. Download the [divide_val.log]() and move it to `.codes/data_scripts/`.

4. Generate simple, medium, hard (class1, class2, class3) validation data. 
```
cd codes/data_scripts
python extract_subimages_branch.py
python divide_sub_images_branch.py
```
5. Download [pretrained models](https://drive.google.com/drive/folders/1jzAFazbaGxHb-xL4vmxc-hHbR1J-uek_) and move them to  `./experiments/pretrained_models/` folder. 

6. Run testing for a single branch.
```
cd codes
python test.py -opt options/test/test_FSRCNN.yml
python test.py -opt options/test/test_CARN.yml
python test.py -opt options/test/test_SRResNet.yml
python test.py -opt options/test/test_RCAN.yml
```

7. The output results will be sorted in `./results`. 

## How to test ClassSR
1. Clone this github repo. 
```
git clone https://github.com/Xiangtaokong/ClassSR.git
cd ClassSR
```
2. Download the testing datasets ([DIV8K](https://competitions.codalab.org/competitions/22217#participate)). Test8K contains the images (index 1401-1500) from DIV8K. Test2K/4K contain the images (index 1201-1300/1301-1400) from DIV8K which are downsampled to 2K and 4K resolution. 

3. Download [pretrained models](https://drive.google.com/drive/folders/1jzAFazbaGxHb-xL4vmxc-hHbR1J-uek_) and move them to  `./experiments/pretrained_models/` folder. 

4. Run testing for ClassSR.
```
cd codes
python test_ClassSR.py -opt options/test/test_ClassSR_FSRCNN.yml
python test_ClassSR.py -opt options/test/test_ClassSR_CARN.yml
python test_ClassSR.py -opt options/test/test_ClassSR_SRResNet.yml
python test_ClassSR.py -opt options/test/test_ClassSR_RCAN.yml
```
5. The output results will be sorted in `./results`. 


## How to train a single branch
1. Clone this github repo. 
```
git clone https://github.com/Xiangtaokong/ClassSR.git
cd ClassSR
```
2. Download the training datasets([DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/)) and validation dataset([Set5]()).

3. Run training for a single branch (default branch1, the simplest branch).
```
cd codes
python train.py -opt options/train/train_FSRCNN.yml
python train.py -opt options/train/train_CARN.yml
python train.py -opt options/train/train_SRResNet.yml
python train.py -opt options/train/train_RCAN.yml
```

## How to train ClassSR

1. Clone this github repo. 
```
git clone https://github.com/Xiangtaokong/ClassSR.git
cd ClassSR
```
2. Download the training datasets ([DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/)) and validation dataset([DIV2K_valid](https://data.vision.ee.ethz.ch/cvl/DIV2K/), index 801-810). 


3. Generate training data (all data).
```
cd codes/data_scripts
python data_augmentation.py
python extract_subimages_ClassSR.py

```
4. Download [pretrained models](https://drive.google.com/drive/folders/1jzAFazbaGxHb-xL4vmxc-hHbR1J-uek_)(pretrained branches) and move them to  `./experiments/pretrained_models/` folder. 

5. Run training for ClassSR.
```
cd codes
python train_ClassSR.py -opt options/train/train_ClassSR_FSRCNN.yml
python train_ClassSR.py -opt options/train/train_ClassSR_CARN.yml
python train_ClassSR.py -opt options/train/train_ClassSR_SRResNet.yml
python train_ClassSR.py -opt options/train/train_ClassSR_RCAN.yml
```

## Contact
Email: xt.kong@siat.ac.cn