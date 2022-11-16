# 训练任务

> [!tip]
> - 训练任务同推理任务的流程一致
> - 唯一不同的是推理任务需要你预先导入模型到项目中

<img src="_media/cloudbrain/train/model_home.png" width = "800" alt="traindetail" align=middle />

## 训练任务代码

- 在开启训练任务之前，请将下列两个示例代码仓Fork到你自己的项目
- 或者你也可以创建自己的项目，将代码文件下载，提交到你的代码仓
    - [GPU示例代码](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_PytorchExample_GPU)
    - [NPU示例代码](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example)

> [!tip]
> - 训练任务只会执行一个脚本代码文件
> - 当你创建自己的训练任务时，请在代码仓提交一个单独的训练脚本

- 你可以在训练脚本中使用下列示例代码来添加训练控制参数

```python
import argparse

# 设置
parser = argparse.ArgumentParser(description='PyTorch MNIST Example')
parser.add_argument('--epoch_size', type=int, default=1, help='how much epoch to train')

# main中加载参数
args, unknown = parser.parse_known_args()
batch_size = args.batch_size
```

## 创建训练任务

在 `项目`->`云脑`->`训练任务` 下，点击 `新建训练任务` 即可以跳转创建训练任务详情界面

<!-- tabs:start -->

#### **GPU训练**

> [!note|label:训练参数|icon:fa-solid fa-list fa-bounce]
> - **基本信息**
>   - **算力集群** *启智或智算都可*
>   - **计算资源** *CPU/GPU*
>   - **任务名称** *只能以小写字母或数字开头且只包含小写字母、数字、_和-，不能以_结尾，最长36个字符*
>   - **任务描述** *可以为空，字数不超过255个字符*
> - **参数信息**
>   - **代码分支** *选择你的代码分支，这将决定脚本代码的版本*
>   - **模型选择** *如果你在新建推理任务或使用预训练模型，请选择你想要的模型及版本，需要预先导入到项目模型中*
>   - **镜像** *可选择平台或外部镜像，示例代码使用 `dockerhub.pcl.ac.cn:5000/user-images/openi:cuda111_python37_pytorch191`*
>   - **数据集** *选择本项目或公开数据集，示例代码使用 `MNIST_PytorchExample_GPU/MnistDataset_torch.zip`*
>   - **运行参数** *根据你的脚本代码输入参数名称及取值，如`batch_size`, `128`*
>   - **资源规格** *根据你的项目需要选择*
> *训练脚本存储在 **/code** 中，数据集存储在 **/dataset** 中，预训练模型存放在运行参数 **ckpt_url** 中，训练输出请存储在 **/model** 中以供后续下载。*

<img src="_media/cloudbrain/train/gpu_create.png" width = "800" alt="traindetail" align=middle />

#### **NPU训练**

> [!note|label:训练参数|icon:fa-solid fa-list fa-bounce]
> - **基本信息**
>   - **算力集群** *启智或智算都可*
>   - **计算资源** *Ascend NPU*
>   - **任务名称** *只能以小写字母或数字开头且只包含小写字母、数字、_和-，不能以_结尾，最长36个字符*
>   - **任务描述** *可以为空，字数不超过255个字符*
> - **参数信息**
>   - **代码分支** *选择你的代码分支，这将决定脚本代码的版本*
>   - **模型选择** *如果你在新建推理任务或使用预训练模型，请选择你想要的模型及版本，需要预先导入到项目模型中*
>   - **AI引擎** *第一项默认`Ascend-Powered-Engine`，第二项根据你的项目选择`MindSpore1.7`，`MindSpore1.8.1`，或者`TensorFlow1.15`*
>   - **数据集** *选择本项目或公开数据集，示例代码使用 `MNISTData_mindspore/MNISTData.zip`*
>   - **运行参数** *根据你的脚本代码输入参数名称及取值，如`batch_size`, `128`*
>   - **资源规格** *默认选项即可*
> *数据集位置存储在运行参数 data_url 中，预训练模型存放在运行参数 ckpt_url 中，训练输出路径存储在运行参数 train_url 中。*

<img src="_media/cloudbrain/train/npu_create.png" width = "800" alt="traindetail" align=middle />

<!-- tabs:end -->

## 训练完成/失败

点击任务名称可查看详情训练详情

<!-- tabs:start -->

#### **GPU训练**

- 你可以在日志中查看训练任务详情
- 若需要输出下载模型文件，请在代码中保存到 **/model** 路径，然后在详情下载界面下载

<img src="_media/cloudbrain/train/gpu_detail.png" width = "800" alt="traindetail" align=middle />

<br>

<img src="_media/cloudbrain/train/gpu_log.png" width = "800" alt="traindetail" align=middle />

<br>

<img src="_media/cloudbrain/train/gpu_download.png" width = "800" alt="traindetail" align=middle />

#### **NPU训练**

- 你可以在训练简况中查看云脑训练信息
- 日志中为训练脚本代码的输出
- 若需要输出下载模型文件，请在代码中保存到 **/cache/output** 路径，然后在详情下载界面下载

<img src="_media/cloudbrain/train/npu_detail.png" width = "800" alt="traindetail" align=middle />

<br>

<img src="_media/cloudbrain/train/npu_log.png" width = "800" alt="traindetail" align=middle />

<br>

<img src="_media/cloudbrain/train/npu_download.png" width = "800" alt="traindetail" align=middle />

<!-- tabs:end -->