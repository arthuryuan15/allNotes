





# 集合

day14 - day16

## 1. 数据结构

### 1.1 什么是数据结构

​		在程序设计中，为了处理方便，把数据按照某种形式组织起立，这个某种形式就是数据结构。

### 1.2 数据结构分类

  1. 传统上，我们把数据结构分为逻辑结构和物理结构

     （1）逻辑结构：指反应数据元素之间的逻辑关系的数据结构，其中的逻辑关系是指数据元素之间的前后间的关系，而与他们在计算机中的储存位置无关。

     （2）物理结构：物理结构又称存储结构，指数据的逻辑结构在计算机储存空间的存形式，也就是真正在计算机储存器中如何储存的。

     **数据结构=逻辑结构+存储结构**

     **数据结构=逻辑结构+存储结构+（在存储结构上的）运算/操作**

![Screen Shot 2019-10-05 at 2.32.52 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mabdquj30lw0ggq73.jpg)



### 1.3 逻辑结构

​		逻辑结构：指反应数据元素之间的逻辑关系的数据结构，其中的逻辑关系是指数据元素之间的前后间的关系，而与他们在计算机中的储存位置无关。

​		

​		逻辑结构也分为两类：

​		（1）线性结构

​			线性结构：有且只有一个开始点和一个终端节点，并且所有的节点都最多有一个直接前驱和直接后继。

​			举例：冰糖葫芦、排队上地铁			

​		（2）非线性结构

​			非线性结构：一个节点元素，对于多个直接前驱和多个直接后继

​			举例：公司组织结构图



### 1.4 物理结构

​		物理结构：物理结构又称存储结构，指数据的逻辑结构在计算机储存空间的存形式，也就是真正在计算机储存器中如何储存的。

​		物理结构分为：

​		顺序存储；

​		链式存储；

​		索引存储；

​		散列存储。

​		**举例：你的逻辑结构的线性表，在存储结构上，可以利用：顺序存储，也可以用链式存储！**

​		（1）顺序存储

​			把**逻辑上相邻的节点存储在物理位置相邻的存储单元**中，节点之间的逻辑关系是由存储单元的邻接关系来体现，由此得到的存储结构为顺序存储结构。

​		（2）链式存储

​			数据元素的存储对应的屎不连续的存储空间，每个存储节点对应一个需要存储的数据元素。

​			每个节点是由数据阈和指针阈组成。元素之间的逻辑关系通过存储节点之间的链接关系反应出来。逻辑上相邻的节点物理上不必相邻。

​		（3）索引存储

​			除建立存储节点信息外，还建立附加的索引来表示节点的地址。

​			举例：给书找一个目录	

​		（4）散列存储

​			散列表，哈希表，非常神奇：查询，添加非常快

​			结构：数组+链表

​		

以下是讨论一下逻辑结构对象的存储结构实现

### 1.5 线性表

#### 1.5.1 逻辑结构

 		线性表中数据元素的个数n定义为线性表的长度，n是个有限值。

​		但n=0时线性表为空表，

​		当非空的线性表中每个数据元素在线性表中都有唯一确定的序号，

​		例如a0的序号是0，ai是序号是i。

​		在一个具有n>0个数据元素的线性表中，数据元素序号的范围是[0,n-1]。

​		线性表逻辑结构对应的顺序存储结构为顺序表，对应的链式存储结构为链表。

#### 1.5.2 存储结构

​		逻辑结构为线性表的结果，存储结构的顺表，链表可以帮助你实现。

​		（1）顺序表

​				数组是顺序表的经典案例

​				数据特点：

​				优点：按照索引查询效率高

​				缺点：按照内容查找效率低	

​		（2）链表

​				单向链表，每个节点只有一个指针域，指向下一个节点！		

​				缺点：查找元素：效率低，因为各个节点的地址完全没有规律可循		



### 1.6 栈和队列

​		栈和队列，是操作受限的线性表，既然是线性表，那么你用顺序表，链表都可以实现。

​		受限的含义：

​		栈：先进后出，后进先出 	

​		队列：先进先出	



```java
package com.leetcode;

import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;

public class Main {

    public static void main(String[] args) {

        // stack
        Stack<Integer> stack = new Stack<>();
      
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack); // [1, 2, 3]
        stack.pop(); // 3
        System.out.println(stack); // [1, 2]
        System.out.println(stack.peek()); // 2
        System.out.println(stack); // [1, 2]

        // queue
        // LinkedList类实现了Queue接口，因此我们可以把LinkedList当成Queue来用。
        Queue<Integer> queue = new LinkedList<>();
      
      
        queue.offer(1); // 避免满队列添加异常
        queue.offer(2);
        queue.offer(3);
        System.out.println(queue); // [1, 2, 3]
        queue.poll(); // 返回第一个并删除, 避免为null的异常
        System.out.println(queue); // [2, 3]
        System.out.println(queue.peek()); // 2
        System.out.println(queue);  // [2, 3]

    }
}
```

Summary:

```
Stack<Integer> stack = new Stack<>();
stack.push() stack.pop() stack.peek()

Queue<Integer> queue = new LinkedList<>();
queue.offer() queue.poll()
```







### 1.7 树

​		我们可以形式地给出树的递归定义如下：

​		数（Tree）是n（n>=0）个节点的有限集。它

​		（1）或者是一颗空树(n = 0) ，空树中不包含任何节点。

​		（2）或者是一颗非空树（n > 0），此时有且仅有一个特定的称为根的节点：

​			当 n > 1时，其余节点可分为m（m>0）个互补相交的有限集T1.T2,….,Tm

​			其中每一个本身又是一棵树，并且称为根的子树(sub tree).

​			

​			**节点的度和数据的度**

​			节点拥有的子树的数目称为节点的度（Degree）。

​			度为0的节点称为叶子（leaf）或者终端节点。

​			度不为0的节点称为非终端节点或分支节点。除了根之外的分支节点也称为内部节点。

​			树内个节点的度的最大值称为树的度。

​		

​			**二叉树**

​			每个节点的度不超过2的有序树，称为二叉树（binary tree）

```java
public class TreeNode {

    // Definition for a binary tree node.
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}
```

​			用数组表示二叉树



			Java 一维数组转换二叉树 ： https://leetcode-cn.com/circle/article/htJ97s/

<img src="https://tva1.sinaimg.cn/large/008eGmZEly1gopcc95ynvj30wx0u0gq9.jpg" alt="image-20210319172639254" style="zoom: 50%;" />



​			**满二叉树**

​			高度为k并且有2^(k+1)-1个节点的二叉树。

​			在满二叉树中，每层节点都到达最大数，即每层节点都是满的，因此称为满二叉树。		

​			

​			**二叉查找树/搜索树/排序树**（Binary Search Tree）

​			或者是一颗空树:

​			或者是具有下列性质的二叉树：

​			（1）若它的左子树不为空，则左子树上所有节点的值均小于它的根节点的值

​			（2）若它的右子树上所有的节点的值均大于它的根节点的值

​			（3）它的左，右子树也分为二叉排序树。

​			![Screen Shot 2019-10-05 at 4.06.11 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5ml96akj30o009iwf8.jpg)

​			特点：

​			左子树上所有节点的值均小于它的根节点的值

​			==注意：对于二叉查找树进行中序遍历，就可以得到有序集合==



​			**平衡二叉树**

​			左右两个子树的高度差（平衡因子）的绝对值不超过1

​			![Screen Shot 2019-10-05 at 4.12.06 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mks9c4j30ji0eg74v.jpg)

​	目的：减少层数，提高查询效率

​			

​			**B-树**	

​			定义：B树是一种多路平衡查找树，它的每一个子节点最多包含k个孩子，k被称为B树的阶。k的大小取决于磁盘页的大小。

​			特征：

​			（1）根节点至少有两个子女

​			（2）每个中间节点包含k-1个元素和k个孩子

​			（3）每个叶子节点都包含k-1个元素

​			（4）所有的叶子节点都位于同一层

​			（5）每个节点中的元素从小到大排列，节点当中k-1个元素正好是k个孩子包含的元素的值域划分。

