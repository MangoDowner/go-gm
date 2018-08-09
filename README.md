> # go-gm
---

## golang标准库国密版本

### 改造源库
基于golang分支**release-branch.go1.9**

```
https://github.com/golang/go/tree/release-branch.go1.9
```

### 主要改动
+ 增加了sm2 / sm3 / sm4 国密算法支持
+ 增加了tls对于国密算法的支持

### 依赖仓库
+ 同济区块链研究院国密算法实现
```
https://github.com/tjfoc/gmsm
```
