# vuepress-theme-journal

一个移植自 [hexo-theme-journal](https://github.com/SumiMakito/hexo-theme-journal/) 的 VuePress 主题，基于 [vuepress-theme-blog](https://github.com/vuepressjs/vuepress-theme-blog) 进行开发。

注意，为了优雅，文章放在 post 目录，而非传统的 _post 目录下。

```sh
yarn add hexo-theme-journal
```

- 示例项目（含 config.js）参见[这里](https://github.com/rikumi/rikumi.github.io/tree/src/)；
- 使用文档参见 [vuepress-theme-blog 的文档](https://vuepress-theme-blog.ulivz.com)；
- 已针对 Disqus 进行优化，对于文章，将采用页面路径作为 disqus identifier；对于非 post 目录下的静态页面，将采用带 .html 的页面路径作为 disqus identifier。这将有助于从 Hexo 迁移过来；
- 暂不支持 Tag 页面，当我个人对此有需求时，将会加上。