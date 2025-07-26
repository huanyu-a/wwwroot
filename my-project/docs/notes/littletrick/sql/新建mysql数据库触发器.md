---
title: 新建mysql数据库触发器
createTime: 2025/07/23 16:21:38
permalink: /littletrick/rtahckf1/
---
```sql
CREATE TRIGGER qw_article_insert
before INSERT
ON `数据_收录查询`
FOR EACH ROW
BEGIN
set NEW.md5 = md5(CONCAT(NEW.`落地页`));
END;
//


delimiter //
drop TRIGGER if EXISTS shoulu_update;
CREATE TRIGGER shoulu_update
before update
ON `数据_收录查询`
FOR EACH ROW
BEGIN
set NEW.shoulu_md5 = md5(CONCAT(NEW.`落地页`));
END
//
```

```sql
//创建插入触发器
CREATE TRIGGER [guest].[news_insert]
ON [guest].[数据_收录查询]
FOR INSERT
AS
BEGIN
UPDATE et
   SET et.shoulu_md5 = LOWER(CONVERT(NVARCHAR(32),hashbytes('MD5',CONCAT(i.落地页,i.body)),2))
   FROM [guest].[数据_收录查询] AS et
   JOIN inserted AS i
   ON et.id = i.id
   WHERE et.shoulu_md5 IS NULL;
END
//

//创建更新触发器
delimiter //
CREATE TRIGGER [guest].[news_update]
ON [guest].aizhan_zhuyu
FOR UPDATE
AS
BEGIN
UPDATE et
   SET et.md5 = LOWER(CONVERT(NVARCHAR(32),hashbytes('MD5',CONCAT(i.主域,i.更新日期)),2))
   FROM [guest].aizhan_zhuyu AS et
   JOIN inserted AS i
   ON et.id = i.id
   WHERE et.md5 IS NULL;
END
//
```

