# 代码生成

## 代码生成

### 代码生成的任务

![](.gitbook/assets/ping-mu-kuai-zhao-2019061514.42.13.png)

#### 给数据分配计算资源

![](.gitbook/assets/ping-mu-kuai-zhao-2019061514.47.07.png)



#### 给源程序的代码选择合适的机器指令

![](.gitbook/assets/ping-mu-kuai-zhao-2019061514.49.37.png)

### 路线图

![](.gitbook/assets/ping-mu-kuai-zhao-2019061514.51.32.png)

## 栈式计算机 代码生成技术

![](.gitbook/assets/ping-mu-kuai-zhao-2019061514.54.37.png)

![&#x7ED3;&#x6784;](.gitbook/assets/ping-mu-kuai-zhao-2019061514.56.34.png)

### ALU 能够执行的指令

push NUM     将一个立即数压入栈顶, 栈的大小 增加一

load x  把一个变量x ,从内存当中 读入到栈顶上, 栈的大小 增加一

store x    把栈顶元素弹出去, 并且把它赋值给内存当中 x 这个变量,  栈的大小 减少一

![](.gitbook/assets/ping-mu-kuai-zhao-2019061515.03.12.png)

### 指令的语义 : push

![&#x5C06;&#x4E00;&#x4E2A;&#x7ACB;&#x5373;&#x6570;&#x538B;&#x5165;&#x6808;&#x9876;](.gitbook/assets/ping-mu-kuai-zhao-2019061515.07.51.png)

### 指令的语义:  load  x

![&#x4ECE;&#x5185;&#x5B58;&#x5F53;&#x4E2D;, &#x8BFB;&#x5230;&#x6808;&#x9876;&#x4E0A;](.gitbook/assets/ping-mu-kuai-zhao-2019061515.09.10.png)

### 指令的语义:  store  x

![&#x4ECE;&#x6808;&#x5F53;&#x4E2D;&#x8BFB;&#x53D6;, &#x8D4B;&#x503C;&#x7ED9;&#x5185;&#x5B58;x](.gitbook/assets/ping-mu-kuai-zhao-2019061515.10.52.png)

### 指令的语义:  add , sub, times, div

![&#x7528;&#x4E00;&#x4E2A;&#x4E34;&#x65F6;&#x503C;&#x5B58;&#x653E;&#x4E24;&#x6570;&#x53EA;&#x548C;, &#x51FA;&#x6808;&#x4E24;&#x4E2A;,&#x5165;&#x6808;&#x4E00;&#x4E2A;, &#x6808;&#x7684;&#x5927;&#x5C0F;   &#x51CF;&#x5C11;&#x4E86;&#x4E00;](.gitbook/assets/ping-mu-kuai-zhao-2019061515.13.47.png)

###  变量内存分配的伪指令

![&#x4F2A;&#x6307;&#x4EE4; &#x662F;&#x6807;&#x8BB0;&#x76F8;&#x5173;&#x53D8;&#x91CF;&#x7684;](.gitbook/assets/ping-mu-kuai-zhao-2019061515.16.27.png)

![&#x5F88;&#x7B80;&#x5355;&#x7684;&#x6307;&#x4EE4;&#x6D41;&#x7A0B;&#x8303;&#x4F8B;, &#x4F7F;&#x7528;&#x6808;&#x6765;&#x8FDB;&#x884C;&#x8D4B;&#x503C;&#x64CD;&#x4F5C;](.gitbook/assets/ping-mu-kuai-zhao-2019061517.53.52.png)



### 递归下降生成算法

![](.gitbook/assets/ping-mu-kuai-zhao-2019061517.58.58.png)

#### 表达式的代码生成

![&#x8868;&#x8FBE;&#x5F0F;&#x7684;&#x4EE3;&#x7801;&#x751F;&#x6210;](.gitbook/assets/ping-mu-kuai-zhao-2019061518.03.34.png)

#### 语句的代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.15.47.png)

#### 类型代码的生成   \(目前只有两个类型, 一个是int , 一个是bool, 但都是数值类型\)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.18.43.png)

#### 程序的代码生成

![D&#x662F;&#x53D8;&#x91CF;&#x58F0;&#x660E;, S&#x662F;&#x8BED;&#x53E5;](.gitbook/assets/ping-mu-kuai-zhao-2019061519.19.39.png)

#### 应用如上代码的示例

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.21.34.png)



### 运行生成的代码

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.26.15.png)





## 寄存器计算机 及其代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.28.43.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061519.31.18.png)

### 寄存器计算机的指令集

![&#x65B9;&#x62EC;&#x53F7;\[\] &#x5185;&#x4EE3;&#x8868;&#x7684;&#x662F; &#x5185;&#x5B58; ](.gitbook/assets/ping-mu-kuai-zhao-2019061519.34.38.png)

* movn  n , r        
  * **将寄存器n 的 `整形值` ,赋值给 寄存器r**
* mov    r1, r2
  * **将寄存器r1 的值 , 赋值给 r2**
* load    \[x\]    r
  * 将**内存 x 位置的值, 赋值给 寄存器 r**
* store   r  \[x\]  
  * **将 寄存器r 的值, 赋值给内存 x 位置**
* add  r1,  r2   ,r3 
  * **将 寄存器r1 和 寄存器r2 的值`相加,`  然后将结果放入到寄存器 r3 里面**
* sub  r1 , r2 ,  r3
  * **将寄存器 r1的值  `减去` 寄存器 r2 的值, 然后将结果放入到寄存器 r3  里面**
* times  r1 , r2 , r3
  * **将寄存器 r1 的值  `乘上`  寄存器r2 的值,  然后将结果存入到寄存器 r3 里面**
* div   r1,  r2  ,r3
  * **将寄存器 r1 的值  `除以` 寄存器r2 的值,   然后将结果存入到寄存器r3 里面**

### 变量的寄存器分配伪指令

![&#x5982;&#x679C;&#x5BC4;&#x5B58;&#x5668;&#x4E0D;&#x591F;&#x7528;,&#x90A3;&#x4E48;&#x5C31;&#x505A;&#x6EA2;&#x51FA;,&#x653E;&#x5230;&#x5185;&#x5B58;&#x91CC;](.gitbook/assets/ping-mu-kuai-zhao-2019061519.38.36.png)



### 递归下降代码生成算法

![R\_T  &#x662F;&#x5BC4;&#x5B58;&#x5668;&#x540D;&#x5B57;](.gitbook/assets/ping-mu-kuai-zhao-2019061519.49.03.png)

### 表达式的代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061610.54.09.png)

### 语句的代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061610.56.58.png)

### 类型的代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061610.57.48.png)

### 变量声明的代码生成

![](.gitbook/assets/ping-mu-kuai-zhao-2019061610.58.51.png)

### 程序的代码生成

![D &#x53D8;&#x91CF;&#x751F;&#x6210;&#x90E8;&#x5206;,  S &#x8BED;&#x53E5;&#x751F;&#x6210;&#x90E8;&#x5206;](.gitbook/assets/ping-mu-kuai-zhao-2019061610.59.27.png)

### 生成范例

![](.gitbook/assets/ping-mu-kuai-zhao-2019061611.10.28.png)

### 运行生成的代码

![](.gitbook/assets/ping-mu-kuai-zhao-2019061611.13.05.png)

**运行的核心是 将`无限`多个寄存器抽象成 `单链表`,   或者 让`两个虚拟的寄存器` `共享` `同一个 物理寄存器`      但是要控制好什么时候可以共享, 什么时候不可以共享.**











































