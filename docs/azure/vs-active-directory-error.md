---
title: Azure AD bağlı hizmeti ile hataları tanılama (Visual Studio)
description: Active Directory bağlı hizmeti uyumsuz bir kimlik doğrulama türü algıladı
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: reference
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: aaddev, vs-azure
ms.openlocfilehash: 4441e8b0191092a3501dc095beff62d4efdc30c4
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805083"
---
# <a name="diagnosing-errors-with-the-azure-active-directory-connected-service"></a>Azure Active Directory bağlı hizmeti ile hataları tanılama

Azure Active Directory bağlı hizmet, önceki kimlik doğrulama kodunu algılarken uyumsuz bir kimlik doğrulama türü algıladı.

Bir projede önceki kimlik doğrulama kodunu doğru bir şekilde algılamak için projenin yeniden oluşturulması gerekir. Bu hatayı görürseniz ve projenizde önceki bir kimlik doğrulama kodunuz yoksa, yeniden derleyin ve tekrar deneyin.

## <a name="project-types"></a>Project türleri

Bağlı hizmet, projenin doğru kimlik doğrulama mantığını ekleyebilmesi için, geliştirmekte olduğunuz projenin türünü denetler. Projede türetilen herhangi bir denetleyici varsa `ApiController` , proje bir WebAPI projesi olarak kabul edilir. Yalnızca projede türetilen denetleyiciler varsa `MVC.Controller` , proje BIR MVC projesi olarak kabul edilir. Bağlı hizmet diğer proje türlerini desteklemiyor.

## <a name="compatible-authentication-code"></a>Uyumlu kimlik doğrulama kodu

Bağlı hizmet, daha önce yapılandırılmış veya hizmetle uyumlu olan kimlik doğrulama ayarlarını da denetler. Tüm ayarlar varsa, bu bir re-entrant durumu olarak kabul edilir ve bağlı hizmet, ayarları görüntüle ' yi açar.  Ayarlardan yalnızca bazıları varsa, bu durum bir hata durumu olarak kabul edilir.

Bir MVC projesinde, bağlı hizmet aşağıdaki ayarlardan herhangi birini denetler ve bu da hizmetin önceki kullanımıyla sonuçlanır:

```xml
<add key="ida:ClientId" value="" />
<add key="ida:Tenant" value="" />
<add key="ida:AADInstance" value="" />
<add key="ida:PostLogoutRedirectUri" value="" />
```

Ayrıca, bağlı hizmet, bir Web API projesinde aşağıdaki ayarlardan herhangi birini denetler ve bu da hizmetin önceki kullanımı ile sonuçlanır:

```xml
<add key="ida:ClientId" value="" />
<add key="ida:Tenant" value="" />
<add key="ida:Audience" value="" />
```

## <a name="incompatible-authentication-code"></a>Uyumsuz kimlik doğrulama kodu

Son olarak, bağlı hizmet, Visual Studio önceki sürümleriyle yapılandırılmış kimlik doğrulama kodu sürümlerini algılamaya çalışır. Bu hatayı aldıysanız, projenizin uyumsuz bir kimlik doğrulama türü içerdiği anlamına gelir. Bağlı hizmet, Visual Studio önceki sürümlerinden aşağıdaki kimlik doğrulama türlerini algılar:

* Windows Kimlik Doğrulaması
* Bireysel kullanıcı hesapları
* Kuruluş hesapları

MVC projesinde Windows kimlik doğrulamasını algılamak için, bağlantılı `authentication` öğeyi `web.config` dosyanızda arar.

```xml
<configuration>
    <system.web>
        <authentication mode="Windows" />
    </system.web>
</configuration>
```

bir Web apı projesinde Windows kimlik doğrulamasını algılamak için, bağlı hizmet `IISExpressWindowsAuthentication` projenizin dosyasındaki öğesini arar `.csproj` :

```xml
<Project>
    <PropertyGroup>
        <IISExpressWindowsAuthentication>enabled</IISExpressWindowsAuthentication>
    </PropertyGroup>
</Project>
```

Bireysel kullanıcı hesapları kimlik doğrulamasını algılamak için, bağlı hizmet dosyanızdaki paket öğesini arar `packages.config` .

```xml
<packages>
    <package id="Microsoft.AspNet.Identity.EntityFramework" version="2.1.0" targetFramework="net45" />
</packages>
```

Eski bir kurumsal hesap kimlik doğrulaması biçimini algılamak için bağlı hizmet içinde aşağıdaki öğeyi arar `web.config` :

```xml
<configuration>
    <appSettings>
        <add key="ida:Realm" value="***" />
    </appSettings>
</configuration>
```

Kimlik doğrulama türünü değiştirmek için, uyumsuz kimlik doğrulama türünü kaldırın ve bağlı hizmeti yeniden eklemeyi deneyin.

Daha fazla bilgi için bkz. [Azure AD Için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization).
