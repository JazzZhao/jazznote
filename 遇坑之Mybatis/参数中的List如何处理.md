### 当参数含有List时，XML怎么批量处理
使用`foreach`标签，它可以在SQL语句中迭代一个集合，它的主要属性有item,index,collection,open,separator,close。
item：表示集合中每一个元素进行迭代时的别名
index：指定一个名字，用于表示在迭代过程中，每次迭代的位置
collection：代表集合本身
open：表示该语句以什么开始
separator：表示在每次进行迭代之间以什么符号作为分隔符
close：表示以什么结束
下面这个例子，批量处理某个集合中的所有ID值，将ID值迭代地放入`in`中

```xml
<update id="deleteBatchSysUser" parameterType="java.util.ArrayList">
    update SYS_USER
    set del_flg = '1'
    where id in
    <foreach collection="ids" item="item" open="(" separator="," close=")">
        #{item}
    </foreach>
</update>
```

下面这个例子为使用mybatis批量插入一组数据,首先要清楚批量插入数据的SQL为

```sql
INSERT INTO table (field1,field2,field3) VALUES ('a',"b","c"), ('a',"b","c"),('a',"b","c")
```

所以我们同样可以使用`froeach`标签进行sql拼接，代码如下

```xml
<!-- myself:批量插入 -->
<insert id="insertBatch" parameterType="java.util.List">
    insert into T_XXXRecord (AutoId, UserId, NoticedTime) values
    <foreach collection="list" item="item" index="index" separator=",">
        (#{item.autoid,jdbcType=BIGINT},
        #{item.userid,jdbcType=BIGINT},
        #{item.noticedtime,jdbcType=TIMESTAMP})
    </foreach>
</insert>
```

>注：mysql批量插入的限制是一次批量：1M