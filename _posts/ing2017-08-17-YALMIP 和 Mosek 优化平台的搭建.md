---
layout: post
title: 基于YALMIP和Mosek的优化平台搭建
date: 2017-8-31
description: Matlab环境下基于YALMIP和Mosek搭建优化平台
categories: [Working]
tags: [Optimization]
mathjax:    true
---

##   基于YALMIP和Mosek的优化平台搭建

### Yalmip简介
Yalmip工具箱是由Johan Lofberg 博士编写的一个基于Matlab的优化软件工具箱。它最初是为求解控制领域中出现的半正定规划问题而设计的。后来经过不断改进，可以用来求解更多的优化问题，比如：

Yalmip目前被广泛应用，因为：

免费，建模语言简洁，书写方便，提供接口可以调用几乎所有的优化软件求解器；

真正实现了建模和算法二者的分离，提供了一种统一的、简单直观的建模语言。

Yalmip工具箱官方链接：[Yalmip](https://yalmip.github.io/)

### Moseck简介

安装Moseck

放置mosek.lic，目录："C:\Users\username\mosek"



参考文献

> 戴江涛，“优化工具箱及其在控制理论中的应用”