![Screen Shot 2019-10-24 at 1.59.14 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mpmvj5j310i0g2jsb.jpg)

​			**B+树**

​			B+树是B树的一种变体，查询性能更好。m阶的B+树的特征：

​			（1）有n棵子树的非叶子节点中包含n个关键字（B树是n-1个），这些关键字不保存数据，只用来索引，所有的数据都保存在叶子节点（B树的每个关键字都保存数据）。

​			（2）所有的叶子节点中包含全部关键字的信息，以及指向这些关键字记录的指针，且叶子节点本身依关键字的大小自小而大顺序连接。

​			（3）所有的非叶子节点都可以看成索引部分，节点中仅含其子树中的最大（或最小）关键字。

​			（4）通常在B+树上有两个头指针，一个指向根节点，一个指向关键字最小的叶子节点。

​			（5）同一个数据会在不同节点中重复出现，根节点的最大元素就是B+树的最大元素。

​		

​			**红黑树**

​			定义：R-B tree，又称为红黑树，它是一种平衡二叉树，红黑树的每个节点上都与存储位表示节点的颜色，可以是红（Red）或者黑（Black）

​			特性：

​			（1）每个节点都是黑色或者红色

​			（2）根节点是黑色

​			（3）每个叶子节点（NIL）是黑色【注意：这里叶子节点，是指为空（NIL或NULL）的叶子节点！】

​			（4）如果每一个节点都是红色的，则它的子节点必须是黑色的。

​			（5）从一个节点到该节点的子孙节点的所有路径上包含相同数目的黑节点

​			java集合中的TreeSet和Treemap， 都是通过红黑树去实现的。 

​		

### 1.8 图

​		图是一种网状数据结构，图是由非空的顶点结合和一个描述顶点之间关系的集合组成的。

​		加权图。

​	

## 2. 集合引入

1. 为什么使用集合？ 

   举例：存储学生的成绩 

   以前：用数组  缺点：长度一旦确定就没有办法再修改了，所以如果删除或者增加元素，大量移动元素的位置。 

   特点：数组只能放一种数据类型，可以是基本数据类型也可以是引用数据类型（类、接口、数组）

   

   引入一个方法东西的-------》容器（集合） 

   优点：增加删除元素效率高 

   特点：一个集合可以方法多种数据类型，（**但是一般我们都使用泛型，让他只放一种类型。**） **但是它只可能放引用数据类型。** （所以数据类型要转换成包装类）

   所以：集合能不能放int类型数据？不能。int类型可以进行自动装箱，转成包装类的Integer类型方放入集合。 

   

2. 我们学习的集合，是各种各样的集合，为啥要学习不同的集合？ 

   数据结构不一样，导致集合不一样，特点不一样。 



3. 集合有哪些？简要结构图： 


![Screen Shot 2019-09-28 at 9.24.11 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5moizqwj32280q8jwe.jpg)

说明：

1. 左边一个一个存，右边一对一对存
2. List 和 Set 是Collection的子接口 List extends Collection
3. ArrayList是List这个interface的implementation class 
4. map不是继承自Collection的，所以会另行介绍。但Map也应被当做Collection Framework的一部分。



1. 集合的应用场景： 

   当需要将相同结构的个体整合到一起的时候，就考虑使用集合。 

![Screen Shot 2019-09-28 at 9.24.47 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mi163jj31x80q8n25.jpg)

​	（1）邮箱： 

![Screen Shot 2019-09-28 at 9.24.59 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mmkvaoj31nc0ta10a.jpg)

​	（2）淘宝： 

![Screen Shot 2019-09-28 at 9.25.06 PM](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mdo29fj31380p0wgs.jpg)

## 3. Collection接口

```java 
public class Test {
    public static void main(String[] args) {
      
        /*
        接口常用方法：
        增加：add(E e)   addAll(Collection<? extends E> c)
        删除：clear()  remove(Object o)
        修改：
        查看：iterator()  size()
        判断：contains(Object o)  equals(Object o)  isEmpty()
        其他：toArray in interface Collection<E>
         */
      
        //Collection:接口不能创建对象：所以用下面的一个实现类创建
        Collection col=new ArrayList(); // 4个实现类都可以
        col.add(11);
        col.add("aaaa");//表面上是int类型数据，实际12进行了自动装箱  然后我放入的是Integer数据
        //Integer i=12;  col.add(i);
        col.add(33);//Double
      
        Collection col2=new ArrayList();
        col2.add(11);
        col2.add(22);
        col2.add(33);
        //col.addAll(col2);
      
        System.out.println(col.equals(col2));//true:证明底层一定重写了equals，比较的是具体的元素的值。
        System.out.println(col==col2);//false：一定返回的是false，因为比较的是地址的值。
      
        System.out.println("------------------");
        col.remove("anc");
        System.out.println(col/*.toString()*/); // 自动补上toString()
        System.out.println("集合中放的元素的个数："+col.size());
        System.out.println( col.contains(11));
      
        /*col.clear();
        System.out.println(col*//*.toString()*//*);
        System.out.println("集合中放的元素的个数："+col.size());
        System.out.println(col.isEmpty());*/
      
        System.out.println("-----------集合的遍历：-----------------");
      
        //方法1：普通for循环：---不行：因为没有提供  根据索引获取元素的 方法
        /*for(int i=0;i<=col.size()-1;i++){
            System.out.println(col);
        }*/
      
        //方法2：增强for循环：
        for(Object o:col){// 因为集合里面放的也可能是字符串和int类型，所以不能用Integer类型接，不用int，是因为Collection存的引用数据类型，没有基本数据类型
            System.out.print(o+"\t");
        }
      
        System.out.println("\n---------------------------------");
        //方法3：iterator()  迭代器：
        Iterator it= col.iterator();
        while(it.hasNext()){ // 判断下面是否有元素，如果有返回True
            System.out.println(it.next());// 把it的next输出，hasnext下移一位
        }
    }
}
```

迭代器原理：

![image_38318](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mndkpjj310n0djtay.jpg)



###  3.1 第一个子接口List

​		大多数时候List只调用add()添加对象，使用get()一次取出一个元素。

```java
public class Demo {
    public static void main(String[] args) {
      
        List list=new ArrayList();
      
      /*
        常用方法：
        增加：add(int index, E element)
        删除：remove(int index)
        修改：set(int index, E element)
        查看：get(int index)
        判断：
         */
      
      	list.add(12);
        list.add(82);
        list.add(20);
        list.add(38);
        list.add(1);
        list.add(1,666);
        
      	list.remove(1);
        list.set(2,999);
        
      	System.out.println(list);
        System.out.println(list.size());
        System.out.println(list.get(3));
        
      	//对List集合的遍历：
        //方式1：普通for循环：
      	System.out.print("[");
        for(int i=0;i<=list.size()-1;i++){
            if(i!=list.size()-1){
                System.out.print(list.get(i)+", ");
            }else{
                System.out.print(list.get(i)+"]");
            }
        }
        
      	System.out.println("\n----------------------");
        //方法2：增强for循环：
        for(Object o:list){
            System.out.println(o);
        }
        
      	System.out.println("\n----------------------");
        //方式3：迭代器：
        Iterator it = list.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }
    }
}
```



#### 3.1.1 实现类:ArrayList

​		下面的总结：ArrayList底层就是数组，那些方法其实就是对数组进行增删改查操作。 

【1】测试代码和源码

```java
public class Test2 {
    public static void main(String[] args) {
        //创建一个ArrayList对象：
        ArrayList al=new ArrayList();//调用构造器，底层数组是{},长度为0
        ////第一次调用add方法：
        al.add("abc");
    }
}
```



