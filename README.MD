#ArcGIS Runtime.NET SDK100.0.0 OAuth step by step demo using Named User

##Overview
For OAuth 2 authentication explaination, please check [this](http://www.bubblecode.net/en/2016/01/22/understanding-oauth2/) great article.

This demo will show you step by step setup of OAuth authentication using ArcGIS Online Named User.

##Steps
1. Register a ArcGIS two month [trial](http://www.esri.com/arcgis/trial). Open the link above. Fill in the forms and following the steps in the web site to complete your ArcGIS trial.
2. Login in to your ArcGIS Online Home Page, click My content:
![](https://ooo.0o0.ooo/2017/02/09/589c2651689ec.jpg)
3. Click Add item, then Click an application
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
9. The Water Mark is gone.
![](https://ooo.0o0.ooo/2017/02/09/589c30a5edf26.jpg)

##Licensing code
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

##System Requirements
- Visual Studio 2015

- ArcGIS Runtime.NET SDK100.0.0
