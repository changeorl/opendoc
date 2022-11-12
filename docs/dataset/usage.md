# 数据使用示例：GPU调试imagenet-1k

<!-- tabs:start -->

#### **GPU调试**

- 首先创建并打开一个项目，点击 `云脑` 即可看见 `新建调试任务`
- 新建调试任务时，选择任意镜像以及官方平台的 `IMAGENET-1K`数据集
- 计算资源选择`GPU`，资源规格任意选择即可

<img src="_media/dataset/usagecreate.png" width = "800" alt="traindetail" align=middle />

- 当任务状态变为 `RUNNING` 时，点击 `调试` 即可进入调试界面
- 如出现以下`502错误界面`，请退出并回到调试任务列表耐心等待3-5分钟，再次点击 `调试` 即可

<img src="_media/dataset/usage502.png" width = "800" alt="traindetail" align=middle />

- 成功进入调试任务后，你将看到 `Jupyter Lab` 主界面
- 你可以在这里使用 `Terminal` 命令行管理调试环境中的文件与安装第三方Python库，也可以新建 `Notebook` 在线调试代码

<img src="_media/dataset/usagelab.png" width = "800" alt="traindetail" align=middle />

- 下列为调试环境中的文件路径，数据集的绝对路`/dataset/数据集解压文件夹`，如本示例中为`/dataset/imagenet`，数据集解压文件夹名与你的数据集文件名相同
- 本项目代码仓中的所有代码文件都在环境中`/code`路径下，你可以通过`Terminal`运行代码或者新建`Notebook`

```text
.
├── /workspace
├── /code
│   ├── 代码仓文件
│   └── 新建Notebook
└── /dataset
    └── /imagenet
        ├── /train
        │   ├── /n01440764  
        │   │   ├── n01440764_12090.JPEG  
        │   │   ├── n01440764_14490.JPEG  
        │   │   ├── n01440764_25361.JPEG
        │   │   └── ...
        │   ├── /n01773157  
        │   ├── /n02051845  
        │   └── ...
        └── /val
            └── ...
```

- 打开`Terminal`，输入下列`cd`命令查看数据集是否在环境中

```shell
# cd /dataset/imagenet/train/n01440764
# ls
n01440764_10026.JPEG  n01440764_12111.JPEG  n01440764_14524.JPEG  
n01440764_8240.JPEG   n01440764_10027.JPEG  n01440764_12129.JPEG  
...
```

- （只为本示例代码） 本示例将会用到 `matplotlib`，此库没有预装在环境里，输入下列命令行安装
- 你可以使用 `pip show 库名` 或 `pip list` 来查看你的需要的库是否已安装

```shell
# pip install matplotlib -i https://pypi.tuna.tsinghua.edu.cn/simple
```

- 新建 `Notebook`，复制下列代码并运行，若成功输出维度与图片，则读取数据成功

```python
import matplotlib.pyplot as plt # plt 用于显示图片
import matplotlib.image as mpimg # mpimg 用于读取图片
import numpy as np

sample = mpimg.imread('/dataset/imagenet/train/n01440764/n01440764_10026.JPEG')
print(sample.shape)

plt.imshow(sample) # 显示图片
plt.axis('off') # 不显示坐标轴
plt.show()
```

<img src="_media/dataset/usagejupyter.png" width = "800" alt="traindetail" align=middle />

> [!tip|label:数据使用教程完成|icon:fa-sharpe fa-solid fa-check fa-beat]
> 🎉 恭喜你！你已经成功在GPU环境下启用调试任务并读取数据。\
> 请点击右侧的下一卷查看更多关于调试任务的介绍

#### **NPU**

#### 调试

<!-- tabs:end -->