# **Spring**

#### 1.Spring 如何解决循环依赖？
Spring bean的创建，本质上是一个对象的创建，完整的对象包含两部分：当前对象实例化和对象属性的实例化

(1).什么是循环依赖
```
@Component
public class A{
    private B b;
    public void setB(B b){
        this.b = b;
    }
}

@Component
public class B{
    private A a;
    public void setA(A a){
        this.a = a;
    }
}

```
(2).循环依赖场景  
a.构造器的循环依赖  
b.field属性的循环依赖  


(3).怎么解决  
a.Spring解决循环依赖的理论依据基于Java的引用传递，当我们获取到对象的引用时，对象的field可以延后设置，但是构造器必须在获取引用之前  
b.Spring三级缓存  
一级缓存：singletonObjects,单例对象的cache  
二级缓存：earlySingletonObjects：提前曝光的单例对象的cache  
三级缓存：singletonFactories：单例对象工厂的cache  


https://blog.csdn.net/u010853261/article/details/77940767  
![Image text](1)





