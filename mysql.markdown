##  连接mysql
    在mysql的bin目录下，打开cmd，输入mysql -u root -p
    退出: exit
##  mysql基本操作
    1.删除shop数据库: DROP DATABASE shop;
    2.创建数据库: CREATE DATABASE shop;
##  1数据库和sql
### 1.1数据库是什么
    1.DB database
        1.1层次数据库: 树形结构
        1.2关系型数据库: 行和列组成的二维表 
    2.DBMS database management system 数据库管理系统(mysql oracle db2 sqlServer)
    3.sql structure query language 专门用来与数据库通信的语言   

### 1.2数据库的结构
    客户端-服务器-数据库
    客户端即个人PC
    服务器需要接受多个客户端和处理庞大的数据库，所以需要性能优于客户端。

- 数据库的特点:
  - 将数据放到表中，再将表放到库中
  - 一个数据库中有多个表，表名具有唯一性
  - 表具有独特的特性，类似java中每个类都有各自的不同特性(属性，方法)
  - 表中的一列称为字段，一列对应java的属性
  - 表中数据按行(行称为记录)存储，每一行类似java的一个对象
  - 主键: 可以通过该列取出特定的商品数据。

<font color='red'> 

注意点：
1.关系数据库必须以行为单位进行读写
2.一个单元格只能输入一个数据
</font>

### 1.3SQL概要
- SQL语句
  - DDL(Data Definition Language, 数据定义语言)
      - CREATE： 创建数据库和表等对象
      - DROP： 删除数据库和表等对象
      - ALTER： 修改数据库和表等对象的结构
  - DML(Data Manipulation Language，数据操纵语言) 使用最多
      - SELECT：查询表中的数据
      - INSERT：向表中插入新数据
      - UPDATE：更新表中的数据
      - DELETE：删除表中的数据
  - DCL（Data Control Language，数据控制语言）
    - COMMIT： 确认对数据库中的数据进行的变更
    - ROLLBACK： 取消对数据库中的数据进行的变更
    - GRANT： 赋予用户操作权限
    - REVOKE： 取消用户的操作权限

<font color='red'>

关键字不区分大小写
字符串和日期常数需要使用单引号（'）括起来。'2010-01-26'
数字常数无需加注单引号（直接书写数字即可）。
</font> 

### 1.4表的创建
    表的创建格式：
        CREATE TABLE <表名>
        (<列名1> <数据类型> <该列所需约束>，
        .
        .
        <该表的约束1>, ……);
    样例:
        create table testTable
        (productId VARCHAR(10) NOT NULL,
        age INTEGER DEFAULT 0,
        PRIMARY KEY(productId));
- 数据类型
  - INTEGER型: 整形
  - CHAR: 字符型, CHAR(10)中10为字符串最大长度，定长字符串: 输入的字符串长度没达到10时，用空格补足。
  - VARCHAR(10): 可变长度字符串: 输入的字符串长度没达到10时，不用空格补足。
  - DATE: 用来指定存储日期（年月日）的列的数据类型（日期型）。

<font color='red'>

VARCHAR更加节省空间，CHAR则效率更加优秀
由于VARCHAR长度可变，若经常修改，会引起行迁移等n'x现象，应尽量避免这种情况，设计为CHAR
</font>

- 约束设置
  - NOT NULL: 要求不能为空
  - PRIMARY KEY (product_id): 主键约束
### 1.5表的删除和更新
    删除表: DROP TABLE 表名
    添加一列(att): alter table testtable add column att char(10) not null;
    删除一列(att): alter table testtable drop column att
    插入数据:
        start transaction;
        insert into testtable values('0001', 18);
        commit;

        testtable为表名称，commit表示提交修改。
    重命名表格:
        RENAME TABLE Poduct to Product;
    
