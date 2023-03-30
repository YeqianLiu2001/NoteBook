![image](https://user-images.githubusercontent.com/113034973/228672711-43f839f6-6ab4-433e-9493-a84429a493a9.png)

对象存放于堆中，类和方法存放在方法区，局部变量在虚拟机栈。 
 
### 内存溢出
![image](https://user-images.githubusercontent.com/113034973/228673913-c22f93bc-1d41-4fdd-9ccf-6d161654aa89.png)
 
### 垃圾回收算法
https://juejin.cn/post/6844903639794843656 

1. 标记-清除算法 

标记-清除算法对根集合进行扫描，对存活的对象进行标记。标记完成后，再对整个空间内未被标记的对象扫描，进行回收。


 优点：
实现简单，不需要进行对象进行移动。


 缺点：
标记、清除过程效率低，产生大量不连续的内存碎片，提高了垃圾回收的频率。


2. **复制算法**//新生代垃圾回收 
 
这种收集算法解决了标记清除算法存在的效率问题。它将内存区域划分成相同的两个内存块。每次仅使用一半的空间，JVM生成的新对象放在一半空间中。当一半空间用完时进行GC，把可到达对象复制到另一半空间，然后把使用过的内存空间一次清理掉。 


优点：
按顺序分配内存即可，实现简单、运行高效，不用考虑内存碎片。


缺点：
可用的内存大小缩小为原来的一半，对象存活率高时会频繁进行复制。


3. **标记-整理算法**//老年代垃圾回收 存活率低 
 
标记-整理算法 采用和 标记-清除算法 一样的方式进行对象的标记，但后续不直接对可回收对象进行清理，而是将所有的存活对象往一端空闲空间移动，然后清理掉端边界以外的内存空间。


优点：
解决了标记-清理算法存在的内存碎片问题。


缺点：
仍需要进行局部对象移动，一定程度上降低了效率。 
 
![image](https://user-images.githubusercontent.com/113034973/228678192-8cca93d9-d643-45d2-a0d8-909b4d1750fe.png) 
 
![image](https://user-images.githubusercontent.com/113034973/228679483-21e59b93-64c1-4276-8b60-8517cb21dc36.png) 
 
 ### 并发漏标问题
 当用户线程和GC线程同时进行，在改动对象引用时需要监控。 
 ![image](https://user-images.githubusercontent.com/113034973/228680569-3ece2ebe-2a90-4fb8-a820-b2df0afb23b4.png) 
  
 ### 内存溢出
 ![image](https://user-images.githubusercontent.com/113034973/228682968-65cf9546-b2fe-4b8c-9be8-feabcbea9d18.png)
1.不要用工具类的线程池，线程池的任务队列没有大小限制，会溢出。 
2.误用带缓冲线程池。  
3.一次查询数据量太多。 
4.动态生成的类太多。 
 
### 类的加载
![image](https://user-images.githubusercontent.com/113034973/228685385-de0d005b-5010-4f02-9f3e-264f39078a4a.png) 
![image](https://user-images.githubusercontent.com/113034973/228687033-28eb2ce0-c731-405c-91e4-9d7f423502bd.png)

**对于final修饰static基本类型，并不会造成类加载。final static 的引用类型会导致类的加载和初始化** 
 
双亲委派机制，上级的加载器对下级可见
![image](https://user-images.githubusercontent.com/113034973/228688612-575e8160-bd68-42d0-b703-9a4af55ff294.png) 
 
![image](https://user-images.githubusercontent.com/113034973/228689270-3c6cac07-deeb-4b44-aa6a-6d10b495a10a.png) 
 
**虚引用**
![image](https://user-images.githubusercontent.com/113034973/228689802-cfb2d1aa-7879-427f-ad01-d0db0499856a.png)







