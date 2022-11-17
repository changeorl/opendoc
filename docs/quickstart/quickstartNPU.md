# 快速开始: MindSpore手写识别NPU训练任务实例

> 在本篇中，你将快速学会如何创建项目，并开启一个GPU训练任务。本教程参考 [代码仓](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example)

## 派生项目

首先你需要注册一个启智社区的账号。

> [!note|label: 加入我们！|icon:fa-solid fa-user fa-bounce]
> 现在就加入启智社区，尽享普惠算力。[立即注册](https://git.openi.org.cn/user/sign_up)

- 注册成功之后，请点击 [Fork示例代码仓](https://openi.pcl.ac.cn/repo/fork/29805)，填写项目名称并点击派生项目
- `派生项目` 指创建一个 `示例代码仓` 的副本到你的账户下
- 你的 `派生项目` 与 `原示例代码仓` 为两个独立项目，各自的改动不会互相影响，除非你向原项目提出 `代码变更申请`

<!-- tabs:start -->

#### **派生代码仓**

 <img src="_media/quickstart/repo_fork.png" width = "800" alt="homepage" align=center />

#### **示例代码说明**

本示例用到的代码文件，只有训练脚本 `train.py` 会被执行

- [train.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/train.py) 训练脚本文件，包含了训练代码，下列的所有代码文件都已被导入到此脚本中
- [config.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/config.py) 模型网络参数设置
- [dataset.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/dataset.py) 数据集读取
- [dataset_distributed.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/dataset_distributed.py) 分布式数据集读取
- [lenet.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/lenet.py) 网络结构定义
- [upload.py](https://openi.pcl.ac.cn/OpenIOSSG/MNIST_Example/src/branch/master/upload.py) 数据集上传
- 启智平台对接 `ModelArts` 和 `OBS` ，将数据集，代码，训练资源池等整合在 `启智AI协同平台` 上供开发者使用
- `ModelArts` 是华为云提供的面向开发者的一站式AI开发平台，集成了昇腾AI处理器资源池，用户可以在 `ModelArts` 下体验 `MindSpore` 框架
- `OBS` 是华为云提供的存储方式。

<!-- tabs:end -->

## 关联数据集

> 本项目将直接使用官方推荐的 `MNIST-mindspore` 数据集。

在项目页面中，依次点击 **数据集**->**关联数据集**->**关联数据集**, 搜索 `MNIST` ，选择 `MNISTData_mindspore` 官方推荐版本。

<!-- tabs:start -->

#### **创建关联**

 <img src="_media/quickstart/dataset.png" width = "800" alt="homepage" align=center />

#### **搜索公开数据集**

 <img src="_media/quickstart/dataset_npu.png" width = "800" alt="homepage" align=center />

#### **关联成功**

 <img src="_media/quickstart/dataset_finish_npu.png" width = "800" alt="homepage" align=center />

<!-- tabs:end -->

## 创建训练任务

接下来创建云脑训练任务，在项目里找到 **云脑** -> **训练任务** -> **新建训练任务**。

<!-- tabs:start -->

#### **创建训练**

 <img src="_media/quickstart/train.png" width = "800" alt="homepage" align=center />

#### **参数配置**

> [!note|label:填写以下参数|icon:fa-solid fa-list fa-bounce]
> - **算力集群** *启智集群*
> - **计算资源** *Ascend NPU*
> - **任务名称** *mnis-npu*
> - **AI引擎** *Ascend-Powered-Engine，MindSpore 1.7-c81-python3.7-euleros2.8-aarch64*
> - **启动文件** *train.py*
> - **数据集** *本项目关联 MNISTData_mindspore/MnistDataset.zip*
> - **其他配置保持默认值即可**

 <img src="_media/quickstart/train_npu_config.png" width = "800" alt="homepage" align=center />

#### **数据集选择**

 <img src="_media/quickstart/train_data_npu.png" width = "800" alt="homepage" align=center />


<!-- tabs:end -->

## 训练完成

当训练任务的状态变为 **COMPLETED**，任务训练成功。点击 `任务名称` 查看详情。

<!-- tabs:start -->

#### **配置信息**

你可以查看任务具体配置，包括镜像，数据集，资源规格，运行时间以及脚本文件。

<img src="_media/quickstart/npu_detail.png" width = "800" alt="traincreate" align=middle />

#### **日志查看**

这里是脚本文以及 `ModelArt` 中的所有输出打印，也叫做你的 `任务日志`。

<img src="_media/quickstart/npu_log.png" width = "800" alt="traindetail" align=middle />

#### **资源占用**

在这里你可以查看训练过程中的资源占用情况。

<img src="_media/quickstart/npu_res.png" width = "800" alt="traindetail" align=middle />

#### **文件下载**

在这里你可以下载在脚本中输出的所有模型文件。

<img src="_media/quickstart/npu_download.png" width = "800" alt="traindetail" align=middle />

<!-- tabs:end -->

> [!note|label:新手教程完成|icon:fa-solid fa-check fa-beat]
> 🎉 恭喜你！你已经完成了一个简单的NPU训练任务。点击右侧的下一卷查看更多功能。