<center><h1> Welcome to NextBlog! <h2></center>

## 开始使用

```Shell
git clone https://github.com/xuwillie/blog.git
npm i
npm run dev
```

*_src/components/layouts/Meta.tsx_, _src/lib/contents.ts_, _src/lib/feeds.tsx_里修改个人信息

## About Project

NextBlog是一个基于NextJS, MDX的下一代博客平台，以提升写作体验和扩展性为目标。

## 支持的特殊功能:

`图片和字体压缩`, `Katex数学公式渲染`, `统计阅读时间`, `Highlight代码高亮`, `文章目录`, `RSS生成`, `标题链接`, `代码标题`, `typographic`,  `自动检测http链接并生成链接`, `删除线`, `文章搜索`, `注释`等

**搜索功能** 请参考 _src/pages/search.tsx_

支持在Markdown中加入jsx语法。比如

```Javascript
import {Chart} from './snowfall.js'
export const year = 2018 #请在MDXComponents文件里创建
<Chart year={year} color="#fcb32c" />
```

例举**typographic**语法

```shell
3 <= 2;     // 3 ≤ 2

4 >= 4;     // 4 ≥ 4

5 +- 1;     // 5 ± 1

10 -+ 1;    // 10 ∓ 1

2 << 100;   // 2 ≪ 10000

999 >> 5;     // 999999 ≫ 5

arrow -> right;     // arrow → right
```

getPostsFrontMatter()中填入数字，可以限制获取文章的数目

支持remark和rehype插件

https://github.com/remarkjs/remark/blob/main/doc/plugins.md#list-of-plugins

https://github.com/rehypejs/rehype/blob/main/doc/plugins.md#list-of-plugins

## 使用方法

### 安装

```shell
npm i
```

### 运行

```
npm run dev
```

### 导出

```
npm run build
npm run export
```

因为静态导出不支持图片优化，你还需要修改两个文件

假如是Github Page，你还需要在_public_文件夹里加入`.nojekyll`屏蔽jekyll

_next.config.js_

```javascript
module.exports = {
  reactStrictMode: true,
  swcMinify: true,
};
```

_src/components/MDXComponents.tsx_

```javascript
export const MDXComponents = {
};
```

### 可以在[vercel](https://vercel.com)云部署

## 使用提示

- Markdown 里只有四种媒体信息: title, description, tags, date。tags 里的内容要用[]包住。

- 引用图片前在 next.config.js 中添加图片的域名

- 添加Highlight的CSS来代码高亮。但没有相应的 CSS。需要给 a 标签 添加 before 伪元素来支持标题链接。

- 阅读时间 功能并没有使用，你可以在 _pages/posts/[slug].tsx_ 中加入 `{frontMatter.readingTime}`

- 使用目录功能请在文章某处添加 `## Table of contents`。其它特殊用法参考 `_posts/test.mdx`


如果自用，请修改 源码中所有涉及到我的信息

## 更新日志

[v1.3.0] 支持了删除线，注释，链接转超链接。支持搜索功能，源代码请见 _src/pages/search.tsx_，参见[Demo](https://blog.wll.moe/search)

[v1.3.1] 修复bugs

[v1.3.2] 支持了目录功能，完善了文档
