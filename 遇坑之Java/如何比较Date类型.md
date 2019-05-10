### 如何比较Date类型？
+ java.util.Date类实现了Comparable接口，可以直接调用Date的compareTo()方法来比较大小，compareTo()方法的返回值，date1小于date2返回-1，date1大于date2返回1，相等返回0，如下图

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class test {
    public void testDate(){
        String beginTime = "2018-07-28 14:42:32";
        String endTime = "2018-07-29 14:23:21";
        SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        try {
            Date date1 = format.parse(beginTime);
            Date date2 = format.parse(endTime);
            int compareTo = date1.compareTo(date2);
            System.out.println(compareTo);
        } catch (ParseException e) {
            e.printStackTrace();
        }
    }
}
```

+ 通过Date自带的before()或者after()方法比较，返回值为boolean类型

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class test {
    public void testDate(){
        String beginTime = "2018-07-28 14:42:32";
        String endTime = "2018-07-29 14:23:21";
        SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        try {
            Date date1 = format.parse(beginTime);
            Date date2 = format.parse(endTime);
            boolean before = date1.before(date2);
            System.out.println(before);
        } catch (ParseException e) {
            e.printStackTrace();
        }
    }
}

```

+ 通过调用Date的getTime()方法获取毫秒数来进行比较

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class test {
    public void testDate(){
        String beginTime = "2018-07-28 14:42:32";
        String endTime = "2018-07-29 14:23:21";
        SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        try {
            Date date1 = format.parse(beginTime);
            Date date2 = format.parse(endTime);

            long bgeginMillisecond = date1.getTime();
            long endMillisecond = date2.getTime();

            System.out.println(bgeginMillisecond > endMillisecond);
        } catch (ParseException e) {
            e.printStackTrace();
        }
    }
}
```