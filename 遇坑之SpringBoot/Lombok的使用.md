### Lombok的使用
Lombok是一个可以通过简单的注解的形式帮我们消除一些必须有但显得臃肿的Java代码工具，比如通常我们需要手动去建立getter和setter方法，构造函数之类的，而lombok的作用就是能够在我们编译源码的时候自动帮我们生成这些方法

#### 如何引入Lombok
```java
<dependencies>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>1.16.10</version>
    </dependency>
</dependencies>
```

同时Intellij idea开发的话还需要安装Lombok plugin,同时设置setting->Compiler-> Annotation Processors -> Enable annotation processing勾选。
