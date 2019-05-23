---
layout: post
title: Lighthouse
subtitle: Chrome DevTool Audits.
date: 2019-03-28
author: huangqing
header-img: img/post-bg-chrome.jpg
catalog: true
categories: [Web]
tags:
  - chrome
---

## Lighthouse

Audits 面板基于谷歌开发的 Lighthouse，它提供了一整套全面的测试来评估网页的质量。测试类别分别是性能、辅助功能、最佳实践和 PWA（Progressive Web Apps）。 Lighthouse 的口号是“Do Better Web”，旨在帮助 Web 开发者改进他们现有的 Web 应用程序。通过运行一整套的测试，开发者可以发现新的 Web 平台 API，意识到性能的隐患，并学习（新的）最佳实践。换句话说，就是让开发者在 Web 开发上做得更好！DBW 作为一套独立的收集器和审查器与 Lighthouse 的核心测试同时运行。

## 如何使用 Lighthouse

Audits 标签是 DevTool 内置选项卡的最后一个标签。想要使用它的话，需要安装 Chrome 60 的开发版或者 Canary 版。

你可以按照以下步骤来审查页面：

1. 按 F12 来打开 DevTool
2. 点击 Audits 标签
3. 点击 Perform an audit
4. 点击 Run audit。 _Lighthouse 启动 DevTool 来模拟一个移动设备，在页面上运行一堆测试，然后将结果显示在 Audit 面板中。_

## 面板

Lighthouse 从 4 个方面来分析页面：性能、辅助功能、最佳实践和 PWA。Lighthouse 会在一系列的测试下运行网页，比如不同尺寸的设备和不同的网络速度。它还会检查页面对辅助功能指南的一致性，例如颜色对比度和 ARIA 最佳实践。

![每个类别的审查报告](/images/chrome/t01acb319fb1b1bc51d1-1.png)

报告顶部的分数是每个类别的总分。报告的其余部分是决定得分的每一个测试项的具体描述。每个类别的分析结果都会以适当的结构展示在指定的面板中。

## PWA

PWA 是可靠的，快速的，迷人的，尽管有很多因素会影响 PWA 的体验是中规中矩的，还是可圈可点的。 为了帮助团队创造最好的体验，Lighthouse 整理了一份详细的清单，里面列举了想要创建一个 Baseline PWA 需要满足的条件，你也可以通过提供更有意义的离线体验，让应用与人交互得更快，以及关注其他更多的重要细节来升级成 Exemplary PWA。

![PWA 结果—失败的测试](/images/chrome/t011229ea54a2b810a11.png)

当我们点击顶部的 PWA 圆圈时，我们首先看到的是失败的测试列表。我们可以研究一下问题出来哪里，然后修复这些失败的测试。

PWA 测试报告的后面部分是通过的测试列表和需要手动检查的测试列表。为了验证某些检查结果，我们必须手动去运行检查。这些检查很重要，但不影响得分。

![PWA 报告—通过的测试项和需要手动检查的部分](/images/chrome/t011b8edc5b3c7dd95e1-1.png)

## 性能

Web 性能是指网页在浏览器上下载和显示的速度。web 性能优化是提高 web 性能的一个技术领域。

更快的网站下载速度已被证明能增加访客的留存率、忠诚度和用户满意度，特别是对于网速较慢的用户和移动设备上的用户。

性能类别的第一部分是指标。这些指标从多个维度对应用程序的性能进行评估。

![性能的指标](/images/chrome/t01416aaf15fef0e6f61-1.png)

正如你所看到的，页面加载有包括 3 个重点：

1. `首次有效绘制`-衡量的是用户看到网页的主要内容所需的时间。
2. `首次互动`-指的是页面加载完成必要的脚本和 CPU 空闲足以应付大多数用户输入时的所需的时间。
3. `持续互动`-指的是页面中的大多数网络资源完成加载并且 CPU 在很长一段时间都很空闲的所需的时间。

性能的下一个部分是`可优化项`。 例如你可以通过压缩资源图像和文本来让程序运行的更快，这些都是可优化的地方。

![可优化项和诊断](/images/chrome/t0122b688cfaef232f61.png)

最后一部分是诊断。这些诊断显示了有关性能的更多信息。其中一个就是关键请求链，它显示了页面首次渲染时所需的资源。我们可以通过减少请求链的长度、减少下载资源的大小或延迟下载不必要的资源来提高页面的加载速度。

## 辅助功能

辅助功能指的是那些可能超出“典型”用户范围之外的用户的体验，他们以不同于你期望的方式访问你的网页或进行交互。具体点说，它关注的是身体正在经历着某种损伤或残疾的用户?-?记住，这种状况可能不是身体上的也可能是暂时的。

辅助功能类别测试屏幕阅读器的能力和其他辅助技术是否能在页面中正常工作。例如：按元素来使用属性，ARIA 属性的最佳实践，可辨别的元素命名等等。

![辅助功能类别报告](/images/chrome/t0153034091405952201.png)

## 最佳实践

最佳实践类别检查一些建议，使页面现代化，并避免性能陷阱。例如：应用程序缓存，HTTPS 使用，不推荐使用的 API, 用户的权限请求等等。这部分包含“失败和通过的测试列表”。

![最佳实践类别报告](/images/chrome/t0101c7008884a1cdd01.png)

## Lighthouse是如何工作的-架构

Lighthouse的工作流程有几个主要的步骤。部分步骤发生在浏览器中，其余的步骤由Lighthouse 运行器执行。

![Lighthouse 架构](/images/chrome/t011f1890390296b6dd1.jpg)

下面是Lighthouse 的组成部分：

1. 驱动-和Chrome Debugging Protocol 进行交互
2. 收集器-使用驱动程序收集网页信息。最小化后处理。收集器的输出结果被称为Artifact。
3. 审查器-将Artifact作为输入，审查器会对其运行1个测试，然后分配通过/失败/得分的结果。
4. 类别-将审查的结果分组到面向用户的报告中（如最佳实践）。对该部分应用加权和总体然后得出评分。

## 结论

辅助功能和PWA成为了现代web开发的主要衡量标准。很多公司投入时间和金钱来改善他们的网页。Lighthouse 在DevTool中的整合是可行的。它有助于Web开发人员变得更专业，还会提高网页的质量。我确信将来我们会在Audits标签中花很多时间，然后在一些热门的网站上运行它，还会有更多的人也会这么做。