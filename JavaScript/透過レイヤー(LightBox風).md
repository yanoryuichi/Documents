# 透過レイヤー（LightBox風）

## 概要
LightBoxのように、画面の全体（背景）を透過したグレーで覆う。

## 方法

- IE6以外
  - 透過PNGを使う。
  - opacityを使う。
- IE6
  - 透過PNGが使えないのでfilter:alphaでアルファ値を下げる。
