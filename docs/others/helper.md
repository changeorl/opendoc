> 想帮助改进本文档？请阅读以下内容

## 准备工作

本文档是基于 `Docsify` 构建的，一款小巧轻量的 `Markdown` 静态文档生成框架 <br>

如果你想要在你的电脑上启动本地静态网页，你需要拉取 `本文档代码仓`，以及安装 `Docsify CLI启动器`

```shell
# git clone https://openi.pcl.ac.cn/chenzh/opendoc.git
# npm i docsify-cli -g
```

>[!note|label:安装须知|icon:fa-solid fa-download fa-bounce]
> - 安装 `Docsify CLI启动器` 需要使用到 `Node.js` 中的 `npm` 指令
> - `npm` 是随同 `Node.js` 一起安装的包管理工具，你可以使用 `npm -v` 来查看其是否安装在你的电脑上
> - 若你的电脑未安装 `Node.js`，请移步至 [Node.js官方下载地址](https://nodejs.org/zh-cn/download/) 下载安装

来到代码仓目录，输入下列指令启动本地服务后，在浏览器打开 http://localhost:3000 即可看到本地运行的文档

```shell
# cd opendoc
# docsify serve ./docs

Serving /你的本地电脑目录/opendoc/docs now. 
Listening at http://localhost:3000
```

## 文档结构

```text
.
├── README.md
└── docs/
    ├── .nojekyll
    ├── _sidebar.md
    ├── index.html
    ├── README.md
    ├── _media/
    │   ├── repo/
    │   │   ├── pic.png
    │   │   └── ...
    │   └── ...
    ├── repo/
    │   ├── create.md
    │   └── ...
    └── ...
```
- 文档工程目录为 `./docs`
- 注意在根目录下的 `README.md` 为文档代码仓描述文件，而`./docs/README.md` 文件为文档首页
- `index.html` 为文档的网页配置界面，你可以在这里更改 `文档页面设置`，配置 `文档渲染插件`，修改网页 `css` 样式等
- `_sidebar.md` 内可编辑文档侧边栏菜单
- `_media/` 文件夹下存放文档内使用的图片素材
- 其余文件，如上示例中 `repo/` 为文档各层级目录，里面存放的每个文件如 `create.md` 为单独文档页面

## 修改侧边栏

- 在 `_sidebar.md` 中编辑侧边栏菜单，格式为 `Markdown列表`结构
- 加入新文档页使用 `Markdown超链接`，在中括号中写入侧边栏显示名称，在小括号内写入 `.md` 文件路径即可

```markdown
<!-- docs/_sidebar.md -->

- 数据集
    - [上传数据](dataset/upload.md)
    - [关联数据](dataset/link.md)
```

## 修改文档

- 在 `_sidebar.md` 中找到文档路径，修改 `.md` 文档即可，建议遵循如下规则
    - 避免编写大段文字内容，尽量使用简短的文字说明，可以使用 `列表结构` 增加可读性
    - 文档内的 `## 二级标题` 会在侧边栏展开，点击可快速跳转到相应部分
    - 使用代码高亮功能 `Highlight` 关键字
    - 你也可以在文档里使用`html`语法来添加网页元素

## 插入图片

- 本文档使用嵌入html语法插入图片，并支持点击放大
    - 请将图片放入 `_media/` 文件夹下
    - 浏览器内截图建议使用 `chrome` 中的 `Standardized Screenshot` 插件，可以为图片边缘增加阴影效果
    - 复制下列范例代码到 `.md` 文档中，修改 `src` 中图片路径即可插入，其他参数可保持不变

```markdown
<img src="_media/home.png" width = "600" alt="homepage" align=center/>
```

<img src="_media/home.png" width = "800" alt="homepage" align=center />

## 插入提示框

- 本文档中使用了提示框插件，使用范例如下

```markdown
>[!note]
> 这是提示框规范样式，内部也支持 `Markdown` 语法
```

>[!note]
> 这是提示框规范样式，内部也支持 `Markdown` 语法

- 你可以自定义提示框来展示其他信息，注意参数分割符 `|` 为英文符号且前后不能有空格

```markdown
>[!note|label:自定义名称|icon:fa-solid fa-wand-magic-sparkles]
> 这是自定义了 `名称` 和 `图标` 的提示框
```

>[!note|label:自定义名称|icon:fa-solid fa-wand-magic-sparkles]
> 这是自定了 `名称` 和 `图标` 的提示框

<br>

| 参数名称 | 取值说明 |
| --------------- | ---- |
| label  | `提示`(default) 或 `自定义中英文或空格`，不能有符号 |
| icon  | `fa-solid fa-lightbulb fa-bounce` (default) 或 使用其他 `FontAwesome6` 图标 |

*更多定制的内容，可以访问 [docsify-plugin-flexible-alerts](https://github.com/fzankl/docsify-plugin-flexible-alerts) 和 [FontAwesome6](https://fa6.dashgame.com/) 查看详情*

## 使用Tab分类框

本文档中使用了 `Tab` 框进行内容分类，例如`GPU`与`NPU`，使用范例如下

```markdown
<!-- tabs:start -->

#### **GPU**

GPU使用实例

#### **NPU**

NPU使用实例

<!-- tabs:end -->

```

<!-- tabs:start -->

#### **GPU**

GPU使用实例

#### **NPU**

NPU使用实例

<!-- tabs:end -->

## 其他

- 可以在 `css/vue.css` 里修改网页样式
- 若想使用其他插件，需将插件源码文件下载到`docs/js/` 目录下，使用本地路径加载 
    - *[Docsify插件列表](https://docsify.js.org/#/awesome?id=plugins)*
