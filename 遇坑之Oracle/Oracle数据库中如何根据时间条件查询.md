### Oracle数据库中如何根据时间条件查询？
语句

```sql
select * from 表名 where 日期 = to_date('2019/01/30 11:00:00', 'yyyy/mm/dd hh:mi:ss')
```

其中日期时间格式根据数据库中的格式设置
