
> [!tip|label:提示|icon:fa-solid fa-bell fa-beat]
> - 你将会在这一步提交代码文件。
> - 如果你的 `模型定义` 和 `训练脚本` 在不同的代码文件里，请务必将他们全部提交。
> - `数据集` 将储存到别的位置，请勿将 `数据集` 上传到代码仓。

- 在项目中的 **代码** 页面，右上角有 **蓝色按钮** 和 **链接地址**，他们是两种不同的提交代码方式
    - 你可以使用蓝色按钮的网页UI，通过 **在线创建** 或 **手动上传文件** 来提交代码
    - 你也可以使用 **http** 或 **ssh** 地址 通过 **Git** 来提交代码

<img src="_media/quickstart/repo_home.png" width = "800" alt="homepage" align=center />


## 网页提交

### 在线创建

- 点击 `新建文件` 按钮，输入代码及文件名称（带后缀）
- 点击 `提交变更` 提交代码文件

<img src="_media/quickstart/repo_code.png" width = "800" alt="homepage" align=center />

 <img src="_media/quickstart/repo_pr.png" width = "800" alt="homepage" align=center />

### 上传提交

- 点击 `上传文件` 按钮，然后点击`虚线区域`选择本地文件，或者将文件直接`拖拽`到区域内
- 你可以在仓库名后面给文件添加`二级目录`
- 点击 `提交变更` 提交代码文件

<img src="_media/repo/repoupload.png" width = "800" alt="homepage" align=center />


## Git提交

### 安装Git



<!-- tabs:start -->

#### **Windows**

> 下面的安装指引参照了[Git官方地址](https://git-scm.com/download/win)

- 请根据你的Windows版本选择下方下载链接
    - [64-位 Git Windows安装](https://github.com/git-for-windows/git/releases/download/v2.38.1.windows.1/Git-2.38.1-64-bit.exe)
    - [32-位 Git Windows安装](https://github.com/git-for-windows/git/releases/download/v2.38.1.windows.1/Git-2.38.1-32-bit.exe)

<img src="_media/repo/gitinstallnoedge.png" width = "400" alt="homepage" align=center />

- 下载完成后，根据安装程序指引完成安装。使用`Git Bash.exe`（下左）命令行进行Git操作
- 你也可以使用其他的命令行工具，如 `Windows Powershell`（下右），详情参照[微软官方文档](https://learn.microsoft.com/zh-cn/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.2) 

<img src="_media/repo/gitbash.png" width = "400" alt="homepage" align=center />

<img src="_media/repo/gitpowershell.png" width = "400" alt="homepage" align=center />


#### **Mac**

> 下面的安装指引参照了[Git官方地址](https://git-scm.com/download/win)

#### Homebrew
请先在你的Mac上面安装 [homebrew](https://brew.sh/)，然后在命令行输入:
```
$ brew install git
```

#### MacPorts
请先在你的Mac上面安装 [MacPorts](https://www.macports.org/)，然后在命令行输入:
```
$ sudo port install git
```

#### Xcode
Apple 将 **Git** 自动安装绑定在了 [Xcode](https://developer.apple.com/xcode/).

#### Binary installer
Tim Harper 提供了一个 **Git** 安装程序 [installer](https://sourceforge.net/projects/git-osx-installer/) 最近版本为 **2.33.0**，大约发布于一年前的2021-08-30

#### Building from Source
如果你喜欢从源码安装，你可以在这里找到压缩包 [kernel.org](https://mirrors.edge.kernel.org/pub/software/scm/git/) 最新版本为 **2.38.1**.

#### Installing git-gui
如果你想要安装 **Git交互程序** [git-gui](https://git-scm.com/docs/git-gui/) 和 **Git浏览器** [gitk](https://git-scm.com/docs/gitk/)，你可以使用[homebrew](https://brew.sh/)来安装
```
$ brew install git-gui
```

#### 安装成功

打开 **终端Terminal**，输入 `git` 指令，如有以下输出，则系统已安装 **Git**

<img src="_media/repo/gitmac.png" width = "400" alt="homepage" align=center />

<!-- tabs:end -->

### 克隆仓库 & 提交代码

- 使用命令行 **Git** 克隆/提交代码需要设置权限。
- 你可以在代码仓文件列表的右上方找到 **项目链接**。通常有两种方式克隆代码仓，`https` 和 `ssh`。
- *推荐在Mac上使用[iTerm2](https://iterm2.com/)， Windows上使用[Windows Terminal](https://learn.microsoft.com/en-us/windows/terminal/install)*

<!-- tabs:start -->

#### **HTTPS**

- 使用 `https` 地址克隆项目，操作 `git pull/push` 到远程仓库的时候需要输入账号密码
- 你可以输入 `git config --global credential.helper store` 保存登录信息，首次输入后，便不再需要输入账号密码

```shell
#克隆代码仓
$ git clone https://git.openi.org.cn/chenzh/quickstart.git
$ cd quickstart

#提交代码
$ git add .
$ git commit -m 'update'
$ git push
username: chenzh
password: 🔑

#保存账户密码
$ git config --global credential.helper store
```

#### **SSH**

使用 `ssh` 链接克隆代码仓需要 **在本地生成ssh密钥** -> **配置ssh密钥** -> **添加ssh密钥到你的启智账号**。

具体步骤请参考[Github SSH Gnerating](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)。

配置好密钥后，直接使用仓库`ssh`链接拉取/提交代码即可，无需额外验证信息

```shell
#克隆代码仓
$ git clone git@git.openi.org.cn:chenzh/quickstart.git
$ cd quickstart

#提交代码
$ git add .
$ git commit -m 'update'
$ git push
```
<!-- tabs:end -->

> 更多Git操作请参考[Git教程](https://gitee.com/all-about-git)