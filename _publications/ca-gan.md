---
title: "Towards Realistic Face Photo-Sketch Synthesis via Composition-Aided GANs (CA-GAN)"
collection: publications
permalink: /publication/ca-gan
excerpt: 'Jun Yu, Xingxin Xu, **Fei Gao**\*, Shengjie Shi, et al. "**Towards Realistic Face Photo-Sketch Synthesis via Composition-Aided GANs**," _IEEE Transactions on Cybernatics_, vol. 51, no. 9, pp. 4350 - 4362, 2021. (Corresponding Author)'
date: 2020-03-05
venue: "March 5"
paperurl: "https://ieeexplore.ieee.org/document/9025751"
citation: ""
---

[[Paper@IEEE]](https://ieeexplore.ieee.org/document/9025751) [[Project@Github]](https://github.com/fei-hdu/ca-gan/) [[Paper@arxiv\]](https://arxiv.org/abs/1712.00899) [[Project Page]](https://fei-hdu.github.io/ca-gan/)

## Our Proposed Framework

### Generator Architecture of CA-GAN

![](../images/ca-gan/architecture1.png)

### Stacked CA-GAN (SCA-GAN)

![](../images/ca-gan/fig_scagan.jpg)

## Sample Result

**left:** sketch synthesis; **right:** photo synthesis

![](../images/ca-gan/result1.png)

> (a)Input Image, (b)cGAN, (c)CA-GAN, (d)SCA-GAN

## Prerequisites

- Linux or similar environment
- Python 2.7
- NVIDIA GPU + CUDA CuDNN

## Getting Started

### Installation

- Clone this repo:

  ```shell script
  git clone https://github.com/fei-hdu/ca-gan
  cd ca-gan
  ```

- Install PyTorch 0.4+ and torchvision from http://pytorch.org and other dependencies (e.g., visdom and dominate). You can install all the dependencies by

  ```shell script
  pip install -r requirments.txt
  ```

### ca-gan train/test

- Download a dataset([CUFS](http://mmlab.ie.cuhk.edu.hk/archive/facesketch.html) split train and test with this [files]())
- Download the [VGG-Face](http://www.robots.ox.ac.uk/~vgg/software/vgg_face/) model. Here we convert torch weight to pyTorch to fit our frame, you can download our converted model directly: [Google Drive](https://drive.google.com/open?id=1V2dfOLXSgAS9V8PvhTeQAP6KGI40aff_)
- Get face parsing
  - here we use [Face Labling](https://github.com/Liusifei/Face_Parsing_2016) to get face parsing
  - Check out the [new parsing branch](https://github.com/fei-hdu/ca-gan/tree/new_parsing) to get the our newly used
- Train a model
  ```shell script
  python main.py --model_vgg {model path}
  ```
- Test the model
  ```shell script
  python test.py --dataroot {data path} --fold {epoch number}
  ```
  - The option `fold` is used for load `./checkpoint/netG_epoch_'+fold+'.weight` and you can edit it in `test.py`

### Pre-trained models

- A face $photo \mapsto sketch$ model pre-trained on the CUSF:
  - CA-GAN： [[Google Drive]](https://drive.google.com/drive/folders/1IY7tV-tyKFcB7t0j1l-ZBSfFhtYIrJbB?usp=sharing) [[Baidu Cloud]](https://pan.baidu.com/s/1jtEXeyRGEVvSaq0KyeT_UA)(pwd：tu9l)
  - SCA-GAN (code & model): [[Google Drive]](https://drive.google.com/file/d/1rDIDrt8eQrj2qxzPtIJzV1bQM6oLNKEJ/view?usp=sharing) [[BaiDu Cloud]](https://pan.baidu.com/s/1bZabOZUwunfmuS8hHpPHhw) (pwd: 6dxk)
  - SCA-GAN：A face photo2sketch model and a face sketch2photo model pre-trained on the CUFS[[BaiDu Cloud]](https://pan.baidu.com/s/11sbcrB3bhkDofaWrAVY5QA)(pwd:2xz5) uses new parsing network(Bisenet)[[BaiDu Cloud]](https://pan.baidu.com/s/1n-PcEoOq9Jb5UvpvTUExTA)(pwd:tqek)
- The pre-trained model need to be save at `./checkpoint` and named it as `netG_epoch_'+fold+'.weight`
- Then you can test the model

### Datasets

- [CUFS](http://mmlab.ie.cuhk.edu.hk/archive/facesketch.html)
- [CUFSF](http://mmlab.ie.cuhk.edu.hk/archive/cufsf/)

### Result

- Our final result with new parsing can be downloaded: [Google Drive](https://drive.google.com/open?id=1EHpQWzbbF3-BSd93rCclpYtbpbEOZ3p3)

### Training/Test Tips

Best practice for training and testing your models.
Feel free to ask any questions about **_coding_**. **Xingxin Xu, [jehovahxu@gmail.com](jehovahxu@gmail.com)**

## Citation

If you find this useful for your research, please cite our paper as:

```
@article{gao2020ca-gan,
	title = {Towards Realistic Face Photo-Sketch Synthesis via Composition-Aided GANs},
	author = {Jun Yu and Xingxin Xu and Fei Gao and Shengjie Shi and Meng Wang and Dacheng Tao and and Qingming Huang},
	booktitle = {IEEE Transactions on Cybernatics},
        doi = {10.1109/TCYB.2020.2972944},
	year = {2020},
	url = {https://github.com/fei-hdu/ca-gan},
}
```

## Acknowledgments

- Our code is inspired by the [pytorch-CycleGAN-and-pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) repository.
- This work is greatly supported by [Nannan Wang](http://www.ihitworld.com/) and [Chunlei Peng](http://chunleipeng.com/). [ (HIT@Xidian University)](http://www.ihitworld.com/)
