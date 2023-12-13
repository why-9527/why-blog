---
external: false
title: '我的第一篇博客文章'
date: 2023-12-13
description: '这是我 Astro 博客的第一篇文章。'
author: 'Astro 学习者'
image:
    url: 'https://docs.astro.build/assets/full-logo-light.png'
    alt: 'The full Astro logo.'
tags: ["astro", "blogging", "learning in public"]
---

# astro基本语法

发表于：2023-12-13

## 定义和使用变量

1. 在 frontmatter 中的代码栅栏之间添加以下一行 JavaScript：
```javascript
const pageTitle = '首页'
```

2. 用动态变量 {pageTitle} 替换 HTML 中静态的“Astro”标题和“关于我”标题:
```html
<html lang="zh">
  <head>
    <meta charset ="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Astro</title>
    <title>{pageTitle}</title>
  </head>
  <body>
  </body>
</html>
```

## 在 Astro 中编写 JavaScript 表达式

1. 把下面的 JavaScript 添加到 frontmatter 的代码栅栏之间:
```javascript
const identity = {
  firstName: "莎拉",
  country: "加拿大",
  occupation: "技术撰稿人",
  hobbies: ["摄影", "观鸟", "棒球"],
};

const skills = ["HTML", "CSS", "JavaScript", "React", "Astro", "Writing Docs"];
```

2. 然后，在你的 HTML 模板现有的内容下面添加以下代码：
```html
<p>以下是关于我的几个事实：</p>
<ul>
  <li>我的名字是{identity.firstName}.</li>
  <li>我住在{identity.country}。我的职业是{identity.occupation}。</li>
  {identity.hobbies.length >= 2 &&
    <li>我的两个习惯：{identity.hobbies[0]}和{identity.hobbies[1]}</li>
  }
</ul>
<p>我的技能是：</p>
<ul>
  {skills.map((skill) => <li>{skill}</li>)}
</ul>
```

## 条件渲染元素

也可以使用脚本变量来选择是否渲染你的 HTML <body>内容中的个别元素。

1. 在 frontmatter 脚本中添加以下几行来定义变量：
```javascript
const happy = true;
const finished = false;
const goal = 3;
```

2. 在现有的段落下面添加以下几行。
然后，就能条件渲染元素：
```html
{happy && <p>我非常乐意学习 Astro！</p>}
{finished && <p>我完成了这节教程！</p>}
{goal === 3 ? <p>我的目标是在三天内完成。</p> : <p>我的目标不是 3 天。</p>}
```

## 为单页面应用样式

使用 Astro 的 style 标签，可以为页面上的元素设置样式。还可以通过给这些标签添加属性和指令，获得更多的样式设置方式。

1. 给想要设置样式的html元素添加一个类名:
```html
<p>我的技能：</p>
<ul>
  {skills.map((skill) => <li class="skill">{skill}</li>)}
</ul>
```

2. 在style标签中用css选择器选择类名并设置css样式即可应用该样式:
```css
.skill {
    color: green;
    font-weight: bold;
}
```
此时页面上该元素就设置了字体颜色为绿色和字体加粗的样式。

## 使用css变量

Astro 的 style 标签还可以使用 define:vars={ {...} } 指令引用 frontmatter 中的任何变量。可以在代码围栏中定义变量，然后在样式标签中将其用作 CSS 变量使用。

1. 先在 frontmatter 中声明一css想使用的变量:
```javascript
const skillColor = "navy"
```

2. 在下面的已有的 style 标签中更新代码，先定义 skillColor 变量，然后在双括号中使用它作为 CSS 变量：
```css
<style define:vars={{skillColor}}>
  h1 {
    color: purple;
    font-size: 4rem;
  }
  .skill {
    color: green;
    color: var(--skillColor);
    font-weight: bold;
  }
</style>
```
