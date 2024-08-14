# 改进自适应噪音完备集成经验模态分解(ICEEMDAN)

## 1. 概念：

- ICEEMDAN为解决CEEMDAN的残留噪音和伪模态分量；
- 主要改进点是添加的噪音不是原始白噪音，而是原始白噪音的IMF分量；

## 2. 运算逻辑:

![ICEEMDAN的运算逻辑图](../../../assets/pictures/ICEEMDAN.PNG)

- 算子$E_j(.)$代表求一个信号EMD分解的第j个IMF分量。
- 算子M(.)代表求信号的局部均值。
- $w^l[n]$表第l个白噪音；
-

## 3. 优缺点:

优点：
缺点：

## 4. 补充

## 5. 相关代码:

[ICEEMDAN](./ICEEMDAN.ipynb)
