---
title: PowerShell betiği kullanarak bir Web uygulaması yayımlama
description: Bir Web projesini Azure Web sitesinde yayımlamayı öğrenin. Bu betik, mevcut değilse, Azure aboneliğinizde gerekli kaynakları oluşturur.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 0a6657f8a6da751614d7d7da3f526aeebd817d5c
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902174"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell betiği)
## <a name="syntax"></a>Syntax
Bir Web projesini bir Azure Web sitesinde yayımlar. Komut dosyası, mevcut değilse, Azure aboneliğinizde gerekli kaynakları oluşturur.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Yapılandırma
Dağıtımın ayrıntılarını açıklayan JSON yapılandırma dosyasının yolu.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |true |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="subscriptionname"></a>SubscriptionName
Web sitesini oluşturmak istediğiniz Azure aboneliğinin adı.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="webdeploypackage"></a>WebDeployPackage
Web sitesinde yayımlanacak Web dağıtım paketinin yolu. Bu paketi Visual Studio 'daki Web 'i Yayımla Sihirbazı 'nı kullanarak oluşturabilirsiniz. Daha fazla bilgi için bkz. [Azure Cloud Services ve ASP.NET ile çalışmaya başlama](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure 'da SQL veritabanı için Kullanıcı adı ve parola.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="sendhostmessagestooutput"></a>Sendhostiletitooutput
Doğru ise, komut dosyasından çıkış akışına iletileri yazdırın.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="remarks"></a>Açıklamalar
Geliştirme ve test ortamları oluşturmak için betiğin nasıl kullanılacağına ilişkin ayrıntılı bir açıklama için, bkz. [geliştirme ve test ortamlarında yayımlamak Için Windows PowerShell betiklerini kullanma](vs-azure-tools-publishing-using-powershell-scripts.md).

JSON yapılandırma dosyası, dağıtılması gereken ayrıntıları belirtir. Projeyi oluştururken belirttiğiniz bilgileri (örneğin, Web sitesinin adı ve Kullanıcı adı) içerir. Ayrıca, sağlaması yapılacak veritabanını da içerir. Aşağıdaki kod örnek bir JSON yapılandırma dosyasını göstermektedir:

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication10554",
            "location": "West US"
        },
        "databases": [
            {
                "connectionStringName": "DefaultConnection",
                "databaseName": "WebApplication10554_db",
                "serverName": "iss00brc88",
                "user": "sqluser2",
                "password": "",
                "edition": "",
                "size": "",
                "collation": "",
                "location": "West US"
            }
        ]
    }
}
```

Dağıtılan öğeleri değiştirmek için JSON yapılandırma dosyasını düzenleyebilirsiniz. Bir Web sitesi bölümü gereklidir, ancak veritabanı bölümü isteğe bağlıdır.

## <a name="next-steps"></a>Sonraki adımlar
Daha fazla bilgi için bkz. [Publish-WebApplicationVM (Windows PowerShell betiği)](vs-azure-tools-publish-webapplicationvm.md).
