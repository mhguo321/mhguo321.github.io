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

此为第一篇，本文将用于测试一些基本功能。

### $$Latex$$数学公式，MathJax


这是段落内的$$Latex$$数学公式测试， $$ \int_a^b f(x)\,dx $$. Does it work well?

有时候，需要的是段落间的$$Latex$$数学公式，比如下面的这个：

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)dx $$

Does it work well?

测试加上自定义编号的公式

$$
\begin{equation}
m\ddot{x} + c\dot{x}+kx = 0 \tag{abc}\label{eq:one}
\end{equation} 
$$

I refer you to e\eqref{eq:one}.

测试加上自动编号的公式

$$
\begin{equation}
E = mc^2 \label{eq:mck}
\end{equation} 
$$

I refer you to e\eqref{eq:mck}.


### 代码高亮，图片显示

例1: Maltab

{% highlight matlab %}

clear;clc;close all; % matlab
aH = 120;aL = 100;c = 10;b = 1;
rho1 = 0.99;
rho2 = 0.00;
ubar = 3000;
p1 = 0:1:120;
p2 = 0:0.1:75;
% Some functions
funL = @(rho,p)(rho*aH+(1-rho)*aL+b*c-2*b*p);
funR = @(rho,p,ubar)((rho.*b.*ubar.*(aH-aL))./(aL-b.*p).^2);

pc = c*ones(length(p1));
ypc = linspace(0,120,length(p1));
paLb = aL/b*ones(length(p1));
yaLb = linspace(0,120,length(p1));
% Point where they meet
pcE = c;
y1pcE = funL(rho1,pcE);
y2pcE = funR(rho1,pcE,ubar);
x3E = 52;
y3E = funL(rho1,x3E);
x4E = 45;
y4E = funR(rho1,x4E,ubar);
% Plot the bogus functions
figure(1), clf, hold on

plot(p1,funL(rho1,p1),'r',  p2,funR(rho1,p2,ubar),'b', 'linewidth', 2);hold on;
plot(p1,funL(rho2,p1),'r--');

% get rid of standard axes decorations
set(gca, 'Xtick', [], 'Ytick', [], 'box', 'off')

% Fix the axes sizes
axis([0 120 0 120])

% the equilibrium point
plot(pcE, y1pcE, 'k.', 'markersize', 20)
plot(pcE, y2pcE, 'k.', 'markersize', 20)
plot(x3E, y3E, 'k.', 'markersize', 20)
plot(x4E, y4E, 'k.', 'markersize', 20)
% 
% % the dashed lines
line([pcE pcE],[0 y1pcE], 'linestyle', '--', 'color', 'k')
line([aL/b aL/b],[0 100], 'linestyle', '--', 'color', 'k')
axp = get(gca,'Position');

% determine startpoint and endpoint for the arrows 
xs=axp(1);
xe=axp(1)+axp(3);
ys=axp(2);
ye=axp(2)+axp(4);

% make the arrows
annotation('arrow', [xs xe],[ys ys]);
annotation('arrow', [xs xs],[ys ye]);
lx = xlabel('$p$','Interpreter','Latex');
ly = ylabel('$y$','Interpreter','Latex');

set(gca,'TickLabelInterpreter','latex')
set(gca,'xtick',[0,10,aL/b]);
set(gca,'xticklabels',{'$0$','$c$','${a_L}/{b}$'});

% % the static texts
text(70, 55, '$y_1\!\!=\!\!\frac{\rho (a_H-a_L)b \bar u}{(a_L-bp)^2}$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',14)
text(58, 20, '$y_2\!\!=\!\!\rho a_H\!\!+\!\!(\!1\!-\!\rho\!)a_L\!\!+\!\!bc-\!\!\!2bp$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',12)
text(pcE+5, y1pcE, '$\rho a_H\!\!+\!\!(\!1\!-\!\rho\!)a_L\!\!-\!\!\!bc$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',12)
text(pcE+2, y2pcE+10, '$\frac{\rho (a_H-a_L)b \bar u}{(a_L-bc)^2}$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',15)
text(x3E-1, y3E+6, '$A$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',15)
text(x4E-3, y4E-6, '$B$',...
    'Interpreter','Latex', 'fontweight', 'bold','fontsize',15)

{% endhighlight %}

下面为上面Maltab代码的运行结果图：

jpg 格式
![test_001](/media/image/test.jpg)

png 格式
![test_001](/media/image/test.png)

例2: Javascript

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


例3： 普通代码

```
$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\]  另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\)  Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\]  另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)\,dx $$

\\[ f(x,y,z) = 3y^2 z \left( 3 + \frac{7x+5}{1 + y^2} \right). \\]
```

## 未完待续。。。