### Mybatis中的特殊符号报错解决
因为Mybatis的mapper文件是xml格式的，所以不允许出现类似“<>&'"”这样的字符，而我们写sql的时候需要用到这些符号，有两种解决方案：
1. 用转义字符，将特殊符号替换掉，下面给出转义字符
![](/images/20190527153427.png)
2. 使用<![CDATA[]]>符号进行说明，将此类符号不进行解析
```sql
    SELECT
    <include refid="Base_Column_List"/>
    FROM BASE_GPS m
    WHERE DEVICE = #{deviceIndex}
    AND m.TIME <![CDATA[ >= ]]> to_date(#{startTime},'yyyy-mm-dd hh24:mi:ss')
    AND m.TIME <![CDATA[ <= ]]> to_date(#{endTime},'yyyy-mm-dd hh24:mi:ss')
    ORDER BY m.TIME ASC
```