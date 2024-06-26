---
title: "[翻译]无痛功能规格说明书——Part3：谁去做？"
url: 无痛功能规格说明书——Part3：谁去做？
date: 2024-04-20 09:46:31
categories:
- 软件项目
tags:
- 软件项目
- 翻译
---

> 原文 [Painless Functional Specifications – Part 3: But… How?](https://www.joelonsoftware.com/2000/10/04/painless-functional-specifications-part-3-but-how/)

<!-- more -->

<head>
  <style>
    .greenTitle {
      color: #008000;
    }
  </style>
</head>

现在，您应该已经阅读了 [为什么要写规格说明](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/) 和 [什么是规格说明](https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/)，接下来让我们聊聊谁去编写规格说明。

<span class="greenTitle">谁去编写规格说明？</span>

允许我和您谈一点微软的历史，在微软认真发展的 1980 年代，微软的每个人都阅读过 [人月神话](http://www.amazon.com/exec/obidos/ASIN/0201835959/ref=nosim/joelonsoftware)，那是软件管理领域的经典著作（如果您还没有读过，我强烈推荐您阅读）。那本书中的主要观点之一就是当您向一个延误的项目增加程序员人手时，项目反而会延误的更加严重。假设您的开发团队有 n 个程序员，那么沟通路径的条数会是 n(n-1)/2，以 O(n^2) 的速度增长。

因此，如何去编写越来越庞大的软件成了微软的一个挑战，当时流行的观点是增加程序员的数目会让事情变得更糟。

Charles Simonyi，彼时微软的“首席架构师”，提出了一个名为 *大师级程序员* 的概念。基本理论是一个大师级程序员应该负责编写所有的代码，但是他可以组织一帮初级程序员作为他的“码农”，这样他就不必要操心调试每个函数，大师级程序员只需要进行每个函数的原型设计、创建简单的程序轮廓，之后丢给码农们去实现。（当然，Simonyi 自己会是“特级大师级程序员”）。考虑到“大师级程序员”这个词过于中世纪，微软将他改名为“程序经理”（Program Manager）。

理论上说，这应该可以解决人月神话问题，因为程序员之间不再必须相互沟通——每个码农只需要和他的程序经理沟通，因此沟通成本的增速度从 O(n^2) 降低到了 O(n)。

好吧，Simonyi 可能非常了解 [匈牙利命名法](http://msdn.microsoft.com/library/techart/hunganotat.htm)，但是他不太了解人心，没人甘于当个码农，这套系统根本没法运作。最终，微软意识到尽管据称他们打破了人月神话，他们确实可以通过向团队里增加聪明的小伙子来增加产出，但是这种效果是边际递减的。在我还在那边工作的时候，Excel 团队拥有 50 名程序员，这个团队的生产力比 25 人团队要高一些——但是远远不到两倍。

这种 编程大师/码农 的架构备受指责，但是微软仍然保留了程序经理这个岗位名称。一个叫做 Jabe Blumenthal 的聪明人基本上重塑了程序经理的定位。从他以后，程序经理将负责产品设计和产品规格说明书。

从那时开始，微软的程序经理负责收集需求，搞清楚代码究竟需要用来支持什么，并 *编写功能规格说明书*。一般来说每个程序经理会配有 5 个程序员，这些程序员负责使用代码实现程序经理已经在规格说明中使用文档实现的内容。程序经理还需要去协调市场、文档、测试、本地化，等等一切程序员不该浪费时间的工作。最后，微软的程序经理需要顾全公司的“大局”，而程序员则可以自由的专注于让他们的代码完全正确。

程序经理至关重要。如果您曾经抱怨过程序员只考虑代码实现而根本不懂市场影响，您需要一个程序经理。如果您曾经抱怨过能写出好代码的人为什么总是写不出好文档，您需要一个程序经理。如果您曾经抱怨过您的产品方向似乎总是左右摇摆，您需要一个程序经理。

<span class="greenTitle">您如何雇佣一位程序经理？</span>

让我感到失望的一点是，大部分公司甚至都还没有程序经理的概念。在我上班的时候，由强大的程序经理带领的微软团队制作了很多成功的产品：Excel、Windos 95、Access 等等。但是有些其他的团队（例如 MSN 1.0 或者 Windows NT 1.0）在开发的过程中则忽略了他们的程序经理（这些程序经理能力一般，被忽略也许情有可原），他们的产品就没有这么成功。

这里是需要避免的三件事。

**1. 不要直接将程序员晋升为程序经理** 程序经理的核心能力（清晰的文档表达、外交能力、市场意识、用户同理心和UI设计能力）和成长为一名优秀程序员没有什么关系，确实，有些人既是优秀的程序员，也具备这些能力，但是这种人很稀缺。把优秀的程序员 *晋升* 到一个他不熟悉的领域，本来他是写 C++ 的，现在开始写文档了，这是 [Peter Principle](http://www.amazon.com/exec/obidos/ASIN/1568491611/ref=nosim/joelonsoftware) 的经典案例：人们会被晋升到他实际上不擅长的岗位。

**2. 不要让市场部的员工去当程序经理** 无意冒犯，但是我认为我的读者会赞同这个观点：市场部的员工通常无法掌握产品设计过程中的技术问题。

基本上，程序经理是一个单独的路径，所有的程序经理都必须对技术了如指掌，但是他们不必成为优秀的程序员。程序经理需要学习 UI 设计，会见客户，*编写规格说明*。他们需要与各种各样的人相处——从“白痴”客户，到穿着《星际迷航》cos服上班的二次元程序员，到穿着 2000 美元西装套装的浮夸销售人员。从某些方面来说，程序经理是软件团队的粘合剂，他的个人魅力至关重要。

**3. 不要让程序员向程序经理汇报** 这是一个很容易被忽视的错误。我在微软担任程序经理时，设计了 Excel 的 Visual Basic 应用程序 (VBA) 策略，并详细制定了 VBA 在 Excel 中的实现规范，这份规格说明书细致到每个细节，足足有 500 多页。在 Excel 5.0 开发高峰期，我估计每天早上有 250 人上班后，基本上都是参照我写的那份庞大规范工作的。我根本不知道这些人是谁，但仅 Visual Basic 团队就有大约十几个人专门负责这项工作的文档编写（更不用说 Excel 团队的文档编写人员，以及负责帮助文件中超链接的全职人员了）。奇怪的是，我在汇报架构中处于“底层”，是的，**没人**向我汇报工作。如果我想让人们做某件事，我必须说服他们，让他们相信这是正确的做法。当首席开发人员 Ben Waldman 不想做我规格说明中的某些内容时，他直接就可以不做。当测试人员抱怨我设计的内容无法完全测试时，我就得进行简化。**如果这里的任何一个人需要向我汇报，那么产品都不会像最终成功那么出色。**有些人可能会认为质疑上级是不合适的，另一些时候，我可能会出于自负或目光短浅，直接命令他们按照我的方式去做。但实际情况是，我别无选择，只能努力达成共识，这种决策方式才是做出*正确决定*的最佳途径。

我关于规格说明系列文章的 [最后一篇](https://www.joelonsoftware.com/articles/fog0000000033.html) 讨论了如何编写一个人们愿意去阅读的规格说明书。