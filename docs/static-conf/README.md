# 静态配置

以下是 `_static_prefix.yml` 的公共 CDN 配置，国内用户可以参考，对于 GitHub Pages 部署的用户提高网页加载速度格外有效。

仅适用于 v1.6.1 版本，后续版本可能会有变化，请对照原文件是否一致。

```yaml
#---------------------------
# 第三方库
# Third-party library
#---------------------------

anchor: https://cdn.staticfile.org/anchor-js/4.2.0/

font_awesome: https://cdn.staticfile.org/font-awesome/5.10.2/

github_markdown: https://cdn.staticfile.org/github-markdown-css/3.0.1/

jquery: https://cdn.staticfile.org/jquery/3.4.1/

bootstrap: https://cdn.staticfile.org/twitter-bootstrap/4.3.1/

mdbootstrap: https://cdn.staticfile.org/mdbootstrap/4.8.9/

popper: https://cdn.staticfile.org/popper.js/1.15.0/umd/

nprogress: https://cdn.staticfile.org/nprogress/0.2.0/

prettify: https://cdn.staticfile.org/prettify/r298/

# 这个没有公共 CDN，建议自己找个 CDN 存放并链接过来
prettify_theme: /lib/prettify

tocbot: https://cdn.staticfile.org/tocbot/4.8.0/

typed: https://cdn.staticfile.org/typed.js/2.0.10/

fancybox: https://cdn.staticfile.org/fancybox/3.5.7/

smooth_scroll: https://cdn.staticfile.org/smooth-scroll/16.1.0/

mathjax: https://cdn.staticfile.org/mathjax/2.7.6/

katex: https://cdn.staticfile.org/KaTeX/0.11.1/
```