### mybatis中“#”和“$”的区别
动态sql是mybatis的主要特征之一，在mapper中定义的参数传给xml中后，在查询之前mybatis会对其进行动态解析。mybatis为我们提供了两种支持动态sql的方法：`#{}`和`${}`。
在下面的语句中,当name为zhangsan时，两种方式无任何区别：

```sql
select * from user where name = #{name};
select * from user where name = ${name};
```

其解析后的结果均为：

```sql
select * from user where name = 'zhangsan';
```

但是`#{}`和`${}`在预编译中的处理是不一样的。`#{}`是预编译处理，`${}`是字符串替换, `#{}`在预处理时，会在参数部分用一个占位符？代替，调用PreparedStatement的set方法来赋值。如下sql语句：

```sql
select * from user where name = ?;
```

而`${}`只是简单的字符替换，在动态解析阶段，该语句被解析为：

```sql
select * from user where name = 'zhangsan';
```

使用`#{}`可以有效的防止SQL注入，提高系统安全性。
预编译是提前对SQL语句进行预编译，而其后注入的参数将不会再进行SQL编译。我们知道，SQL注入是发生在编译的过程中，因为恶意注入了某些特殊字符，最后被编译成了恶意的执行操作。而预编译机制则可以很好的防止SQL注入。
那么，在使用过程中我们应该使用哪种方式呢？
答案是，优先使用 `#{}`。因为 `${}` 会导致 sql 注入的问题。看下面的例子：

```sql
select * from ${tableName} where name = #{name}
```

在这个例子中，如果表名为

```sql
user; delete user; --
``` 

则动态解析之后 sql 如下：

```sql
select * from user; delete user; -- where name = ?;
```

在`--`之后的语句被注释掉，而原本查询用户的语句变成了查询所有用户信息+删除用户表的语句，会对数据库造成重大损伤，极大可能导致服务器宕机。
但是表名用参数传递进来的时候，只能使用 `${}` ，具体原因可以自己做个猜测，去验证。这也提醒我们在这种用法中要小心sql注入的问题。