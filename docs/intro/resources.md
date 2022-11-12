
#  资源说明

> 详细信息请参照[启智AI协作平台资源说明](https://git.openi.org.cn/resource_desc)

?> 点击下列任务类型即可跳转相应示例代码仓

<!-- tabs:start -->

#### **🐶启智集群**
<!-- tabs:start -->
#### **🐶GPU**
| 任务类型 | 卡类型 | 可用镜像 |  网络类型 |数据集处理方式|容器目录说明|
|---------|:-|:------:|:------:|:--------|:------------|
| 调试任务 | T4 |外部公开镜像，如dockerhub镜像；平台镜像；| 能连外网|平台解压数据集| 数据集存放路径/dataset，模型存放路径/model，代码存放路径/code |
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_PytorchExample_GPU) | V100 |	平台镜像；| 不能连外网|平台解压数据集| 训练脚本存储在 /code 中，数据集存储在 /dataset 中，预训练模型存放在运行参数 ckpt_url 中，训练输出请存储在 /model 中以供后续下载。 |
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_PytorchExample_GPU) | A100 |外部公开镜像，如dockerhub镜像；平台镜像；| 能连外网|平台解压数据集| 训练脚本存储在 /code 中，数据集存储在 /dataset 中，预训练模型存放在运行参数 ckpt_url 中，训练输出请存储在 /model 中以供后续下载。 |
| [推理任务](https://git.openi.org.cn/OpenIOSSG/MNIST_PytorchExample_GPU/src/branch/master/inference.py)	 | V100 | 平台镜像；| 不能连外网 |平台解压数据集| 数据集存储在 /dataset 中，模型文件存储在 /model 中，推理输出请存储在 /result 中以供后续下载。 |
| [评测任务](https://git.openi.org.cn/OpenIOSSG/aisafety)	 | V100 | 平台镜像；| 不能连外网 |平台解压数据集|  |
>[!warning|label:备注|icon:fa-sharp fa-solid fa-pen]
>启智集群V100不能连外网，只能使用平台的镜像，不可使用外部公开镜像，否则任务会一直处于waiting状态
#### **🐶NPU**
| 任务类型 | 卡类型 | 可用镜像 |  网络类型 |数据集处理方式|容器目录说明|
|---------|:-:|:------:|:------:|:--------|:------------|
| 调试任务 | Ascend 910 | 平台镜像；| 能连外网|平台解压数据集,但需要自己拷贝到容器中。| |
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_Example) | Ascend 910 |	平台镜像；| 能连外网|平台解压数据集,但需要自己拷贝到容器中。| 数据集位置存储在运行参数 data_url 中，预训练模型存放在运行参数 ckpt_url 中，训练输出路径存储在运行参数 train_url 中。 |
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_Example) | Ascend 910 |平台镜像；| 能连外网|平台解压数据集,但需要自己拷贝到容器中。| 数据集位置存储在运行参数 data_url 中，预训练模型存放在运行参数 ckpt_url 中，训练输出路径存储在运行参数 train_url 中。 |
| [推理任务](https://git.openi.org.cn/OpenIOSSG/aisafety)	 | Ascend 910 | 平台镜像；| 能连外网 |平台解压数据集,但需要自己拷贝到容器中。|  
<!-- tabs:end -->

#### **🐱智算集群**
<!-- tabs:start -->
#### **🐱GPU**
| 任务类型 | 卡类型 | 可用镜像 |  网络类型 |数据集处理方式|容器目录说明|
|--------------|:-:|:------:|:------:|:--------|:---------|
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_PytorchExample_GPU/src/branch/master/train_for_c2net.py) | V100 |	外部公开镜像，如dockerhub镜像；平台镜像；| 不能连外网|用户自行解压数据集| 训练脚本存储在 /tmp/code 中，数据集存储在 /tmp/dataset 中，预训练模型存放在运行参数 ckpt_url 中，训练输出请存储在 /tmp/output 中以供后续下载。 |
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_PytorchExample_GPU/src/branch/master/train_for_c2net.py) | A100 |	外部公开镜像，如dockerhub镜像；平台镜像；| 能连外网|用户自行解压数据集| 训练脚本存储在 /tmp/code 中，数据集存储在 /tmp/dataset 中，预训练模型存放在运行参数 ckpt_url 中，训练输出请存储在 /tmp/output 中以供后续下载。 |
>[!warning|label:备注|icon:fa-sharp fa-solid fa-pen]
>启智集群V100不能连外网，只能使用平台的镜像，不可使用外部公开镜像，否则任务会一直处于waiting状态
#### **🐱NPU**
| 任务类型 | 卡类型 | 可用镜像 |  网络类型 |数据集处理方式|容器目录说明|
|--------------|:-:|:------:|:------:|:---------|:---------|
| [训练任务](https://git.openi.org.cn/OpenIOSSG/MNIST_Example/src/branch/master/train_for_c2net.py) | Ascend 910 |平台镜像；| 能连外网|用户自行解压数据集| 训练脚本存储在 /tmp/code 中，数据集存储在 /训练脚本存储在 /cache/code 中，预训练模型存放在运行参数 ckpt_url 中，训练输出请存储在 /cache/output 中以供后续下载。 |
<!-- tabs:end -->

<!-- tabs:end -->