## 2.查询基础
### 2.1 select语句基础
    选择列: select 列名1, 列名2 from 表名
    选择所有列: select * from 表名
    为列设置别名: select 列名1 as 别名1, select 列名2 as 别名2 from 表名
        当别名是中文时，需要用双引号括起来
    从结果中删除重复行:select distinct 列名1, 列名2 from 表名; 该命令表示删除列名1和列名2同时重复的。
        null也被算为一类，删除重复后会只剩下一个null
    where语句筛选数据: select 列名1, 列名2 from 表名 where 表达式。
        其运行原理为首先通过WHERE 子句查询出符合指定条件的记录，然后再选取出 SELECT 语句指定的列
    注释: -- 和 /* */
### 2.2 算数运算符和比较运算符
    算数运算符: 
        select age * 2 as age_x2 from testtable;
<font color='red'>

所有包含 NULL 的计算，结果肯定是 NULL。
</font>

    比较运算符: 
        在where中已经使用，
        不等号为<>
        对字符串进行比较时，是先比较首字母，后比较之后的字母。
        IS NULL和IS NOT NULL: 比较运算符(比如<> 2000)是无法调出NULL数据的,所有需要使用is null来调出null数据。
### 2.3 逻辑运算符
    NOT 
    OR 
    AND 
    分为真，假和不确定，当值为NULL时为不确定，不确定and真为不确定，不确定or假为不确定，不确定or真为真。

## 3 聚合与排序
### 3.1 对表进行聚合查询
    聚合函数
        COUNT: 计算表中的记录数（行数）
            select count(*), count(have_null) from testtable;
            COUNT(*)会得到包含NULL的数据行数，而COUNT(列名)会得到NULL之外的数据行数。
        SUM: 计算表中数值列中数据的合计值
            SELECT SUM(列名) FROM Product;
        AVG: 计算表中数值列中数据的平均值
            同SUM
        MAX: 求出表中任意列中数据的最大值
            同SUM
        MIN: 求出表中任意列中数据的最小值
            同SUM

    DISTINCT特殊用法: 
        计算去除重复数据后的数据行数
            SELECT COUNT(DISTINCT product_type) FROM Product;
        计算去除重复数据后的数据行数
            SELECT DISTINCT COUNT(product_type) FROM Product;
### 3.2 对表进行分组
    SELECT <列名1>, <列名2>, <列名3>, ……
    FROM <表名>
    GROUP BY <列名1>, <列名2>, <列名3>, ……;

    例如
    SELECT product_type, AVG(sale_price)
    ROM Product
    GROUP BY product_type;

    语句的书写顺序
        SELECT → FROM →  WHERE →  GROUP BY
    语句的执行顺序
        FROM → WHERE → GROUP BY → SELECT
<font color='red'>

- 当聚合键中包含 NULL 时，也会将NULL作为一组特定的数据，
- 使用聚合函数时， SELECT 子句中只能存在: 常数，聚合函数，聚合键(groupby中指定的列名)，也就是说，select子句中不能出现聚合键之外的列名。
- GROUP BY子句结果的显示是无序的。
- 在GROUP BY子句中不能使用SELECT子句中定义的别名。
- 只有SELECT子句和HAVING子句（以及ORDER BY子句）中能够使用聚合函数。
</font>

### 3.3 为聚合结果指定条件
    having功能: 指定条件来选取特定组:
        语句的书写顺序
            SELECT → FROM →  WHERE →  GROUP BY → HAVING
        语句的执行顺序
            FROM → WHERE → GROUP BY → SELECT → HAVING
            
```sql
    SELECT product_type, AVG(sale_price)  
    FROM Product  
    GROUP BY product_type
    HAVING AVG(sale_price) >= 2500;
```

    having子句能使用的三种要素:
        常数(字符串也是)
        聚合函数
        group by指定的列名
    
    聚合键的条件在having中和where中都可以实现，建议使用where，理由:
        1.WHERE 子句 = 指定行所对应的条
          HAVING 子句 = 指定组所对应的条件
        2.执行count函数等对表中数据进行聚合操作时，DBMS内部会进行排序操作。因为where是在count函数之前执行的，所以可以提高处理速度。
