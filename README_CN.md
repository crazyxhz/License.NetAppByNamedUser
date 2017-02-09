#ArcGIS Runtime.NET SDK100.0.0 使用 Named User 进行OAuth授权

##Overview
关于OAuth的概念,建议阅读一下这篇[文章](http://www.bubblecode.net/en/2016/01/22/understanding-oauth2/) 

这个例子将一步步的解释ArcGIS Runtime.NET SDK100.0.0 进行 Named User OAuth授权的详细步骤.

##Steps
1. 注册ArcGIS Online两个月的[试用](http://www.esri.com/arcgis/trial). 点击打开链接,根据网站中的提示完成两个月试用的注册.
2. 登录ArcGIS Online的主页,点击我的内容:
![](https://ooo.0o0.ooo/2017/02/09/589c2651689ec.jpg)
3. 点击添加
![](https://ooo.0o0.ooo/2017/02/09/589c26a94c351.jpg)
4. Select Application type. Fill in title and tags as you need.
![](https://ooo.0o0.ooo/2017/02/09/589c26c1d9357.jpg)
5. After Application has been added. Click the item you just added. Click Settings tab.
![](https://ooo.0o0.ooo/2017/02/09/589c28a7e4fcc.jpg)
6. Scroll to the bottom. Click Registered Info to check you Oauth app Client Id stuff.
![](https://ooo.0o0.ooo/2017/02/09/589c276e46c4f.jpg)
7. Fill Registered Info into your code match the infos on the web:
![](https://ooo.0o0.ooo/2017/02/09/589c27dcb4478.jpg)
![](https://ooo.0o0.ooo/2017/02/09/589c27a70117f.jpg)
8. Build and run OAuth project. Done!
![](https://ooo.0o0.ooo/2017/02/09/589c28239f45b.jpg)


##System Requirements
- Visual Studio 2015

- ArcGIS Runtime.NET SDK100.0.0
