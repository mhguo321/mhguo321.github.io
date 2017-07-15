---
layout: post
title: "Hello World!"
date: 2017-7-15
description: "Render latex in Github with MathJax and Jekyll"
categories: [Working]
tags: [MathJax]
mathjax:    true
---

## Before we start

It is quite popular for researchers to have a blog to write down your ideas and make some summaries from time to time.


## Build a github blog with jerkll

## Rendering latex with MathJax

在jekyll中调用$$MathJax$$ <https://www.mathjax.org> 的JavaScript就能实现LaTeX公式渲染。我测试的markdown渲染工具是kramdown,Github Flavored Markdown。

### 首先

你需要将一段script加入到_layout/post.html 里面。我是不会告诉你这段代码是从knited的html里面copy过来的(在最后面)。

{% highlight javascript %}

// mathjax 
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>

{% endhighlight %}


### 其次

需要说明的是这里引发渲染的与Rmarkdown里面的略有区别：`$公式$`在这个里面是不能用的; `$$ 公式 $$` 在Rmarkdown里面是居中的公式，而在这里是Inline公式；这里的居中另起一行的是 `\\[ 公式 \\]`；也可以用 `\\( 公式 \\)`来实现Inline公式。

### 示例

这是原始LaTeX公式语法：

```
$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\]  另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\)  Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\]  另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)\,dx $$

\\[ f(x,y,z) = 3y^2 z \left( 3 + \frac{7x+5}{1 + y^2} \right). \\]
```


这是对应生成的公式样子：

$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\] #另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\) #Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\] #另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)dx $$

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)dx $$ #Inline公式

\\[ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)dx \\]

### **炫酷吗** 右键选择 Math Settings -> zoom trigger -> click 点击就能放大公式了。
