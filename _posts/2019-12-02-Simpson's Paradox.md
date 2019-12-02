---
layout:     post
title:      辛普森悖论 - Simpson's Paradox
subtitle:   
date:       2019-12-02
author:     Yi
header-img: img/post-bg-math.jpg
catalog: true
tags:
    - 统计
    - 数据分析
---
### 辛普森悖论
 在数据分析过程中，我们通常根据数据本身产生结论，然而我们需要格外小心，以免掉入统计分析的陷阱，得到与事实相悖的结论。辛普森悖论阐述了一种将数据综合考虑而产生的谬误。

### 加州大学伯克利分校的性别偏差

有人对加州大学伯克利分校的研究生录取情况做调查。研究期间，加州大学伯克利分校共得到$8,442$男性学生与$4,321$名女性学生的入学申请，但仅有$44\%$的男性学生与$35\%$的女性学生得到批准。从数据上看，男生的录取率高于女生，因此我们容易得到结论：加州大学伯克利分校具有性别歧视，学校更倾向招收男学生。

实际上，学校的招生工作由各个专业独立进行。如果大学的招生确实存在性别歧视，我们单独地观察每个专业，我们就可以找出“性别歧视”的“罪魁祸首”。然而，我们在逐个审视每个专业录取情况时，奇怪的事情出现了：在对每个专业独立考察时，并没有发现男女的性别偏差，即男生与女生的录取比率基本一致！到底是哪里出现了问题呢？

下表显示了伯克利分校其中6个较大专业的录取情况。
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-cly1{text-align:left;vertical-align:middle}
.tg .tg-1wig{font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-baqh{text-align:center;vertical-align:top}
.tg .tg-wa1i{font-weight:bold;text-align:center;vertical-align:middle}
.tg .tg-amwm{font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-yla0{font-weight:bold;text-align:left;vertical-align:middle}
.tg .tg-nrix{text-align:center;vertical-align:middle}
</style>
<table class="tg">
  <tr>
    <td class="tg-cly1"></td>
    <td class="tg-wa1i" colspan="2">Men</td>
    <td class="tg-amwm" colspan="2">Women</td>
  </tr>
  <tr>
    <td class="tg-wa1i">Major</td>
    <td class="tg-yla0">Number of applications</td>
    <td class="tg-wa1i">Percent admitted</td>
    <td class="tg-1wig">Number of applications</td>
    <td class="tg-1wig">Percent admitted</td>
  </tr>
  <tr>
    <td class="tg-wa1i">A</td>
    <td class="tg-nrix">825</td>
    <td class="tg-nrix">62%</td>
    <td class="tg-baqh">108</td>
    <td class="tg-baqh">82%</td>
  </tr>
  <tr>
    <td class="tg-wa1i">B</td>
    <td class="tg-nrix">560</td>
    <td class="tg-nrix">63%</td>
    <td class="tg-baqh">25</td>
    <td class="tg-baqh">68%</td>
  </tr>
  <tr>
    <td class="tg-amwm">C</td>
    <td class="tg-baqh">325</td>
    <td class="tg-baqh">37%</td>
    <td class="tg-baqh">593</td>
    <td class="tg-baqh">34%</td>
  </tr>
  <tr>
    <td class="tg-amwm">D</td>
    <td class="tg-baqh">417</td>
    <td class="tg-baqh">33%</td>
    <td class="tg-baqh">375</td>
    <td class="tg-baqh">35%</td>
  </tr>
  <tr>
    <td class="tg-amwm">E</td>
    <td class="tg-baqh">191</td>
    <td class="tg-baqh">28%</td>
    <td class="tg-baqh">393</td>
    <td class="tg-baqh">24%</td>
  </tr>
  <tr>
    <td class="tg-amwm">F</td>
    <td class="tg-baqh">373</td>
    <td class="tg-baqh">6%</td>
    <td class="tg-baqh">341</td>
    <td class="tg-baqh">7%</td>
  </tr>
</table>

这种现象似乎与之前得到的结论产生了矛盾，但仔细观察男女申请各专业的人数与录取比例，我们或许能够发现一些端倪。不难发现，大多男生申请的是录取率高的AB专业，而女生倾向于申请录取率低的CDEF专业，所以总体来看，男生显得更容易被录取。在此案例中，专业的选择为隐含变量，学生的性别决定了专业的选择的分布不同，而专业的选择决定了录取比率，录取比率与性别却没有直接关系。

### 小明求医

小明同学生病了，想去看医生，但他希望自己得到更好的治疗，因此他收集了两家医院的数据，A医院就诊的康复率为$90\%$，而B医院的康复率为$70\%$。那么小明是否应该就诊A医院呢？

细心的你一定发现，如果单纯根据总体康复率来决定医院，很容易掉入数据的陷阱。A医院很可能治疗大部分患者为普通的感冒，而就诊于B医院的患者大部分为疑难杂症，因此很容易得到A医院具有较高的康复率，所以单就康复率而言并不能得出A医院较好的结论，因此小明需要搜集更多的信息来判断了。


案例告诉我们，简单地分析总体情况看似正确，但在许多情况下并没有意义，甚至产生错误的结论，因此我们需要细心地发现所研究变量的潜在影响因素。

参考文献：
Freedman D, Pisani R, Purves R. Statistics. 3rd edition.[M]// Statistics, 4th Edition. 2007.
---



