# 调试任务

> [!tip|icon:fa-solid fa-bars fa-bounce]
> - 在项目页面的 `云脑`->`调试任务`->`新建调试任务` 可以开启调试任务
> - 调试任务将启动 `镜像容器`，GPU任务与NPU任务的容器有着不同的层级构造
> - 调试任务将会在选择的镜像容器里提供 `Jupyter Lab` 控制台，你可以使用控制台里的 `Terminal` 管理镜像中的文件与Python库
> - 启动调试任务时，当状态由 `WAITING` 转为 `RUNNING` 后，需继续等待3-5分再点击 `调试` 跳转到控制台，提前点击 `调试` 会看到 `502错误界面`， 请退出并耐心等待

<!-- tabs:start -->

#### **GPU**

#### GPU新建
在项目页面的 `云脑`->`调试任务`->`新建调试任务` 开启调试任务，并填写下列配置信息
- 计算资源: 选择 `CPU/GPU`
- 任务名称：只能包含 `小写字母，数字，以及下划线`
- 镜像：可以选择任意 `平台镜像` 或者使用 `外部镜像`，粘贴镜像链接到框内即可
- 数据集：点击 `选择数据集` 即可选择数据集
    - 数据集可 `多选` ，在弹窗中选中多个数据集即可
    - 你可以使用 `项目数据集` 或 `关联数据集`，你也可以在调试代码里下载 `外部数据集`
    - 此选项可以为 `空白` ，即不使用数据集
- 资源规格：任意选择你想要的资源规格即可

<img src="_media/dataset/usagecreate.png" width = "800" alt="traindetail" align=middle />

#### GPU调试控制台
调试任务 `Jupyter Lab` 控制台 *如果你有使用 Jupyter Notebook/Lab 的经验，你可以跳过以下部分*
- 点击左上角蓝色 `+按钮` 可以新建Tab标签页
- 在新标签页，你可以新建 `.ipynb` Notebook代码文件来进行调试代码
- 你也可以在 `Terminal` 里直接运行代码仓文件
- 在 `Terminal` 中使用 `pip` 进行 `Python库` 的安装与管理

<img src="_media/dataset/usagelab.png" width = "800" alt="traindetail" align=middle />

#### 调试环境代码与数据集位置

- `/workspace` 打开 `Terminal` 时的默认目录，可输入 `cd ..` 返回根目录
- `/code` 下已经自动拉取了本项目代码仓
- `/data` 下可以找到创建时选取的数据集，并且已解压
- `/model` 若有需要下载的输出文件可放在此目录下，在调试任务列表下拉 `更多`->`模型下载` 即可下载 

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
│   └── .
├── ...
├── ...    
└── workspace/
    └── .
```



#### **NPU**

#### NPU 新建

#### NPU 控制台

#### NPU Notebook

#### NPU Terminal

<!-- tabs:end -->