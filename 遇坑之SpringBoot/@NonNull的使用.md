### @NonNull的使用
使用@NonNull相当于在方法或构造函数的参数上生成了null-check语句，示例如下：

```java
package com.amos.lombok;

import lombok.NonNull;

public class NonNullExample {

    private String name;

    // 在构造器上使用@NonNull
    public NonNullExample(@NonNull String name) {
        this.name = name;
    }

    // 在普通方法上使用@NonNull
    public static void example(@NonNull String str) {
        System.out.println(str);
    }

    public static void main(String[] args) {
        // 异常1
        NonNullExample example = new NonNullExample(null);
        // 异常2
        example(null);
    }
}
```

执行main方法后
异常1堆栈信息如下:
```java
Exception in thread “main” java.lang.NullPointerException: name is marked @NonNull but is null
```

异常2堆栈信息如下:
```java
Exception in thread “main” java.lang.NullPointerException: str is marked @NonNull but is null
```

相当于以下代码
```java
package com.amos.lombok;

import lombok.NonNull;

public class NonNullExample {
    private String name;

    public NonNullExample(@NonNull String name) {
        if (name == null) {
            throw new NullPointerException("name is marked @NonNull but is null");
        } else {
            this.name = name;
        }
    }

    public static void example(@NonNull String str) {
        if (str == null) {
            throw new NullPointerException("str is marked @NonNull but is null");
        } else {
            System.out.println(str);
        }
    }

    public static void main(String[] args) {
        example((String)null);
        new NonNullExample((String)null);
    }
}
```
