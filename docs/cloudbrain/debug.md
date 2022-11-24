# 调试任务

 项目页面的 `云脑`->`调试任务`->`新建调试任务` 可以开启调试任务

<img src="_media/cloudbrain/debug/start.png" width = "800" alt="traindetail" align=middle />

>[!note|label:提示|icon:fa-solid fa-lightbulb fa-bounce]
> - 调试任务将启动 `镜像容器`，GPU任务与NPU任务的容器有着不同的文件路径，与数据集使用方法
>   - 在GPU调试代码中使用数据集时，请使用绝对路径，如 `/dataset/数据集解压文件夹/`
>   - 在NPU调试代码中使用数据集时，需要使用 `wget` 与 `unzip` 命令行指令下载解压数据集
> - 调试任务将会在镜像容器里提供 `Jupyter Lab` 控制，包含 `Terminal` 与 `Notebook` 功能
>   - 建议使用清华镜像安装Python包以及搭建Anaconda，详情请查看[清华镜像官方](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)
> - 启动调试任务时，当状态由 `WAITING` 转为 `RUNNING` 后，需继续等待3-5分钟，提前点击调试会看到 `502错误界面`， 请退出并耐心等待
> - 调试任务的时长限制为4小时，未关闭的调试任务将在4小时后自动关闭



<!-- tabs:start -->

#### **GPU**

### GPU 新建调试任务
*点击新建调试任务，在弹窗中配置下列信息来启动调试任务，其余字段可保持默认设置*
- **计算资源**: 选择 `CPU/GPU`
- **任务名称**：只能包含 `小写字母，数字，以及下划线与连接号`
- **镜像**：可以选择任意 `平台镜像` 或者使用 `外部镜像`，粘贴镜像链接到框内即可
- **数据集**：点击 `选择数据集` 即可选择数据集
    - 数据集可 `多选` ，在弹窗中选中多个数据集即可
    - 你可以使用 `本项目数据集` 或 `关联数据集`，你也可以在调试代码里下载 `外部数据集`
    - 此选项可以为 `空白` ，即不使用数据集
- **资源规格**：任意选择你想要的资源规格

<img src="_media/cloudbrain/debug/gpu_create.png" width = "800" alt="traindetail" align=middle />

### GPU Jupyter Lab 控制台
*如果你有使用过 Jupyter Notebook/Lab 的经验，你可以跳过这一部分*
- 点击左上角蓝色 `+按钮` 可以新建Tab标签页
- 在新标签页，你可以新建 `.ipynb` Notebook代码文件来进行调试代码
- 你也可以新建Python控制台 `Console` 来进行简单的代码测试
- 新建 `Terminal` 窗口进行 `Python库` 的安装以及运行 `.py` 代码文件

<img src="_media/cloudbrain/debug/gpu_lab.png" width = "800" alt="traindetail" align=middle />

### GPU 调试环境文件路径

- `/workspace`： 打开 `Terminal` 时的默认目录，可输入 `cd ..` 返回根目录
- `/code`：本目录下已经自动拉取了本项目代码仓
- `/data`： 本目录下可以找到创建调试任务时选取的数据集，平台已解压
- `/model`： 若代码中有需要下载的输出文件可放在此目录下，在调试任务列表右侧下拉 `更多`->`模型下载` 即可下载 

``` text
# 调试环境镜像容器目录
.
├── code/
│   ├── train.py
│   └── ...
├── dataset/
│   ├── unzip_data
│   └── ...
├── model/
│   └── export_model.pth
├── ...  
└── workspace/
    └── .
```

### GPU 调试任务示例

*新建一个云脑调试任务，填入以下参数*

