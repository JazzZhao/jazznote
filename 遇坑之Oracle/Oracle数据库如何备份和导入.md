### Oracle数据库如何备份和导入？
使用`imp`命令导入:
+ 导入一个完整数据库，`imp 用户名/密码@数据库IP/数据库实例 file=E:\Dmp位置 log=E:\日志位置 full=y`
+ 将一个用户所属的数据导入另一个用户, `imp 用户名/密码@数据库IP/数据库实例 file=E:\Dmp位置 log=E:\日志位置 fromuser=用户名 touser=拷贝用户名`
+ 导入一个表，`imp 用户名/密码@数据库IP/数据库实例 file=E:\Dmp位置 log=E:\日志位置 fromuser=用户名 TABLES=(表名1,表名2)`

