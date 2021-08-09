---
description: 这个模块 最庞大 最复杂
---

# 语义分析

## 语义分析

**`语义分析器`它依赖于 `语法分析器` 生成出来的 `抽象语法树` 来当作输入, 然后输出`中间表示 给后端.`**

### 语义分析的任务

* **语义分析也称为 `类型检查` , `上下文相关分析`.**
* **负责检查程序 `(抽象语法树)`  的 `上下文相关`  的属性:**
  * **这是具体语言相关的, 典型的情况包括:**
    * 变量在使用前 先进行声明
    * 每个表达式都有合适的类型
    * 函数调用和函数的定义一致
    * ..... \(等等\)

![&#x8BED;&#x4E49;&#x5206;&#x6790;&#x5668;&#x6240;&#x8981;&#x5B8C;&#x6210;&#x7684;&#x5DE5;&#x4F5C;](.gitbook/assets/ping-mu-kuai-zhao-2019061509.53.18.png)

### 

### 语义分析器概念上的结构

![](.gitbook/assets/ping-mu-kuai-zhao-2019061509.55.31.png)



### 程序语言的语义

![](.gitbook/assets/ping-mu-kuai-zhao-2019061509.58.57.png)



## 语义检查

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.07.55.png)

### 类型检查算法

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.10.54.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.13.39.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.14.30.png)

### 

### 变量声明的处理

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.17.16.png)

### 类型检查算法

![&#x6B63;&#x5E38;&#x7684;&#x7C7B;&#x578B;&#x68C0;&#x67E5;](.gitbook/assets/ping-mu-kuai-zhao-2019061510.21.25.png)



![&#x8868;&#x8FBE;&#x5F0F;&#x7684;&#x7C7B;&#x578B;&#x68C0;&#x67E5;](.gitbook/assets/ping-mu-kuai-zhao-2019061510.25.31.png)

### 语句的处理

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.27.09.png)



## 其他问题

* 语义分析中要考虑的其他问题:
  * **类型相容性? \(或者相等\)**
  * **错误诊断?**
  * **代码翻译?**

### 类型相等

![](.gitbook/assets/ping-mu-kuai-zhao-2019061511.36.22.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061511.55.53.png)

### 

### 错误诊断

![](.gitbook/assets/ping-mu-kuai-zhao-2019061511.57.45.png)



### 代码翻译

![](.gitbook/assets/ping-mu-kuai-zhao-2019061512.00.08.png)





