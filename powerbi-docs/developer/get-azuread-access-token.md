---
title: 对用户进行身份验证并获取应用的 Azure AD 访问令牌
description: 了解如何在 Azure Active Directory 中注册应用程序，用于嵌入 Power BI 内容。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 7b2249964f2fff26bc68fea19fd0010d8990110b
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762527"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>获取 Power BI 应用程序的 Azure AD 访问令牌

了解如何在 Power BI 应用中对用户进行身份验证，并检索要用于 REST API 的访问令牌。

必须先获取 Azure Active Directory (Azure AD) 身份验证访问令牌（简称“访问令牌”），才能调用 Power BI REST API。 使用访问令牌允许应用访问 Power BI 仪表板、磁贴和报表。 若要了解有关 Azure Active Directory **访问令牌**流的详细信息，请参阅 [Azure AD 授权代码授予流](https://msdn.microsoft.com/library/azure/dn645542.aspx)。

访问令牌的检索方式不同，具体视内容的嵌入方式而定。 本文使用了两种不同方法。

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Power BI 用户（用户拥有数据）的访问令牌

此示例适用于用户使用组织登录名手动登录 Azure AD 的情况。 在嵌入 Power BI 用户（这些用户访问可以使用 Power BI 服务的内容）的内容时，使用此任务。

### <a name="get-an-authorization-code-from-azure-ad"></a>从 Azure AD 获取授权代码

获取**访问令牌**的第一步是从 **Azure AD** 获取授权代码。 构造具有以下属性的查询字符串，并重定向到 Azure AD。

#### <a name="authorization-code-query-string"></a>授权代码查询字符串

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

构造查询字符串后，重定向到 **Azure AD** 以获取**授权代码**。  下面是构造**授权代码**查询字符串的并重定向到 **Azure AD** 的完整 C# 方法。 获取授权代码后，将使用**授权代码**获取**访问令牌**。

在 redirect.aspx.cs 中，调用 [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) 生成令牌。

#### <a name="get-authorization-code"></a>获取授权代码

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.net/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>通过授权代码获取访问令牌

现在应该已有从 Azure AD 获取的授权代码。 **Azure AD** 使用**授权代码**重定向回 Web 应用后，请使用**授权代码**获取访问令牌。 下面的 C# 示例可用于重定向页和 default.aspx 页的 Page_Load 事件。

可以从 [Active Directory 身份验证库](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 包检索 Microsoft.IdentityModel.Clients.ActiveDirectory 命名空间。

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>非 Power BI 用户（应用拥有数据）的访问令牌

这种方法通常用于 ISV 类型的应用，即应用拥有数据访问权限。 用户不一定是 Power BI 用户，且应用程序控制最终用户的身份验证和访问权限。

### <a name="access-token-with-a-master-account"></a>主帐户的访问令牌

若要使用这种方法，请使用一个是 Power BI Pro 用户的主帐户。 此帐户的凭据存储在应用名下。 应用程序使用这些存储的凭据进行 Azure AD 身份验证。 下面显示的示例代码来自[“应用拥有数据”示例](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>服务主体的访问令牌

若要使用这种方法，请使用一个是仅限应用的令牌的[服务主体](embed-service-principal.md)。 应用程序使用服务主体进行 Azure AD 身份验证。 下面显示的示例代码来自[“应用拥有数据”示例](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="next-steps"></a>后续步骤

至此，已拥有访问令牌，可以调用 Power BI REST API 嵌入内容了。 有关如何嵌入内容的信息，请参阅[如何嵌入 Power BI 内容](embed-sample-for-customers.md#embed-content-within-your-application)。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)