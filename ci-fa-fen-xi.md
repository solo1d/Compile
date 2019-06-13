---
description: '标识符, 正则表达式,  语法糖'
---

# 词法分析

## 编译器的阶段和词法分析任务

### 编译器的阶段

#### 源程序  ----&gt;  编译器  ----&gt; target program \(目标程序\)

#### 源程序 ---&gt;  front end\(前端\) ---&gt;  IR\(中间表示\)  ---&gt; back end\(后端\)  ---&gt; target program\(目标程序\)

### 

### 前端

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-9.16.35.png)

**前端包含: 词法分析器, 语法分析器,  语义分析器**

#### 

### 词法分析器的任务

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-9.19.46.png)

#### 

#### 一个词法分析的例子

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-9.20.17.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-9.21.31.png)



### 词法分析器的任务:  字符流到记号流

* **字符流**
  * 和被编译的语言密切相关 \( ASCII , UNICODE, or ....\)
* **记号流**
  * 编译器内部定义的数据结构, 编码所标记 识别出的词法单元



## 词法分析的实现方法

* **至少有两种实现方法:**
  * _手工编码实现法_
    * `相对复杂, 且容易出错`
    * `但是目前非常流行的实现方法`
      * _`GCC , LLVM .....`_
  * _词法分析器的生成器  \(这是个工具\)_
    * `可快速原型, 代码较少`
    * `但较难控制细节`

## 手工编码实现法

#### 转移图是理解手工编码实现的核心.

![&#x8F6C;&#x79FB;&#x56FE;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-9.39.10.png)

转移图中 `4号` 上面的 \*  代表回滚, 将 `1号` 读取过来的字符放回到原有的字符流中,然后识别为`小于号`.

![&#x8F6C;&#x79FB;&#x56FE;&#x7B97;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.11.49.png)

![&#x6807;&#x8BC6;&#x56FE;&#x7684;&#x8F6C;&#x79FB;&#x56FE;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.27.40.png)

![&#x6807;&#x8BC6;&#x7B26;&#x548C;&#x5173;&#x952E;&#x5B57;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.34.22.png)

### 第一类识别关键字的算法

![&#x8BC6;&#x522B;&#x5173;&#x952E;&#x5B57;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.36.18.png)

### 第二类识别关键字的算法

![&#x54C8;&#x5E0C;&#x5173;&#x952E;&#x5B57;&#x7B97;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.46.08.png)

## 词法分析器的生成器

#### 这个就是依靠工具来实现, 程序员只需要填充少量代码就可以进行自动生成.

**词法分析器的生成需要 正则表达式**

* **有两种实现方式方式**
  * 手工实现算法
  * 自动生成法
    * 用到: 正则表达式,  语法糖,  有限状态自动机,  

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-10.57.33.png)

### 正则表达式 \( RE \)

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-11.05.46.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-shang-wu-11.15.37.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-12.47.18.png)

### 

### 标识符

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-12.54.19%20%281%29.png)

### 

### 语法糖

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-2.02.37.png)

### 

### 有限状态自动机   \(FA, DFA, NFA\)

#### 确定有限状态自动机 DFA

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-2.13.36.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-2.19.58.png)



#### 非确定有限状态自动机  NFA

![&#x975E;&#x786E;&#x5B9A;&#x6709;&#x9650;&#x72B6;&#x6001;&#x81EA;&#x52A8;&#x673A;](.gitbook/assets/ping-mu-kuai-zhao-20190611-xia-wu-5.54.59.png)

**有限状态自动机DFA 比 非确定有限状态自动机NFA 更加容易进行判断, 一般情况下需要将 NFA 转换成 DFA 来进行判断** 

### 有限自动状态机小结

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-8.59.38.png)

### 有限状态自动机 DFA 的实现

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.09.19.png)



### ER 转换到 NFA \(正则表达式到非确定有限状态自动机的转换算法\)

 **正则表达式ER ---&gt;  NFA  ---&gt;  DFA  ---&gt;  词法分析器代码**

![&#x6574;&#x4E2A;&#x6D41;&#x7A0B;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.17.52.png)

#### RE --&gt; NFA 过程的算法  Thompson算法

![&#x6B63;&#x5219;&#x8868;&#x8FBE;&#x5F0F; &#x5230; &#x6709;&#x9650;&#x786E;&#x5B9A;&#x81EA;&#x52A8;&#x673A;&#x7684;&#x8F6C;&#x6362;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.24.12.png)

![&#x7B97;&#x6CD5;&#x7684;&#x5177;&#x4F53;&#x6784;&#x9020;&#x8FC7;&#x7A0B;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.32.05.png)

![&#x8F6C;&#x6362;&#x8FC7;&#x7A0B;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.36.20.png)

#### 结合性顺序: 括号的优先级最高, 然后是闭包 , 随后是链接

![a\(b\|c\)\*   NFA&#x975E;&#x786E;&#x5B9A;&#x6709;&#x9650;&#x72B6;&#x6001;&#x81EA;&#x52A8;&#x673A;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-9.42.27.png)

### 

### NFA 转换到  DFA   \(非确定转换到确定  有限自动机 算法\)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-10.20.53.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-10.36.59.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-10.44.47.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-10.46.19.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-11.01.30.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-11.10.26.png)

### DFA 最小化算法 \(作用于 DFA,相当于压缩\)

![&#x7B97;&#x6CD5;&#x601D;&#x60F3;](.gitbook/assets/ping-mu-kuai-zhao-20190612-shang-wu-11.53.54.png)

![Hopcroft&#x7B97;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-2.57.30.png)

![Hopcroft &#x7B97;&#x6CD5;&#x5DE5;&#x4F5C;&#x8FC7;&#x7A0B;](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-3.12.06.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-3.19.28.png)

### 

### DFA 生成分析算法 \(代码表示\)

**DFA代码表示, 将前面得到的状态积转变成一个最终能够实际运行的代码,从而制造一个词法分析器**

#### DFA 的代码表示

* 概念上讲, DFA是一个有向图
* 实际上, 有不同的 DFA 的代码表示
  * **转移表 \(类似于邻接矩阵\)**
  * **哈希表**
  * **跳转表**  _**&lt;效率比转移表高一些,内存占用相对少一些&gt;**_
  * ......等等 各种形式
* 取决于在实际实现中, 对时间空间的权衡

_**转移表**_

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-4.15.07.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-4.14.12.png)

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-4.23.26.png)

_\*\*\*\*_

_**跳转表**_

![](.gitbook/assets/ping-mu-kuai-zhao-20190612-xia-wu-5.48.23.png)

















