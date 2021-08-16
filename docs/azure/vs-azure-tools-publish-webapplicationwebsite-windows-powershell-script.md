---
title: PowerShell betiği kullanarak web uygulaması yayımlama
description: Azure web sitesinde web projesi yayımlamayı öğrenin. Bu betik, azure aboneliğiniz yoksa gerekli kaynakları oluşturur.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: a5ea7e231025a70eec3f54b804a58039df0dded14340ad0c4887005b908c343a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121406625"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell betiği)
## <a name="syntax"></a>Syntax
Azure web sitesinde bir web projesi yayımlar. Betik, azure aboneliğiniz yoksa gerekli kaynakları oluşturur.

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
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="subscriptionname"></a>SubscriptionName
Web sitesini oluşturmak istediğiniz Azure aboneliğinin adı.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="webdeploypackage"></a>WebDeployPackage
Web sitesinde yayımlayacak web dağıtım paketinin yolu. Web'de Yayımla sihirbazını kullanarak bu paketi Visual Studio. Daha fazla bilgi için [bkz. Kullanmaya başlayın ve Azure Cloud Services ile ASP.NET.](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md)

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure'daki veritabanına SQL adı ve parolası.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True ise, betikten çıkış akışına iletileri yazdırabilirsiniz.

| Parametre | Varsayılan değer |
| --- | --- |
| Diğer adlar |yok |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="remarks"></a>Açıklamalar
Geliştirme ve Test ortamları oluşturmak için betiği kullanma hakkında eksiksiz bir açıklama için bkz. Geliştirme ve Test Ortamlarına Yayımlamak Windows PowerShell [Betiklerini Kullanma.](vs-azure-tools-publishing-using-powershell-scripts.md)

JSON yapılandırma dosyası, nelerin dağıtılacağına ilişkin ayrıntıları belirtir. Projeyi oluşturulduğunda belirttiğiniz web sitesinin adı ve kullanıcı adı gibi bilgileri içerir. Ayrıca sağlanmayacak veritabanını da (varsa) içerir. Aşağıdaki kod, örnek bir JSON yapılandırma dosyasını gösterir:

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

Dağıtılanları değiştirmek için JSON yapılandırma dosyasını düzenleyebilirsiniz. WebSite bölümü gereklidir, ancak veritabanı bölümü isteğe bağlıdır.

## <a name="next-steps"></a>Sonraki adımlar
Daha fazla bilgi için bkz. [Publish-WebApplicationVM (Windows PowerShell betiği)](vs-azure-tools-publish-webapplicationvm.md).
