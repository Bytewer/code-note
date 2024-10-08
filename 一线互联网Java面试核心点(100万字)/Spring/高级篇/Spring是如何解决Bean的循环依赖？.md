Spring是如何解决的循环依赖： 采用三级缓存解决的 就是三个Map ； 关键： 一定要有一个缓存保存它的早期对象作为死循环的出口

1. 1、一级缓存singletonObjects存放可以使用的单例。  
2、二级缓存earlySingletonObjects存放的是早期的bean，即半成品，此时还无法使用。  
3、三级缓存singletonFactories是一个对象工厂，用于创建对象并放入二级缓存中。同时，如果对象有Aop代理，则对象工厂返回代理对象。

面试官还可能问：

1. 二级缓存能不能解决循环依赖？
    1. 如果只是循环依赖导致的死循环的问题： 一级缓存就可以解决 ，但是解决在并发下获取不完整的Bean。
    2. 二级缓存完全解决循环依赖：  只是需要在实例化后就创建动态代理，不优化也不符合spring生命周期规范。
2. Spring有没有解决多例Bean的循环依赖？
    1. 多例不会使用缓存进行存储（多例Bean每次使用都需要重新创建）
    2. 不缓存早期对象就无法解决循环
3. Spring有没有解决构造函数参数Bean的循环依赖？
    1. 构造函数的循环依赖也是会报错
    2. 可以通过人工进行解决：@Lazy
        1. 就不会立即创建依赖的bean了
        2. 而是等到用到才通过动态代理进行创建
