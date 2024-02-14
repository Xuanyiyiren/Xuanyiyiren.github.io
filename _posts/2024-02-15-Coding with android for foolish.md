---
layout: post
title:  "Coding on Android for Foolish"
date:   2024-02-15 01:21:00 +0800
author: "Xuan Zhang"
categories: Other
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>



当你因为俗务缠身无法接触到你的PC时，可以尝试使用你的android手机进行coding。

本文专为小白和非科班人士分享一些想法，因为我本身也是小白且非计算机科班出身。

# 百度输入法的飞桨皮肤
使用andriod端进行coding最大的阻力在于手机上的输入各种符号实在是太麻烦了，我之前考虑过给平板装一个键盘，但是这样一来平板就丧失了一部分的便携性，那我为什么不直接带一个轻薄本？

所以我想有没有专门为程序员准备的安卓输入法，最近查了一下还真发现有，感谢这位[知乎网友的专栏](https://zhuanlan.zhihu.com/p/374353822?utm_psn=1741257550820147200)。百度输入法的飞桨皮肤确实好用，安装的话，在软件商店里面搜百度输入法下载安装之后，在里面搜飞桨找到并使用皮肤即可。

# 加速器和浏览器
我们总是要搜索别人的工作和代码的，手机自带的浏览器一言难尽。我的评价是不如百度。

加速器我一直在用的是v2rayN，它也有.apk文件。最近也是发现了一个新的，更新手友好的加速器[pigcha](https://www.pigcha.com/)，给点钱就可以无脑使用。

我只是一个魔法小白，可能我的推荐并不是最好用的。

android端的浏览器我觉得Edge就可以了，也可以直接在软件商店下载，而且可以不同设备同步，也就是说你手机里Edge的收藏夹和浏览历史什么的和PC端保持同步，这简直太棒了！（虽然Edge在PC上只是个pdf阅读器.jpg）

# 免费现成的云编译环境
在android端搭建编译环境不考虑，这不是小白能做的（内心os：我也不会）。我们可以考虑在上一部分做好的基础上使用云编译环境。当然，你可以就此搭建云服务器。但是这对小白来说也是有一些挑战的，而且你只是手边没有PC闲得无聊coding一下，没必要搭建云服务器。可以考虑下面几种免费的直接搭建好的python编译环境，它们本来是人工智能的coding平台，但我还不会机器学习所以至今拿它们当普通python用

* 如果你在android上掌握了魔法 那么[colab](https://colab.research.google.com/)可以考虑，这个是Google弄的，可以和Google drive以及GitHub联动
* 如果你不会魔法，那么[百度飞桨](https://aistudio.baidu.com/projectoverview)里面创建个人项目也是一个不错的选择

# Markdown编辑
我们经常需要编写Markdown文件，这里也考虑线上云Markdown编辑器，我正在用的这个是[stackedit编辑器](https://stackedit.cn)，链接改成.com是国际版，不过中文版的功能基本一致。

不知道大家怎么接触到markdown，我比较反常。我是先接触的 $\LaTeX$ ，用的是overleaf，然后接触markdown，所以我在PC上编写md文件也是使用的云编辑器，直到最近才开始试一试typora。

# 结语
最近在被拖着到处拜年，有时候亲戚打牌消遣时间，我技术很烂就不一起玩了。但是电脑又不在身边，只有手机。我又不喜欢玩手游，只玩元气骑士，玩多了也玩腻了。所以想一下能不能coding一下消遣时间，没事干刷一刷leetcode啥的。

使用上述方法，我成功在手机上写完了我[刷题仓库里的快排](https://github.com/Xuanyiyiren/leetcode-exercise/tree/main/Sorting%20algorithm/Some%20Classic%20Algorithm/Quicksort)。

我觉得实现方法还算蛮有趣的，所以写出来给大家分享一下。
