# 介绍Java的设计模式

### 5种单例模式
1) 单线程，不加锁的懒汉式（不好）
> public class Singleton{<br/>
　　private static Singleton instance = null;<br/>
  　private Singleton(){<br/>
　　}<br/>
  　public static Singleton getInstance(){<br/>
　　　if(instance == null){<br/>
　　　　　instance = new Singleton();<br/>
　　　}<br/>
　　　return instance;<br/>
　　}<br/>
}<br/>

注解：Singleton的静态属性instance中，只有instance为null的时候才创建一个实例，构造函数私有，确保每次都只创建一个，避免重复创建。
缺点：只有在单线程的情况下正常运行，在多线程的情况下，就会出问题。例如：当两个线程同时运行到判断instance是否为空的if语句，并且instance确实没有创建好时，那么两个线程都会创建一个实例。

2) 多线程，类方法外加锁的懒汉式（不好）
> public class Singleton{<br/>
　　private static Singleton instance = null;<br/>
　　private Singleton(){<br/>
　　}<br/>
　　public static synchronized Singleton getInstance(){<br/>
　　　if(instance == null){<br/>
　　　　instance = new Singleton();<br/>
　　　}<br/>
　　　return instance;<br/>
　　}<br/>
}

注解：在解法一的基础上加上了同步锁，使得在多线程的情况下可以用。例如：当两个线程同时想创建实例，由于在一个时刻只有一个线程能得到同步锁，当第一个线程加上锁以后，第二个线程只能等待。第一个线程发现实例没有创建，创建之。第一个线程释放同步锁，第二个线程才可以加上同步锁，执行下面的代码。由于第一个线程已经创建了实例，所以第二个线程不需要创建实例。保证在多线程的环境下也只有一个实例。
缺点：每次通过getInstance方法得到singleton实例的时候都有一个试图去获取同步锁的过程。而众生周知，加锁是很耗时的。能避免则避免。

3) 多线程，类方法内加锁的懒汉式（可行）
> public class Singleton{<br/>
　　private static Singleton instance = null;<br/>
　　private Singleton(){<br/>
　　}<br/>
　　public static Singleton getInstance(){<br/>
　　　if(instance == null){<br/>
　　　　　synchronized(Singleton.class){<br/>
　　　　　　　if(instance == null){<br/>
　　　　　　　　　instance = new Singleton();<br/>
　　　　　　　}<br/>
　　　　　}<br/>
　　　}<br/>
　　}<br/>
}<br/>
