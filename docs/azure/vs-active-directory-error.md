---
title: Azure AD bağlı hizmetiyle ilgili hataları tanılama (Visual Studio)
description: Active Directory bağlı hizmeti uyumsuz bir kimlik doğrulaması türü algıladı
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: reference
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: aaddev, vs-azure
ms.openlocfilehash: 525e774728b4740d8503d539a5afdaf9cffdf727
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386749"
---
# <a name="diagnosing-errors-with-the-azure-active-directory-connected-service"></a>Azure Active Directory Bağlı Hizmet ile hataları tanılama

Önceki kimlik doğrulama kodu algılandığında, Azure Active Directory bağlı hizmet uyumsuz bir kimlik doğrulama türü algıladı.

Projede önceki kimlik doğrulama kodunu doğru algılamak için projenin yeniden oluşturulmuş olması gerekir. Bu hatayı görüyorsanız ve projenize daha önce kimlik doğrulama kodunuz yoksa yeniden oluştur ve yeniden deneyin.

## <a name="project-types"></a>Project türleri

Bağlı hizmet, projeye doğru kimlik doğrulama mantığını eklemesi için geliştirmekte olduğunu projenin türünü denetler. Projeden türeten herhangi bir denetleyici `ApiController` varsa, proje bir WebAPI projesi olarak kabul edilir. Yalnızca projeden türeten `MVC.Controller` denetleyiciler varsa, proje bir MVC projesi olarak kabul edilir. Bağlı hizmet başka bir proje türünü desteklemez.

## <a name="compatible-authentication-code"></a>Uyumlu kimlik doğrulama kodu

Bağlı hizmet ayrıca daha önce yapılandırılmış veya hizmetle uyumlu olan kimlik doğrulama ayarlarını da denetler. Tüm ayarlar mevcutsa, yeniden kabul edilir ve bağlı hizmet açılırken ayarlar görüntülenir.  Yalnızca bazı ayarlar varsa, bu bir hata durumu olarak kabul edilir.

Bir MVC projesinde, bağlı hizmet aşağıdaki ayarlardan herhangi birini denetler ve bu da hizmetin önceki kullanımından kaynaklandır:

```xml
<add key="ida:ClientId" value="" />
<add key="ida:Tenant" value="" />
<add key="ida:AADInstance" value="" />
<add key="ida:PostLogoutRedirectUri" value="" />
```

Ayrıca bağlı hizmet, Web API projesinde aşağıdaki ayarlardan herhangi birini denetler ve bu da hizmetin önceki kullanımından kaynaklandır:

```xml
<add key="ida:ClientId" value="" />
<add key="ida:Tenant" value="" />
<add key="ida:Audience" value="" />
```

## <a name="incompatible-authentication-code"></a>Uyumsuz kimlik doğrulama kodu

Son olarak, bağlı hizmet, kimlik doğrulama kodunun önceki sürümleriyle yapılandırılmış olan sürümlerini algılamaya Visual Studio. Bu hatayı aldıysanız projenizin uyumsuz bir kimlik doğrulama türü içerdiği anlamına gelir. Bağlı hizmet, önceki sürümlerden gelen aşağıdaki kimlik doğrulama türlerini Visual Studio:

* Windows Kimlik Doğrulaması
* Bireysel Kullanıcı Hesapları
* Kuruluş Hesapları

Bir MVC Windows kimlik doğrulamasını algılamak için bağlı öğesi `authentication` dosyanıza `web.config` bakarak.

```xml
<configuration>
    <system.web>
        <authentication mode="Windows" />
    </system.web>
</configuration>
```

Web API Windows kimlik doğrulamasını algılamak için bağlı hizmet `IISExpressWindowsAuthentication` projenizin dosyasındaki öğesini `.csproj` aramaz:

```xml
<Project>
    <PropertyGroup>
        <IISExpressWindowsAuthentication>enabled</IISExpressWindowsAuthentication>
    </PropertyGroup>
</Project>
```

Bireysel Kullanıcı Hesapları kimlik doğrulamasını algılamak için bağlı hizmet dosyanız içinde paket öğesini `packages.config` okur.

```xml
<packages>
    <package id="Microsoft.AspNet.Identity.EntityFramework" version="2.1.0" targetFramework="net45" />
</packages>
```

Kuruluş Hesabı kimlik doğrulamasının eski bir formunu algılamak için bağlı hizmet içinde aşağıdaki öğeyi `web.config` aramaz:

```xml
<configuration>
    <appSettings>
        <add key="ida:Realm" value="***" />
    </appSettings>
</configuration>
```

Kimlik doğrulama türünü değiştirmek için uyumsuz kimlik doğrulama türünü kaldırın ve bağlı hizmeti yeniden eklemeyi deneyin.

Daha fazla bilgi için [bkz. Azure AD için Kimlik Doğrulama Senaryoları.](/azure/active-directory/develop/authentication-vs-authorization.md)