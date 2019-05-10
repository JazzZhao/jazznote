### 如何将Java中的Date类型保存到Oracle数据库中？
Oracle数据库时间格式为DATE，无法使用Java直接将`Java.util.Date`格式的时间对象直接插入到数据库，需要利用java中`SimpleDateFormat`类将时间对象转为需要的字符串形式，再用数据库中的`to_date`方法将字符串转化为date格式插入数据库，具体代码如下

```sql
SimpleDateFormat df = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");
update 表名 set 时间 = to_date('"+df.format(new Date())+"','yyyy/mm/dd hh24:mi:ss') 
```

该段代码实现了将当前时间插入数据库的操作
>注：Java中HH表示24小时制，hh表示12小时制；Oracle中hh表示12小时，hh24表示24小时
