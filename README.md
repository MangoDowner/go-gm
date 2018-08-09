> # go-gm
---

## golang标准库国密版本

### 一 改造源库
基于golang分支**release-branch.go1.9**
```
https://github.com/golang/go/tree/release-branch.go1.9
```

### 二 主要改动
+ 增加了sm2 / sm3 / sm4 国密算法支持
+ 增加了tls对于国密算法的支持

### 三 依赖仓库
+ 同济区块链研究院国密算法实现
```
https://github.com/tjfoc/gmsm
```

### 四 如何从源码安装
go的源码安装非常简单，只需运行源码包中src/make.bash，等到出现 ALL TESTS PASSED 字样就安装好了，但是在源码安装1.5版本以上的go时会报
```
ERROR: Cannot find /root/go1.4/bin/go
```
这个错误，这是由于go 1.5版以后的编译安装需要1.4版本go，所以如果想要通过源码方式安装高版本go，必须先安装好1.4版本的go。

#### 1 先编译得到go1.4环境
+ 下载go1.4源码，并解压进入源码src目录
+ 运行make.bash
```
# ./make.bash
```
如果遇到报错
```
cannot load DWARF output from $WORK/os/user/_obj//_cgo_.o: decoding dwarf section info at offset 0x4: unsupported version 0
```
需要 build without cgo
```
# export CGO_ENABLED=0
# ./make.bash
```
+ 之后你就能得到1.4版本的go了

#### 2 编译得到go1.9gm环境

+ 进入go-gm的源码src目录
+ 设置由go1.4进行编译
```
# export GOROOT_BOOTSTRAP=/usr/local/go1.4
```
+ 为了编译好的go能够支持c语言，需要开启环境变量
```
# export CGO_ENABLED=1
```
+ 运行make.bash
```
# ./make.bash
```
+ 之后你就能得到1.9gm版本的go了
+ 配置GOROOT和GOPATH等环境变量，老生常谈，不再赘述

![Gopher image](doc/gopher/fiveyears.jpg)
*Gopher image by [Renee French][rf], licensed under [Creative Commons 3.0 Attributions license][cc3-by].*
