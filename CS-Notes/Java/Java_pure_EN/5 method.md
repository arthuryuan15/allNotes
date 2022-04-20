# 方法

【6】面试题：考虑下面的代码是否交换成功，为什么

```java
public class TestM{
        public static void main(String[] args){
                int a=10;
                int b=20;
                System.out.println("输出交换前的两个数："+a+"---"+b);
                changeNum(a,b);
                System.out.println("输出交换后的两个数："+a+"---"+b);
        }
        
        //定义一个方法，交换两个数：
        public static void changeNum(int num1,int num2){
                int t;
                t=num1;
                num1=num2;
                num2=t;
        }
}
```

内存分析：



![image_47421](https://tva1.sinaimg.cn/large/0081Kckwly1gmc4nal8d4j311a0dvtac.jpg)



说明：

1. changeNum方法白调，因为操作的是num1和num2，但方法结束时，num1和num2就消失了，对原来的a和b没有影响。
2. 给num1和num2是10和20这两个值，不是a和b