#ArcGIS Runtime.NET SDK100.0.0 使用 Named User 进行OAuth授权

##Overview
关于OAuth的概念,建议阅读一下这篇[文章](http://www.bubblecode.net/en/2016/01/22/understanding-oauth2/) 

这个例子将一步步的解释ArcGIS Runtime.NET SDK100.0.0 进行 Named User OAuth授权的详细步骤.

##Steps
1. 注册ArcGIS Online两个月的[试用](http://www.esri.com/arcgis/trial). 点击打开链接,根据网站中的提示完成两个月试用的注册.
2. 登录ArcGIS Online的主页,点击我的内容:
![](https://ooo.0o0.ooo/2017/02/09/589c2651689ec.jpg)
3. 点击添加项目,点击添加程序
![](https://ooo.0o0.ooo/2017/02/09/589c26a94c351.jpg)
4. 选择程序类型,选择标题和标签
![](https://ooo.0o0.ooo/2017/02/09/589c26c1d9357.jpg)
5. 程序创建之后,点击刚刚创建的程序,点击设置标签页
![](https://ooo.0o0.ooo/2017/02/09/589c28a7e4fcc.jpg)
6. 将页面滚动到底部,点击Registered Info查看Oauth2信息
![](https://ooo.0o0.ooo/2017/02/09/589c276e46c4f.jpg)
7. 将对应的信息填入你的代码中
![](https://ooo.0o0.ooo/2017/02/09/589c27dcb4478.jpg)
![](https://ooo.0o0.ooo/2017/02/09/589c27a70117f.jpg)
8. 编译Oauth项目,完成!
![](https://ooo.0o0.ooo/2017/02/09/589c28239f45b.jpg)
9. 水印已经消除.
![](https://ooo.0o0.ooo/2017/02/09/589c30a5edf26.jpg)

##授权代码
```csharp
// Challenge the user for portal credentials (OAuth credential request for arcgis.com)
            CredentialRequestInfo loginInfo = new CredentialRequestInfo();

            // Use the OAuth implicit grant flow
            loginInfo.GenerateTokenOptions = new GenerateTokenOptions
            {
                TokenAuthenticationType = TokenAuthenticationType.OAuthImplicit
            };

            // Indicate the url (portal) to authenticate with (ArcGIS Online)
            loginInfo.ServiceUri = new Uri("https://www.arcgis.com/sharing/rest");


            // Call GetCredentialAsync on the AuthenticationManager to invoke the challenge handler
            Credential cred = await AuthenticationManager.Current.GetCredentialAsync(loginInfo, false);

            // Connect to the portal (ArcGIS Online) using the credential
            ArcGISPortal arcgisPortal = await ArcGISPortal.CreateAsync(loginInfo.ServiceUri, cred);

            // Get LicenseInfo from the portal
            Esri.ArcGISRuntime.LicenseInfo licenseInfo = arcgisPortal.PortalInfo.LicenseInfo;
            var licenseJson = licenseInfo.ToJson();
            using (StreamWriter outputFile = new StreamWriter(@"lincese.json"))
            {
                // you can save the license file for latter offline use.
                outputFile.WriteLine(licenseJson);
            }
            // ... code here to license the app immediately and/or save the license (JSON string) to take the app offline ...
            // License the app using the license info
            Esri.ArcGISRuntime.ArcGISRuntimeEnvironment.SetLicense(licenseInfo);
```

##系统需求
- Visual Studio 2015

- ArcGIS Runtime.NET SDK100.0.0