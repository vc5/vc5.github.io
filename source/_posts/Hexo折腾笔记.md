---
title: Hexo折腾笔记
date: 2016-05-08 17:00:29
tags: Hexo
---
+ 多标签的写法
```yaml
tags:
- foo
- bar
```
# Hexo环境配置
`npm install -g hexo-cli`

# Hexo更新
```bash
//以下命令分别执行即可
npm install -g npm-check     //安装npm-check
npm-check                    //查看系统插件是否需要升级
npm install -g npm-upgrade   //安装npm-upgrade
npm-upgrade        //更新package.json
//在执行npm-upgrade命令后会要求输入yes或者no，直接输入Yes或Y即可
npm update -g      //更新全局插件
npm update --save  //更新系统插件

hexo clean #清理hexo数据并重新生成页面并部署
hexo g -s
hexo d
```

# 主题配置
将next的配置文件放在hexo site的配置文件里目前来说是最优配置了
+ [Hexo博客SEO优化](http://www.arao.me/2015/hexo-next-theme-optimize-seo/)
+ [为绑定域名的 GitHub Pages 启用 HTTPS](https://mazhuang.org/2016/05/21/enable-https-for-github-pages/)