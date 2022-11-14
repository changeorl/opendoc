# 训练任务

<img src="_media/cloudbrain/train/model_home.png" width = "800" alt="traindetail" align=middle />

## 训练任务代码

- 在开启训练任务之前，请将下列示例代码提交到你的代码仓，并命名为 `train.py`

<!-- tabs:start -->

#### **GPU训练示例代码**

``` python
#!/usr/bin/python
#coding=utf-8    
'''
If there are Chinese comments in the code，please add at the beginning：
#!/usr/bin/python
#coding=utf-8    

Due to the adaptability of a100, before using the training environment, please use the recommended image of the 
platform with cuda 11.Then adjust the code and submit the image.
The image of this example is: dockerhub.pcl.ac.cn:5000/user-images/openi:cuda111_python37_pytorch191
In the training environment, the uploaded dataset will be automatically placed in the /dataset directory. 
If it is a single dataset: 
if MnistDataset_torch.zip is selected,Then the dataset directory is /dataset/train, /dataset/test;
If it is a multiple dataset: 
If MnistDataset_torch.zip and checkpoint_epoch1_0.73.zip are selected, 
the dataset directory is /dataset/MnistDataset_torch/train, /dataset/MnistDataset_torch/test
and /dataset/checkpoint_epoch1_0.73/mnist_epoch1_0.73.pkl

The model download path is under /model by default. Please specify the model output location to /model, 
and the Qizhi platform will provide file downloads under the /model directory.
'''

import numpy as np
import torch
from torchvision.datasets import mnist
from torch.nn import CrossEntropyLoss
from torch.optim import SGD
from torch.utils.data import DataLoader
from torchvision.transforms import ToTensor
import argparse
from torch.nn import Module
from torch import nn


class Model(Module):
    def __init__(self):
        super(Model, self).__init__()
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.relu1 = nn.ReLU()
        self.pool1 = nn.MaxPool2d(2)
        self.conv2 = nn.Conv2d(6, 16, 5)
        self.relu2 = nn.ReLU()
        self.pool2 = nn.MaxPool2d(2)
        self.fc1 = nn.Linear(256, 120)
        self.relu3 = nn.ReLU()
        self.fc2 = nn.Linear(120, 84)
        self.relu4 = nn.ReLU()
        self.fc3 = nn.Linear(84, 10)
        self.relu5 = nn.ReLU()

    def forward(self, x):
        y = self.conv1(x)
        y = self.relu1(y)
        y = self.pool1(y)
        y = self.conv2(y)
        y = self.relu2(y)
        y = self.pool2(y)
        y = y.view(y.shape[0], -1)
        y = self.fc1(y)
        y = self.relu3(y)
        y = self.fc2(y)
        y = self.relu4(y)
        y = self.fc3(y)
        y = self.relu5(y)
        return y


# Training settings
parser = argparse.ArgumentParser(description='PyTorch MNIST Example')
#The dataset location is placed under /dataset
parser.add_argument('--traindata', default="/dataset/train" ,help='path to train dataset')
parser.add_argument('--testdata', default="/dataset/test" ,help='path to test dataset')
parser.add_argument('--epoch_size', type=int, default=1, help='how much epoch to train')
parser.add_argument('--batch_size', type=int, default=256, help='how much batch_size in epoch')

if __name__ == '__main__':
    args, unknown = parser.parse_known_args()
    #log output
    print('cuda is available:{}'.format(torch.cuda.is_available()))  
    device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
    batch_size = args.batch_size
    train_dataset = mnist.MNIST(root=args.traindata, train=True, transform=ToTensor(),download=False)
    test_dataset = mnist.MNIST(root=args.testdata, train=False, transform=ToTensor(),download=False)
    train_loader = DataLoader(train_dataset, batch_size=batch_size)
    test_loader = DataLoader(test_dataset, batch_size=batch_size)
    model = Model().to(device)
    sgd = SGD(model.parameters(), lr=1e-1)
    cost = CrossEntropyLoss()
    epoch = args.epoch_size
    print('epoch_size is:{}'.format(epoch))
    for _epoch in range(epoch):
        print('the {} epoch_size begin'.format(_epoch + 1))
        model.train()
        for idx, (train_x, train_label) in enumerate(train_loader):
            train_x = train_x.to(device)
            train_label = train_label.to(device)
            label_np = np.zeros((train_label.shape[0], 10))
            sgd.zero_grad()
            predict_y = model(train_x.float())
            loss = cost(predict_y, train_label.long())
            if idx % 10 == 0:
                print('idx: {}, loss: {}'.format(idx, loss.sum().item()))
            loss.backward()
            sgd.step()

        correct = 0
        _sum = 0
        model.eval()
        for idx, (test_x, test_label) in enumerate(test_loader):
            test_x = test_x
            test_label = test_label
            predict_y = model(test_x.to(device).float()).detach()
            predict_ys = np.argmax(predict_y.cpu(), axis=-1)
            label_np = test_label.numpy()
            _ = predict_ys == test_label
            correct += np.sum(_.numpy(), axis=-1)
            _sum += _.shape[0]
        print('accuracy: {:.2f}'.format(correct / _sum))
        #The model output location is placed under /model
        #state = {'model':model.state_dict(), 'optimizer':sgd.state_dict(), 'epoch':epoch}
        torch.save(model, '/model/pytroch.pth')
```


