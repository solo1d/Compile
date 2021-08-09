# 符号表

## 符号表

**`符号表`是在`语义检查`和`语义分析`当中的一个`非常核心`的一个`数据结构.`**

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.48.52.png)

### 

### 符号表的接口

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.50.59.png)



### 符号表的数据结构

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.54.08.png)



### 符号表的高效实现

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.55.53.png)



### 作用域

![](.gitbook/assets/ping-mu-kuai-zhao-2019061510.58.45.png)

### 符号表处理作用域的方法

* **方法1 :   一张表的方法**
  * **`进入`**作用域时, **`插入元素 (新元素在头部插入,方便删除)`**
  * **`退出`**作用域时, **`删除元素`**
* **方法2:  采用符号表构成的 `栈`**
  * **`进入`**作用域时,  **`插入新的符号表`**
  * **`退出`**作用域时,  **`删除栈顶符号表`**



![&#x65B9;&#x6CD5;&#x4E00; &#x793A;&#x4F8B;](.gitbook/assets/ping-mu-kuai-zhao-2019061511.03.59.png)

![&#x65B9;&#x6CD5;&#x4E8C;  &#x793A;&#x4F8B;](.gitbook/assets/ping-mu-kuai-zhao-2019061511.20.57.png)

### 

### 名字空间

![](.gitbook/assets/ping-mu-kuai-zhao-2019061511.25.56.png)

![](.gitbook/assets/ping-mu-kuai-zhao-2019061511.30.15.png)