```java
public class ArrayList{
  	
  	private static final int DEFAULT_CAPACITY = 10; // 默认的长度为10
  
    //ArrayList底层是一个Object类型的数组
    transient Object[] elementData; 

    //这个Object类型的数组被使用的数量。
    private int size; // 这个size用private修饰了，所以只能用构造器访问

    //就是一个空的Object的数组
    private static final Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};

    //空构造器：底层数组 长度0
    public ArrayList() {
      this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
      //赋予了一个{}数组---->this.elementData = {}
    }

    public boolean add(E e) {//实际参数："abc"
      ensureCapacityInternal(size + 1);  // 经历了这个方法，底层已经将数组扩容为10了
      elementData[size++] = e;//elementData[0]="abc"   然后size+1操作
      return true;
    }

    private void ensureCapacityInternal(int minCapacity) {//1
      //ensureExplicitCapacity(10)
      ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));      
    }

    private static int calculateCapacity(Object[] elementData, int minCapacity) {//参数：{},1
      //  现在elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA满足，返回的是true，走这个if了
      if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {
        //return Math.max(10,1);---->10                     
        return Math.max(DEFAULT_CAPACITY, minCapacity);
      }
      return minCapacity;
    }

    private void ensureExplicitCapacity(int minCapacity) {//参数：10
      modCount++;
      // overflow-conscious code
      if (minCapacity - elementData.length > 0)//10-0》0--》if是执行的
        grow(minCapacity);//grow(10)
    }

    // 数组的扩容
    private void grow(int minCapacity) {	//minCapacity:10
      
      int oldCapacity = elementData.length;	//oldCapacity:0
      int newCapacity = oldCapacity + (oldCapacity >> 1);	//newCapacity:0
      if (newCapacity - minCapacity < 0)	//if(0-10<0)-->这个分支走：
        newCapacity = minCapacity;	//newCapacity:10
      if (newCapacity - MAX_ARRAY_SIZE > 0)	//不走
        newCapacity = hugeCapacity(minCapacity);	//不走
      //完成了数组的扩容，将原来的{}数组复制到长度为10的新数组中
      //并且将ArrayList底层的老数组变成了长度为10的新数组。
      elementData = Arrays.copyOf(elementData, newCapacity);
      
    }                                             
```

总结：调用空构造器和第一次add做了什么事？ 

​			首先将底层的数组扩容为长度为10 ，然后在长度为10的新数组中添加元素： 如果放小于10个元素在数组中，那么数组不扩展，当放入第11个字符串，扩充到原来的1.5倍，数组长度从10变成15，（见下面的代码）然后再在长度为15的长度上放数。

【2】`int newCapacity = oldCapacity + (oldCapacity >> 1);`

```java
public class Test2 {
    public static void main(String[] args) {
        //创建一个ArrayList对象：
        ArrayList al=new ArrayList();//调用构造器，底层数组是{},长度为0
        ////第一次调用add方法：
        al.add("abc");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("ggg");
        al.add("asdfasdfasdf");//放入第11个字符串：
        x
    }
}
```



```java
public class ArrayList{
  
        //ArrayList底层是一个Object类型的数组
        transient Object[] elementData; 
        //这个Object类型的数组被使用的数量。
        private int size;
        //就是一个空的Object的数组
         private static final Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};
         
         
         public boolean add(E e) {//参数："asdfasdfasdf"
        ensureCapacityInternal(size + 1);  // 经历完这个方法，底层数组已经扩容为新的长度为15的了
        elementData[size++] = e;//elementData[10]="asdfasdfasdf"  然后进行size+1操作 size:11
        return true;
    }
        
        
        private void ensureCapacityInternal(int minCapacity) {//11
                //calculateCapacity(长度为10的老数组，11)
                //ensureExplicitCapacity(11)
        ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));//
    }
        
        private static int calculateCapacity(Object[] elementData, int minCapacity) {
        if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {//分支不走
            return Math.max(DEFAULT_CAPACITY, minCapacity);
        }
        return minCapacity;//走这个返回11
    }
         
         
         private void ensureExplicitCapacity(int minCapacity) {//11
        modCount++;
        // overflow-conscious code
        if (minCapacity - elementData.length > 0)//11-10>0--->走
            grow(minCapacity);//grow(11)
    }
         
         
         private void grow(int minCapacity) {//minCapacity:11
        
        int oldCapacity = elementData.length;//oldCapacity:10
        int newCapacity = oldCapacity + (oldCapacity >> 1);//newCapacity:15 :扩容长度是原来的1.5倍
        if (newCapacity - minCapacity < 0)//不走
            newCapacity = minCapacity;//不走
        if (newCapacity - MAX_ARRAY_SIZE > 0)//不走
            newCapacity = hugeCapacity(minCapacity);//不走
        			//底层老的数组 从长度为10变成了长度为15
                //并且ArrayList底层数组的指向  指向了新的长度为15的数组
        elementData = Arrays.copyOf(elementData, newCapacity);
    }        
}
```

【3】`al.isEmpty();`

```java
public boolean isEmpty(){
  return size == 0;
}
```

【4】`al.clear();`

```java
 public void clear() {
   
        modCount++;
        
        for (int i = 0; i < size; i++)//对数组进行遍历
            elementData[i] = null;//数组中的每个位置都置为null
        size = 0;//数组中被占用的数量size置为0
    }
```

【5】` al.remove("abc");`

```java
public boolean remove(Object o) {//参数：“abc”
        if (o == null) {//不走
            for (int index = 0; index < size; index++)
                if (elementData[index] == null) {
                    fastRemove(index);
                    return true;
                }
        } else {//走这个       
            for (int index = 0; index < size; index++)	//对数组进行遍历
                if (o.equals(elementData[index])) {	//找数组中有没有元素"abc"
                    //假如找到了才走下面的方法
                    //fastRemove:删除这个元素了
                    //fastRemove（这个元素对应的索引）
                    fastRemove(index);	//fastRemove(0)
                    return true;
                }
        }
        return false;
    }
        
        
   	private void fastRemove(int index) {//0
        modCount++;
        int numMoved = size - index - 1;//numMoved:5
        if (numMoved > 0)//走这个分支
                //System.arraycopy(elementData,1，elementData，0,5）---》底层通过数组的复制完成了删除操作
            System.arraycopy(elementData, index+1, elementData, index, numMoved);
        elementData[--size] = null; //将数组中有效位置最后一个置为null
    }
```

​	总结：通过System.arraycopy， 从下标为1的开始，把其元素移动到复制到下标为0实现。

【6】`al.get(3);`

```java
public E get(int index) {//3
        rangeCheck(index);
        return elementData(index);//elementData(3)
    }        
         E elementData(int index) {
        return (E) elementData[index];//elementData[3]
    }
```

【7】`al.set();`

```java
    public static void main(String[] args) {
        // 创建一个ArrayList对象
        ArrayList al = new ArrayList(); // 调用构造器，底层数组是{},长度为0
        al.add(12);
        al.add(13);
        al.add(14);
        System.out.println(al);
        al.set(2, 100); //set(int index, E element)
        System.out.println(al);
    }
```



2. 自己模拟一个ArrayList

```java
package com.sxt.test02;

import java.util.Arrays;

public class MyArrayList {

    // MyArrayList底层也是一个Object类型的数组
    Object[] value;

    // 数组中被使用的数量
    int count;

    // 空构造器
    public MyArrayList() {
//        value = new Object[10];
        this(10); // 2. 空构造器底层又调用一个有参构造器
    }

    // 有参构造器
    public MyArrayList(int length){ // 3. 然后这个有参构造器传了一个10
        value = new Object[length]; // 4. value是一个长度为10的数组
    }

    // 添加add方法
    public void add(Object o){
        value[count] = o;
        count++;

        // 进行数组扩容
        if(count >= value.length){ //长度不够

            // 扩容方式1：Object[] new Obj = Arrays.copyOf(value, 20);

            // 扩容方式2: 有新数组
            Object[] newObj = new Object[value.length*2 + 1]; // 10*2+1=21
          
            // 将老数组中的东西 复制 到新数组中；
            for(int i = 0; i <= value.length-1; i++){
                newObj[i] = value[i]; // 手动完成数组的复制
            }
          
            // 将value的指向：指向新的数组
            value = newObj;

            // 扩容方式3: System.arraycopy();
        }
    }

    // 重写toString
    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder(); // new一个可变字符串
        sb.append("["); // 拼接左边的[
        for(int i = 0; i <= count-1; i++){
            sb.append(value[i] + ","); // 将数组遍历拼接
        }
        sb.setCharAt(sb.length()-1, ']'); // 将最后一个逗号换成], 注意替换的是char类型
        return sb.toString();
    }

    // 增加一个计算数组中元素个数的方法：
    public int length(){
        return count;
    }

    // 判断是否为空;
    public boolean isEmpty(){
        return count==0;
    }

    public static void main(String[] args) {
        // 创建一个我自定义的数组的对象
        MyArrayList list = new MyArrayList(); // 1. 这里调用的是空构造器，底层数组长度为10
        list.add("assf");
        list.add("asdadadff");
        list.add(1244);
        list.add("assf");
        list.add("asdadadff");
        list.add(1244);
        list.add("assf");
        list.add("asdadadff");
        list.add(1244);
        list.add("qeqeqe");
        list.add("sadada"); // 添加第11个数

        System.out.println(list);// 这里打印调用的是object的ToString，子类对父类的方法不满意了，要override

        System.out.println("集合中元素的数量:" + list.length());
        System.out.println(list.isEmpty());
    }
}
```



