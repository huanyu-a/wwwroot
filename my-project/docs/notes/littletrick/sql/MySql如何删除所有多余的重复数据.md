---
title: MySql如何删除所有多余的重复数据
createTime: 2025/07/23 16:21:19
permalink: /littletrick/v7flc2qd/
---
- 需要处理的数据，如：

![](https://cdn.nlark.com/yuque/0/2023/png/683747/1677639923654-df5ccd37-3274-4227-a05c-cd75fc883b38.png)

- 出现重复的数据，如：  
    ![](https://cdn.nlark.com/yuque/0/2023/png/683747/1677639923723-2df1935f-a962-4bae-8702-a368151bc1b6.png)
- 先用SELECT查询看看结果：

```sql
-- 方法一
SELECT * FROM t_user WHERE user_name IN (
	SELECT user_name FROM t_user GROUP BY user_name HAVING COUNT(1)>1
) 
AND id NOT IN (
	SELECT MIN(id) FROM t_user GROUP BY user_name HAVING COUNT(1)>1
)
```

- 方法一查询出的所有多余的重复记录：  
    ![](https://cdn.nlark.com/yuque/0/2023/png/683747/1677639923690-eff8eab5-5d2d-4b0d-ac74-f1802d85ea9b.png)

```sql
-- 方法二
SELECT * FROM t_user WHERE id NOT IN (
	SELECT MIN(id) FROM t_user GROUP BY user_name
)
```

- 方法二查询出的所有多余的重复记录（与方法一的结果相同）：

![](https://cdn.nlark.com/yuque/0/2023/png/683747/1677639923669-d24064c7-2281-4376-a44b-6397621c3d3e.png)

```sql
-- 方法三
SELECT * FROM t_user AS t1 WHERE t1.id <> (
	SELECT MAX(t2.id) FROM t_user AS t2 WHERE t1.user_name=t2.user_name
)
```

- 方法三查询出的所有多余的重复记录：

![](https://cdn.nlark.com/yuque/0/2023/png/683747/1677639923709-2b7dbcf2-1825-476f-9e45-8ddf28590fee.png)  
这里方法三因为用了MAX()方法（也可改用MIN()），查询结果记录的id不太一样，但也可以被视为重复多余的数据，关键是你希望选择保留哪一条记录而已。

- 下面是对上面的SELECT语句稍作修改并加入了DELETE

```sql
-- 方法一（笨方法但容易理解）
DELETE FROM t_user WHERE user_name IN (
	SELECT t1.user_name FROM (
		-- 查询出所有重复的user_name
		SELECT user_name FROM t_user GROUP BY user_name HAVING COUNT(1)>1
	) t1
) 
AND id NOT IN (
	SELECT t2.min_id FROM (
		-- 查询出所有重复的记录并各自只取其中一条（MIN(id)或MAX(id)都可以）
		SELECT MIN(id) AS min_id FROM t_user GROUP BY user_name HAVING COUNT(1)>1
	) t2
)
```

```sql
-- 方法二（推荐方法也容易理解）
DELETE FROM t_user WHERE id NOT IN (
	SELECT t.min_id FROM (
		-- 过滤出重复多余的数据，比如，如果所有记录中存在1条记录是user_name=zhangsan的，那么就取出它；
    	-- 如果所有记录中存在多条记录是user_name=lisi的，那么只取其中1条，其他的不查询出来
		SELECT MIN(id) AS min_id FROM t_user GROUP BY user_name
  ) t
)
```

```sql
-- 方法三（推荐方法但不太容易理解）
DELETE FROM t_user WHERE id IN (
	SELECT t.id FROM (
		-- 1. 关于所有存在相同user_name的记录，只查询出（保留）重复记录中的1条，假设这样查询出来的集合为A集合。
		-- 2. 在所有记录中，只要id不在A集合中的，都把它们查询出来
		SELECT t1.id FROM t_user AS t1 WHERE t1.id <> (SELECT MAX(t2.id) FROM t_user AS t2 WHERE t1.user_name=t2.user_name)
	) t
)
-- 或
DELETE FROM t_user t1
WHERE t1.id <> (
	SELECT t2.max_id FROM (
		SELECT MAX(t3.id) AS max_id FROM t_user t3 WHERE t1.user_name=t3.user_name
	) t2
)
```

- 最后删除成功之后，显示数据已经没有重复的了