### 如何用Mybatis实现组织单位树形结构查询
1. 在组织实体类中加入以下对象，使其包含子类列表

```java
/**
    * 当前部分下的子部门集合
    */
private List<SysOrg> children;
```

2. 在XML文件中编写结果MAP,以及查询组织和子类的查询语句

```xml
<resultMap id="DepartmentTreeMap" type="com.hisense.road.smartroad.manage.model.SysOrg">
    <result column="ID" jdbcType="DECIMAL" property="id"/>
    <result column="CODE" jdbcType="VARCHAR" property="code"/>
    <result column="ORG_LEVEL" jdbcType="DECIMAL" property="orgLevel"/>
    <result column="LABEL" jdbcType="VARCHAR" property="label"/>
    <result column="ORDER_NUM" jdbcType="DECIMAL" property="orderNum"/>
    <collection column="ID" property="children" ofType="DepartmentTreeMap" javaType="java.util.ArrayList"
                select="selectChildrenByid"/>
</resultMap>
<select id="selectChildrenByid" resultMap="DepartmentTreeMap" parameterType="java.lang.Long">
    select
    ID, CODE, ORG_LEVEL, LABEL,ORDER_NUM
    from SYS_ORG
    where DEL_FLG = '0' and PARENT_ID = #{id}
</select>
<select id="getDepartmentTree" resultMap="DepartmentTreeMap">
    select
    ID, CODE, ORG_LEVEL, LABEL,ORDER_NUM
    from SYS_ORG
    where DEL_FLG = '0' and PARENT_ID is null
</select>
```