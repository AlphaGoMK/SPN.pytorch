# PyTorch implementation of SPN

Soft Proposal Networks for Weakly Supervised Object Localization, ICCV 2017.

[[Project Page]](http://yzhu.work/spn) [[Paper]](https://arxiv.org/pdf/1709.01829) [[Supp]](http://yzhu.work/pdffiles/SPN_Supp.pdf) 

[[Torch code]](https://github.com/ZhouYanzhao/SPN)  

## Experiments
### upsample with bn
* image size=112,           pa=10.59
* image size=224,           pa=34.17

### upsample without bn
* image size=112,224,560,   pa=21
* image size=224,           pa=27.52


## Thoughts
1. 采用只有224x224的random crop训练可以提升point accuracy但仍然很低 (21->34.17)
2. load model时选择更小的image-size
3. 尝试较浅层网络，太深层网络的proposal可能效果不太好
4. loss无法收敛：random crop image size从112->224时，产生Loss的gap，且无法收敛

## Bugs
1. image-size 224x224时不输出 trainLoss,trainMAP,testLoss,testMAP

## Citation 
If you use the code in your research, please cite:
```bibtex
@INPROCEEDINGS{Zhu2017SPN,
    author = {Zhu, Yi and Zhou, Yanzhao and Ye, Qixiang and Qiu, Qiang and Jiao, Jianbin},
    title = {Soft Proposal Networks for Weakly Supervised Object Localization},
    booktitle = {ICCV},
    year = {2017}
}
```

## Acknowledgement
In this project, we reimplemented SPN on PyTorch based on [wildcat.pytorch](https://github.com/durandtibo/wildcat.pytorch). To keep consistency with the Torch version, we use the VGG16 model exported from caffe in [fcn.pytorch](https://github.com/wkentaro/pytorch-fcn).
