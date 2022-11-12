# plugin tutorial
> 👍 this is a test documentation

!> this is a warining quote

?> this is a questioned quote



<!-- tabs:start -->

#### **English**

Hello!

#### **French**

Bonjour!

#### **Italian**

![图标](https://git.openi.org.cn/chenzh/model_convert_test/raw/branch/master/VMGsDCUg4c.png "图标")

<!-- tabs:end -->





> [!note|icon:fa-solid fa-heart fa-beat]
> animated icon from fontawesome https://fontawesome.com/docs/web/style/animate



> [!TIP|style:flat]
> styple `flat`



> [!WARNING]
> An alert of type 'warning' using global style 'callout'.



> [!ATTENTION]
> An alert of type 'attention' using global style 'callout'.





<br>

![图标](https://git.openi.org.cn/chenzh/model_convert_test/raw/branch/master/VMGsDCUg4c.png "图标")


```
.
├── quickstartGPU
├── intro/
│   ├── intro
│   ├── functions
│   └── resources
├── repo/
│   ├── gitrepo
│   └── files
├── dataset/
│   ├── upload
│   ├── public
│   ├── link
│   └── fileupload
├── cloudbrain/
│   ├── mirror
│   ├── debug
│   ├── train/test
│   └── eval
├── model/
│   ├── online
│   ├── local
│   ├── convert
│   └── space
└── user/
    ├── center
    └── group
```
*made with https://tree.nathanfriend.io/*



[cinwell](/_media/record.mp4 ':include :type=vedio controls width=100%')


![](/_media/giftest.gif "-gifcontrol-mode=click;")


<!-- select:start -->
<!-- select-menu-labels: 操作系统 -->

#### --macOS--

Common content can go here above the first heading in a section and be rendered for all selections!

#### --Linux--

Linux instructions here

<!-- select:end -->


<!-- select:start -->
<!-- select-menu-labels: Operating System,Installation Method -->

### --macOS,Git--

macOS + Git

### --macOS,Homebrew--

macOS + Homebrew

### --Linux,Git--

Linux + Git

<!-- select:end -->


<!-- select:start -->
<!-- select-menu-labels: Operating System,Installation Method -->

### --macOS,Git--

macOS + Git

### --macOS,Homebrew--

macOS + Homebrew

### --Linux,Git--

Linux + Git

### --Docsify Select Default--

No selection for this combination. Sorry!

<!-- select:end -->



## label generating

```python

#tar -zcvf 

import matplotlib.pyplot as plt # plt 用于显示图片
import matplotlib.image as mpimg # mpimg 用于读取图片
import numpy as np
import os

idx_lookup = { idx:label_idx for idx,label_idx in enumerate(os.listdir('/dataset/imagenet/train/'))}

list_of_label = dict()
idx = 0

def imagenet_preview(list_of_label, idx, idx_lookup):
    
    label_idx = list_of_label[idx]

    train = os.listdir('/dataset/imagenet/train/' + label_idx)
    val = os.listdir('/dataset/imagenet/val/' + label_idx)

    for i,data_idx in enumerate(train):
        if i < 3:
            sample = mpimg.imread('/dataset/imagenet/train/' + label_idx + '/' + data_idx)
            #print(sample.shape)

            plt.imshow(sample) # 显示图片
            plt.axis('off') # 不显示坐标轴
            plt.show()

    print(label_idx,idx)
    label = input('enter label value:')

    list_of_label[idx] = [label_idx,label]

    idx += 1
```

<!-- tabs:start -->

#### **GPU**


#### **NPU**


<!-- tabs:end -->