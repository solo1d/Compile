# 语法分析

## 语法分析

### 语法分析的主要任务

**语法分析的主要任务的是从 `词法分析器` 输入过来的`记号流`  , 然后 `分析语法是否有错误 (如果有错误,则要给出如何修改为正确的提示),` 随后通过`某种语言的语法规则`输出为`抽象语法树 .`**

![&#x8BED;&#x6CD5;&#x5206;&#x6790;&#x7684;&#x4EFB;&#x52A1;](.gitbook/assets/ping-mu-kuai-zhao-2019061308.52.40.png)

### 

### 语法错误处理

![](.gitbook/assets/ping-mu-kuai-zhao-2019061309.00.45.png)

### 语法树构建

**当语法错误处理完成后,无错误的情况下 会进行语法树的构建.**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061309.14.04.png)

### \*\*\*\*

### **路线图**

* **数学理论 :  上下文无关文法\( CFG \)**
  * 描述语言 语法规则 的数学工具
* **自顶向下分析算法**
  * 递归下降分析算法 \( 也称 分析算法\)
  * LL分析算法
* **自顶向上分析算法**
  * LR 分析算法

### 

### 上下文无关文法

**上下文无关文法 是描述`程序语言语法`的 一个强有力的`数据学工具`** 

**四元组都包含**  $$G = ( N, T, P, S)$$  **.**

