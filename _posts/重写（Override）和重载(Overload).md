---
layout:     post
title:      "Welcome to Anderson7 Blog"
subtitle:   " \"Hello World, Hello Blog\""
date:       2018-06-27 12:00:00
author:     "李少博"
header-img: "img/post-bg-2015.jpg"
tags:
    - 生活
---
> “Yeah It's on. ”

# 重写（Override）和重载(Overload)

##  重写（Override)

重写是子类对父类允许访问的方法的实现过程进行重新编写，返回值和形参都不能改变，即外壳不变，核心重写。

```java
class Animal{
   public void move(){
      System.out.println("动物可以移动");
   }
}
 
class Dog extends Animal{
   public void move(){
      System.out.println("狗可以跑和走");
   }
}
 
public class TestDog{
   public static void main(String args[]){
      Animal animal = new Animal(); // Animal 对象
      Animal dog = new Dog(); // Dog 对象
 
      animal.move();// 执行 Animal 类的方法
 
      dog.move();//执行 Dog 类的方法
   }
}
//运行结果：
//动物可以移动
//狗可以跑和走
```

 在上面的例子中，可以看到dog尽管属于Animal类，但是他运行的是Dog类的方法。

在编译的阶段，只是检查参数的引用类型。

然而在运行的时候，java虚拟机指定对象的类型并且运行改对象的方法。

上面的例子之所以能编译成功，是因为Animal中存在move方法，然而运行的是特定对象的方法。



```java

```

## 方法重写的规则

- 参数列表必须完全与被重写的方法相同
- 返回类型必须完全与被重写方法的返回类型相同 
- 父类的成员方法只能被字类重写
- 声明为final的方法不能被重写
- 声明为static的方法不能被重写，但是能够被再次声明
- 字类和父类在用一个包中，那么字类可以重写父类的所有方法，除了声明为private和final的方法
- 子类和父类不在同一个包中，那么子类只能够重写父类的声明为public和protected的非final方法 
- 构造方法不能被重写
- 如果不能继承一个方法，则不能重写这个方法

## Super关键字的使用

当需要在子类中调用父类的被重写方法时，要使用super关键字。 

```java
class Animal{
   public void move(){
      System.out.println("动物可以移动");
   }
}
 
class Dog extends Animal{
   public void move(){
      super.move(); // 应用super类的方法
      System.out.println("狗可以跑和走");
   }
}
 
public class TestDog{
   public static void main(String args[]){
 
      Animal b = new Dog(); // Dog 对象
      b.move(); //执行 Dog类的方法
 
   }
}
//运行结果：
//动物可以移动
//狗可以跑和走
```

## 重载（Overload）

重载是在一个类里面，方法名字都相同，而参数不同，返回类型可以相同也可以不同，每个重载的方法或者构造函数都必须有一个独一无二的参数类型列表。

最常用的就是构造器的重载

#### 重载的规则：

- 被重载的方法必须该百年参数列表
- 被重载的方法可以该改变返回值类型
- 被重载的方法可以改变访问修饰符
- 被重载的方法可以声明新的检查异常
- 方法能够在同一类中或者字类中被重载
- 无法有返回值类型作为重载函数的区分标准

```java
public class Overloading {
    public int test(){
        System.out.println("test1");
        return 1;
    }
 
    public void test(int a){
        System.out.println("test2");
    }   
 
    //以下两个参数类型顺序不同
    public String test(int a,String s){
        System.out.println("test3");
        return "returntest3";
    }   
 
    public String test(String s,int a){
        System.out.println("test4");
        return "returntest4";
    }   
 
    public static void main(String[] args){
        Overloading o = new Overloading();
        System.out.println(o.test());
        o.test(1);
        System.out.println(o.test(1,"test3"));
        System.out.println(o.test("test4",1));
    }
}
```

| 区别点     | 重载方法 | 重写方法                                       |      |      |
| :--------- | -------- | ---------------------------------------------- | ---- | ---- |
| 参数列表   | 必须修改 | 一定不能修改                                   |      |      |
| 返回值类型 | 可以修改 | 一定不能修改                                   |      |      |
| 异常       | 可以修改 | 可以减少或删除，一定不能抛出新的或者更广的异常 |      |      |
| 访问       | 可以修改 | 一定不能做更严格的限制（可以降低限制）         |      |      |
|            |          |                                                |      |      |

![](C:\Users\29084\Desktop\20171102-1.jpg)