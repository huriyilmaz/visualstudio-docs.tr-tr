---
title: Azure AD'ye bağlanarak MVC projesinde yapılan değişiklikler
description: Bağlı hizmetleri kullanarak Azure AD'ye bağlandıktan sonra MVC projenize Visual Studio açıklar
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: reference
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: devx-track-csharp, aaddev, vs-azure
ms.openlocfilehash: 441fe89c1d032cdc1a3de711dcf665a1110aaee7
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386748"
---
# <a name="what-happened-to-my-mvc-project-visual-studio-azure-active-directory-connected-service"></a>MVC projeme (bağlı Visual Studio Azure Active Directory) ne oldu?

> [!div class="op_single_selector"]
> - [Başlarken](vs-active-directory-dotnet-getting-started.md)
> - [Ne oldu](vs-active-directory-dotnet-what-happened.md)

Bu makalede, ASP.NET kullanarak Azure Active Directory MVC projesinde yapılan tam [değişiklikler Visual Studio.](vs-active-directory-add-connected-service.md)

Bağlı hizmetle çalışma hakkında daha fazla bilgi için [bkz. Başlarken.](vs-active-directory-dotnet-getting-started.md)

## <a name="added-references"></a>Başvurular eklendi

Proje dosyasını (*.NET başvuruları) ve `packages.config` (NuGet etkiler.

| Tür | Başvuru |
| --- | --- |
| .NET; NuGet | Microsoft.IdentityModel.Protocol.Extensions |
| .NET; NuGet | Microsoft.Owin |
| .NET; NuGet | Microsoft.Owin.Host.SystemWeb |
| .NET; NuGet | Microsoft.Owin.Security |
| .NET; NuGet | Microsoft.Owin.Security.Cookies |
| .NET; NuGet | Microsoft.Owin.Security.OpenIdConnect |
| .NET; NuGet | Owin |
| .NET        | System.IdentityModel |
| .NET; NuGet | System.IdentityModel.Tokens.Jwt |
| .NET        | System.Runtime.Serialization |

Dizin verilerini oku seçeneğini **seçtiyseniz ek** başvurular:

| Tür | Başvuru |
| --- | --- |
| .NET; NuGet | EntityFramework |
| .NET        | EntityFramework.SqlServer (yalnızca Visual Studio 2015) |
| .NET; NuGet | Microsoft.Azure.ActiveDirectory.GraphClient |
| .NET; NuGet | Microsoft.Data.Edm |
| .NET; NuGet | Microsoft.Data.OData |
| .NET; NuGet | Microsoft.Data.Services.Client |
| .NET; NuGet | Microsoft.IdentityModel.Clients.ActiveDirectory |
| .NET        | Microsoft.IdentityModel.Clients.ActiveDirectory.WindowsForms (yalnızca Visual Studio 2015) |
| .NET; NuGet | System.Spatial |

Aşağıdaki başvurular kaldırılmıştır (ASP.NET 2015'te olduğu gibi yalnızca 4 Visual Studio vardır):

| Tür | Başvuru |
| --- | --- |
| .NET; NuGet | Microsoft.AspNet.Identity.Core |
| .NET; NuGet | Microsoft.AspNet.Identity.EntityFramework |
| .NET; NuGet | Microsoft.AspNet.Identity.Owin |

## <a name="project-file-changes"></a>Project değişiklikleri

- özelliğini ayrı `IISExpressSSLPort` bir sayı olarak ayarlayın.
- Özelliği `WebProject_DirectoryAccessLevelKey` 0 olarak veya Dizin verilerini oku seçeneğini seçtiyseniz 1 **olarak** ayarlayın.
- özelliğini `IISUrl` değeriyle `https://localhost:<port>/` eşleşen yere `<port>` `IISExpressSSLPort` ayarlayın.

## <a name="webconfig-or-appconfig-changes"></a>web.config veya app.config değişiklikleri

- Aşağıdaki yapılandırma girdileri eklendi:

    ```xml
    <appSettings>
        <add key="ida:ClientId" value="<ClientId from the new Azure AD app>" />
        <add key="ida:AADInstance" value="https://login.microsoftonline.com/" />
        <add key="ida:Domain" value="<your selected Azure domain>" />
        <add key="ida:TenantId" value="<the Id of your selected Azure AD tenant>" />
        <add key="ida:PostLogoutRedirectUri" value="<project start page, such as https://localhost:44335>" />
    </appSettings>
    ```

- ve `<dependentAssembly>` için düğümü altına öğeler `<runtime><assemblyBinding>` `System.IdentityModel.Tokens.Jwt` `Microsoft.IdentityModel.Protocol.Extensions` eklendi.

Dizin verilerini oku seçeneğini **seçtiyseniz ek** değişiklikler:

- altına aşağıdaki yapılandırma girdisini `<appSettings>` ekledik:

    ```xml
    <add key="ida:ClientSecret" value="<Azure AD app's new client secret>" />
    ```

- altına aşağıdaki öğeler `<configuration>` eklendi; project-mdf-file ve project-catalog-id değerleri farklılık gösterir:

    ```xml
    <configSections>
      <!-- For more information on Entity Framework configuration, visit https://go.microsoft.com/fwlink/?LinkID=237468 -->
      <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
    </configSections>

    <connectionStrings>
      <add name="DefaultConnection" connectionString="Data Source=(localdb)\MSSQLLocalDB;AttachDbFilename=|DataDirectory|\<project-mdf-file>.mdf;Initial Catalog=<project-catalog-id>;Integrated Security=True" providerName="System.Data.SqlClient" />
    </connectionStrings>

    <entityFramework>
      <defaultConnectionFactory type="System.Data.Entity.Infrastructure.LocalDbConnectionFactory, EntityFramework">
        <parameters>
          <parameter value="mssqllocaldb" />
        </parameters>
      </defaultConnectionFactory>
      <providers>
        <provider invariantName="System.Data.SqlClient" type="System.Data.Entity.SqlServer.SqlProviderServices, EntityFramework.SqlServer" />
      </providers>
    </entityFramework>
    ```

- , `<dependentAssembly>` ve için düğüm altına öğeler `<runtime><assemblyBinding>` `Microsoft.Data.Services.Client` `Microsoft.Data.Edm` `Microsoft.Data.OData` eklendi.

## <a name="code-changes-and-additions"></a>Kod değişiklikleri ve eklemeler

- özniteliği ve `[Authorize]` diğer `Controllers/HomeController.cs` mevcut denetleyicilere eklendi.

- Azure AD kimlik doğrulaması için başlangıç `App_Start/Startup.Auth.cs` mantığını içeren bir kimlik doğrulama başlangıç sınıfı eklendi. Dizin verilerini oku **seçeneğini seçtiyseniz,** bu dosya bir OAuth kodu almak ve bunu erişim belirteci ile takas etmek için kod da içerir.

- ve yöntemlerini içeren bir `Controllers/AccountController.cs` denetleyici `SignIn` sınıfı `SignOut` eklendi.

- ve için bir eylem bağlantısı `Views/Shared/_LoginPartial.cshtml` içeren kısmi bir görünüm `SignIn` `SignOut` eklendi.

- Oturum açma kullanıcı arabirimi için `Views/Account/SignoutCallback.cshtml` HTML içeren kısmi bir görünüm eklendi.

- yöntemi, sınıfı zaten varsa çağrısı içerecek şekilde güncelleştirildi; aksi takdirde yöntemini `Startup.Configuration` `ConfigureAuth(app)` `Startup` çağıran bir sınıf eklendi.

- Bağlı Visual Studio izlemek için Visual Studio bilgileri `Connected Services/AzureAD/ConnectedService.json` `Service References/Azure AD/ConnectedService.json` içeren (2017 Visual Studio 2017) veya (Visual Studio 2015) eklendi.

- Dizin verilerini oku seçeneğini **belirttiyseniz,** `Models/ADALTokenCache.cs` belirteci `Models/ApplicationDbContext.cs` önbelleğe almayı desteklemek için ve eklendi. Ayrıca, Azure graph API'lerini kullanarak kullanıcı profili bilgilerine erişimi göstermek için ek bir denetleyici ve görünüm eklendi: `Controllers/UserProfileController.cs` , `Views/UserProfile/Index.cshtml` ve `Views/UserProfile/Relogin.cshtml`

### <a name="file-backup-visual-studio-2015"></a>Dosya yedekleme (Visual Studio 2015)

Bağlı hizmeti eklerken, Visual Studio ve kaldırılan dosyaları 2015'e geri ekler. Etkilenen tüm dosyalar klasörüne `Backup/AzureAD` kaydedilir. Visual Studio 2017 ve sonrası yedekleme oluşturmaz.

- `Startup.cs`
- `App_Start\IdentityConfig.cs`
- `App_Start\Startup.Auth.cs`
- `Controllers\AccountController.cs`
- `Controllers\ManageController.cs`
- `Models\IdentityModels.cs`
- `Models\ManageViewModels.cs`
- `Views\Shared\_LoginPartial.cshtml`

## <a name="changes-on-azure"></a>Azure'da değişiklikler

- Bağlı hizmeti eklerken seçtiğiniz etki alanında bir Azure AD Uygulaması oluşturdunız.
- Uygulama, bu seçenek belirtildiyse **Dizin verilerini okuma** iznini içerecek şekilde güncelleştirildi.

[hakkında daha fazla bilgi Azure Active Directory.](https://azure.microsoft.com/services/active-directory/)

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization)
- [Microsoft ile bir web uygulamasına ASP.NET ekleme](/azure/active-directory/develop/quickstart-v2-aspnet-webapp)