# 使用Docsify制作个人笔记博客



## 简介

​	docsify 可以快速帮你生成文档网站。不同于 GitBook、Hexo 的地方是它不会生成静态的 `.html` 文件，所有转换工作都是在运行时。如果你想要开始使用它，只需要创建一个 `index.html` 就可以开始编写文档并直接[部署在 GitHub Pages](https://docsify.js.org/#/zh-cn/deploy)。

## 快速上手

### 环境搭建		

安装node环境，node是一个javascript的运行环境，我们需要使用里面的npm这个小工具来管理项目相关的资源包。

​		node官网：[https://nodejs.org/zh-cn/](https://nodejs.org/zh-cn/)

Windows XP 只能安装 v5.x.x

安装好以后，通过以下指令验证已经安装好了。

```shell
node -v #看到正确的版本
```

为了提高下载速度，请配置taobao镜像。

```shell
npm config set registry https://registry.npm.taobao.org
```

### 创建项目

```shell
# i install安装
# g 表示全局安装
# docsify-cli 创建项目用到的一个客户端工具
npm i docsify-cli -g

# 创建项目(网站、工程)
docsify init ./docs
# 开启服务器
docsify serve docs
```

## 侧边栏

首先，您需要设置`loadSidebar`为**true**

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

创建`_sidebar.md`：

```markdown
<!-- docs/_sidebar.md -->

* [Home](/)
* [Guide](guide.md)
```

您需要创建一个`.nojekyll`in`./docs`来防止GitHub Pages忽略以下划线开头的文件。

## 目录

创建完成后`_sidebar.md`，边栏内容将根据markdown文件中的标题自动生成。

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true,
    subMaxLevel: 2
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

# 主题

有一些官方和社区制作的主题。复制[Vue](https://vuejs.org/)和[buble](https://buble.surge.sh/)网站自定义主题和[@ liril-net](https://github.com/liril-net)对黑色风格的主题的贡献。

```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/buble.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/pure.css" />
```

## 打赏

![谢谢大家](03.jpg)