![&#x5386;&#x53F2;&#x80CC;&#x666F;&#x548C;&#x5E94;&#x7528;](.gitbook/assets/ping-mu-kuai-zhao-2019061309.44.57.png)

#### 意义作用和文法结构

![&#x610F;&#x4E49;&#x6587;&#x6CD5;&#x548C;&#x7ED3;&#x6784;](.gitbook/assets/ping-mu-kuai-zhao-2019061309.52.53.png)

![&#x5F62;&#x5F0F;&#x5316;&#x7684;&#x7B26;&#x53F7;&#x8868;&#x793A;](.gitbook/assets/ping-mu-kuai-zhao-2019061309.58.49.png)

![&#x6570;&#x5B66;&#x5B9A;&#x4E49;](.gitbook/assets/ping-mu-kuai-zhao-2019061310.11.34.png)

![&#x66F4;&#x52A0;&#x5F62;&#x5F0F;&#x5316;&#x7684;&#x63CF;&#x8FF0;](.gitbook/assets/ping-mu-kuai-zhao-2019061311.24.23%20%281%29.png)

**`终结符小写,  非终结符大写, 开始符号也是大写 可以看成是第一个非终结符.`**

![&#x7B97;&#x6570;&#x8868;&#x8FBE;&#x5F0F;](.gitbook/assets/ping-mu-kuai-zhao-2019061311.35.23.png)

![&#x63A8;&#x5BFC;&#x548C;&#x66FF;&#x6362;](.gitbook/assets/ping-mu-kuai-zhao-2019061311.40.28.png)

#### 最左推导和最右推导

![](.gitbook/assets/ping-mu-kuai-zhao-2019061311.55.24.png)

![&#x8BED;&#x6CD5;&#x5206;&#x6790; &#x6240;&#x8981;&#x7ED9;&#x51FA;&#x7684;&#x7B54;&#x6848;](.gitbook/assets/ping-mu-kuai-zhao-2019061311.57.53.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061311.59.34.png)

### 

### 分析树 与 二义性

#### 推导与分析树

![](.gitbook/assets/ping-mu-kuai-zhao-2019061313.54.14.png)

#### 分析树

#### 分析树 一般是后续遍历,   左右中.

* 推导可以表达成树状结构
  * 和推导所用的顺序无关 \(最左, 最右, 其他\).
* 特点
  * 树中的每个**`内部节点`** 代表**`非终结符`**
  * 每个**`叶子结点`**代表**`终结符`**
  * 每一步推导代表从**`双亲节点`**生成它的直接**`孩子节点`**

![&#x8FD9;&#x4E24;&#x79CD;&#x63A8;&#x5BFC;&#x5B58;&#x5728;&#x6B67;&#x4E49;](.gitbook/assets/ping-mu-kuai-zhao-2019061314.09.18.png)

#### 二义性文法

**在编译器中, 不应该出现二义性文法**

* 给定文法 **`G`**, 如果存在句子 **`s`** , 他油两棵不同的分析树, 那么称 G 是**`二义性文法`**
* **从编译器角度,  二义性文法存在问题**
  * 同一个程序会有不同的含义
  * 因此程序运行的结果不是唯一的
* 解决方法:  **`表达式文法的重写`**

#### 表达式文法的重写

![&#x91CD;&#x5199;&#x4F8B;&#x5B50; 3+4\*5  ](.gitbook/assets/ping-mu-kuai-zhao-2019061314.39.43.png)

![&#x91CD;&#x5199;&#x4F8B;&#x5B50;2](.gitbook/assets/ping-mu-kuai-zhao-2019061314.43.01.png)

## 语法分析算法

### 自顶向下分析算法

**推导的过程中,往往需要`回溯`来帮助推导**

![&#x7B97;&#x6CD5;&#x601D;&#x60F3;](.gitbook/assets/ping-mu-kuai-zhao-2019061314.49.41.png)

![&#x7B97;&#x6CD5;&#x601D;&#x60F3;&#x8303;&#x4F8B;](.gitbook/assets/ping-mu-kuai-zhao-2019061314.57.52.png)

### 算法实现 \(伪代码描述\)

![&#x7B97;&#x6CD5;&#x5B9E;&#x73B0;](.gitbook/assets/ping-mu-kuai-zhao-2019061318.23.06.png)

#### 算法的讨论

* **算法需要用到回溯**
  * `给分析效率带来问题, 效率不够理想`
* 而就这部分而言 \( 就所有部分 \) , 编译器必须要**`高效`**来执行编译
  * _比如编译成千上万行的内核代码, 就要求高效率来执行编译_
* **因此, 实际上我们需要 `线性时间` 的算法来避免如下低效率内容**
  * **避免回溯**
  * 引出 **`递归下降分析算法`** 和  **`LL(1)  分析算法`**

#### 修改之后的算法思路,  它避免了频繁的回溯

![&#x907F;&#x514D;&#x4E86;&#x9891;&#x7E41;&#x7684;&#x56DE;&#x6EAF;](.gitbook/assets/ping-mu-kuai-zhao-2019061320.17.29.png)

### 递归下降分析算法

* 也称为 **`预测分析`**
  * **`分析高效  (线性时间)`**
  * **`容易实现 (方便手工编码)`**
  * **`错误定位和诊断信息准确`**
  * **`被很多开源和商业的编译器所采用`**
    * **`GCC 4.0 ,   LLVM (苹果的c, c++, object c 编译器) ,.....`**
* **算法基本思想**
  * **每个非终结符构造一个分析函数**
  * **用`前看符号`知道产生式规则的选择**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061320.34.48.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061320.38.36.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061320.46.07.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061320.52.40.png)

![&#x4F18;&#x5316;, &#x53BB;&#x9664;&#x4E86;&#x65E0;&#x7528;&#x7684;&#x5FAA;&#x73AF;&#x548C;&#x4E00;&#x4E9B;&#x56DE;&#x6EAF;](.gitbook/assets/ping-mu-kuai-zhao-2019061321.10.25.png)

### 

### LL\(1\)  分析算法

#### 简化的分析和实现

![&#x7B97;&#x6CD5;&#x5206;&#x6790;&#x7684;&#x57FA;&#x672C;&#x601D;&#x60F3;](.gitbook/assets/ping-mu-kuai-zhao-2019061321.01.41.png)

![&#x67B6;&#x6784;](.gitbook/assets/ping-mu-kuai-zhao-2019061321.03.32.png)

![&#x5206;&#x6790;&#x8868;](.gitbook/assets/ping-mu-kuai-zhao-2019061410.42.36.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061410.53.51%20%281%29.png)

![&#x5206;&#x6790;&#x8868;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.00.11.png)

#### LL\(1\) 分析表的冲突

![&#x5B58;&#x5728;&#x51B2;&#x7A81;&#x7684;&#x4E00;&#x5F20;&#x5206;&#x6790;&#x8868; , &#x4EE3;&#x8868;&#x4E0D;&#x53EF;&#x4EE5;&#x4F7F;&#x7528; LL\(1\)&#x5206;&#x6790;&#x7B97;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.04.02.png)

####  一般条件下的 LL\(1\) 分析表构造算法

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.16.59.png)



#### NULLABLE集合计算

![NULLABLE&#x96C6;&#x5408;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.19.24.png)

![NULLABLE&#x96C6;&#x5408;&#x8BA1;&#x7B97;&#x516C;&#x5F0F;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.22.49.png)

#### FIRST集合计公式

![FIRST&#x96C6;&#x5408;&#x8BA1;&#x7B97;&#x516C;&#x5F0F;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.25.35%20%281%29.png)

![FIRST&#x96C6;&#x7684;&#x4E0D;&#x52A8;&#x70B9;&#x7B97;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-2019061410.53.51.png)

![&#x7B97;&#x6CD5;&#x5B9E;&#x4F8B;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.31.38.png)

#### FOLLOW 集的不动点算法

![&#x4ECE;&#x540E;&#x5411;&#x524D;&#x505A;&#x8FED;&#x4EE3;](.gitbook/assets/ping-mu-kuai-zhao-2019061411.36.40.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.40.21.png)

#### 计算FIRST\_S 集合

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.47.57.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.48.51.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.49.18.png)

### 语法分析  驱动代码

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.51.16.png)

### LL\(1\) 分析处理冲突处理

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.54.03.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.54.32.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.55.08.png)

### \*\*\*\*

### **自底向上分析算法**

* **研究其中最重要爷是最广泛应用的一类**
  * **LR 分析算法 \(移进 - 归约算法\)**
    * **算法运行高效**
    * **有现成的工具可用**
  * **这也是目前采用广泛的一列语法分析器的自动生成器中采用的算法**
    * **YACC, bison, CUP , C\# yacc, 等等**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061412.04.34.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.57.14.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061412.19.53.png)

### **点记号**

![&#x5DF2;&#x7ECF;&#x8BFB;&#x5165;&#x7684;&#x662F;&#x5408;&#x6CD5;&#x7684;, &#x5269;&#x4F59;&#x7684;&#x4E0D;&#x4E00;&#x5B9A;&#x662F;&#x5408;&#x6CD5;&#x7684;](.gitbook/assets/ping-mu-kuai-zhao-2019061412.05.46.png)

![&#x5176;&#x4E2D;&#x4E00;&#x79CD;&#x5199;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-2019061412.07.28.png)

![&#x53E6;&#x4E00;&#x79CD; &#x6808;  &#x7ED3;&#x6784;&#x5199;&#x6CD5;](.gitbook/assets/ping-mu-kuai-zhao-2019061412.17.31.png)



### LR\(0\) 分析算法

![](.gitbook/assets/ping-mu-kuai-zhao-2019061411.57.14.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.31.33.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.36.29.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.37.59.png)

### LR\(0\) 算法思想

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.25.35.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.29.34.png)

### 

### SLR 分析算法

**是根据LR\(0\) 算法的一个改进**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.40.21.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.43.45.png)

### 

### LR\(1\) 分析算法

**根据LR\(0\) 算法改进的另一个算法, 这个算法避免了 `SLR分析表` 中的冲突情况.**

**LR\(1\) 和 LR\(0\) 的区别就是 `闭包` 算法不同.**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.46.12.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.47.56.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.51.09.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.52.35.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.54.06.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.54.43.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061413.55.59.png)



## LR\(1\) 分析工具

![](.gitbook/assets/ping-mu-kuai-zhao-2019061414.00.43.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061414.04.43.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061414.06.47.png)



























