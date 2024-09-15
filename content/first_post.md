+++
title = "第一篇博客"
date = 2024-09-15

[taxonomies]
categories = ["博客"]
tags = ["私人"]
+++

测试时使用

<!-- more -->

第二段，中间有注释！

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

- 一级列表
    - 二级列表
        - 三级列表

<!--  测试Latex代码
行内实例
{{ katex(body="\KaTeX") }}
居中写法
{% katex(block=true) %}\KaTeX{% end %}
简写内联写法
\\( \KaTeX\ \\)
简写居中写法
\\[ \KaTeX \\]
-->

{{ katex(body="\KaTeX") }}
{% katex(block=true) %}
\KaTeX
{% end %}

\\( \KaTeX \\)
\\[ \KaTeX \\]


我们的代码 \\( \KaTeX \\) 生生世世
我们的代码 \\( \sqrt{a^2 + b^2} \\) 生生世世

\\( \\int u \frac{\mathrm{d}v}{\mathrm{d}x}\,\mathrm{d}x=uv-\int \frac{\mathrm{d}u}{\mathrm{d}x}v\,\mathrm{d}x  \\) 

$\int u \frac{\mathrm{d}v}{\mathrm{d}x}\,\mathrm{d}x=uv-\int \frac{\mathrm{d}u}{\mathrm{d}x}v\,\mathrm{d}x$



```plantuml
你好 -> 中文支持如何 : 看起来还是可以的
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response
```
