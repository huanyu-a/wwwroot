---
title: 百度统计数据api导出流程
createTime: 2025/07/23 17:10:29
permalink: /littletrick/yeuf89xt/
---
调用百度账号的 API 接口，用户需要通过百度开发者中心的身份验证，具体步骤如下：

1. 进入百度统计-管理-[数据导出服务](https://tongji.baidu.com/sc-web/home/dataapi)
2. 开通数据导出服务，获得API Key与Secret Key
3. 通过如下URL进入百度账号登录页，此处的登录账号就是您登录百度统计查看报告数据的账号，登录完成后将跳转至获取code的页面： http://openapi.baidu.com/oauth/2.0/authorize?response_type=code&client_id=g3Qtqhxdprzd7w8u3rRkFnEYcOvIG5n0&redirect_uri=oob&scope=basic&display=popup 其中：

- {CLIENT_ID}填写您的API Key

1. 通过身份验证获取ACCESS_TOKEN用户同意授权后，将跳转至一个获取CODE的页面。复制CODE值后可将其加入以下URL换取ACCESS_TOKEN ：http://openapi.baidu.com/oauth/2.0/token?grant_type=authorization_code&code=234af6b485db13e7ae5b211061c87a95&client_id=g3Qtqhxdprzd7w8u3rRkFnEYcOvIG5n0&client_secret=lMQvIfLlIyqteUyB1a2a0mjMMSaEl0Dr&redirect_uri=oob 其中：返回如下：
```json
{"expires_in":2592000,"refresh_token":"122.bacbdea6922f8ccee086a018e016f15f.Ynvh-60A8k1wZ1t4GmUAhBrvp_Ntu16pB6H1XCO.it02yA","access_token":"121.6228e3dfb68b6fc56e466885e7c1ef62.YHzrI_BszP3s4do0fj6glBv4hMk90XgF5YWnc8-.AMRYDQ","session_secret":"","session_key":"","scope":"basic"}
``` 

3. **您可以使用****ACCESS_TOKEN****进行接下来的API请求。**

- {CLIENT_ID}填写您的API Key
- {CLIENT_SECRET}填写您的Secret Key
- {CODE}填写您刚才拿到的CODE

6. 调用百度统计API

获取的ACCESS_TOKEN是所调用API的用户级参数，结合各API的应用级参数即可正常调用API获取数据，例子如下所示：https://openapi.baidu.com/rest/2.0/tongji/config/getSiteList?access_token=1.a6b7dbd428f731035f771b8d15063f61.86400.1292922000-2346678-124328
```json
{"expires_in":2592000,"refresh_token":"122.5a5baa3e978a73e2bef982c200371667.Y_mHEXJyFhHWaM3T0gEyYQslfdgdcrW7R3-nGdn.auCIMw","access_token":"121.0fec0b142e2c6d7913c2f8328a6675a6.Y7NGmhGAFmdjxvraQnAvB6w5-zURQ6ysvAp49vT.xcjx2A","session_secret":"","session_key":"","scope":"basic"}
```

7. 更新 ACCESS_TOKEN

从上述步骤得到的数据中包含ACCESS_TOKEN和REFRESH_TOKEN两个值，其中ACCESS_TOKEN的有效期为一个月，REFRESH_TOKEN的有效期为十年。REFRESH_TOKEN的作用就是刷新获取新的ACCESS_TOKEN和REFRESH_TOKEN，如此反复操作来实现ACCESS_TOKEN有效期永久的机制。一旦ACCESS_TOKEN过期，可根据以下请求更换新的ACCESS_TOKEN和REFRESH_TOKEN：

```text
http://openapi.baidu.com/oauth/2.0/token?grant_type=refresh_token&refresh_token=122.ec0edd7383a4ec87ba752c49bd5c61c3.Ym6CSW4zSrVYG8SODtpl9CHOuF9_vBrhTBQ3U55.hAq-KQ&client_id=SHs0C6zTH3mZsT4w8HWCrbjVX1rjLsim&client_secret=jMA848kHy1PawHVMMfjhr9yYepl3NMv5
```

返回如下：

```json
{"expires_in":2592000,"refresh_token":"122.ec0edd7383a4ec87ba752c49bd5c61c3.Ym6CSW4zSrVYG8SODtpl9CHOuF9_vBrhTBQ3U55.hAq-KQ","access_token":"121.61baa99604eef39b11e75a401cb5c29b.Y7otWhE-XZTUkjUBL4EVqJU0gBKDheRFRCFkh8p.lyFd5A","session_secret":"","session_key":"","scope":"basic"}
```

受访页json
```text
https://openapi.baidu.com/rest/2.0/tongji/report/getData?access_token=121.204c827460a2d539d7727fd2ea1138da.YQJLfxNSa9rr7r5LhidmxbpZusLtVsfTtSav1h5.tf0KbQ&site_id=6508238&start_date=20230119&end_date=20230119&metrics=visitor_count&method=visit/landingpage/a&order=e.g%3Avisitor_count,desc&max_results=90000

https://openapi.baidu.com/rest/2.0/tongji/report/getData?access_token=[百度统计api生成的token]&site_id=[百度统计中的网站id]&start_date=[统计开始时间]&end_date=[统计结束时间=统计开始时间]&metrics=pv_count,visitor_count&method=visit/toppage/a&order=e.g%3Avisitor_count,desc&max_results=90000
```
参考资料：

- [Tongji API用户手册](https://tongji.baidu.com/api/manual/)
- [Tongji API调试工具](https://tongji.baidu.com/api/debug/)
- [实时访客API](https://openapi.baidu.com/rest/2.0/tongji/report/getData?access_token=121.a2678177d54510eab13579686b27d067.Y_AwUMQNWg8dmsrgSwE8iq9mx4pDeJ4odAvxJcp.WnxGdw&site_id=6508238&metrics=area%2Caccess_page%2CvisitorId%2Cip%2Cvisit_time%2Cvisit_pages%2Cstart_time&method=trend%2Flatest%2Fa&max_results=10&source=through&area=)