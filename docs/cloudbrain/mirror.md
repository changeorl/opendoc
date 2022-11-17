# 镜像

## 平台官方镜像

- 在 `导航栏`->`探索`->`云脑镜像` 下，你可以查看所有公开镜像，你创建的镜像，和收藏的镜像
- 勾选 仅显示平台推荐 选项可以看到所有启智AI协作平台官方推荐镜像，[快速查看平台镜像](https://openi.pcl.ac.cn/explore/images)

<img src="_media/cloudbrain/mirror/mirror_list.png" width = "800" alt="traindetail" align=middle />

## 创建镜像

>[!note|label:提示|icon:fa-solid fa-lightbulb fa-bounce]
> - 目前只有GPU环境支持创建镜像，NPU环境只能使用平台提供 `Tensorflow` 与 `Mindspore` 两种镜像
> - `/dataset` 下的数据集文件也将一并提交到新镜像，但是 `/code` 与 `/model` 下的文件不会

- 你可以定制你自己的镜像，根据你的项目配置环境以及第三方包
- 打开一个调试任务时，在调试任务里安装你所需要的的第三方包，不要关闭或停止你的调试任务
- 来到调试任务列表，在调试任务为 RUNNING 状态的时候，点击更多下拉菜单，点击提交镜像
- 为你的镜像设置名字，描述，以及标签
- 选择公开镜像将使其他用户也能搜索并使用你的镜像

<img src="_media/cloudbrain/mirror/mirror_submit.png" width = "800" alt="traindetail" align=middle />

<img src="_media/cloudbrain/mirror/mirror_create.png" width = "800" alt="traindetail" align=middle />

- 在你的镜像列表，下拉更多菜单可修改镜像名称，描述信息以及标签

<img src="_media/cloudbrain/mirror/mirror_modify.png" width = "800" alt="traindetail" align=middle />