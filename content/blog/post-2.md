---
external: false
title: '我的第二篇博客文章'
date: 2023-12-13
description: '这是我 Astro 博客的第二篇文章。'
author: 'Astro 学习者'
---

# 应用全局样式

发表于：2023-12-13

## 添加全局样式

 Astro 的 style 标签默认是有作用域的，意味着它只能影响到当前文件中的元素。

有几种方法可以在 Astro 中定义全局样式，但在此，你将创建并引入global.css文件到你的所有页面。样式文件和 style 标签的组合使你可以控制全局的样式，并可以将某些特定样式准确地应用到你想要的位置。

1. 在src/styles/global.css创建一个新文件（默认全局样式放在这个文件里面）。

2. 在 global.css 中写入全局样式:
```css
html {
  background-color: #f1f5f9;
  font-family: sans-serif;
}

body {
  margin: 0 auto;
  width: 100%;
  max-width: 80ch;
  padding: 1rem;
  line-height: 1.5;
}

* {
  box-sizing: border-box;
}

h1 {
  margin: 1rem 0;
  font-size: 2.5rem;
}
```

3. 在想要使用全局样式的 astro 文件的 frontmatter 中使用 import 引入全局样式:
```css
import '../styles/global.css';
```

**注意：当全局样式和astro的style标签中的局部样式冲突时，局部样式会覆盖全局样式**
