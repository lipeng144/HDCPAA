## Requirements
- [PyTorch >= version 1.1](https://pytorch.org)
- tqdm

## Datasets and pretrained models
We follow [FSCIL](https://github.com/xyutao/fscil) setting to use the same data index_list for training.  

## Training scripts
MSTAR
    $ python train.py -project cec -dataset MSTAR -epochs_base 100 -episode_way 15 -episode_shot 1 -low_way 15 -low_shot 1 -lr_base 0.002 -lrg 0.0002 -step 20 -gamma 0.5 -gpu 0,1,2,3 -model_dir params/cifar100/session0_max_acc7455_cos.pth
nwpu

    $ python train.py -project cec -dataset nwpu -epochs_base 100 -episode_way 15 -episode_shot 1 -low_way 15 -low_shot 1 -lr_base 0.0002 -lrg 0.0002 -step 20 -gamma 0.5 -gpu 0,1,2,3 -model_dir params/miniimagenet/session0_max_acc70367_cos.pth


## Pretrain scripts
MSTAR

    $python train.py -project base -dataset MSTAR  -base_mode 'ft_cos' -new_mode 'avg_cos' -gamma 0.1 -lr_base 0.1 -lr_new 0.1 -decay 0.0005 -epochs_base 100 -schedule Milestone -milestones 60 70 -gpu 0,1,2,3 -temperature 16
    
nwpu

    $python train.py -project base -dataset nwpu -base_mode 'ft_cos' -new_mode 'avg_cos' -gamma 0.1 -lr_base 0.1 -lr_new 0.1 -decay 0.0005 -epochs_base 100 -schedule Milestone -milestones 40 70 -gpu 0,1,2,3 -temperature 16
## Acknowledgment
Our project references the codes in the following repos.

- [fscil](https://github.com/xyutao/fscil)
