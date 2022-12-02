# 本地上传

> 不同于在线任务导入，本地模型需要先创建模型，再上传模型文件

- 在模型界面点右侧上方，点击 <img src="_media/model/local-buttom.png" width = "100" alt="traindetail" align=center /> 即可跳转模型上传界面

> [!note|label:参数填写|icon:fa-solid fa-list fa-bounce]
> - **可用集群** `CPU/GPU` *或者* `Ascend NPU` *选择模型类型*
> - **模型名称** *只能包含**大小写英文**以及**下划线***
> - **模型框架** *从列表中选择你的模型框架* `PyTorch` `TensorFlow` `Mindspore` `PaddlePaddle` `OneFlow` `MXNet` `Other`

<img src="_media/model/local-create.png" width = "800" alt="traindetail" align=middle />

- 点击创建之后，将会来到模型文件上传界面，在这里点击选择或者拖拽文件上传
- 若在此步骤取消，模型依然会创建成功，你可以稍后在模型详情页继续上传文件

<img src="_media/model/local-upload.png" width = "800" alt="traindetail" align=middle />

<img src="_media/model/list-local.png" width = "800" alt="traindetail" align=middle />

- 点击模型名称即可进入模型详情界面
- 在此你可以删除或者继续上传本地模型文件

<img src="_media/model/local-detail.png" width = "800" alt="traindetail" align=middle />