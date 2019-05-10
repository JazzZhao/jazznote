### Mybatis中的if-else
代码如下：

```xml
<choose>
    <when test="searchContent != null">
        <bind name="searchContent" value="'%' + searchContent + '%'" />
    </when>
    <otherwise>
        <bind name="searchContent" value="'%%'" />
    </otherwise>
</choose>
```
