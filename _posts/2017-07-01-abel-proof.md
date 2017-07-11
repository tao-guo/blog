---
layout: post
title: 读书笔记--《阿贝尔的证明》
categories: book
published: true
author: Tao
---

## 5次方程不可解的描述
  - [二次方程](https://zh.wikipedia.org/wiki/%E4%B8%80%E5%85%83%E4%BA%8C%E6%AC%A1%E6%96%B9%E7%A8%8B)
    - 配平方的思想
    - 韦达定理，包含了根的置换思想，后来的群理论发展很重要的一环
  - [三次方程](https://zh.wikipedia.org/wiki/%E4%B8%89%E6%AC%A1%E6%96%B9%E7%A8%8B)
    - 包含了卡尔达诺(1545)的解法和例子
  - [四次方程](https://zh.wikipedia.org/wiki/%E5%9B%9B%E6%AC%A1%E6%96%B9%E7%A8%8B)
    - 包含了费拉里(卡尔达诺的学生)的解法
    - 核心思想是配成完全平方数，转化为三次方程的解法
  - [Abel–Ruffini theorem](https://en.wikipedia.org/wiki/Abel%E2%80%93Ruffini_theorem)
    - 基于后来的伽罗瓦群理论重新阐述
    - <http://www.math.caltech.edu/~jimlb/abel.pdf>
    - <https://www.maa.org/sites/default/files/pdf/upload_library/22/Chauvenet/Rosen.pdf>
    - Peter Pesic的书本中包含原始未使用群论语言的证明

## 参考书目

### 《Abel's Proof》by Peter Pesic
  - 附录中有阿贝尔原始的6页论文及简要说明
  - 利用初等代数证明

### 《ABEL’S THEOREM IN PROBLEMS AND SOLUTIONS》
  - 副标题: Based on the lectures of Professor [V.I. Arnold](https://en.wikipedia.org/wiki/Vladimir_Arnold)
    - V.I. Arnold 19岁即证明了[希尔伯特的第13道数学难题](https://en.wikipedia.org/wiki/Hilbert%27s_thirteenth_problem)
      - 和七次方程的解有关
  - 给高中生的暑期数学讲义，介绍基本的群论和黎曼几何
    - 利用几何来直观理解
    - [V.I. Arnold 论数学教育](https://book.douban.com/subject/3202119/discussion/1364384/)
     - 鼓励数学教育中的几何表示
      - 警告数学建模解决现实问题的潜在危害(类比于Wigner原理和爱因斯坦的论断)
      - 复杂公理系统的毒害
      - 强调概念的直观理解:

        ```
        这样的例子并不鲜见，作为数学中最迷人的性质之一，Jacobi曾指出：用同一个函数
        就既可以理解能表示为4个数平方和的整数的性质，又可以描述一个单摆的运动。
        这些不同种类的数学对象之间联系的发现，就好比在物理学中电与磁之间联系的发
        现，也类同于地质学上对美洲大陆的东海岸与非洲大陆的西海岸之间相似性的发现。

        这些发现对于教学所具有的令人激动的非凡意义是无法估量的。正是它们指引着我
        们去研究和发现宇宙中和谐而精彩的现象。

        然而，数学教育的非几何化以及与物理学的分离却割断了这种联系。例如，不仅仅
        学习数学的学生而且绝大部分的代数几何学家都对以下提及的Jacobi 事实一无所知：一
        个第一类型的椭圆积分表示了相应的哈密顿系统中沿某个椭圆相曲线的运动所走的时间。
        ```

      - 纯粹公理化推导的弊端:

        ```
        试图创造所谓的纯粹推导式的公理化数学的做法，使得我们不再运用物理学中的研究
        方法（观察-建模－模型的研究－得出结论－用更多的观察检验模型）取而代之的是这样的
        方法：定义－定理－证明。人们根本不可能理解一个毫无动机的定义，但我们却无法阻止
        这些有罪的“代数－公理学家”。例如，他们总是想用长乘规则的手段来定义自然数的乘
        积。但用这种方法乘法的交换性却难以证明，不过从一堆的公理中仍有可能推导出这样的
        定理。而且完全可能逼着那些可怜的学生们来学习这个定理以及它的证明（其目的不外乎
        是提升这门学科以及教授它的人的社会地位）。显然，这种定义和这样的证明对教学和实
        际工作有百害而无一益。

        理解乘法交换性的唯一可能的方式，打个比方就是分别按行序和列序来数一个方阵里
        士兵的人数，或者说用两种方式来计算长方形的面积。任何试图只做不与物理和现实世界
        打交道的数学都属于宗派主义和孤立主义，这必将损毁在所有敏感的人们眼中把数学创造
        视为一项有用的人类活动的美好印象。
        ```

###　其他
  - 基于根置换和复平面几何解释: <https://news.ycombinator.com/item?id=14685466>
  - Abel证明中用到的一个柯西1815年证明过的引理: <http://nonagon.org/ExLibris/cauchy-permutations-origin-group-theory>

### 群论/近世代数
  - Modern Algebra(Visual Group Theory)
    - <http://web.bentley.edu/empl/c/ncarter/vgt/>
    - <http://www.math.clemson.edu/~macaule/classes/m17_math4120/index.html>
      - 全课程Youtube讲解和讲义下载
      - 形象直观，比普通教材更容易理解掌握
      - 除了环基本学习完毕，很多概念还要再巩固
  - Michael Artion's [《Algebra》](https://book.douban.com/subject/5496239/)也是经典的好教材
  - 胡冠章的《应用近世代数》也是不错的教材，入门，学习名词和做题