---
title: "創傷領域切取画像を入力としたUNetによる組織型分類"
date: 2019-08-16T23:43:08+09:00
draft: false
tags: ["FCN","UNet","組織型分類"]
---

### **Abstract**
創傷以外を青く塗りつぶした画像30枚にデータ拡張を施し，UNetに学習させ，3種類の組織型分類を行った．


### **Result**
mIoU = 0.762
<center>{{< figure src="../media/bunet_prediction.jpg" title="テストデータに対する推定結果" class="center">}}</center>

### **Source**

- [Github](https://github.com/hrichii/dog_or_cat)【Code】
- [Asgard](<file://///asgard/usr/horiuchi/program/pro_dog_or_cat/dog_or_cat>)【Code&Data】

(Asgardへのアクセスはリンクのアドレスをエクスプローラーに貼付)
