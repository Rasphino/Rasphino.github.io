+++ 
draft = false
date = 2021-06-15T18:43:06+08:00
title = "修复IPA条形码缺失问题"
description = ""
slug = ""
tags = ["新加坡", "IPA", "ICA", "学生准证", "字体", "条形码"]
categories = ["教程"]
externalLink = ""
series = []
+++

**TLDR**：直接[下载](https://drive.google.com/file/d/1UhIntXs3CZ62jr9i4TBa_5N4nEfLYKIM/view?usp=sharing)、安装我修改过的字体。

## 背景：什么是IPA
IPA，全称In-Principle Approval。对于我们留学生，它是新加坡移民与关卡局（ICA）颁发给外国学生的原则同意该人士来新加坡学习的函件。当我们获得IPA后，可以使用IPA单次入境新加坡，并继续在新加坡完成我们学生准证（Student Pass）的申请。

IPA上有我们的个人信息、课程信息以及学生准证的信息。我们需要将IPA信打印出来，以备出入境时核验之需。但是当我们直接在SOLAR系统中打开IPA时，条形码的显示可能会发生错误，条码只能以备选的文字形式展现。

![缺失条形码的IPA](/images/IPA/wrong.png)


查阅网上的相关资料，有同学表示这里的条码缺失是正常的，学校随后会发送一份完整的IPA信到你的邮箱，我们只需要耐心等待即可。很遗憾的是，新国立的计算学部（School of Computing，SoC）在相关的邮件内明确表示全日制的国际学生需要自行打印IPA信，学校不会通过邮件发送IPA信：

> *All full-time international students will be required to print their own ICA’s In-Principle Approval (IPA) letters via SOLAR once approval has been granted by ICA. We will not be sending any IPA letter to you by email after the application is approved by ICA.

看来今年我们只能自己解决这个棘手的问题了！我们不难发现IPA使用条形码字体直接将字符串以条形码的形式显示，而条码的缺失是因为我们的电脑系统里缺少相关的条形码字体。

## 字体的安装
通过一番研究（指google），我们可以从[squaregear下载相关字体](https://squaregear.net/fonts/free3of9.zip)并安装。此时firefox用户应该已经能正确显示IPA中的条形码了，但是chrome和safari用户可能还是无法显示条形码。这是因为IPA使用的Free 3 of 9字体太过老旧，以至于它的名称、字体族都是不符合标准的。

![条形码字体信息](/images/IPA/font.png)

为了让浏览器能正确调用这些字体进行条码的显示，我们有两种解决办法：
1. 直接修改IPA的网页源码；
2. 修改字体的元信息。

### 修改网页源码
这是一种临时的解决方法，我们通过浏览器修改IPA网页源码中调用字体显示条码的部分，让浏览器能找到名称错误的字体。

首先我们选中条码部分，鼠标右键单击，选择“Inspect”进入审阅视图。可以看到这里使用依次尝试使用“Free 3 of 9 Extended”和“Free 3 of 9”字体渲染条形码。

![查看字体](/images/IPA/edit_2.png)

我们只需要把font-family修改为：`font-family: 'New'`即可让此条码正常显示。

![修改字体](/images/IPA/edit_3.png)

对于其他缺失的条形码，我们也进行同样的修改，即可让IPA正确显示。


### 修改字体元信息
相比于修改网页源码这种简单粗暴的方法，修改字体的元信息更加优雅、简单。我们使用[FontForge](https://fontforge.org/)软件就可以轻松修改字体的元信息，修改完成后重新生成并安装TrueType字体即可。

## 效果
经过一番努力，带有条形码的IPA如下：

![正常显示条形码的IPA](/images/IPA/final.png)

我们可以将其保存为PDF文件，以便后续打印。