### 3.4 对查询结果进行排序

    order by子句:
        子句使用样例:
            SELECT 列名1, 列名2, 列名3
            FROM 表名
            ORDER BY 排序基准列1, 排序基准列2
        子句书写顺序 select → from → where → group by → having → order by
        语句执行顺序 from → where → group by → having → select → order by
    指定升序或降序:
        order by 列名 asc \desc
    指定多个排序键:
        order by 列名1, 列名2
    排序键中含有NULL时，会显示在开头或者末尾

<font color='red'>

order by可以使用select子句中没有使用过的列名，也可以使用聚合函数

</font>

## 4 数据更新
### 4.1 数据的插入(INSERT)
    单行插入: 
        INSERT INTO 表名 (列1, 列2, 列3, ……) VALUES (值1, 值2, 值3, ……);
    多行插入:
        INSERT INTO 表名> (列1, 列2, 列3, ……) VALUES (值1, 值2, 值3, ……), (值1, 值2, 值3, ……);       
    如果是全列, 可以把(列1, 列2, 列3, ……)省略掉
    插入默认值, 值为default
    插入NULL, 值为null
    插入一行时，如果省略一列名称，没有非0约束的话就是默认值，又非0约束的话就会报错。
    复制表至另一个表
        insert... select...
        这里的select语句可以使用任何的sql函数，例如: 
        但需要注意的是select中不能出现除聚合键外的键，这就意味着如果用了group by，该表最好都是存放使用聚合函数的列。
```sql
INSERT INTO ProductType (product_type, sum_sale_price, sum_purchase_price)
SELECT product_type, SUM(sale_price), SUM(purchase_price)
FROM Product
GROUP BY product_type;
```
### 4.2 数据的删除(DELETE)
delete语句删除的是记录(行)，不是表或者列。

    删除全部行数据: delete from 表名
    删除部分数据, 通过where指定条件: delete from 表名 where 条件
    truncate也是删除全部记录, 但是他不能用where, 也因此速度比delete快

### 4.3 数据的更新(UPDATE)
    update是修改表中已有的记录

例如:
修改Product表中的regist_date列，使该列值全为'2009-10-10'
```sql
    UPDATE Product
    SET regist_date = '2009-10-10';
```
    也可以使用where语句来指定记录
    将数据更新为 NULL（该更新俗称为 NULL 清空）: 
        SET regist_date = NULL
    
update指定多行: 
```sql
UPDATE Product
--方法1
SET (sale_price, purchase_price) = (sale_price * 10, purchase_price / 2)
--方法2
SET sale_price = sale_price * 10,
    purchase_price = purchase_price / 2
WHERE product_type = '厨房用具';
```
### 4.4 事务
    事务就是需要在同一个处理单元中执行的一系列更新处理的集合。
事务例子:
```sql
START TRANSACTION;
-- 将运动T恤的销售单价降低1000日元
UPDATE Product
SET sale_price = sale_price - 1000
WHERE product_name = '运动T恤';
-- 将T恤衫的销售单价上浮1000日元
UPDATE Product
SET sale_price = sale_price + 1000
WHERE product_name = 'T恤衫';
COMMIT;
```
    如果不执行事务的话，将commit换成rollback
<font color='red'>

commit提交之后就无法更改，一定要小心谨慎
</font>

## 第五章
### 5.1 视图
    视图的优点
        1.由于视图无需保存数据，因此可以节省存储设备的容量
        2.可以将频繁使用的SELECT语句保存成视图，这样就不用每次都重新书写了。

视图的创建
```sql
CREATE VIEW 视图名称(视图列名1, 视图列名2, ……)
AS
SELECT语句

CREATE VIEW ProductSum (product_type, cnt_product)
AS
SELECT product_type, COUNT(*)
FROM Product
GROUP BY product_type;
```
使用视图
```sql
SELECT product_type, cnt_product
FROM ProductSum
```
### 5.2 子查询
### 5.3 关联子查询