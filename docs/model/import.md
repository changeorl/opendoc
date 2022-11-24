# 在线导入

- 在模型界面点右侧上方，点击 <img src="_media/model/online-buttom.png" width = "100" alt="traindetail" align=center /> 即可跳转模型上传界面

<img src="_media/model/list-empty.png" width = "800" alt="traindetail" align=center />

> [!note|label:参数填写|icon:fa-solid fa-list fa-bounce]
> - **选择训练任务** *选择你要导入的训练任务名称*
> - **版本** *可忽视，目前平台预设默认值* `V0001`
> - **模型名称** *只能包含**大小写英文**以及**下划线***
> - **模型框架** *从列表中选择你的模型框架* `PyTorch` `TensorFlow` `Mindspore` `PaddlePaddle` `OneFlow` `MXNet` `Other`
> - **模型文件** *可多选，从训练任务的结果文件中选择你的模型文件，创建成功后**不可修改***

<img src="_media/model/online-create.png" width = "800" alt="traindetail" align=middle />

- 导入模型之后，便可在推理任务中选择你要使用的模型
- 在模型列表你可以进行删除，下载等操作

<img src="_media/model/list-online.png" width = "800" alt="traindetail" align=middle />

- 点击模型名称可进入模型信息详情页

<img src="_media/model/online-detail.png" width = "800" alt="traindetail" align=middle />