---
title: 织梦dedeCMS常用MySQL指令
createTime: 2025/07/23 16:21:09
permalink: /littletrick/shcm30u3/
---
```sql
update dede_addonarticle set body=replace(body,'原来的字符','替换后的字符')
#例子解释：#
update dede_addonarticle set body=replace(body,'软件下载','插件下载')
```

```sql
update `dede_arctype` set namerule='{typedir}/{aid}.html';
例子解释：把站内所有文章模型命名规则全部替换成{typedir}/{aid}.html这样一种形式
```

```sql
update dede_archives set arcrank=0
update dede_arctiny set arcrank=0
例子解释：①arcrank=0 仅动态；②两串代码分别执行
```

```sql
Delete from dede_keywords
例子解释：直接将文档关键词维护里的所有数据都清空。
```

```sql
delete from dede_addonarticle where aid>0;
delete from dede_arctiny where id>0;
delete from dede_archives where id>0;
```

```sql
delete from dede_addonarticle where aid >= 100 and aid< =5000;
delete from dede_arctiny where id >= 100 and id< =5000;
delete from dede_archives where id >= 100 and id<=5000;
这段sql命令就是把文章id从100到5000的全部删除掉
```

```sql
delete from dede_addonimages where typeid = 5;
delete from dede_arctiny where typeid = 5;
delete from dede_archives where typeid = 5;
```

```sql
delete from dede_arctype where id in (93,94,95,96,97)
注：这段sql命令就是把栏目id为93、94、95、96、97的栏目删除掉了
```

```sql
update dede_archives set typeid='70' where typeid in (93,94,95,96,97)
注：这段sql命令就是把栏目栏目id为93,94,95,96,97里面的文章归为栏目id为70的栏目下面
```

```sql
Update `dede_arctype` set reid='目标父栏目ID' where id in(2,3,4,5)
```

```sql
delete from dede_addonarticle;
delete from dede_addonimages;
delete from dede_archives;
delete from dede_arctiny;
delete from dede_co_htmls;
delete from dede_co_urls;
delete from dede_co_mediaurls;
delete from dede_tagindex ;
delete from dede_taglist;
delete from dede_keywords;
注：这段sql命令意思是清空文章和原来采集过的记录
```

```sql
alter table `dede_archives` auto_increment =141;
alter table `dede_arctiny` auto_increment =141;
alter table `dede_addonarticle` auto_increment =141;
```

```sql
alter table `dede_arctype` auto_increment =1;
注：表示新发布的文章或者栏目id从1开始，数字1也可以改为指定从任意id开始
```

```sql
alter table dede_archives modify column title varchar(200)
修改dedecms系统》系统基本参数》其他选项》文档标题最大长度为200，改此参数后需要手工修改数据表
注：以上sql语句的标点是中文标点，大家复制的时候切记要把标点切换为英文符号比如“”切换为""。
```



