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

注解：Singleton的静态属性instance中，只有instance为null的时候才创建一个实例，构造函数私有，确保每次都只创建一个，避免重复创建。<br/>
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

注解：在解法一的基础上加上了同步锁，使得在多线程的情况下可以用。例如：当两个线程同时想创建实例，由于在一个时刻只有一个线程能得到同步锁，当第一个线程加上锁以后，第二个线程只能等待。第一个线程发现实例没有创建，创建之。第一个线程释放同步锁，第二个线程才可以加上同步锁，执行下面的代码。由于第一个线程已经创建了实例，所以第二个线程不需要创建实例。保证在多线程的环境下也只有一个实例。<br/>
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

注解：只有当instance为null时，需要获取同步锁，创建一次实例。当实例被创建后，则无需试图加锁。<br/>
缺点：用双重if判断，复杂，容易出错。

4) 饿汉式（建议使用）
> public class Singleton{<br/>
　　private static Singleton instance = new Singleton();<br/>
　　private Singleton(){<br/>
　　}<br/>
　　public static Singleton getInstance(){<br/>
　　　return instance;<br/>
　　}<br/>
}

注解：初始化静态的instance创建一次。如果我们在Singleton类里面写一个静态的方法不需要创建实例，它仍然会早早的创建一次实例。而降低内存的使用率。<br/>
缺点：没有lazy loading的效果，从而降低内存的使用率。

5) 静态内部内。（建议使用）
> public class Singleton{<br/>
　　private Singleton(){<br/>
　　}<br/>
　　private static class SingletonHolder{<br/>
　　　private final static Singleton instancee = new Singleton();<br/>
　　}<br/>
　　public static Singleton getInstance(){<br/>
　　　return SingletonHolder.instance;<br/>
　　}<br/>
}

注解：定义一个私有的内部类，在第一次用这个嵌套类时，会创建一个实例。而类型为SingletonHolder的类，只有在Singleton.getInstance()中调用，由于私有的属性，他人无法使用SingleHolder，不调用Singleton.getInstance()就不会创建实例。<br/>
优点：达到了lazy loading的效果，即按需创建实例。

参考资料：<br/>
https://www.cnblogs.com/hupp/p/4487521.html<br/>
https://jingyan.baidu.com/article/f79b7cb309c11c9145023e7a.html<br/>
https://blog.csdn.net/sai739295732/article/details/62411016<br/>
