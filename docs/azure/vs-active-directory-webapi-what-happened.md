---
title: Azure AD 'ye bağlanılırken, WebAPI projelerinde yapılan değişiklikler
description: Visual Studio kullanarak Azure AD 'ye bağlandığınızda, WebAPI projenizde ne olacağını açıklar
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.topic: reference
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: devx-track-csharp, aaddev, vs-azure
ms.openlocfilehash: fb7fb04fe80beac50841e1976971c162e8523149
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386747"
---
# <a name="what-happened-to-my-webapi-project-visual-studio-azure-active-directory-connected-service"></a>WebAPI projem 'e ne oldu (Visual Studio Azure Active Directory bağlı hizmeti)

> [!div class="op_single_selector"]
> - [Başlarken](vs-active-directory-webapi-getting-started.md)
> - [Ne oldu](vs-active-directory-webapi-what-happened.md)

bu makalede, [Azure Active Directory kullanarak Visual Studio bağlı hizmeti](vs-active-directory-add-connected-service.md)eklerken ASP.NET WebAPI, ASP.NET Single-Page uygulaması ve ASP.NET Azure apı projelerine yapılan tam değişiklikler tanımlanmaktadır. ayrıca, Visual Studio 2015 ' de Azure mobil hizmet projeleri ASP.NET için de geçerlidir.

Bağlı hizmetle çalışma hakkında daha fazla bilgi için [bkz. Başlarken](vs-active-directory-webapi-getting-started.md).

## <a name="added-references"></a>Eklenen başvurular

proje dosyasını *. NET başvuruları) ve `packages.config` (başvuruları NuGet) etkiler.

| Tür | Başvuru |
| --- | --- |
| NET NuGet | Microsoft. Owin |
| NET NuGet | Microsoft.Owin.Host.SystemWeb |
| NET NuGet | Microsoft. Owin. Security |
| NET NuGet | Microsoft. Owin. Security. ActiveDirectory |
| NET NuGet | Microsoft. Owin. Security. JWT |
| NET NuGet | Microsoft. Owin. Security. OAuth |
| NET NuGet | Owın |
| NET NuGet | System. IdentityModel. Tokens. JWT |

**Dizin verilerini oku** seçeneğini belirlediyseniz ek başvurular:

| Tür | Başvuru |
| --- | --- |
| NET NuGet | EntityFramework |
| .NET        | entityframework. SqlServer (yalnızca Visual Studio 2015) |
| NET NuGet | Microsoft. Azure. ActiveDirectory. GraphClient |
| NET NuGet | Microsoft. Data. Edm |
| NET NuGet | Microsoft. Data. OData |
| NET NuGet | Microsoft. Data. Services. Client |
| NET NuGet | Microsoft.IdentityModel.Clients.ActiveDirectory |
| .NET        | Microsoft. IdentityModel. clients. ActiveDirectory. WindowsForms<br>(yalnızca Visual Studio 2015) |
| NET NuGet | System. uzamsal |

aşağıdaki başvurular kaldırılır (yalnızca ASP.NET 4 proje, Visual Studio 2015):

| Tür | Başvuru |
| --- | --- |
| NET NuGet | Microsoft. AspNet. Identity. Core |
| NET NuGet | Microsoft. AspNet. Identity. EntityFramework |
| NET NuGet | Microsoft. AspNet. Identity. Owin |

## <a name="project-file-changes"></a>Project dosya değişiklikleri

- Özelliği `IISExpressSSLPort` ayrı bir sayı olarak ayarlayın.
- Özelliği 0 olarak ayarlayın `WebProject_DirectoryAccessLevelKey` veya **Dizin verilerini oku** seçeneğini belirlediyseniz 1 yapın.
- Özelliğini `IISUrl` `https://localhost:<port>/` değeri eşleşen olarak ayarlayın `<port>` `IISExpressSSLPort` .

## <a name="webconfig-or-appconfig-changes"></a>web.config veya app.config değişiklikleri

- Aşağıdaki yapılandırma girdileri eklendi:

    ```xml
    <appSettings>
        <add key="ida:ClientId" value="<ClientId from the new Azure AD app>" />
        <add key="ida:Tenant" value="<your selected Azure domain>" />
        <add key="ida:Audience" value="<your selected domain + / + project name>" />
    </appSettings>
    ```

- yalnızca 2017 Visual Studio: ayrıca, aşağıdaki giriş `<appSettings>` "

    ```xml
    <add key="ida:MetadataAddress" value="<domain URL + /federationmetadata/2007-06/federationmetadata.xml>" />
    ```

- `<dependentAssembly>`İçin düğümünün altına öğe eklendi `<runtime><assemblyBinding>` `System.IdentityModel.Tokens.Jwt` .

- **Dizin verilerini oku** seçeneğini belirlediyseniz aşağıdaki yapılandırma girişi altına eklendi `<appSettings>` :

    ```xml
    <add key="ida:Password" value="<Your Azure AD app's new password>" />
    ```

## <a name="code-changes-and-additions"></a>Kod değişiklikleri ve eklemeler

- `[Authorize]`Özniteliği `Controllers/ValueController.cs` ve diğer mevcut denetleyicilere eklendi.

- `App_Start/Startup.Auth.cs`Azure AD kimlik doğrulaması için başlangıç mantığını içeren veya uygun şekilde değiştirilen bir kimlik doğrulama başlangıç sınıfı eklendi. **Dizin verilerini oku** seçeneğini belirlediyseniz, bu dosya Ayrıca bir OAuth kodu alacak kodu içerir ve bir erişim belirteci için onu değiş tokuş sağlar.

- (yalnızca ASP.NET 4 uygulamayla birlikte Visual Studio 2015) kaldırıldı `App_Start/IdentityConfig.cs` ve eklendi `Controllers/AccountController.cs` , `Models/IdentityModel.cs` ve `Providers/ApplicationAuthProvider.cs` .

- `Connected Services/AzureAD/ConnectedService.json` `Service References/Azure AD/ConnectedService.json` bağlı hizmetin eklenmesini izlemek için Visual Studio tarafından kullanılan bilgileri içeren (Visual Studio 2017) veya (Visual Studio 2015) eklendi.

### <a name="file-backup-visual-studio-2015"></a>dosya yedekleme (Visual Studio 2015)

bağlı hizmet eklenirken Visual Studio 2015, değiştirilen ve kaldırılan dosyaları yedekler. Etkilenen tüm dosyalar klasörüne kaydedilir `Backup/AzureAD` . Visual Studio 2017, yedeklemeler oluşturmaz.

- `Startup.cs`
- `App_Start\IdentityConfig.cs`
- `App_Start\Startup.Auth.cs`
- `Controllers\AccountController.cs`
- `Controllers\ManageController.cs`
- `Models\IdentityModels.cs`
- `Models\ApplicationOAuthProvider.cs`

## <a name="changes-on-azure"></a>Azure 'daki değişiklikler

- Bağlı hizmeti eklerken seçtiğiniz etki alanında bir Azure AD uygulaması oluşturuldu.
- Uygulama, bu seçenek seçildiyse, **Dizin verilerini oku** iznini içerecek şekilde güncelleştirildi.

[Azure Active Directory hakkında daha fazla bilgi edinin](https://azure.microsoft.com/services/active-directory/).

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization)
- [Microsoft 'a ASP.NET web uygulamasına oturum açma ekleme](/azure/active-directory/develop/quickstart-v2-aspnet-webapp)