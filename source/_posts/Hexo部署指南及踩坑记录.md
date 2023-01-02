---
title: Hexo部署指南及踩坑记录
date: 2023-01-02 17:42:12
categories: 教程
tags: Web
---

# 为什么选择 Hexo

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

从上面的介绍我们可以注意到这个东西：

> 即可利用靓丽的主题生成静态网页。

也就是说，我们可以很容易的将基于 Hexo 搭建的博客系统运行在 Github Pages 上

这意味着：能白嫖！能白嫖！（参见：[《如何用最少的钱开一个网站？》][1]）

# 初始化 Hexo

您需要先准备以下环境：

1. [Node.js][2]（>=12）
2. Git

使用 npm 安装 hexo

```bash
# Windows
npm install -g hexo-cli
# Linux
sudo npm install -g hexo-cli
```

之后，使用 `hexo init` 命令初始化您的博客

```bash
hexo init [目录名称]
```

> 如果不传入`[目录名称]`参数，hexo-cli 在当前目录下初始化博客

创建完成后，目标目录看起来像这样

```text
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

您需要按自己需求修改 hexo 站点配置（`_config.yml`）文件，参考 [配置 | Hexo][3]

一般来说，您只需要修改以下配置项：

1. `title`：站点标题
2. `subtitle`：站点副标题
3. `author`：作者名，也就是您的名字
4. `language`：语言，可直接设为`zh-CN`
5. `timezone`：时区，可直接设为`Asia/Shanghai`
6. `url`：站点网址

{% colorpanel info 测试您的配置 %}

您可以在站点根目录使用`hexo server`指令启动 hexo 自带的服务器，之后使用浏览器访问 `127.0.0.1:4000` 查看您的更改

{% endcolorpanel %}

# 修改主题

您可以前往[这里][4]选择您的主题

部分主题可以直接用 npm 安装

部分主题需要您下载压缩包并解压到`themes`目录下

随后，修改 hexo 站点配置，将`them`项改为您的主题

> 部分主题可能会拥有自己的配置文件，主题配置在博客根目录下的`_config.主题名.yml`内（可能需要您手动复制/创建），具体参见主题的 README.md 文件

# 部署到 github

具体部署方法详见[在 Github 上部署 Hexo][5]

{% colorpanel warning 注意事项 %}

如果您是使用 git 创建仓库或您修改了设置，您的仓库的默认分支名称可能为`master`或其他而不是`main`

请修推送改指令为：

```bash
git push -u origin 您分支的名称，如master
```

和`.github/workflows/pages.yml`的`on.push.branches`项

```yaml

on:
  push:
    branches:
      - 您的分支名称，如master # default branch
```

在每次推送后，github 会自动执行编译任务

> 如果您的仓库名不是*用户名.github.io*，默认请在`用户名.github.io/仓库名`访问您的博客

{% endcolorpanel %}



# 配置评论

因为 Hexo 是静态，所以 Hexo 默认不带有评论

可以使用`gitalk`、`gitment`等将issue作为您博客的评论，具体参考其项目主页

但是此处有大坑需要注意

上文提到的两个评论插件会要求您申请 OAuth APP以登录github帐号，进入 `Strring>Developer strring` 创建

- `Application name`：您的站点名
- `Homepage URL`：您的博客首页URL
- `Authorization callback URL`：回调URL

回调URL 需要填您的博客所使用的协议（一般是`https://`）+所在的域名（一般不含二级域名）

比如本博客的主页地址为：`https://blog.thisisxd.top/index.html`

则 回调URL 为：`https://thisisxd.top`

如果 回调URL 错误，登录就会返回`error`

> 具体多试试，不成功可以在下面发评论问



  [1]: https://blog.thisisxd.top/202209/%E5%A6%82%E4%BD%95%E7%94%A8%E6%9C%80%E5%B0%91%E7%9A%84%E9%92%B1%E5%BC%80%E4%B8%80%E4%B8%AA%E7%BD%91%E7%AB%99%EF%BC%9F/
  [2]: https://nodejs.org
  [3]: https://hexo.io/zh-cn/docs/configuration
  [4]: https://hexo.io/themes/
  [5]: https://hexo.io/zh-cn/docs/github-pages


