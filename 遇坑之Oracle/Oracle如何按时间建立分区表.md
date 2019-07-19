### Oracle如何按时间建立分区表？
#### 为什么分区？
1. 一般一张表超过2G的大小，Oracle就推荐分区表
2. 这张表主要用于查询，而且可以按分区查询，只会修改当前最新分区的数据，对以前的不怎么做删除和修改
3. 数据量大查询慢
4. 便于维护，可扩展
5. 与普通表的sql一致，不需要因为普通表变分区表而修改代码

#### oracle 11g如何按天、周、月、年自动分区
1. 按年创建
```sql
    CREATE TABLE VEHICLE_PASSING_RECORD (
        ID NUMBER(38,0) not null,
        PLATE_NUM VARCHAR2(20),
        PLATE_TYPE VARCHAR2(20),
        PLATE_COLOR VARCHAR2(20),
        DATE_TIME DATE,
    );
    PARTITION BY RANGE (DATE_TIME) INTERVAL (numtoyminterval(1, 'year'))
    (partition part_t01 values less than(to_date('2019-01-12', 'yyyy-mm-dd')));
```

2. 按月创建
```sql
    CREATE TABLE VEHICLE_PASSING_RECORD (
        ID NUMBER(38,0) not null,
        PLATE_NUM VARCHAR2(20),
        PLATE_TYPE VARCHAR2(20),
        PLATE_COLOR VARCHAR2(20),
        DATE_TIME DATE,
    );
    PARTITION BY RANGE (DATE_TIME) INTERVAL (numtoyminterval(1, 'month'))
    (partition part_t01 values less than(to_date('2019-01-12', 'yyyy-mm-dd')));
```

3. 按天创建
```sql
    CREATE TABLE VEHICLE_PASSING_RECORD (
        ID NUMBER(38,0) not null,
        PLATE_NUM VARCHAR2(20),
        PLATE_TYPE VARCHAR2(20),
        PLATE_COLOR VARCHAR2(20),
        DATE_TIME DATE,
    );
    PARTITION BY RANGE (DATE_TIME) INTERVAL (NUMTODSINTERVAL(1, 'day'))
    (partition part_t01 values less than(to_date('2019-01-12', 'yyyy-mm-dd')));
```

4. 按周创建
```sql
    CREATE TABLE VEHICLE_PASSING_RECORD (
        ID NUMBER(38,0) not null,
        PLATE_NUM VARCHAR2(20),
        PLATE_TYPE VARCHAR2(20),
        PLATE_COLOR VARCHAR2(20),
        DATE_TIME DATE,
    );
    PARTITION BY RANGE (DATE_TIME) INTERVAL (NUMTODSINTERVAL(7, 'day'))
    (partition part_t01 values less than(to_date('2019-01-12', 'yyyy-mm-dd')));
```

#### 查询当前表有多少分区
```sql
    select table_name,partition_name from user_tab_partitions where table_name='TEST_PART';
```

#### 查询表中的某个分区里的数据
```sql
    select * from TEST_PART partition(SYS_P21);
```