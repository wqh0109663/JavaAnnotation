# Java注解的理解与使用
##  序
*   首先是为什么我想写这个，因为最近一直在研究框架，各种各样的注解，加上对一些注解的使用，我到现在只知道怎么使用注解(也是当初学的时候没去追根问底)不知道为什么是这样，也就是并不知其所以然，所以我就想自己写。也是对自己的一个监督，逼迫自己来完成这样一个任务。
* 其次是我想搞明白的问题是什么?第一个问题当然是何为注解(从定义开始),以及Java中的注解有那些,和如何自己手写一些注解,最后思考Spring中的注解是如何实现的，最后想到什么就添加什么吧
###  详细分析
* 定义:(Java编程思想第四版上是这样定义的) 注解，也被称为元数据，为我们在代码中添加信息提供了一种形式化的方法，使我们可以在稍后的某个时刻非常方便的使用这些数据,通俗的将就是用来描述数据的数据.
* Java中的注解主要有三种标准注解(jdk1.6)(定义在java.lang包中):
  * @Override 覆盖父类中方法添加
  * @Deprecated 已过时，标示此类中的成员变量或者方法可能在将来的jdk版本中被删除，并不建议使用而且ide会发出警告，但是现在并没有删除是因为兼容性的原因.
  * @SuppressWarings  关闭不当的编译器警告
  * @SafeVarargs  jdk 7 专门为抑制“堆污染”警告提供的(没见过也没用过)
  * @FunctionalIterface （jdk 8）指定某个接口必须是函数式接口，否则就会编译出错。
* 以及四种元注解（一种专门用来注解其他注解的注解）(后来又增加了几个)
  * @Target
  * @Retention
  * @Documented
  * @Inherited
  * 图示为jdk1.8
   ![](https://raw.githubusercontent.com/wqh0109663/MyOwnMarkDownPhoto/master/annotation/annotation.png)

####  注解深度解析
* 源码
  * 首先来看@Override
  * 源码很简单:
  
```java
@Target({ElementType.METHOD})
@Retention(RetentionPolicy.SOURCE)
public @interface Override {
}
  ```
  *  再来看看使用这个注解

    <!-- lang: Java -->
    ```Java
         package demo;

            /**
             - @author wqh
             - @date 18-8-20
            */

          public class User {
              private Integer id;
              private String username;
              @Override
              public String toString() {
                  return "User{" +
                          "id=" + id +
                          ", username='" + username + '\'' +
                          '}';
              }
              public Integer getId() {
                  return id;
              }
              public void setId(Integer id) {
                  this.id = id;
              }
              public String getUsername() {
                  return username;
              }
              public void setUsername(String username) {
                  this.username = username;
              }
          }
      ```
    * 顺带提一句MarkDown中代码块高亮使用的是:
      - `` <!-- lang:java --> ``如果要代码高亮就在第一行加上第三种就可以实现
      - ``<p>`` 当然前面一个就要加上三个反引号`
      - 直接使用三个反引号加上语言类型也是可行的
    * 问题就来了，加上了@Override注解编译器

    * 需要预备的知识点包含动态代理和反射
    * 首先来看Java中的动态代理
      * 代码
    * 然后就是反射



* Spring的部分注解探究
#####  自定义注解
* 如何自定义一个注解
