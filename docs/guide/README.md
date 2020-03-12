---
metaTitle: 配置指南 | Hexo Fluid
meta:
  - name: description
    content: Fluid 是一款 Material-Design 风格的 Hexo 博客主题。Fluid is an elegant Material-Design theme for Hexo. https://github.com/fluid-dev/hexo-theme-fluid
  - name: keywords
    content: hexo,theme,fluid,hexo主题,fluid文档,用户文档,博客,文档,博客,文章
---

# 配置指南

## 主题简介

Fluid 是基于 Hexo 的一款 Material Design 风格的主题，由 [Fluid-dev](https://github.com/fluid-dev) 负责开发与维护。

主题 GitHub: [https://github.com/fluid-dev/hexo-theme-fluid](https://github.com/fluid-dev/hexo-theme-fluid)

示例网站：

[Rook1e's blog](https://rook1e.com)

[zkqiang's blog](https://zkqiang.cn)

[吃白饭的休伯利安号](https://eatrice.top)

[上屋顶看北斗七星](https://ruru.eatrice.top)

## 关于指南

本指南仅为部分配置说明，**并不包括所有配置项**，具体配置要求请参照**主题配置**中的注释，若存在更多疑问请在 [issues](https://github.com/fluid-dev/hexo-theme-fluid/issues/new) 留言。

本指南网页是使用 [VuePress](https://vuepress.vuejs.org/) 生成。

:::tip
本指南中提到的：
- "**博客配置**" 指的 Hexo 博客目录下的 `_config.yml`
- "**主题配置**" 指的是 `theme/fluid/_config.yml`

博客与主题的 source 目录最终会合并，因此存放的文件优先选择博客的 source
:::

## 快速开始

### 搭建 Hexo 博客

如果你还没有 Hexo 博客，请按照 [Hexo 官方文档](https://hexo.io/zh-cn/docs/) 进行安装、建站。

### 获取最新版本

请优先下载 [最新 release 版本](https://github.com/fluid-dev/hexo-theme-fluid/releases)，master 分支无法保证稳定。

下载后解压到 themes 目录下并重命名为 `fluid`。

### 必要的配置

必须如下修改博客目录下的 `_config.yml`：

```yaml
theme: fluid  # 指定主题

language: zh-CN  # 指定语言，可不改
```

### 创建「关于页」

自 v1.7.0 开始，「关于页」需要手动创建：

```bash
$ hexo new page about
```

创建成功后修改 `/source/about/index.md`，添加 `layout` 属性。

修改后的文件示例如下：

```yaml
---
title: about
date: 2020-02-23 19:20:33
layout: about
---

# 这里可以写正文
支持 Markdown, HTML
```

## 全局

### 覆盖配置

:::warning
启用此功能将使原**主题配置**失效，如果不清楚此功能的用处，请不要设置
:::

覆盖配置可以使**主题配置**放置在 fluid 目录之外，避免在更新主题时丢失自定义的配置。

使用该功能必须保证 Hexo 版本不低于 3.0，因为该功能利用了 [Hexo 数据文件](https://hexo.io/zh-cn/docs/data-files.html) 功能

使用方式：

1. 进入博客目录的 source 目录下（不是主题目录的 source），创建 `_data` 目录（和 `_post` 目录同级）；
2. 在 `_data` 目录下创建 `fluid_config.yml` 文件，将 `/theme/fluid/_config.yml` 中全部内容复制到 `fluid_config.yml` 中；
3. 以后配置都在 `fluid_config.yml` 中修改，配置会在 `hexo g` 时自动覆盖。

### 静态资源

所有静态资源文件的 Url 可以通过 `fluid/_static_prefix.yml` 自定义配置，同样也支持覆盖配置，写入 `/source/_data/fluid_static_prefix.yml` 即可。

比如需要指定公共 CDN 的 JQuery 库，只需将原配置改为：

```yaml
jquery: https://cdn.staticfile.org/jquery/3.4.1/
```

### 本地搜索

- 已集成 hexo-generator-search 插件，若已安装其他搜索插件请关闭，以避免生成多余的索引文件。

- 默认在根目录生成并使用 `local-search.xml`。

### 页面顶部大图

- 图片来源

主题配置中，每个页面都有名为 `banner_img` 的属性，可以为外链的绝对链接，也可以使用相对链接。

若使用相对链接，建议将图片放置在 `/source/img/` 目录下，对应填写的图片地址为 `/img/your_img_name`。

比如 `/img/example.jpg` 对应的是存放在 `/source/img/example.jpg`。

:::tip
目录文件夹也可自定义，但必须在 source 目录下

博客与主题的 source 目录最终会合并，因此优先选择博客的 source
:::

- 高度

鉴于每个人的喜好不同，开放对页面 `banner_img` 高度的控制。

**主题配置**中，每个页面对应的 `banner_img_height` 属性，有效值为 0 - 100。100 即为全屏，个人建议 70 以上。

::: tip
每篇文章可单独设置 Banner，具体见文章页设置
:::

### 博客标题

页面左上角的博客标题，默认使用**博客配置**中的 `title`，这个配置同时控制着网页在浏览器标签中的标题。

如需单独区别设置，可在**主题配置**中设置：

```yaml
navbar:
  blog_title: 博客标题
```

### 顶部菜单

```yaml
navbar:
  menu:
    Home: /
    Archives: /archives/
    Categories: /categories/
    Tags: /tags/
    About: /about/
```
左边键是菜单名，右边值是对应链接。

默认的菜单名关联有[多语言](/guide/#多语言)，如需修改，建议改多语言配置。

新增菜单直接加入其中。

删除默认菜单，直接将右边值注释留空即可。

### 图片懒加载

```yaml
lazyload:
  enable: true
  onlypost: false
```

开启后，当图片滚动到可见范围内才会加载，可以大幅提高网页整体加载速度

`onlypost` 为 true 时，仅在文章页才使用懒加载。

### 网页统计

目前支持多种统计网站，开启后按需填入 Key 或 ID 即可。

```yaml
web_analytics:
  enable: true
  baidu:  # 百度统计的Key，参见 https://tongji.baidu.com/sc-web/10000033910/home/site/getjs?siteId=13751376 代码获取中 hm.js? 后边的字符串
  google:  # Google统计的Tracking ID，参见 https://analytics.google.com/analytics/web/
  tencent:  # 腾讯统计的H5 App id，参见 https://mta.qq.com/h5/manage/ctr_app_manage
  woyaola:  # 51.la站点统计ID，参见 https://www.51.la/user/site/index
  cnzz:  # 友盟/cnzz站点统计web_id，参见 https://web.umeng.com/main.php?c=site&a=show
```

### 多语言

不同语言会影响一些主题自带的文字。

设置语言是在**博客配置**中，需要对应 `fluid/languages/` 目录内的配置文件名:

```yaml
language: zh-CN
```

默认提供英文(en)、简体中文(zh-CN)、日文(ja)。

如果想自定义，建议单独复制一份新文件进行修改，然后指定该文件名。

### 加快网页加载

1. 对于所有用户，将各种第三方库配置公共 CDN 是最有效的方式，可以通过配置 `_static_prefix.yml` 来链接（默认已经使用 staticfile CDN，国内用户可不做改动）；

2. 如果你的域名已备案，可以使用[七牛云](https://portal.qiniu.com/signup?code=1hlwhx3ztjz2q)、腾讯云、百度云等大厂的 OSS 服务并绑定域名，将生成后的 public 目录下全部上传到 OSS，然后你不仅可以无服务器部署博客，加载速度也将无可比拟；

3. 其他自定义的图片，特别是顶部大图，建议先使用 [tinypng](https://tinypng.com) 进行压缩，然后注册私有 CDN 存放，推荐一份 [CDN 使用指南](https://www.julydate.com/post/60859300)。

### 强制全局 HTTPS

当你的域名升级到 HTTPS 后，可能之前存在部分图片等资源使用的是 HTTP，这时混用出现网页报错，造成图片无法显示。

这种情况可以启动如下配置：

```yaml
force_https: true
```

即可将所有请求强制升级为 HTTPS（如是外部图片需要本身支持 HTTPS）。

### 二级站点路径

如果你的博客部署在二级路径（如: xxx.com/blog/），需要修改**博客配置**中：

```yaml
url: http://xxx.com/blog
root: /blog/
```

### 自定义页面

如果想单独生成一个页面，步骤和创建「关于页」类似。

1. 首先用命令行创建页面：

```sh
$ hexo new page example
```

2. 创建成功后编辑博客目录下 `/source/example/index.md`：

```markdown
---
title: example
subtitle: 若不填默认是 title
---

这里写正文，支持 Markdown, HTML
```

正文默认没有 Markdown 样式，如果希望和文章相同的样式，可以加上：

```html
<div class="markdown-body">
正文
</div>
```

3. 页面的属性配置可以在**主题配置**中统一设置：

```yaml
page:
  banner_img: /img/default.png
  banner_img_height: 70
```

也可以直接在 [Front-matter](https://hexo.io/zh-cn/docs/front-matter) 里单独设置：

```markdown
---
title: example
banner_img: /img/default.png
banner_img_height: 60
---

# 这里可以写正文
```

### 自定义 JS / CSS / HTML

如果你想引入外部的 JS、CSS（比如 IconFont）或 HTML，可以通过以下**主题配置**，具体见注释：

```yaml
# 指定自定义 js 文件路径，路径是相对 source 目录
custom_js: /js/custom.js

# 指定自定义 css 文件路径，路径是相对 source 目录
custom_css: /css/custom.css

# 自定义底部 HTML 内容（位于 footer 上方），也可用于外部引入 js css 这些操作，注意不要和 post.custom 配置冲突
custom_html: '<link rel="stylesheet" href="//at.alicdn.com/t/font_1067060_qzomjdt8bmp.css">'
```

## 首页

### Slogan(打字机)

首页大图中的打字机文字，可在**主题配置**中设定是否开启：

```yaml
index:
  slogan:
    enable: true
    text: 这是一条 Slogan
```

如果 `text` 为空则按**博客配置**的 `subtitle` 显示。

相关的打字机动效设置在：

```yaml
fun_features:
  typing: # 为 subtitle 添加打字机效果
    enable: true
    typeSpeed: 70 # 打印速度
    cursorChar: "_" # 游标字符
    loop: false # 是否循环播放效果
```

### 自动摘要

:::tip
优先级: 手动摘要 > 自动摘要

如果关闭自动摘要，并且没有设置手动摘要，摘要区域空白
:::

开关自动摘要：

```yaml
index:
  auto_excerpt:
    enable: true
```

### 文章跳转方式

```yaml
index:
  post_url_target: _self
```

可选值：

1. _blank：新标签页打开
2. _self：当前标签页打开

### 文章信息

可配置隐藏包括发布时间、分类、标签。

经过测试，如果首页的文章列表中没有略缩图和摘要，标题+文章信息的显示方式会使页面过于拥挤，所以给出此项配置供喜欢首页只显示文章标题的同学使用。

```yaml
index:
  post_meta:
    date: true
    category: true
    tag: true
```

## 文章页

### 文章在首页的略缩图

文章开头 [Front-matter](https://hexo.io/zh-cn/docs/front-matter) 中配置`index_img` 属性。

```
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```

和 Banner 配置相同，`/img/example.jpg` 对应的是存放在 `/source/img/example.jpg` 目录下的图片（目录也可自定义，但必须在 source 目录下）。

也可以使用外链 Url 的绝对路径。

### 文章页顶部大图

默认显示**主题配置**中的 `post.banner_img`，如需要设置单个文章的 Banner，在 [Front-matter](https://hexo.io/zh-cn/docs/front-matter) 中指定 banner_img 属性。

本地图片存放位置同上。

```yaml
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
banner_img: /img/post_banner.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```

### 文章内容图片

本地图片存放位置同上。

```markdown
![](/img/example.jpg)
```

### 日期/字数/阅读时长/阅读数

显示在文章页大标题下的文章信息，默认这些功能都是开启的。

```yaml
post:
  meta:
    date:  # 日期
      enable: true
      format: "dddd, MMMM Do YYYY, h:mm a"  # 格式参照 ISO-8601 日期格式化
    wordcount:  # 字数统计
      enable: true
      format: "{} 字"  # 显示的文本，{}是数字的占位符（必须包含)，下同
    min2read:  # 阅读时间
      enable: true
      format: "{} 分钟"
    views:  # 阅读次数，统计基于不蒜子
      enable: true
      format: "{} 次"
```

:::tip

日期格式必须遵循 ISO-8601 规范，否则无法正常显示；

其他格式必须包括 `{}` 符号代替数字，文字可自由设置。

:::

### 手动摘要

:::tip
优先级: 手动摘要 > 自动摘要

显示字数固定 3 行，因此当屏幕宽度不足时会隐藏部分摘要。
:::

手动指定摘要，使用 `<!-- more -->` 划分文章，例：

```
这里是摘要
<!-- more -->
这里是正文
```

或者在 [Front-matter](https://hexo.io/zh-cn/docs/front-matter) 里设置 `excerpt: 这里是摘要` 字段

### 代码高亮样式

:::warning
请确保已关闭 Hexo 默认代码高亮，否则会出现异常样式
:::

关闭默认代码高亮的方式，修改**博客配置**：

```yaml
highlight:
  enable: false
```

可以修改样式的主题，在主题 congig 中指定：

```yaml
highlight:
  theme: tomorrow-night-eighties
```

主题自带了 4 种配置样式：

- github-v2
- tomorrow
- tomorrow-night
- tomorrow-night-eighties

使用更多主题的方式：

1. 进入[该链接](https://jmblog.github.io/color-themes-for-google-code-prettify/)下载 `min.css` 文件，并保存为 `文件名.min.css` 到 `/source/lib/prettify/`
2. 找到文件中的 `.prettyprint{ background: ***; ...}`，在 *** 后面加上 `!important`，例如：`.prettyprint{background:#fafbfc!important; ...}`
3. 最后**主题配置**中设置 `theme: 文件名`（不含后缀）

### 代码行号

可以在**博客配置**中开关：

```yaml
highlight:
  line_number: true
```

### 评论

开启评论需要在**主题配置**中开启并指定评论模块：

```yaml
post:
  comments:
    enable: true
    type: disqus
```

然后在下方还要设置对应评论模块的参数，比如 disqus 对应设置：

```yaml
disqus:
  shortname: fluid
```

当前支持 Valine、Disqus、Gitalk、Utterances、畅言、来必力(livere)，使用和参数设置需要自行查询各自的文档（文档地址在配置注释里）。

若需要自定义添加其他评论系统，请自行在 `fluid/layout/_partial/comments/` 目录内创建 ejs 文件，参照自带的 ejs 填入评论服务商提供的代码，再修改 `post.comments.type` 为对应文件名。

:::warning
disqus 仅为演示，实际上 disqus 已经被墙，国内用户请不要使用，推荐使用 Utterances

如果设置后评论模块没有显示，说明配置没有完成，或者配置有误出现报错（请在浏览器控制台查看具体报错）
:::

### 在线聊天（daovoice）

默认未开启此功能，需要在 https://dashboard.daovoice.io 注册并查看，然后将应用 ID 填入配置：

```yaml
daovoice:
  enable: true
  appid: ''
```


### 文章样式

文章样式使用的是 github-markdown，暂时不支持配置，细节调整可自行修改 `fluid/source/lib/github-markdown/github-markdown.min.css`

### LaTeX 数学公式

当需要使用 [LaTeX](https://www.latex-project.org/help/documentation/) 语法的数学公式时，可手动开启本功能，需要完成三步操作：

**1. 设置主题配置**

```yaml
post:
  math:
    enable: true
    specific: false
    engine: mathjax
```

`specific`: 当为 true 时，只有在文章 [Front-matter](https://hexo.io/zh-cn/docs/front-matter) 里指定 `math: true` 才会在文章页启动公式转换，以便在页面不包含公式时提高加载速度。

`engine`: 公式渲染引擎，目前支持 `mathjax` 或 `katex`。

**2. 更换 Markdown 渲染器**

由于 Hexo 默认的 Markdown 渲染器不支持复杂公式，所以必须更换渲染器。

先卸载原有渲染器：

`npm uninstall hexo-renderer-marked --save`

然后根据上方配置不同的 `engine`，推荐更换如下渲染器：

mathjax: `npm install hexo-renderer-kramed --save`

katex: `npm install @upupming/hexo-renderer-markdown-it-plus --save`

**3. 安装完成后执行 `hexo clean`**

:::warning

不可同时安装多个渲染器，如果更换公式引擎，对应渲染器也要一并更换。

如果公式没有被正确渲染，请仔细检查是否符合上面三步操作。

:::

:::tip

不同的公式引擎有不同的优缺点。

**MathJax**

优点
- 对 LaTeX 语法支持全面
- 右键点击公式有扩展功能

缺点
- 需要加载 JS，页面加载会比较慢，并且有渲染变化
- kramed 渲染器对内联公式的转义字符 `\` 支持不足

**Katex**

优点
- 没有 JS 不会影响页面加载
- 渲染器效果好 (相对 kramed 对 MathJax 的内联公式)

缺点
- 小部分 LaTeX 不支持

:::

## 归档页

除 Banner 配置外，暂无其他配置项。

## 分类页

除 Banner 配置外，暂无其他配置项。

[添加分类的方法](https://hexo.io/zh-cn/docs/front-matter)

## 标签页

可以设置词云的一些样式：

```yaml
tag:
  tagcloud:
    min_font: 15
    max_font: 30
    unit: px  # 字号单位
    start_color: "#BBBBEE"
    end_color: "#337ab7"
```

[添加标签的方法](https://hexo.io/zh-cn/docs/front-matter)

## 关于页

### 编辑关于内容

只需编辑 `fluid/pages/about.md`，再次 `hexo g` 时会自动渲染。

`about.md` 可以在**主题配置**中修改位置，建议修改到 fluid 目录之外，避免更新主题时丢失内容，比如：

```yaml
about:
  md_path: ../../source/_data/fluid_about.md  # 实际位置： blog/source/_data/fluid_about.md
```
#### 创建「关于页」

自 v1.7.0 开始，「关于页」需要手动创建：

```bash
$ hexo new page about
```

创建成功后，编辑博客目录下 `/source/about/index.md`，添加 `layout` 属性。

修改后的文件示例如下：

```yml
title: about
date: 2020-02-23 19:20:33
layout: about
---

这里写正文，支持 Markdown, HTML
```

如果原先是自写about页面，把.md文件放到 /source/about/index.md中(index.md需要自己创建)
```yml
title: about
date: 2020-02-23 19:20:33
layout: about # 需要加上layout:about
---

这里写正文，支持 Markdown, HTML
```


### 社交页图标

图标均引用自 [fontawesome](https://fontawesome.com/v5.10.0/icons?d=gallery)。只需要将属性名替换为图标名称，属性值替换为 url 即可。

## 404 页

404 页是在访问不存在的博客链接时，出现的错误提示页面。

开启此页面需要在博客的部署环境上配置：

- 如果博客部署在云服务器，需要 Nginx 配置文件设置 `error_page 404 = /404.html`；
- 如果部署在 Github Pages 上，不需要额外配置，但必须绑定顶级域名才生效；
- 其他 OSS 等平台，请参考各平台关于 404 页的配置文档，但并不是所有平台都支持跳转 Html。

## 常见问题

#### 代码高亮样式异常

- 请确认已完成上述『[关闭默认的代码高亮](/guide/#必要的配置)』步骤
- 尝试清除命令 `hexo clean && hexo g`

#### 配置无效

- 请检查配置文件是否符合 yaml 语法，如冒号后需要有空格，缩进需要 2 个空格等

## 关于更多配置

[博客 _config.yml 配置](https://hexo.io/zh-cn/docs/configuration)

[文章 Front-matter 配置](https://hexo.io/zh-cn/docs/front-matter)

## 微信交流群

[查看微信群二维码](https://github.com/fluid-dev/hexo-theme-fluid/issues/96)

## 开源协议

[MIT](https://github.com/fluid-dev/hexo-theme-fluid/blob/master/LICENSE)
