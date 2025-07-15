直接宝塔创建网站目录、绑定域名
将程序放到网站目录中
设置public目录为执行目录
进到public目录，将命名为.htaccess的文件右键打开使用text方式编辑，将文件内容改为这个代码 然后保存。
```bash
AddType application/x-httpd-php71 .php
<IfModule mod_rewrite.c>
  Options +FollowSymlinks -Multiviews
  RewriteEngine On
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
</IfModule>
```
可选项）默认用户名密码都是admin,改一下route/route.php目录文件，把后台路由地址随便改一下，如下我改成了aizrf，然后保存，进后台就用你修改的路径。
```bash
//后台
Route::rule('admin/:c/:a', 'admin/:c/:a');
Route::rule('aizrf', function(){
    return redirect('admin/index/index');
});
```



## 使用serv00 部署
教程：[serv00免费部署一个在线工具箱](https://blog.aizrf.com/p/tool)

## 1 docker

设置用户名密码

- username：用户名（默认值：admin）
- password：密码（默认值：admin）

后台管理地址：`http://192.168.3.34:8080/admin`

```bash
docker run -d --restart always \
	--name tools \
	-p 8080:80 \
	-e username=admin \
	-e password=admin \
	cleverest/toolbox
```



## 2 docker compose

创建 `docker-compose.yml` 文件。如果不指定 `username` `password` ，默认用户名密码均为：`admin` 

设置用户名密码

- username：用户名（默认值：admin）
- password：密码（默认值：admin）

后台管理地址：`http://192.168.3.34:8080/admin`


```yaml
version: '3'

services:
  tools:
    image: cleverest/toolbox
    container_name: tools
    restart: unless-stopped
    ports:
      - "8080:80"
    environment:
      - username=admin
      - password=admin
```

```bash
# 启动服务
docker-compose up -d
```

## 致谢
[iCloudBot](https://github.com/iCloudBot/toolbox)