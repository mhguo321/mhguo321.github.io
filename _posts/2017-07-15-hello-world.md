---
layout: post
title: "Hello World!"
date: 2017-7-15
description: "Render latex in Github with MathJax and Jekyll"
categories: [Working]
tags: [MathJax]
mathjax:    true
---

# Hello world!

This is the first blog. Some basic functions will be added and tested here one by one.

### MathJax Latex


This is a latex equation $$ \int_a^b f(x)\,dx $$. Is it OK?

Sometimes, we need to write a latex equation in the middle of a new line, like this:

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)dx $$

Is it OK?



### Highlight codes

matlab example:

```Matlab
some code
some more code
```

Is it OK?
---

javascript example:

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

plain example

```
$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\]  另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\)  Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\]  另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)\,dx $$

\\[ f(x,y,z) = 3y^2 z \left( 3 + \frac{7x+5}{1 + y^2} \right). \\]
```

