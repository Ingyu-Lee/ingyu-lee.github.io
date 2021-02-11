---
layout: posts
title:  "Welcome to Jekyll!"
page.toc: true
toc_sticky: true
use_math: true
excerpt: "A unique line of text to describe this post that will display in an archive listing and meta description with SEO benefits."
tags:
  - test0
  - test1
category: testCategory
---
<h1>{{ page.tags }}</h1>

{% include toc.html %}

**Hello world**, this is my first Jekyll blog post.

I hope you like it!

<!-- # this is a H1 -->

<!-- aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaahowlongdoesitgoesaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa -->

## This is a H2

... which is shown in the screenshot below:
![My helpful screenshot](/assets/screenshot.png)

<img src="/assets/screenshot.png" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck">
<img src="/assets/screenshot.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck">

<!-- # This is a H1_1 -->
This formula \[f(x) = x^2\] is an example.

## This is a H2_1
\[f(x)\]

test text:

\\[
\lim_{x\to 0}{\frac{e^x-1}{2x}}
\overset{\left[\frac{0}{0}\right]}{\underset{\mathrm{H}}{=}}
\lim_{x\to 0}{\frac{e^x}{2}}={\frac{1}{2}}
\\]

test text

## This is a H2_2
this is a normal paragraph

    this is a code block

return to normal paragraph

*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

~~cancelline~~