3. 将自定义的引用数据类型存入ArrayList集合

【1】代码：

```java
package com.sxt.test03;

import java.util.ArrayList;
import java.util.Iterator;

public class Student {
    // 属性
    private int age;
    private  String name;

    // 方法

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public String getName(){
        return name;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }

    // 构造器

    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

    // main方法
    public static void main(String[] args) {

        // 创建一个ArrayList集合对象
        ArrayList al = new ArrayList();
        Student s = new Student(19, "feifei"); // 在堆和栈中均开辟空间
        al.add(s);
        al.add(new Student(21, "lulu")); // 匿名对象存入集合，只在堆中开辟空间，然后把引用地址给al
        al.add(new Student(22, "lili"));

        // 遍历
        // 普通for循环
        // 增强for循环
        // 迭代器
        Iterator it = al.iterator();
        while(it.hasNext()){
//            Object stu =it.next(); //放到集合里的不一定只是object类，也有可能是其他的类
            Student o = (Student)(it.next()); // 将object类型转成Student类型
            System.out.println(o.getName() + "--------" + o.getAge());

        }

    }
}
```



【2】代码尝试改动：

```java
Iterator it = al.iterator();
        while (it.hasNext()){
            System.out.println(((Student)(it.next())).getName() + "--------" + ((Student)(it.next())).getAge());
        }
```

结果出错

分析原因就是next方法“指针下移“，导致错位现象、



#### 3.1.2 实现类:Vector

【1】将之前代码中的ArrayList全部替换为Vector，执行结果一模一样 

【2】

![image_29044](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mqac6dj30s50e775x.jpg)

​	联系：实现的效果一样，底层都是数组

​	区别： ArrayList扩容：1.5倍 ； Vector扩容:2倍 —》底层数组扩容数量不一样

​				ArrayList: 	JDK1.2     效率高	 线程不安全

​				Vector：	  JDK1.0     效率低     线程安全

​				数组：有点查询快, 缺点;    增加和删除效率低



#### 3.1.3 泛型

1.基本应用

```java
package com.sxt.test03;

import java.util.ArrayList;
import java.util.Iterator;

public class Student {
    // 属性
    private int age;
    private  String name;

    // 方法

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public String getName(){
        return name;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }


    // 构造器
    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

    // main方法
    public static void main(String[] args) {

        // 创建一个ArrayList集合对象
        // 加入泛型，作用：限制放入集合中元素的类型的，将类型限制为同一种类型
        // 加入泛型：其实就是对编译期间生效，在编译期间就不允许我添加其他的类型了
      	// 泛型是在JDK1.5之后出现的，所以只能用<>
        ArrayList<Student> al = new ArrayList<Student>();
        al.add(new Student(21, "lulu")); // 匿名对象存入集合，只在堆中开辟空间，然后把引用地址给al
        al.add(new Student(21, "lulu2"));
        al.add(new Student(21, "lulu3"));
        al.add(new Student(21, "lulu4"));

        /*al.add("1222");
        al.add(12);
        al.add(8.3); // Collection可以放任何类型的元素
        */

        // 增加for循环的遍历：
        /*for(Object o:al){ // Object o=学生对象 父类引用指向子类对象
            System.out.println(o); // 表示是调父类toString，实际上是调子类重写的toString
        }*/

        // 加了泛型之后，遍历更加简单了，直接用泛型类型接收即可
        for(Student s:al){
            System.out.println(s);
        }
    }
}

```



扩展：

​		就是为了让你能看懂API： 不是为了让你自己写代码用的。 

1. 泛型类

   ```java
   package com.sxt.test04;
   
   import com.sxt.test01.Test;
   
   public class TestGeneric<AA> {
   
       // 泛型其实就是一个普通的类，加了<>就变成了泛型类
       // <>中的字母可以是什么？啥都行，但是在API中一般叫E
       // <AA>就好像是一个占位符，就是告诉别人这里加了泛型，但是这个泛型是什么还不能确定
       // 什么时候确定，创建对象的时候才确定
   }
   
   class A{
       public static void main(String[] args) {
           // 创建一个普通类的对象：
           TestGeneric tg = new TestGeneric();
           // 加上泛型：
           TestGeneric<Integer> tg1 = new TestGeneric<Integer>();
           TestGeneric<String> tg2 = new TestGeneric<String>(); 
   
       }
   }
   ```

2. 泛型方法

   ```java
   package com.sxt.test04;
   
   import com.sxt.test01.Test;
   
   public class TestGeneric<AA> {
   
       // 普通方法：可以
       public void a(){}
       // 方法的参数是AA，AA的类型确定吗？确定，AA在创建的时候就已经确定了
       public void b(AA a){}
       // 方法的参数是BB，BB的类型确定吗？BB类型不确定
       // 帮我们解决了不同数据类型做参数的重载问题
       public<BB> void c(BB b){}
   
       //public static void d(AA a){} // static 是先于对象存在的，然而对于AA，是有对象才能确定
       public static <BB> void e(BB b){} // 然而无论有没有BB，都知道对象是谁
   
       public void f(AA[] a){}
   
       public<QQ> QQ[] g(QQ...q) {
           // 参数为可变参数，内部当做数组处理；
           for(QQ a:q){
               System.out.println(a);
           }
           return q; 
       }
   }
   
   class A{
       public static void main(String[] args) {
           // 创建一个对象：
           TestGeneric<Integer> tg = new TestGeneric<Integer>();
           // AA的类型确定为Integer
           tg.b(12);
           tg.c(12);
           tg.c("adada");
           tg.f(new Integer[]{12,34,43});
           tg.g();
           tg.g(12,3,4,5,5);
           tg.g("adaed","adada", "adada");
   
       }
   }
   ```

   

3. 泛型接口

   ```java
   package com.sxt.test05;
   
   public interface MyInterface<AA> {
   
   }
   
   class A implements MyInterface{}
   
   class B implements MyInterface<String>{}
   
   // 实现类在实现的时候不确定，那么这个实现类就变成了泛型类
   class C<BB> implements MyInterface<BB>{
       public void a(BB b){
           
       }
   }
   ```

   

4. 泛型受限

    泛型的上限： ` ? extends A`   :只要泛型为A或者A的子类都可以传入 

   泛型的下限： ` ?  super A` :只要泛型为A或者A的父类都可以传入 

	`<? extends A>` 代表小于等于A的范围，`<? super A>`代表大于等于A的范围，`<?>`代表全部范围

   **List<?>和List 是相等的，都代表最大范围**

    ```java
   package com.sxt.test06;
   
   import java.util.ArrayList;
   
   public class Person {
   
       int age;
       
       public Person(int age) {
           this.age = age;
       }
       
       @Override
       public String toString() {
           return "Person{" +
                   "age=" + age +
                   '}';
       }
       
       public Person(){
       }
   }
   
   class Student extends Person{
       String name;
   
       public Student(int age, String name) {
           super(age);
           this.name = name;
       }
       
       public Student(String name) {
           this.name = name;
       }
       
       @Override
       public String toString() {
           return "Student{" +
                   "name='" + name + '\'' +
                   '}';
       }
   }
   
   class Test{
   
       public static void main(String[] args) {
           // 创建一个Person类，将对象放入集合中
           ArrayList<Person> al = new ArrayList<Person>();
           al.add(new Person(18));
           al.add(new Person(20));
           al.add(new Person(14));
           show(al);
       
           ArrayList<Student> al2 = new ArrayList<Student>();
           al2.add(new Student("nana"));
           al2.add(new Student("feifei"));
           al2.add(new Student("lili"));
       
           show(al2);
       }
       
       // 泛型受限：泛型的上限：只要是Person或者Person子类 都可以传入
        public static void show(ArrayList<? extends Person> al){
            // 对集合进行遍历
            for(Person p:al){
                System.out.println(p);
            }
       }
   
   
    /*public static void show(ArrayList<Student> al2){
           for(Student s: al2){
               System.out.println(s);
        }
       }*/
   }
    ```

