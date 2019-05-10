### 如何使tomcat8.5不输出catalina.out
1. 找到tomcat下的   bin/catalina.sh;  找到下面这一段,
2. 把#CATALINA_OUT="$CATALINA_HOME"/logs/catalina.out 注释掉,改为CATALINA_OUT=/dev/null,
```java
if [ -z "$CATALINA_OUT" ] ; then
  #CATALINA_OUT="$CATALINA_HOME"/logs/catalina.out
  CATALINA_OUT=/dev/null
fi
```
对于/dev/null,它相当于垃圾桶一样,输出什么到它哪里,它直接丢了.所有我们在/dev/null,看到null这个文件,大小是空的,所有并不会占用空间大小了。