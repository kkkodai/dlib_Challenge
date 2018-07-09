# Overview
- Contents
    - dlibをインストール → [Install](#install)
    - dlibを使ってみる → [Practice](#practice)
    - **行いたいこと(これが一番重要) → [Task](#task)**
        1. 口認識
        2. マーカー認識
        3. 口のどの位置にマーカーがあるか特定

- OS
    - Mac OSX(El Caption)

# Install
## 方法1: ソースからビルド(imglabを使う事が目的の場合)
## procedure
1. Xcode
2. homebrew
3. boost
4. boost-python
5. cmake
6. OpenCV
7. dlib
8. XQuartz
9. CMakeCache.txt
10. imglab

_＊1と6は[OpenCV_challenge](https://github.com/kkkodai/OpenCV_challenge#install)レポジトリをチェック_

### - homebrew
まず、Xcode入れる
```
$ xcode-select --install
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
参照:[MacにHomebrewを導入する方法](https://qiita.com/balius_1064/items/ac7dff5ef10eaf69996f) 

### - boost & boost-python & cmake 
```
$ brew install boost
$ brew install boost-python --with-python3
$ brew install cmake
```

### - dlib
ここから本番
```
(http://dlib.net/　から最新版(2018.07.01時点ではdlib-19.13)をダウンロードして解凍)
$ cd dlib-19.13
$ sudo python setup.py install
```
## 方法2: Python APIとしてインストール(サクッと試したい場合はこっち)
## procedure
1. Xcode
2. homebrew
3. boost
4. boost-python
5. cmake
6. OpenCV
7. dlib

_＊6まで方法1を参照_

### - dlib
```sh
$ pip install dlib
```

- importする際に[記事](https://stackoverflow.com/questions/45923202/import-dlib-importerror-symbol-not-found-pyclass-type)のようなエラーが発生することがあるらしいが今回は上手くいった

### 参考サイト
- [Dlibの高性能な顔器官検出をMacでさくっと試す](https://qiita.com/naoyu822/items/7cce2f2dbad24931cc87)
# Practice
- face_detect.py
    - 顔認識
    - opencv2のように認識範囲が四角い
- face_detect_dot.py
    - 顔認識(一人分しか認識しない)
    - 点描みたいに出力

# Task
### Step1. 口認識
- mouth_detect_dot.py
    - 口認識は全68のラベルのうち49から68(プログラム内では48から67)で行う
- mouth_detect_dot_RGB.py
    - RGB化
### Step2. マーカー認識
- 参考サイト
    - [HOG特徴とSVMによる物体検出](http://ishi.main.jp/ros/ros_obj_detection.html)
    - [dlibで機械学習して物体検出する](https://qiita.com/atotto/items/ef34c046c2222adf1679)
### Step3. 口のどの位置にマーカーがあるか特定