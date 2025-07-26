---
title: 常用sql指令大全
createTime: 2025/07/23 16:37:04
permalink: /littletrick/p6dbooat/
---
批量修改内容，路径和超链接等信息。
```text
update (表名) 
set (要修改的 字段名+修改后的 赋值) 
where (筛选条件)
update：是一个数据库sql语法用语，用途是更新表中原有数据
where：筛选条件，指你要修改哪些数据内容，用条件语句筛选提取指定内容
```


## 查询
### 双条件查询
```sql
SELECT * FROM `shuju`.`zixun` WHERE `PageUrl` LIKE '%.39.net%' AND `ctime` LIKE '2023-12-%'
```

### ID区间查询
```sql
SELECT *  FROM wenda where Id > 0 and  id <= 400000;
```

### 单条件查询
```sql

SELECT * FROM `shuju`.`zixun` WHERE `ctime` LIKE '%2023-10%'
查找所有包含字母“s”的名字
SELECT * FROM `shuju`.`zixun` WHERE REGEXP_LIKE(ctime,'2023-10');

SELECT * FROM `zixun` WHERE title REGEXP '尖锐湿疣' OR keyword REGEXP '漫画|嘿嘿|直播';

SELECT * FROM `zixun` WHERE title REGEXP '夏季.*养生|冬季.*养生|春季.*养生';

```

### 最新1000条数据查询
```sql
SELECT * FROM wenda ORDER BY id DESC LIMIT 200000;
```



### 关键词批量查询并返回查询词
```sql
SELECT *,   regexp_substr(`title` ,'避孕|人流|同房|艾滋病|青春期|前列腺炎|阴道炎') as tagkey FROM `zixun` where title REGEXP '避孕|人流|同房|艾滋病|青春期|前列腺炎|阴道炎'
```

### 关键词组合查询
```sql
%可作为通用匹配
SELECT * FROM `zixun` where title like '%尖锐湿疣%' or keyword like '%漫画%' or keyword like '%嘿嘿%'  or keyword like '%直播%'
下列为组合查询
SELECT * FROM `zixun` where title like '%夏季%养生%'
union  SELECT * FROM `zixun` where title like '%冬季%养生%'
union  SELECT * FROM `zixun` where title like '%春季%养生%'
下列为，批量查询后并标注所匹配到的关键词
SELECT *,   regexp_substr(`title` ,'白癜风|养生') as tagkey FROM `zixun` where title REGEXP '白癜风|养生'

```

### 查询去重后的数据
```sql
SELECT * FROM `wenda` group by title,answer;
```

### mysql 查询某字段里不含某字符的所有记录
```sql
SELECT *FROM zixun WHERE !find_in_set('无', keyword);
```

### mysql 查询某字段里含有某字符的所有记录
```sql
SELECT *FROM zixun WHERE find_in_set('无', keyword);
```

### 双条件查询
```sql
SELECT * FROM `shuju`.`zixun` WHERE `PageUrl` LIKE '%.39.net%' AND `ctime` LIKE '2023-12-%'
```



## 删除
### 删除数据
```sql
先试用select查询语句，然后再将select * 修改为delete
DELETE FROM `zixun` WHERE `body` LIKE '%吸毒%'

批量删除
DELETE FROM zixun WHERE id IN ({})
```



### 删除重复数据
```sql
方法一：
DELETE w
FROM wenda w
INNER JOIN (
  SELECT MIN(id) AS min_id, ask_md5
  FROM wenda
  GROUP BY ask_md5
  HAVING COUNT(*) > 1
) t ON w.ask_md5 = t.ask_md5
WHERE w.id > t.min_id;

方法二：
DELETE zixun
FROM
 zixun, 
 (
  SELECT
   min(id) id,
   body_md5
  FROM
   zixun
  GROUP BY
   body_md5
  HAVING
   count(*) > 1
 ) t2
WHERE
 zixun.body_md5 = t2.body_md5
AND zixun.id > t2.id;

方法三：
START TRANSACTION; -- 开始事务

-- 创建临时表
CREATE TEMPORARY TABLE TempTable AS
SELECT MIN(id) AS min_id, ask_md5
FROM yiyaoask
GROUP BY ask_md5
HAVING COUNT(*) > 1;

-- 删除重复记录
DELETE y
FROM yiyaoask y
INNER JOIN TempTable t ON y.ask_md5 = t.ask_md5
WHERE y.id > t.min_id;

-- 删除临时表
DROP TEMPORARY TABLE IF EXISTS TempTable;

COMMIT; -- 提交事务
```



## 替换
### 关键词单词替换
```sql
update dede_addonarticle set body=replace(body,'原来的字符','替换后的字符')
```

## 插入
### <font style="color:rgb(77, 77, 77);">批量插入且对已存在数据忽略</font>
```sql
insert ignore into table_name (field1, field2...) values (value1, value2...),(value1, value2...);
```