#### 3.1.4 实现类:LinkedList

​		**LinkedList可以实现栈、队列以及双端队列等数据结构.**

​		实现队列

```java
        LinkedList q =  new LinkedList();
        q.add(1);
        q.add(2);
        q.add(3);
				System.out.println(q.remove()); // 1
```

​		实现栈

```java
        LinkedList stack = new LinkedList();
        stack.add(1);
        stack.add(2);
        stack.add(3);
				System.out.println(q.removeLast()); // 3
```

​	

​	对于添加和删除操作add和remove，一般LinkedList要比ArrayList快。

​		

【1】基本代码

 ```java
package com.sxt.test07;

import java.util.LinkedList;

public class Test {

    /*
    LinkedList 常用方法：
    增加：addFirst(E e)       addLast(E e)
         offerFirst(E e)     offerFirst(E e)
    删除：pollFirst()         pollLast()   --->JDK1.6 处理异常的方式更加健壮
    修改：removeFirst()       removeLast() --->JDK1.2
    查看：getFirst()          getLast()	
         peekFirst()         peekLast()  区别是peeklast在链表为空时会返回null而不会报错
    判断：
    * */
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<String>();
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        list.add("eee");
        list.add("fff");
        System.out.println(list);

        list.clear();
        list.pollFirst();
        list.pollFirst();
        System.out.println(list);

  /*      list.removeLast();
        list.removeFirst();
        System.out.println(list);
*/

    }
}
 ```

【2】底层结构

```java
public class Test {
    
    public static void main(String[] args) {
        LinkedList<String> list=new LinkedList<String>();
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        
    }
}
```

