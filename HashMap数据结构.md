## 哈希函数
哈希函数能迅速将一个数值转化成哈希值，所以哈希表必须保持哈希值的运算一致，如果两个哈希值是不同的，那哈希值的原始输入也是不同的。 
如果两个不同输入得到同样的哈希值（在取余中很容易得到相同的），这是哈希冲突。 
输入关键字x，利用哈希函数y=f(X)算出哈希值y，利用哈希值y寻找数组下标，并在对应位置插入新数据。 
![image](https://user-images.githubusercontent.com/113034973/227087257-6ef80a92-2129-4397-be07-2c645919de7c.png)
```java
// 存储时:
int hash = key.hashCode(); // 这个hashCode方法这里不详述,只要理解每个key的hash是一个固定的int值
int index = hash % Entry[].length;
Entry[index] = value;
 
// 取值时:
int hash = key.hashCode();
int index = hash % Entry[].length;
return Entry[index];
``` 
 
 
**put** 
>疑问：如果两个key通过hash%Entry[].length得到的index相同，会不会有覆盖的危险？
这里HashMap里面用到链式数据结构的一个概念。上面我们提到过Entry类里面有一个next属性，作用是指向下一个Entry。

打个比方： 第一个键值对A进来，通过计算其key的hash得到的index=0，记做:Entry[0] = A. 一会后又进来一个键值对B，通过计算其index也等于0. 
HashMap会这样做:B.next = A,Entry[0] = B；如果又进来C,index也等于0,那么C.next = B,Entry[0] = C； 
这样我们发现index=0的地方其实是利用单链表的头插法存取了A,B,C三个键值对,他们通过next这个属性链接在一起。所以会发生覆盖的情况，数组中存储的总是最后插入的元素. 
 
 >解决哈希冲突的方法 
 >开放定址法（线性探测再散列，二次探测再散列，伪随机探测再散列）
 >
 >再哈希法
 >
 >链地址法（Java中HashMap使用的算法）
 >
 >建立一个公共溢出区
 
 >防止一个数组的一个bucket里链表过长
 >
 >1.扩容。当总<key,Value>数大于数组长度的3、4时，扩容
 >
 >2.当数组下标不变时，虽然链表长度>8，但会先选择扩容当数组长度>64时且链表长度大于8，再树化。DOS攻击 
  
  ![image](https://user-images.githubusercontent.com/113034973/227101328-c39988f8-f9b8-44d7-8ce1-5a29b4b22fc9.png)
  
 二次哈希：右移16位

  
  