> [!note|label:填写以下参数|icon:fa-solid fa-list fa-bounce]
> - **计算资源** CPU/GPU
> - **任务名称** imagenet-sample-gpu
> - **镜像** 复制并粘贴地址 *dockerhub.pcl.ac.cn:5000/user-images/openi:cuda111_python37_pytorch191*
> - **数据集** 请搜索并关联 *quickstart/imagenet-sample.zip*，*MNIST_PytorchExample_GPU/MnistDataset_torch.zip* 或自行下载[imagenet-sample](https://openi.pcl.ac.cn/chenzh/quickstart/datasets),[MNIST_Pytorch](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_PytorchExample_GPU/datasets)并上传到你的项目中(选择GPU版本)
> - **资源规格** 请选择任意一张 **GPU不为0** 的卡
> - **其他配置保持默认值即可**

<img src="_media/cloudbrain/debug/gpu_create.png" width = "800" alt="traindetail" align=middle />

- 当任务状态变为 `RUNNING` 时，点击 `调试` 即可进入调试界面
- 如出现以下`502错误界面`，请退出并回到调试任务列表耐心等待3-5分钟，再次点击 `调试` 即可

<img src="_media/cloudbrain/debug/usage502.png" width = "800" alt="traindetail" align=middle />

- 成功进入调试任务后，你将看到 `Jupyter Lab` 主界面
- 调试任务中的代码，数据集及输出文件路径为以下所示（以本示例为例）：

```text
.
├── workspace
├── code/
│   ├── 代码仓文件
│   ├── 新建Notebook文件
│   └── ...
├── datasaet/
│   └── imagenet-sample/
│       ├── train/
│       │   ├── n01986214/
│       │   │   ├── n01986214_49.JPEG
│       │   │   ├── n01986214_50.JPEG
│       │   │   └── ...
│       │   └── ...
│       └── val/
│           └── ...
└── model/
    └── ...
```

- 点击新建 `Terminal` 窗口，输入下列命令行指令检查数据集文件路径是否存在

```shell
ls /dataset/imagenet-sample/train/n01986214
```

<img src="_media/cloudbrain/debug/gpu_datapath.png" width = "800" alt="traindetail" align=middle />


- 本示例中将用到镜像中未预装 `matplotlib` 库，请在 `Terminal` 中使用 `pip` 安装
- 安装完成后使用 `pip show matplotlib` 查看是否安装成功

```shell
pip install matplotlib -i https://pypi.tuna.tsinghua.edu.cn/simple
```

<img src="_media/cloudbrain/debug/gpu_pip.png" width = "800" alt="traindetail" align=middle />

- 新建 `Notebook` 文件，将下列代码拷贝并运行，若成功打印图片数据维度与图片，则数据读取成功

```python
import matplotlib.pyplot as plt # plt 用于显示图片
import matplotlib.image as mpimg # mpimg 用于读取图片
import numpy as np

sample = mpimg.imread('/dataset/imagenet-sample/train/n01986214/n01986214_15101.JPEG')
print(sample.shape)

plt.imshow(sample) # 显示图片
plt.axis('off') # 不显示坐标轴
plt.show()
```

<img src="_media/cloudbrain/debug/gpu_code.png" width = "800" alt="traindetail" align=middle />

> [!note|label:调试成功|icon:fa-sharpe fa-solid fa-check fa-beat]
> 🎉 恭喜你！你已经成功在GPU环境下启用调试任务并读取数据。\
> 你可以回到顶部查看[NPU的调试任务介绍](/cloudbrain/debug.md#npu-新建调试任务)，或者点击下一卷前往镜像介绍



#### **NPU**

### NPU 新建调试任务

*点击新建调试任务，在弹窗中配置下列信息来启动调试任务，其余字段可保持默认设置*
- **计算资源**: 选择 `NPU`
- **任务名称**：只能包含 `小写字母，数字，以及下划线与连接号`
- **镜像**：只能选择 `平台镜像`，提供 `TensorFlow` 和 `Mindspore`
- **数据集**：点击 `选择数据集` 即可选择数据集
    - 数据集可 `多选` ，在弹窗中选中多个数据集即可
    - 你可以使用 `本项目数据集` 或 `关联数据集`，你也可以在调试代码里下载 `外部数据集`
    - 此选项可以为 `空白` ，即不使用数据集
- **资源规格**：任意选择你想要的资源规格

<img src="_media/cloudbrain/debug/npu_create.png" width = "800" alt="traindetail" align=middle />

### NPU Model Arts 控制台

*与GPU调试任务不同，NPU调试提供华为 [Model Arts](https://support.huaweicloud.com/modelarts/index.html) 控制台*

<img src="_media/cloudbrain/debug/npu_lab.png" width = "800" alt="traindetail" align=middle />

### NPU 代码与数据下载

*NPU调试任务的文件路径与GPU并不相同，代码仓与数据集也需要你手动下载到调试环境*

- NPU调试任务需要手动下载代码仓与数据集
- 你不需要改变NPU调试环境的工作目录，所有文件都应放在默认路径下
- 在控制台中，点击左侧搜索框上方最右边的Git图标，输入代码仓地址
- 你也可以在 `Terminal` 中使用 `git clone` 来克隆代码仓

<img src="_media/cloudbrain/debug/npu_git.png" width = "800" alt="traindetail" align=middle />

- 在调试任务列表点击任务名称，在详情页可以找到数据集下载链接

<img src="_media/cloudbrain/debug/npu_datalink.png" width = "800" alt="traindetail" align=middle />

- 输入下列命令行指令，使用 `wget -O 自定义数据集名称 '下载地址'` 来下载数据集压缩包

```shell
wget -O dataset 'https://open-data.obs.cn-south-222.ai.pcl.cn:443/attachment/2/1/21f17b25-2a3e-4b42-a717-5547b72036cd/imagenet-sample.zip?response-content-disposition=attachment%3B+filename%3D%22imagenet-sample.zip%22&AWSAccessKeyId=ZSCXA9TLRN1USYWIF7A5&Expires=1668419095&Signature=xcL10IAPRSjAkEjNlITwD3CsFXM%3D'
```

<img src="_media/cloudbrain/debug/npu_data.png" width = "800" alt="traindetail" align=middle />

- 下载完成后，你还需要输入下列命令行指令将数据集解压到当前目录

```shell
unzip dataset
```

### NPU 调试任务示例

- 新建 `Notebook` 文件，将下列代码拷贝并运行，若成功打印图片数据维度与图片，则数据读取成功
- 请注意，与GPU调试任务不同，NPU的数据路径为当前目录，不需要使用绝对路径

```python
import matplotlib.pyplot as plt # plt 用于显示图片
import matplotlib.image as mpimg # mpimg 用于读取图片
import numpy as np

sample = mpimg.imread('imagenet-sample/train/n01986214/n01986214_15101.JPEG')
print(sample.shape)

plt.imshow(sample) # 显示图片
plt.axis('off') # 不显示坐标轴
plt.show()
```

<img src="_media/cloudbrain/debug/npu_code.png" width = "800" alt="traindetail" align=middle />

> [!note|label:调试成功|icon:fa-sharpe fa-solid fa-check fa-beat]
> 🎉 恭喜你！你已经成功在NPU环境下启用调试任务并读取数据。\
> 你可以回到顶部查看[GPU的调试任务介绍](/cloudbrain/debug.md#gpu-新建调试任务)，或者点击下一卷前往镜像介绍

<!-- tabs:end -->