#### **NPU训练示例代码**


```python
"""
######################## single-dataset train lenet example ########################
This example is a single-dataset training tutorial. If it is a multi-dataset, please refer to the multi-dataset training 
tutorial train_for_multidataset.py. This example cannot be used for multi-datasets!

######################## Instructions for using the training environment ########################
The image of the debugging environment and the image of the training environment are two different images, 
and the working local directories are different. In the training task, you need to pay attention to the following points.
1、(1)The structure of the dataset uploaded for single dataset training in this example
 MNISTData.zip
  ├── test
  └── train


2、Single dataset training requires predefined functions
(1)Copy single dataset from obs to training image
function ObsToEnv(obs_data_url, data_dir)

(2)Copy the output to obs
function EnvToObs(train_dir, obs_train_url)

(3)Download the input from Qizhi And Init 
function DownloadFromQizhi(obs_data_url, data_dir)

(4)Upload the output to Qizhi 
function UploadToQizhi(train_dir, obs_train_url)

3、3 parameters need to be defined
--data_url is the dataset you selected on the Qizhi platform

--data_url,--train_url,--device_target,These 3 parameters must be defined first in a single dataset task, 
otherwise an error will be reported.    
There is no need to add these parameters to the running parameters of the Qizhi platform, 
because they are predefined in the background, you only need to define them in your code.                 

4、How the dataset is used
A single dataset uses data_url as the input, and data_dir (ie:'/cache/data') as the calling method
of the dataset in the image.
For details, please refer to the following sample code.

In addition, if you want to get the model file after each training, you can call the UploadOutput.
"""

import os
import argparse
import moxing as mox
from config import mnist_cfg as cfg
from dataset import create_dataset
from dataset_distributed import create_dataset_parallel
from lenet import LeNet5
import mindspore.nn as nn
from mindspore import context
from mindspore.train.callback import ModelCheckpoint, CheckpointConfig, LossMonitor, TimeMonitor
from mindspore.train import Model
from mindspore.nn.metrics import Accuracy
from mindspore.context import ParallelMode
from mindspore.communication.management import init, get_rank
import mindspore.ops as ops
import time
from upload import UploadOutput

### Copy single dataset from obs to training image###
def ObsToEnv(obs_data_url, data_dir):
    try:     
        mox.file.copy_parallel(obs_data_url, data_dir)
        print("Successfully Download {} to {}".format(obs_data_url, data_dir))
    except Exception as e:
        print('moxing download {} to {} failed: '.format(obs_data_url, data_dir) + str(e))
    #Set a cache file to determine whether the data has been copied to obs. 
    #If this file exists during multi-card training, there is no need to copy the dataset multiple times.
    f = open("/cache/download_input.txt", 'w')    
    f.close()
    try:
        if os.path.exists("/cache/download_input.txt"):
            print("download_input succeed")
    except Exception as e:
        print("download_input failed")
    return 
### Copy the output to obs###
def EnvToObs(train_dir, obs_train_url):
    try:
        mox.file.copy_parallel(train_dir, obs_train_url)
        print("Successfully Upload {} to {}".format(train_dir,obs_train_url))
    except Exception as e:
        print('moxing upload {} to {} failed: '.format(train_dir,obs_train_url) + str(e))
    return      
def DownloadFromQizhi(obs_data_url, data_dir):
    device_num = int(os.getenv('RANK_SIZE'))
    if device_num == 1:
        ObsToEnv(obs_data_url,data_dir)
        context.set_context(mode=context.GRAPH_MODE,device_target=args.device_target)
    if device_num > 1:
        # set device_id and init for multi-card training
        context.set_context(mode=context.GRAPH_MODE, device_target=args.device_target, device_id=int(os.getenv('ASCEND_DEVICE_ID')))
        context.reset_auto_parallel_context()
        context.set_auto_parallel_context(device_num = device_num, parallel_mode=ParallelMode.DATA_PARALLEL, gradients_mean=True, parameter_broadcast=True)
        init()
        #Copying obs data does not need to be executed multiple times, just let the 0th card copy the data
        local_rank=int(os.getenv('RANK_ID'))
        if local_rank%8==0:
            ObsToEnv(obs_data_url,data_dir)
        #If the cache file does not exist, it means that the copy data has not been completed,
        #and Wait for 0th card to finish copying data
        while not os.path.exists("/cache/download_input.txt"):
            time.sleep(1)  
    return
def UploadToQizhi(train_dir, obs_train_url):
    device_num = int(os.getenv('RANK_SIZE'))
    local_rank=int(os.getenv('RANK_ID'))
    if device_num == 1:
        EnvToObs(train_dir, obs_train_url)
    if device_num > 1:
        if local_rank%8==0:
            EnvToObs(train_dir, obs_train_url)
    return

### --data_url,--train_url,--device_target,These 3 parameters must be defined first in a single dataset, 
### otherwise an error will be reported.
###There is no need to add these parameters to the running parameters of the Qizhi platform, 
###because they are predefined in the background, you only need to define them in your code.
parser = argparse.ArgumentParser(description='MindSpore Lenet Example')
parser.add_argument('--data_url',
                    help='path to training/inference dataset folder',
                    default= '/cache/data/')

parser.add_argument('--train_url',
                    help='output folder to save/load',
                    default= '/cache/output/')

parser.add_argument(
    '--device_target',
    type=str,
    default="Ascend",
    choices=['Ascend', 'CPU'],
    help='device where the code will be implemented (default: Ascend),if to use the CPU on the Qizhi platform:device_target=CPU')

parser.add_argument('--epoch_size',
                    type=int,
                    default=5,
                    help='Training epochs.')

if __name__ == "__main__":
    args, unknown = parser.parse_known_args()
    data_dir = '/cache/data'  
    train_dir = '/cache/output'
    if not os.path.exists(data_dir):
        os.makedirs(data_dir)
    if not os.path.exists(train_dir):
        os.makedirs(train_dir)
    ###Initialize and copy data to training image
    DownloadFromQizhi(args.data_url, data_dir)
    ###The dataset path is used here:data_dir +"/train"   
    device_num = int(os.getenv('RANK_SIZE'))
    if device_num == 1:
        ds_train = create_dataset(os.path.join(data_dir, "train"),  cfg.batch_size)
    if device_num > 1:
        ds_train = create_dataset_parallel(os.path.join(data_dir, "train"),  cfg.batch_size)
    if ds_train.get_dataset_size() == 0:
        raise ValueError("Please check dataset size > 0 and batch_size <= dataset size")

    network = LeNet5(cfg.num_classes)
    net_loss = nn.SoftmaxCrossEntropyWithLogits(sparse=True, reduction="mean")
    net_opt = nn.Momentum(network.trainable_params(), cfg.lr, cfg.momentum)
    time_cb = TimeMonitor(data_size=ds_train.get_dataset_size())

    if args.device_target != "Ascend":
        model = Model(network,
                      net_loss,
                      net_opt,
                      metrics={"accuracy": Accuracy()})
    else:
        model = Model(network,
                      net_loss,
                      net_opt,
                      metrics={"accuracy": Accuracy()},
                      amp_level="O2")

    config_ck = CheckpointConfig(
        save_checkpoint_steps=cfg.save_checkpoint_steps,
        keep_checkpoint_max=cfg.keep_checkpoint_max)
    #Note that this method saves the model file on each card. You need to specify the save path on each card.
    # In this example, get_rank() is added to distinguish different paths.
    if device_num == 1:
        outputDirectory = train_dir + "/"
    if device_num > 1:
        outputDirectory = train_dir + "/" + str(get_rank()) + "/"
    ckpoint_cb = ModelCheckpoint(prefix="checkpoint_lenet",
                                directory=outputDirectory,
                                config=config_ck)
    print("============== Starting Training ==============")
    epoch_size = cfg['epoch_size']
    if (args.epoch_size):
        epoch_size = args.epoch_size
        print('epoch_size is: ', epoch_size)
    #Custom callback, upload output after each epoch
    uploadOutput = UploadOutput(train_dir,args.train_url)
    model.train(epoch_size,
                ds_train,
                callbacks=[time_cb, ckpoint_cb,
                           LossMonitor(), uploadOutput])

    ###Copy the trained output data from the local running environment back to obs,
    ###and download it in the training task corresponding to the Qizhi platform
    #This step is not required if UploadOutput is called
    UploadToQizhi(train_dir,args.train_url)
```

<!-- tabs:end -->

## 创建训练任务

在 `项目`->`云脑`->`训练任务` 下，点击 `新建训练任务` 即可以跳转创建训练任务详情界面