![image_19284](https://tva1.sinaimg.cn/large/008eGmZEly1gonwwnz4wzj30qm0aeq2x.jpg)

【3】遍历

```java
public class Test {
    public static void main(String[] args) {
        LinkedList<String> list=new LinkedList<String>();
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        list.add("eee");
        list.add("ffff");
        //遍历：
        //普通for循环：
        for(int i=0;i<=list.size()-1;i++){
            System.out.println(list.get(i));
        }
        //增强for：
        for(String s:list){
            System.out.println(s);
        }
        
        //迭代器：
        //理解简单
        /*Iterator<String> it = list.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }*/
        // for(条件初始化;条件判断;)
        // 虽然难理解，但是这个好；因为这个定义的it只在{}之内起作用,上面的it，只要main方法不结束就一直运行
        for(Iterator<String> it = list.iterator();it.hasNext();){
            System.out.println(it.next());
        }
    }
}
```

【4】模拟LinkedList

​		构造节点

```java
package com.sxt.test08;

public class Node { // 节点类

    // 定义属性
    private Object pre; //节点前一个元素的指向
    private Object obj; //节点当前的元素
    private Object nex; // 节点后一个元素的指向

    // 提供setget方法

    public void setPre(Object pre) {
        this.pre = pre;
    }

    public void setObj(Object obj) {
        this.obj = obj;
    }

    public void setNex(Object nex) {
        this.nex = nex;
    }

    public Object getPre() {
        return pre;
    }

    public Object getObj() {
        return obj;
    }

    public Object getNex() {
        return nex;
    }

    @Override
    public String toString() {
        return ""+obj;
    }
}
```



​	(1) add 方法模拟

```java
package com.sxt.test08;

public class MyLinkedList {
  
    // 这个链表中一定有一个头结点
    Node first;
    // 这个链表中一定有一个尾节点
    Node last;
    // 计数器：
    int count = 0;

    public MyLinkedList(){}

    // 添加元素：
    public void add(Object o){
        // 如果你放入的是第一个元素
        if(first==null){
            // 创建一个节点的对象
            Node n = new Node();
            n.setPre(null);
            n.setObj(o);
            n.setNex(null);

            // 将这个链表的first和last都指向新的这个节点n
             first = n;
             last = n;

        }else { 
          	// 第二个节点以后都走这个分支
          
            // 1. 创建第一个节点的对象
            Node n = new Node();
            n.setPre(last); // 放入当前链表中的last节点
            n.setObj(o);
            n.setNex(null);
            
          	// 2. 再将链表中的最后一个节点的next指向新创建的节点
            last.setNex(n);
            
          	// 3. 将链表的最后一个节点变成我新创建的节点
            last = n;
          
        }
        count ++;
    }

    public Object get(int index){
         Node n = first;
         for(int i = 0; i <index; i++){
             n = (Node)(n.getNex());
         }
         return n.getObj();
    }


    public static void main(String[] args) {
         // 创建我自定义的链表集合的对象：
        MyLinkedList ml = new MyLinkedList();
        ml.add("aaa");
        ml.add("bbb");
        ml.add("ccc");
        System.out.println(ml.count);

        System.out.println(ml.get(1));

        System.out.println(ml.get(2));
    }
}
```

​		注：可以用数组模拟链表

【2】源码简单查看： 

 a.构造器

```java
		public LinkedList() {
    }
```

​		注：构造器里面什么也没有  

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable {
  
  	/*省略*/
		
  	private static class Node<E> { // 定义的内部类
        E item;
        LinkedList.Node<E> next;
        LinkedList.Node<E> prev;

        Node(LinkedList.Node<E> prev, E element, LinkedList.Node<E> next) {
            this.item = element;
            this.next = next;
            this.prev = prev;
        }
    }
  	
  	/*省略*/

}
```

​	注：与上面定义一个单独的类不同的是这里定义了一个内部类

b.add第一个元素

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable {
  
  	/*省略*/
		

		//假如放入的是第一个结点“aaa”-->first=null  last=null
    void linkLast(E e) {//"aaa"
        
      	final Node<E> l = last;//l:null
      
       	//将我放入的元素封装成为一个Node对象：利用构造器进行赋值：(null,"aaa",null)
      	final Node<E> newNode = new Node<>(l, e, null);
        last = newNode;//将链中last指向新的结点newNode
        
      	if (l == null)//如果last等于空的话（第一个），走
            first = newNode;//将链中first指向新的结点newNode
        else
            l.next = newNode;
        size++;//size计数器加1
        modCount++;
    }
  	
  	/*省略*/

}
```



c.add第2个元素

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable {
  
  	/*省略*/

	//假如放入的是第2个结点“bbb”-->first="aaa"  last="aaa"
  void linkLast(E e) {//"bbb"
    final Node<E> l = last;//l:"aaa"
    
    //将我放入的元素封装成为一个Node对象：利用构造器进行赋值：("aaa","bbb",null)
    final Node<E> newNode = new Node<>(l, e, null);
    last = newNode;//将链中last指向新的结点newNode
    if (l == null)//不走
      first = newNode;
    else//走
      l.next = newNode;//将“aaa”的下一个指向newNode
    size++;//size计数器再加1
    modCount++;
  }
  
	/*省略*/
  
}
```



d.clear()

​		将链表中能是空的全部为空

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable {
  
  	/*省略*/

	public void clear() {
  	// Clearing all of the links between nodes is "unnecessary", but:
    // - helps a generational GC if the discarded nodes inhabit
    //   more than one generation
    // - is sure to free memory even if there is a reachable Iterator
    for (Node<E> x = first; x != null; ) {
    	Node<E> next = x.next;
      x.item = null;
      x.next = null;
      x.prev = null;
      x = next;
    }
    first = last = null;
    size = 0;
    modCount++;
  }

	/*省略*/
  
}
```



e.get(index)

​		size是链表的计数器，size/2将索引分为左右两部分， 

​		如果是左面的部分：正序查找 

​		如果是右面的部分：倒叙查找 

```java
public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable {
  
  	/*省略*/
  
    Node<E> node(int index) {
        // assert isElementIndex(index);
      	// 分为前半段和后半段分别查找
        if (index < (size >> 1)) { // size除2
            Node<E> x = first;
            for (int i = 0; i < index; i++)
                x = x.next;
            return x;
        } else {
            Node<E> x = last;
            for (int i = size - 1; i > index; i--)
                x = x.prev;
            return x;
        }
    }
  
  
	/*省略*/
  
}
```



### 3.2 第二子接口Set

 【1】放入Integer类型数据：

  		特点：唯一，无序

```java
import java.util.HashSet;
import java.util.Set;

public class Test {

    public static void main(String[] args) {
        // 创建一个Set集合
        Set set = new HashSet(); //接口是不能直接创建对象，要写一个实现类
        set.add(12);
        System.out.println(set.add(26));
        set.add(12);
        System.out.println(set.add(26));
        set.add(12);
        set.add(26);
        set.add(13);
        set.add(26);
        System.out.println(set); // 特点：唯一，无序
        System.out.println(set.size()); //3
    }
}
```

【2】放入String类型数据： 	

```java 	
import java.util.HashSet;
import java.util.Set;

public class Test {

    public static void main(String[] args) {
        // 创建一个Set集合
        Set set = new HashSet(); //接口是不能直接创建对象，要写一个实现类
        set.add("java");
        System.out.println(set.add("html"));
        set.add("css");
        System.out.println(set.add("html"));
        set.add("python");
        System.out.println(set); // 特点：唯一，无序
        System.out.println(set.size()); //3
    }
}
```

【3】放入自定义的引用数据类型：

```java
package com.sxt.test02;

import java.util.HashSet;
import java.util.Set;

public class Test {

    public static void main(String[] args) {
        Set set = new HashSet();
        set.add(new Student(18, "nana", "male", 180.4));
        set.add(new Student(18, "lili", "male", 160.4));
        set.add(new Student(18, "feifei", "female", 160.4));
        set.add(new Student(18, "lili", "male", 160.4));

        System.out.println(set);
        System.out.println(set.size());


    }
}
```

```java
package com.sxt.test02;

public class Student {

    private int age;
    private String name;
    private String sex;
    private double height;

    public int getAge() {
        return age;
    }

    public String getName() {
        return name;
    }

    public String getSex() {
        return sex;
    }

    public double getHeight() {
        return height;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public Student(int age, String name, String sex, double height) {
        this.age = age;
        this.name = name;
        this.sex = sex;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", sex='" + sex + '\'' +
                ", height=" + height +
                '}';
    }
}
```



【4】上面发现，放入Integer数据和String类型的数据都没有问题，都遵照HashSet的特点，但是放入自定义的引用数据类型就不行了 

【5】为啥？---》底层原理到底是什么？（以Integer为案例讲解） 

![image_57309](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5m9opzqj31160edjuo.jpg)


 【6】结论： 

​		只要向HashSet中放东西，对应的那个类型必须要重写hashCode和equals方法 



#### 3.2.1 实现类:HashSet 

<深入理解HashSet>

**1.哈希表的结构和特点 **

​         哈希表又叫散列表：底层：数组+链表 

 ![image_9352](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mp7hgoj310z0e077j.jpg)



**2.哈希表是如何查找数据的，如何添加数据的?** 

​		**哈希冲突**的定义：当关键字集合很大时，关键字值不同的元素可能会映像到哈希表的同一地址上

​		**添加数据：**

​      （1）计算哈希码x(调用hashCode()，结果是一个int值，整数的哈希码取自身即可) 

​      （2）计算在哈希表中的存储位置  y=k(x)=x%11

​				其中，k：函数	y：在哈希表中的存储位置 

​       （3）存入哈希表 

​               情况1：一次添加成功 

​               情况2：多次添加成功（出现了冲突，调用equals()和对应链表的元素进行比较， 

​                             比较到最后，结果都是false，创建新节点，存储数据，并加入链表末尾） 

​               情况3：不添加（出现了冲突，调用equals()和对应链表的元素进行比较， 

​                             经过一次或者多次比较后，结果是true，表明重复，不添加） 



​                  结论1：哈希表添加数据快（3步即可，不考虑冲突） 

​                  结论2：唯一 

​                  结论2：无序3.哈希表是如何查询数据的 

​                  和添加数据的过程是相同的 

​                  情况1：一次找到   23  86  76 

​                  情况2：多次找到   67  56  78 

​                  情况3：找不到   100 200 

​                  结论1：哈希表查询数据快 



**3.hashCode和equals到底有什么神奇的作用** 

​		hashCode():计算哈希码，是一个整数，根据哈希码可以计算出数据在哈希表中的存储位置 

​		equals()：添加时出现了冲突，需要通过equals进行比较，判断是否相同 

​                          查询时也需要使用equals进行比较，判断是否相同



**4.hashcode和equals执行了几次？ **

​		hashCode是放入几个元素，就执行几次 

​		equals：在相同位置放入元素的时候才会去比较。 

   

**5.各种类型数据的hashCode()返回的值是什么？** 

​		Integer：返回的就是value值 

```java 
public static int hashCode(int value){
  return value;
}
```

​		String：

```java
 public int hashCode() {
        int h = hash;
        if (h == 0 && value.length > 0) {
            char val[] = value;
            for (int i = 0; i < value.length; i++) {
                h = 31 * h + val[i];
            }
            hash = h;
        }
        return h;
    }

"abc"
		a:97
		b:98
		c:99
    // h = 31 * h + val[i]
		h=31*0+97=97 // 加上系数是为了防止”abc"和"bac" 的hashcode一样
		h=31*97+98=3105
		h=31*3105+99
		--->h ---哈希码
```

​		Student：

​		假如看不懂，只要知道hashCode方法返回一个int类型的数据即可

```java
public static int hashCode(Object[] a) {
        if (a == null) {
            return 0;
        } else {
            int result = 1;
            Object[] var2 = a;
            int var3 = a.length;

            for(int var4 = 0; var4 < var3; ++var4) {
                Object element = var2[var4];
                result = 31 * result + (element == null ? 0 : element.hashCode());
            }

            return result;
        }
    }
}
```



**6.如何减少冲突**

​		1）哈希表的长度和表中的记录数的比例--装填因子： 	 	       

​				 如果Hash表的空间远远大于最后实际存储的记录个数，则造成了很大的空间浪费， 	 	        

​				如果选取小了的话，则容易造成冲突。 	 	       

​				在实际情况中，一般需要根据最终记录存储个数和关键字的分布特点来确定Hash表的大小。 	 	        				还有一种情况时可能事先不知道最终需要存储的记录个数，则需要动态维护Hash表的容量，此时可能需要重新计算Hash地址。 	 	        

​				**装填因子=表中的记录数/哈希表的长度**，               4/ 16  =0.25      8/ 16 =0.5   12/16=0.75 	 	        

​				如果装填因子越小，表明表中还有很多的空单元，则添加发生冲突的可能性越小； 	 	        

​				而装填因子越大，则发生冲突的可能性就越大，在查找时所耗费的时间就越多。 	 	        

​				有相关文献证明当装填因子在0.5左右的时候，Hash的性能能够达到最优。 	 	        

​				因此，一般情况下，装填因子取经验值0.5。 	 	        

​		2）哈希函数的选择 	 	                

​				直接定址法    平方取中法  折叠法   除留取余法（y = x%11）查询相关资料

​        3）链地址法（数组里面是链表）     

​		当然还有其他的方法：开放地址法，再散列法，建立一个公共溢出区	



**7.复习**

​	(1) hashCode（）是做什么事的？ 

​		放入的类型要重写这个方法，然后返回一个int类型的数，--》哈希码 

​		得到哈希码，根据一个表达式，算出在主数组中的位置。 

​	(2) equals（）是做什么事的？ 

​		当在相同位置放元素的时候，要先进行比较（只比较是否相等即可，不用比谁大谁小） 	

​	(3) 底层的计算位置的表达式 真的是取余数那个吗？不一定 

​		y=x%5--没有验证 

​	(4) 底层主数组长度是多少？？--没有验证 

​	(5) 数组长度为16，但是我放了20个元素，现在冲突的概率是不是就大了? 是

​		有没有处理办法？？？---》扩容  --没有验证 

​	(6) 主数组---》是什么类型的？--没有验证 

​	(7) 组中的那个链表啥样的？结点啥样？--没有验证 

​	(8) 链表追加元素  请问在哪加？--没有验证 



#### 3.2.2 实现类:TreeSet

【1】放入Integer类型数据：

```java 
package com.sxt.test03;

import java.util.Set;
import java.util.TreeSet;

public class Test {

    public static void main(String[] args) {
        Set set = new TreeSet();
        set.add(12);
        set.add(13);
        System.out.println(set.add(3));
        set.add(7);
        System.out.println(set.add(3));
        set.add(16);
        System.out.println(set); // 有序：按照升序进行排列 无序：没有按照输入顺序输出
        System.out.println(set.size()); // 唯一
      
      	TreeSet<Integer> treeSet = new TreeSet<>();
        treeSet.add(1);
        treeSet.add(2);
        treeSet.add(4);
        treeSet.add(3);
        System.out.println(treeSet);

        System.out.println(treeSet.floor(5)); //  4 方法返回在这个集合中小于或者等于给定元素的最大元素，如果不存在这样的元素,返回null.
        System.out.println(treeSet.ceiling(0)); //  1 方法返回在这个集合中大于或者等于给定元素的最小元素，如果不存在这样的元素,返回null.


      
      	
    }
}
```

 【2】原理：

​		注：二叉树的中序遍历输出结果是升序的![image_16392](https://tva1.sinaimg.cn/large/008eGmZEly1gpmz6hpx03j30mq0ejq41.jpg)



【3】验证Integer底层真的实现了内部比较器：

```java
public final class Integer extends Number implements Comparable<Integer> { // 内部比较器
} 
```

【4】放入String类型数据： 

```java
public class Test {
    public static void main(String[] args) {
        Set set=new TreeSet();
        set.add("cjava");
        System.out.println(set.add("ejava"));;
        set.add("ajava");
        set.add("djava");
        System.out.println(set.add("ejava"));;
        set.add("bjava");
        System.out.println(set);//有序：按照升序进行排列   无序：没有按照输入顺序进行输出
        System.out.println(set.size());//5:   唯一
        
    }
}
```

发现放入String同样遵照这个特点：

```java
public final class String implements Serializable, Comparable<String>, CharSequence {
}
```

【5】放入自定义的引用数据类型的数据： 

​		必须实现内部比较器： 

```java
package com.sxt.test03;

public class Student implements Comparable{

    @Override
    public int compareTo(Object o) {
        // 比较规则：
        // 按照年龄进行排序
        Student other = (Student) o;
//        return this.getAge() - other.getAge(); // 如果大于零，往左边放，从小到大
        // return -this.getAge() - other.getAge(); // 如果大于零，往右边放，从大到小

        // 按照身高进行比较
//        return ((Double)(this.height)).compareTo(((Double)(other.getHeight())));

        // 按照姓名进行比较
//        return this.getName().compareTo(other.getName());

        // 按照姓名和年龄比较
        if(this.getName().compareTo(other.getName())==0){// 姓名相等了才比较年龄
            return -this.getAge() - other.getAge();
        }else { // 姓名不等
            return this.getName().compareTo(other.getName());
        }
    }

    private String name;
    private int age;
    private double height;

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public double getHeight() {
        return height;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
}
```

```java
package com.sxt.test03;

import java.util.Set;
import java.util.TreeSet;

public class Test2 {

    public static void main(String[] args) {
        Set st = new TreeSet();
        st.add(new Student("lili", 19, 150.4));
        st.add(new Student("nana", 20, 165.4));
        st.add(new Student("lili", 21, 167.4));
        st.add(new Student("feifei", 23, 155.4));
        st.add(new Student("huahua", 22, 180.4));

        System.out.println(st);

    }
}
```

【2】外部比较器

```java
package com.sxt.test03;

import java.util.Comparator;
import java.util.Set;
import java.util.TreeSet;

public class Test2 {

    public static void main(String[] args) {

        // Comparator c01 = new compare01();
        // Comparator c01 = new compare01(); // 接口等于它的实现类，多态
        //Set st = new TreeSet(c01); // 将外部比较器跟TreeSet集合利用构造器进行关联，将比较的规则以构造器参数的形式传到这里来
        // 匿名内部类：如果这个比较规则 在项目中只用一次，就用匿名内部类写即可。
        Set st = new TreeSet(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                // 规则：按照年龄进行比较
                Student s1 = (Student)o1;
                Student s2 = (Student)o2;
                return s1.getAge() - s2.getAge();
            }
        });
        st.add(new Student("lili", 19, 150.4));
        st.add(new Student("nana", 20, 165.4));
        st.add(new Student("lili", 21, 167.4));
        st.add(new Student("feifei", 23, 155.4));
        st.add(new Student("huahua", 22, 180.4));

        System.out.println(st);

    }
}

class compare01 implements Comparator{
    @Override
    public int compare(Object o1, Object o2) {
        // 规则：按照年龄进行比较
        Student s1 = (Student)o1;
        Student s2 = (Student)o2;
        return s1.getAge() - s2.getAge();
    }
}
```



### 3.3 完整结构图

![image_32677](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5m86260j30we070q3j.jpg)

![image_41515](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mjgpchj30zi0dowhe.jpg)



### 3.4 iterator(),iterator, iterable

【面试】：iterator(),iterator, iterable 关系

​	【1】之间的关系图：

![image_26467](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mjuu6pj30zi0dowhe.jpg)

​	 【2】hasNext和next具体是怎么实现的？在ArrayList中的实现

![image_42259](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5mkgn72j310n0dfq4m.jpg)

ListLiterator

【1】在指定的字符串之后添加一个新的字符串：

```java
public class Test {
    public static void main(String[] args) {
        ArrayList al=new ArrayList();
        al.add("aaa");
        al.add("bbb");
        al.add("ccc");
        al.add("ddd");
        //在“ccc”之后添加一个字符串“eeeeee”:
        Iterator it = al.iterator();
        while(it.hasNext()){
            if("ccc".equals(it.next())){
                al.add("eeeeee");
            }
        }
    }
}
```

上面的代码出错了：

并发修改异常：

```
Exception in thread "main" java.util.ConcurrentModificationException // 并非修改异常
	at java.base/java.util.ArrayList$Itr.checkForComodification(ArrayList.java:1042)
	at java.base/java.util.ArrayList$Itr.next(ArrayList.java:996)
	at com.sxt.test09.Test.main(Test.java:16)

Process finished with exit code 1
```

错误原因:因为迭代器和集合同时在操纵这个数组，同时发生的修改异常，出错。 

解决办法  	

```java
public class Test {
    public static void main(String[] args) {
        ArrayList al=new ArrayList();
        al.add("aaa");
        al.add("bbb");
        al.add("ccc");
        al.add("ddd");
        //在“ccc”之后添加一个字符串“eeeeee”:
        ListIterator li = al.listIterator();
        while(li.hasNext()){
            if("ccc".equals(li.next())){
                li.add("eeeee");
            }
        }
        System.out.println(al);
    }
}
```

可以进行倒序遍历：

```java
public class Test {
  
    public static void main(String[] args) {
        ArrayList al=new ArrayList();
        al.add("aaa");
        al.add("bbb");
        al.add("ccc");
        al.add("ddd");
        //在“ccc”之后添加一个字符串“eeeeee”:
        ListIterator li = al.listIterator();
        while(li.hasNext()){
            if("ccc".equals(li.next())){
                li.add("eeeee");
            }
        }
        //System.out.println(li.hasNext());
        //System.out.println(li.hasPrevious());
      
        //倒着遍历：
        while(li.hasPrevious()){
            System.out.println(li.previous());
        }
        System.out.println(li.hasPrevious());
        System.out.println(li.hasNext());
        //System.out.println(al);
    }
}
```



##4. Map接口

#### 4.1 HashMap

【1】总结： 

​		HashMap的特点是按照key来说的，无序，**唯一 **,可以插入null

​		HashMap中提供了各种方法，对于查找的方法很全面： 

​		对key遍历，对value遍历，对key-value的映射键值对 一起遍历的 

 ```java
package com.sxt.test01;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class Test {

    /*
    接口  Map<K,V>---：key,value  “键值对”
    增加：put(K key, V value)
    删除：clear() remove(Object key)
    修改：
    查看：entrySet()  get(Object key)  keySet() values()
         size()
    判断：containsKey(Object key)
          containsValue(Object value)
          isEmpty()
     */

    public static void main(String[] args) {
        // 创建一个Map集合的对象；
        Map<Integer,String> map = new HashMap<Integer, String>();
        map.put(6,"zhaoss");   //存入的成对的信息，存入的键值对，都是有映射关系。
        System.out.println(map.put(8,"lili")); // 输出null--这个value把谁替换了，因为没有被替换的所以打出来是null
        map.put(4,"nana");
        System.out.println(map.put(8,"lulu")); // 输出lili--这个lulu把老的lili替换了，输出被替换的lili
        map.put(2,"feifei");
        System.out.println(map.put(8,"ganggang"));

////        map.clear();
//        map.remove(4);
//        System.out.println(map.containsKey(4));
//        System.out.println(map.containsValue("ganggang"));
//        System.out.println(map.containsValue("lili"));
//        System.out.println(map.isEmpty());
//        System.out.println(map);
//        System.out.println(map.size()); // 特点：唯一，无序（按照key进行总结）

        // 遍历查看 entrySet()  get(Object key)  keySet() values()

        // keySet():对集合的key部分进行遍历
        System.out.println("----------------");
        Set<Integer> set = map.keySet();
        for(Integer i:set){
            System.out.println(i);
        }

        //values():对集合的value部分进行遍历
        System.out.println("-----------------");
        Collection<String>  col = map.values();
        for(String s:col){
            System.out.println(s);
        }

        //get():根据key得到value
        System.out.println("------------------");
        for(Integer i:set){
            System.out.println(map.get(i));
        }

        //entrySet:
        // entrySet返回值是Set类型，有泛型，泛型为：Entry类型--》这个东西是Map接口的内部接口
        Set<Map.Entry<Integer, String>> set1 = map.entrySet();
        for(Map.Entry<Integer, String> m:set1){
            System.out.println(m.getKey() + "-----" + m.getValue()); // 把整个一对都返回回来了，把一对一对的信息放到Set中
        }

    }

 ```

【2】将代码中的HashMap全部替换为Hashtable，发现结果一模一样 

​	


 #### 4.2 TreeMap

【1】内部比较器

```java
 package com.sxt.test02;

public class Student implements Comparable{

    private int age;
    private String name;
    private Double height;

    public int getAge() {
        return age;
    }

    public String getName() {
        return name;
    }

    public Double getHeight() {
        return height;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setHeight(Double height) {
        this.height = height;
    }

    public Student(int age, String name, Double height) {
        this.age = age;
        this.name = name;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", height=" + height +
                '}';
    }

    @Override
    public int compareTo(Object o) {
        Student other = (Student)o;
        return this.getAge()-other.getAge();
    }
}
```

```java
package com.sxt.test02;

import java.util.TreeMap;

public class Test {

    public static void main(String[] args) {
        TreeMap<Student, String> tm = new TreeMap<Student, String>();

        Student s1 = new Student(18, "lili", 160.14);
        tm.put(s1, s1.getName());

        Student s2 = new Student(16, "nana", 160.14);
        tm.put(s2, s1.getName());

        Student s3 = new Student(18, "lada", 160.14);
        tm.put(s3, s1.getName());

        Student s4 = new Student(12, "dad", 160.14);
        tm.put(s4, s1.getName());

        System.out.println(tm);
        System.out.println(tm.size());
    }
}
```



【2】外部比较器

```java
package com.sxt.test02;

public class Student{

    private int age;
    private String name;
    private Double height;

    public int getAge() {
        return age;
    }

    public String getName() {
        return name;
    }

    public Double getHeight() {
        return height;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setHeight(Double height) {
        this.height = height;
    }

    public Student(int age, String name, Double height) {
        this.age = age;
        this.name = name;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", height=" + height +
                '}';
    }
}
```



```java
package com.sxt.test02;

import java.util.Comparator;
import java.util.TreeMap;


public class Test {

    public static void main(String[] args) {
        TreeMap<Student, String> tm = new TreeMap<Student, String>(new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                Student s1 = (Student)o1;
                Student s2 = (Student)o2;
                return s1.getAge() - s2.getAge();
            }
        });

        Student s1 = new Student(18, "lili", 160.14);
        tm.put(s1, s1.getName());

        Student s2 = new Student(16, "nana", 160.14);
        tm.put(s2, s1.getName());

        Student s3 = new Student(18, "lada", 160.14);
        tm.put(s3, s1.getName());

        Student s4 = new Student(12, "dad", 160.14);
        tm.put(s4, s1.getName());

        System.out.println(tm);
        System.out.println(tm.size());

    }

}
```



#### 4.3 Map结构图

![image_18980](https://tva1.sinaimg.cn/large/0081Kckwly1gmc5m98kvoj30tn0dzac8.jpg)

#### 4.4 源码

（暂时省略 2019年10月08日09:28:29）

##### 4.4.1 TreeMap,TreeSet

验证红黑树

```java
package com.sxt.test04;

import java.util.TreeMap;

public class Test {

    public static void main(String[] args) {
        TreeMap<Student, Integer> tm = new TreeMap<Student, Integer>();
        tm.put(new Student(1), 1001);
        tm.put(new Student(2), 1001);
        tm.put(new Student(3), 1001);
        tm.put(new Student(4), 1001);
        tm.put(new Student(-5), 1001); // 红黑树 为了平衡，会转到另外一次
    }
}
```



```java
package com.sxt.test04;

public class Student implements Comparable{

    int age;

    public Student(int age){
        this.age = age;
    }

    @Override
    public String toString() {
        return age + "";
    }

    @Override
    public int compareTo(Object o) {
        Student s = (Student)o;
        System.out.println(this + "和" + s + "在比较");
        return this.age - s.age;
    }
}
```



#### 4.5 Collection工具类

```java
package com.bjsxt.test007;
import java.util.ArrayList;
import java.util.Collections;
 
public class TestCollections {
        public static void main(String[] args) {
                
                ArrayList<String> al=new ArrayList<String>();
                al.add("apple");
                al.add("banana");
                al.add("java");
                System.out.println(al);
                //addAll(Collection<? super T> c, T... elements)
                Collections.addAll(al, "merry","lili","abc");
                System.out.println(al);
                Collections.addAll(al, new String[]{"nihao","jsp"});//可变参数相当于数组
                System.out.println(al);
                
                //binarySearch(List<? extends Comparable<? super T>> list, T key) 
                System.out.println(Collections.binarySearch(al, "lili"));//发现不准确  为什么？因为要对排序后的查找
                Collections.sort(al);
                System.out.println(al);
                System.out.println(Collections.binarySearch(al, "abc"));//发现不准确  为什么？因为要对排序后的查找---返回索引
                System.out.println(Collections.binarySearch(al, "aaaa"));//找不到  返回负数
                
                //copy(List<? super T> dest, List<? extends T> src) 
                ArrayList<String> sl=new ArrayList<String>();
                Collections.addAll(sl, "a","b","c","d","e","a","b","c","d","e");
                System.out.println("==");
                System.out.println(al);
                System.out.println(sl);
                
                Collections.copy(sl, al);//sl的长度必须大于al的长度的时候在可以进行赋值替换
                System.out.println(al);
                System.out.println(sl);//其实相当于替换
                
                
                //fill(List<? super T> list, T obj) 
                System.out.println(al);
//		Collections.fill(al, "java");
                System.out.println(al);
                
                //
                System.out.println(Collections.max(al));;
        }
}
```
