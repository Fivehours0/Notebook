<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [连接mysql](#%E8%BF%9E%E6%8E%A5mysql)
- [mysql基本操作](#mysql%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C)
- [1.数据库和sql](#1%E6%95%B0%E6%8D%AE%E5%BA%93%E5%92%8Csql)
  - [1.1数据库是什么](#11%E6%95%B0%E6%8D%AE%E5%BA%93%E6%98%AF%E4%BB%80%E4%B9%88)
  - [1.2数据库的结构](#12%E6%95%B0%E6%8D%AE%E5%BA%93%E7%9A%84%E7%BB%93%E6%9E%84)
  - [1.3SQL概要](#13sql%E6%A6%82%E8%A6%81)
  - [1.4表的创建](#14%E8%A1%A8%E7%9A%84%E5%88%9B%E5%BB%BA)
  - [1.5表的删除和更新](#15%E8%A1%A8%E7%9A%84%E5%88%A0%E9%99%A4%E5%92%8C%E6%9B%B4%E6%96%B0)
- [2.查询基础](#2%E6%9F%A5%E8%AF%A2%E5%9F%BA%E7%A1%80)
  - [2.1 select语句基础](#21-select%E8%AF%AD%E5%8F%A5%E5%9F%BA%E7%A1%80)
  - [2.2 算数运算符和比较运算符](#22-%E7%AE%97%E6%95%B0%E8%BF%90%E7%AE%97%E7%AC%A6%E5%92%8C%E6%AF%94%E8%BE%83%E8%BF%90%E7%AE%97%E7%AC%A6)
  - [2.3 逻辑运算符](#23-%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6)
- [3 聚合与排序](#3-%E8%81%9A%E5%90%88%E4%B8%8E%E6%8E%92%E5%BA%8F)
  - [3.1 对表进行聚合查询](#31-%E5%AF%B9%E8%A1%A8%E8%BF%9B%E8%A1%8C%E8%81%9A%E5%90%88%E6%9F%A5%E8%AF%A2)
  - [3.2 对表进行分组](#32-%E5%AF%B9%E8%A1%A8%E8%BF%9B%E8%A1%8C%E5%88%86%E7%BB%84)
  - [3.3 为聚合结果指定条件](#33-%E4%B8%BA%E8%81%9A%E5%90%88%E7%BB%93%E6%9E%9C%E6%8C%87%E5%AE%9A%E6%9D%A1%E4%BB%B6)
  - [3.4 对查询结果进行排序](#34-%E5%AF%B9%E6%9F%A5%E8%AF%A2%E7%BB%93%E6%9E%9C%E8%BF%9B%E8%A1%8C%E6%8E%92%E5%BA%8F)
- [4 数据更新](#4-%E6%95%B0%E6%8D%AE%E6%9B%B4%E6%96%B0)
  - [4.1 数据的插入(INSERT)](#41-%E6%95%B0%E6%8D%AE%E7%9A%84%E6%8F%92%E5%85%A5insert)
  - [4.2 数据的删除(DELETE)](#42-%E6%95%B0%E6%8D%AE%E7%9A%84%E5%88%A0%E9%99%A4delete)
  - [4.3 数据的更新(UPDATE)](#43-%E6%95%B0%E6%8D%AE%E7%9A%84%E6%9B%B4%E6%96%B0update)
  - [4.4 事务](#44-%E4%BA%8B%E5%8A%A1)
- [第五章](#%E7%AC%AC%E4%BA%94%E7%AB%A0)
  - [5.1 视图](#51-%E8%A7%86%E5%9B%BE)
  - [5.2 子查询](#52-%E5%AD%90%E6%9F%A5%E8%AF%A2)
  - [5.3 关联子查询](#53-%E5%85%B3%E8%81%94%E5%AD%90%E6%9F%A5%E8%AF%A2)
- [第六章](#%E7%AC%AC%E5%85%AD%E7%AB%A0)
  - [6.1 各种各样的函数](#61-%E5%90%84%E7%A7%8D%E5%90%84%E6%A0%B7%E7%9A%84%E5%87%BD%E6%95%B0)
  - [6.2 谓词](#62-%E8%B0%93%E8%AF%8D)
  - [6.3 case表达式](#63-case%E8%A1%A8%E8%BE%BE%E5%BC%8F)
- [第七章 集合运算](#%E7%AC%AC%E4%B8%83%E7%AB%A0-%E9%9B%86%E5%90%88%E8%BF%90%E7%AE%97)
  - [表的加减法(表的合并)](#%E8%A1%A8%E7%9A%84%E5%8A%A0%E5%87%8F%E6%B3%95%E8%A1%A8%E7%9A%84%E5%90%88%E5%B9%B6)
    - [集合运算](#%E9%9B%86%E5%90%88%E8%BF%90%E7%AE%97)
  - [联结(以列为单位对表进行联结)](#%E8%81%94%E7%BB%93%E4%BB%A5%E5%88%97%E4%B8%BA%E5%8D%95%E4%BD%8D%E5%AF%B9%E8%A1%A8%E8%BF%9B%E8%A1%8C%E8%81%94%E7%BB%93)
      - [inner join(内联结)](#inner-join%E5%86%85%E8%81%94%E7%BB%93)
      - [outer join(外联结)](#outer-join%E5%A4%96%E8%81%94%E7%BB%93)
      - [三张以上表的联结](#%E4%B8%89%E5%BC%A0%E4%BB%A5%E4%B8%8A%E8%A1%A8%E7%9A%84%E8%81%94%E7%BB%93)
      - [cross join(交叉联结)](#cross-join%E4%BA%A4%E5%8F%89%E8%81%94%E7%BB%93)
- [第八章 SQL高级处理](#%E7%AC%AC%E5%85%AB%E7%AB%A0-sql%E9%AB%98%E7%BA%A7%E5%A4%84%E7%90%86)
- [第九章 JAVA与SQL连接](#%E7%AC%AC%E4%B9%9D%E7%AB%A0-java%E4%B8%8Esql%E8%BF%9E%E6%8E%A5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## ACID特性
    DBMS 的事务都遵循四种特性，将这四种特性的首字母结合起来统称为 ACID 特性。这是所有 DBMS 都必须遵守的规则。

 1.原子性（Atomicity）
 
    原子性是指在事务结束时，其中所包含的更新处理要么全部执行，要
    么完全不执行，也就是要么占有一切要么一无所有。例如，在之前的例
    子中，在事务结束时，绝对不可能出现运动 T 恤的价格下降了，而 T 恤
    衫的价格却没有上涨的情况。该事务的结束状态，要么是两者都执行了
    （COMMIT），要么是两者都未执行（ROLLBACK）。
    从事务中途停止的角度去考虑，就能比较容易理解原子性的重要性了。
    由于用户在一个事务中定义了两条 UPDATE 语句， DBMS 肯定不会只执
    行其中一条，否则就会对业务处理造成影响。
 
 2.一致性（Consistency）
 
    一致性指的是事务中包含的处理要满足数据库提前设置的约束，如主
    键约束或者 NOT NULL 约束等。例如，设置了 NOT NULL 约束的列是
    不能更新为 NULL 的，试图插入违反主键约束的记录就会出错，无法执行。
    对事务来说，这些不合法的 SQL 会被回滚。也就是说，这些 SQL 处理会
    被取消，不会执行。

 3.隔离性（Isolation）
    
    隔离性指的是保证不同事务之间互不干扰的特性。该特性保证了事务
    之间不会互相嵌套。此外，在某个事务中进行的更改，在该事务结束之前，
    对其他事务而言是不可见的。因此，即使某个事务向表中添加了记录，在
    没有提交之前，其他事务也是看不到新添加的记录的。
    
 4.持久性（Durability）
 
    持久性也可以称为耐久性，指的是在事务（不论是提交还是回滚）结
    束后， DBMS 能够保证该时间点的数据状态会被保存的特性。即使由于系
    统故障导致数据丢失，数据库也一定能通过某种手段进行恢复。
    如果不能保证持久性，即使是正常提交结束的事务，一旦发生了系统
    故障，也会导致数据丢失，一切都需要从头再来。
    保证持久性的方法根据实现的不同而不同，其中最常见的就是将事务
    的执行记录保存到硬盘等存储介质中（该执行记录称为日志）。当发生故
    障时，可以通过日志恢复到故障发生前的状态。

##  连接mysql
    在mysql的bin目录下，打开cmd，输入mysql -u root -p
    退出: exit
##  mysql基本操作
    1.删除shop数据库: DROP DATABASE shop;
    2.创建数据库: CREATE DATABASE shop;
##  1.数据库和sql
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

注意点：
1. 关系数据库必须以行为单位进行读写
2. 一个单元格只能输入一个数据

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
    
注意点：
1. 关键字不区分大小写
2. 字符串和日期常数需要使用单引号（'）括起来。'2010-01-26'
3. 数字常数无需加注单引号（直接书写数字即可）。

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

注意点：
1. VARCHAR更加节省空间，CHAR则效率更加优秀
2. 由于VARCHAR长度可变，若经常修改，会引起行迁移等现象，应尽量避免这种情况，设计为CHAR


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
        
注意点：
所有包含 NULL 的计算，结果肯定是 NULL。

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
        
注意点：
- 当聚合键中包含 NULL 时，也会将NULL作为一组特定的数据，
- 使用聚合函数时， SELECT 子句中只能存在: 常数，聚合函数，聚合键(groupby中指定的列名)，也就是说，select子句中不能出现聚合键之外的列名。
- GROUP BY子句结果的显示是无序的。
- 在GROUP BY子句中不能使用SELECT子句中定义的别名。
- 只有SELECT子句和HAVING子句（以及ORDER BY子句）中能够使用聚合函数。

### 3.3 为聚合结果指定条件
    having功能: 指定条件来选取特定组:
        语句的书写顺序
            SELECT → FROM →  WHERE →  GROUP BY → HAVING
        语句的执行顺序
            FROM → WHERE → GROUP BY → SELECT → HAVING
            
```
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

**order by可以使用select子句中没有使用过的列名，也可以使用聚合函数**

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
```
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
```
    UPDATE Product
    SET regist_date = '2009-10-10';
```
    也可以使用where语句来指定记录
    将数据更新为 NULL（该更新俗称为 NULL 清空）: 
        SET regist_date = NULL
    
update指定多行: 
```
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
```
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
    如果不执行事务的话，将commit换成rollback,可进行回滚，取消事务。

注意点：
commit提交之后就无法更改，一定要小心谨慎

## 第五章
### 5.1 视图
    视图的优点
        1.由于视图无需保存数据，因此可以节省存储设备的容量
        2.可以将频繁使用的SELECT语句保存成视图，这样就不用每次都重新书写了。
    视图中的数据会随着原表的变化而不断更新。视图的更新同样会影响到表。


视图的创建
```
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
```
SELECT product_type, cnt_product
FROM ProductSum
```
    可以从视图中创建视图，但最好不要这么做，多重视图会降低SQL的性能

视图的限制

    1.定义视图时不能使用order by语句, 因为视图和表一样是无序的
    2.在视图满足一定条件时，可使用insert等对视图进行更新。
        条件:
            1.select语句中未使用distinct
            2.from子句中只有一张表
            3.未使用group by子句
            4.未使用having子句
    postgre中, 视图为只读, 需要额外的指令才能更新视图

删除视图
    drop view 视图名称 (列名1, 列名2, ...)
    在PostgreSQL中，如果删除以视图为基础创建出来的多重视图，由于存在关联的视图，若要删除，则使用cascade关键字(DROP VIEW ProductSum CASCADE;)(ProductSum是视图名称)
### 5.2 子查询
    子查询是一张一次性视图(用在from里面)
    子查询包含有嵌套结构，且可多层嵌套。首先执行FROM子句中的SELECT，然后执行外层的SELECT
例子:
```
SELECT product_type, cnt_product
FROM (SELECT *
FROM (SELECT product_type, COUNT(*) AS cnt_product
FROM Product
GROUP BY product_type) AS ProductSum
WHERE cnt_product = 4) AS ProductSum2;
```
子查询的名称

    必须设定子查询名称。ProductSum和ProductSum2即为名称, 尽量从处理内容的角度出发为子查询设定恰当的名称。

标量子查询

    返回一个数值

下述代码需要找出销售单价高于全部商品平均单价的商品, 因为需要计算均值，所以使用了标量子查询
```
SELECT product_id, product_name, sale_price
FROM Product
WHERE sale_price > (SELECT AVG(sale_price)
FROM Product);
```

标量子查询能够使用常数或者列名的地方，无论是 SELECT 子句、 GROUP BY 子句、 HAVING 子句，还是ORDER BY 子句，几乎所有的地方都可以使用。

```
SELECT product_id,
product_name,
sale_price,
(SELECT AVG(sale_price)
FROM Product) AS avg_price
FROM Product;
```
<font color=red>不能返回多行结果</font>

### 5.3 关联子查询
    关联条件一定要写在子查询中。因为内部看的到外部, 外部看不到内部。在如下例子中，p1看不到p2, p2可以看到p1。

例子:

    选取出各商品种类中高于该商品种类的平均销售单价的商品
```
SELECT product_type, product_name, sale_price
FROM Product AS P1
WHERE sale_price > (SELECT AVG(sale_price)
FROM Product AS P2
-- 下面这句是关联条件
WHERE P1.product_type = P2.product_type
GROUP BY product_type);
```

总结:

    1、关联子查询的执行逻辑完全不同于正常的SELECT语句。

    2、关联子查询执行逻辑如下：

    （1）先从主查询的Product表中product _type列取出第一个值，进入子查询中，得到子查询结果，然后返回父查询，判断父查询的where子句条件，则返回整个语句的第1条结果。

    （2）重复上述操作，直到所有主查询中的Product表中product _type列记录取完为止。得出整个语句的结果集，就是最后的答案。

参考链接
    https://zhuanlan.zhihu.com/p/41844742
    https://www.cnblogs.com/fuyusheng/p/12510957.html

## 第六章
### 6.1 各种各样的函数
算数函数(用法与聚合函数一致):

    绝对值: ABS(数值) 
    求余: MOD(被除数，除数) 例: MOD(7, 3) = 1
    四舍五入: ROUND(对象数值, 保留小数的位数)
字符串函数(str1, str2, str3为列名称):

    拼接: CONCAT(str1, str2, str3)(mysql)
          || (postgreSql)
    字符串长度: LENGTH(str1)
        半角英文字母占1个字节, 全角字符占用2个字节
    小写转换: LOWER(str1)
    字符串的替换: REPLACE(对象字符串，需要替换的字符串，替换成该字符串)
        使用 REPLACE 函数，可以将字符串的一部分替换为其他的字符串
    字符串的截取: SUBSTRING（对象字符串 FROM 截取的起始位置 FOR 截取的字符数）
        例如: SUBSTRING(str1 FROM 3 FOR 2)
    大写转换: UPPER(字符串)
日期函数

    获得当前日期: SELECT CURRENT_DATE;
    获得当前时间: SELECT CURRENT_DATE;
    获取当前日期和时间: select current_timestamp;
    截取日期元素: SELECT CURRENT_TIMESTAMP,
                 EXTRACT(YEAR FROM CURRENT_TIMESTAMP) AS year;
转换函数

    类型转换: SELECT CAST('0001' AS SIGNED INTEGER);
        signed interge 有符号整数
    将null转化为其他值: COALESCE(str1, str2, '0002');
        判断str1是否为null值, 若为null，则判断str2，否则返回str1中的值，以此类推。(str1是列名, 也可以是值)
聚合函数
### 6.2 谓词
返回值是真值(TRUE/FALSE/UNKNOWN), 例如之前的=, <>, >, <为比较谓词

LIKE谓词:
```
select *
from testtable
where type like 'java%'
```
    上述程序中, testtable为表名, type为列名. 其中'java%'能够匹配到开头含有java的字符串, 例如java, javase等。该模式为前方一致查询。还有中间一致'%java%', 后方一致'%java'.

    %不限制字符的个数, ‘ja__’可以匹配java但是不能匹配javase. 一个_表示一个字符, %则不限制字符的个数. 

BETWEEN谓词:
```
select *
from testtable
where age between 19 and 23;
```
    上述程序筛选出age列数据大于等于19, 小于等于23的记录。
    若不想包含等号, 则where age > 19 and age < 23
IS NULL和IS NOT NULL

IN和NOT IN:
```
select *
from testtable
where age IN (19, 23);
```
    IN也可以用OR实现, 条件一多的话, 用OR就比较繁琐了。

### 6.3 case表达式
相当于程序语言中的switch case

例子: 

```
-- 使用搜索CASE表达式的情况（重写代码清单6-41）
SELECT product_name,
CASE WHEN product_type = '衣服'
THEN 'A：' ||product_type
WHEN product_type = '办公用品'
THEN 'B：' ||product_type
WHEN product_type = '厨房用具'
THEN 'C：' ||product_type
ELSE NULL
END AS abc_product_type
FROM Product;
```
```
-- 使用简单CASE表达式的情况
SELECT product_name,
CASE product_type
WHEN '衣服' THEN 'A：' || product_type
WHEN '办公用品' THEN 'B：' || product_type
WHEN '厨房用具' THEN 'C：' || product_type
ELSE NULL
END AS abc_product_type
FROM Product;
```

效果: 相当于增加了abc_product_type列

    product_name | abc_product_type
    ---------------+------------------
    T恤衫 | A ：衣服
    打孔器 | B ：办公用品
    运动T恤 | A ：衣服
    菜刀 | C ：厨房用具
    高压锅 | C ：厨房用具
    叉子 | C ：厨房用具
    擦菜板 | C ：厨房用具
    圆珠笔 | B ：办公用品

* 单重的when then意义上等同于if else。
* 在mysql中，可以使用if来完成case when then。

if表达式为(expr2, 3也可以返回真值(TRUE/FALSE的表达式)):
    
    IF(expr1,expr2,expr3)，如果expr1的值为true，则返回expr2的值，如果expr1的值为false，则返回expr3的值。

## 第七章 集合运算
### 表的加减法(表的合并)
#### 集合运算
UNION(去掉重复行)/UNION ALL(包含重复行), 表的加法:
```
SELECT product_id, product_name
FROM Product
UNION
SELECT product_id, product_name
FROM Product2;
```

INTERSECT(交集), 选取表的公共部分, 用法与UNION一致
EXCEPT(差集), 记录的减法, 用法与UNION一致

集合运算的注意事项

* 作为运算对象的记录的列数必须相同

```
-- 列数不一致时会发生错误
SELECT product_id, product_name
FROM Product
UNION
SELECT product_id, product_name, sale_price
FROM Product2;
```
* 作为运算对象的记录中列的类型必须一致 
* 可以使用任何SELECT语句，但ORDER BY子句只能在最后使用一次

```
SELECT product_id, product_name
FROM Product
WHERE product_type = '厨房用具'
UNION
SELECT product_id, product_name
FROM Product2
WHERE product_type = '厨房用具'
ORDER BY product_id;
```

### 联结(以列为单位对表进行联结)
##### inner join(内联结)

example:
1. on中可以使用<=等, 不一定要是=
2. 该example中结合了where
```
select t.age, s.age, s.student_id
from teacher as t inner join student as s
on s.student_id = t.teacher_id
where s.age = 18;
```

##### outer join(外联结)

example:
1. 需要选定主表, 结果中包含主表的所有数据。
2. 与inner的区别: 主表中有，但另外一张表中没有，outer会保留而inner不会
```
select t.age, s.age, s.student_id
from teacher as t left outer join  student s
on t.age = s.age
```

##### 三张以上表的联结

example:
inner join ... on ... inner join ... on
```
select t.age, t.teacher_id, th.height, tw.weight
from teacher as t inner join teacher_height th
    on t.teacher_id = th.teacher_id
inner join teacher_weight tw on t.teacher_id = tw.teacher_id;
```

##### cross join(交叉联结)

结果中的记录数是两张表中行数的乘积:

    因为 ShopProduct表存在 13 条记录， Product 表存在 8 条记录，所以结果中就包含了13 × 8 = 104 条记录。
  
## 第八章 SQL高级处理
mysql不支持
## 第九章 JAVA与SQL连接

