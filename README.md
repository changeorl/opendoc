# opendoc

本文档基于 [Docsify](https://docsify.js.org/#/?id=docsify) 框架构建

- 文档内容由 **Markdown** 格式编辑，放置于 **/docs/二级目录** 下
- 侧边栏菜单可在 **/docs/_sidebar.md** 中修改
- 文档页面元素，插件可在 **/docs/index.html** 中配置
- 文档首页为 **/docs/README.md**

### 运行本地服务

安装 docsify

```shell
npm i docsify-cli -g
```

克隆本代码仓

```shell
git clone https://openi.pcl.ac.cn/chenzh/opendoc.git
```

启动本地服务，在浏览器输入 `http://localhost:3000` 查看

```shell
docsify serve ./docs
```