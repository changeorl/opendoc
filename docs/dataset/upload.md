# 上传数据

> 在启智平台上，你可以在项目下创建数据集，再将数据文件打包上传。

## 初始界面

点击 `创建数据集`，为项目创建数据集。

- 项目与数据集是绑定的，每个项目只能创建唯一数据集，但是你可以在数据集里上传多个打包文件。
- 数据集与项目绑定，一旦创建便无法单独删除。你可以通过删除打包文件与修改数据集来更新你的数据集。


<img src="_media/dataset/uploadhome.png" width = "800" alt="traindetail" align=middle />

## 创建数据集

创建详情界面，数据集名称只能包括 `字母，数字，_和-`。\
创建成功后，点击`修改`即可返回详情界面修改数据集名称，说明，以及标签。

<img src="_media/dataset/uploadcreate.png" width = "800" alt="traindetail" align=middle />

- 在数据集界面点击蓝色`上传`按钮，跳转到上传文件界面

<img src="_media/dataset/uploadempty.png" width = "800" alt="traindetail" align=middle />

## 文件上传

- 请注意，打包文件的格式必须为 `.zip` `.tar` `.gz`
- 需要选择你数据运行环境 `CPU/GPU` 或 `NPU` 
- 然后点击`虚线区域`选择本地文件，或者将文件直接`拖拽`到区域内
- 点击绿色`上传`按钮开始上传，上传成功将自动跳转到数据集界面

<img src="_media/dataset/uploadload.png" width = "800" alt="traindetail" align=middle />

- 某个文件上传失败，不会影响其他文件

<img src="_media/dataset/uploadfail.png" width = "800" alt="traindetail" align=middle />

## 上传成功

- 上传成功的文件会出现在数据集列表中
- 点击`文件名`或`下载`可下载打包文件
- 平台会自动解压打包文件，点击`预览`可查看

<img src="_media/dataset/uploadlist.png" width = "800" alt="traindetail" align=middle />

<img src="_media/dataset/uploadpreview.png" width = "800" alt="traindetail" align=middle />
