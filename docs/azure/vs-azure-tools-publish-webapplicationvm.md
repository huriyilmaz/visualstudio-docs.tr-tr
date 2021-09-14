---
title: Publish-WebApplicationVM | Microsoft Docs
description: Bir web uygulamasını sanal makineye dağıtmayı öğrenin. Bu betik, azure aboneliğiniz yoksa gerekli kaynakları oluşturur.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9443fbf7abe1098d56c41bf25dadca7ff60ced79
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633073"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell betiği)
Bir web uygulamasını sanal makineye dağıtır. Betik, azure aboneliğiniz yoksa gerekli kaynakları oluşturur.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Yapılandırma
Dağıtımın ayrıntılarını açıklayan JSON yapılandırma dosyasının yolu.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |true |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="subscriptionname"></a>SubscriptionName
Sanal makineyi oluşturmak istediğiniz Azure aboneliğinin adı.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |Abonelik dosyasındaki ilk aboneliği kullanır |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="webdeploypackage"></a>WebDeployPackage
Sanal makinede yayımlamak için web dağıtım paketinin yolu. Web'de Yayımla sihirbazını kullanarak bu paketi Visual Studio. Bkz. [How to: Create a Web Deployment Package in Visual Studio](/previous-versions/aspnet/dd465323(v=vs.110)).

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="allowuntrusted"></a>AllowUntrusted
True ise, güvenilen bir kök yetkili tarafından imza olmayan sertifikaların kullanımına izin ver.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="vmpassword"></a>VMPassword
Sanal makine hesabının kimlik bilgileri. Örnek: -VMPassword @{Name = "admin"; Password = "password"}

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure'da SQL kimlik bilgileri. Örnek: -DatabaseServerPassword @{Name = "admin"; Password = "password"}

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True ise, betikten çıkış akışına iletileri yazdırabilirsiniz.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

## <a name="remarks"></a>Açıklamalar
geliştirme ve test ortamları oluşturmak için betiğin nasıl kullanılacağına ilişkin ayrıntılı bir açıklama için bkz. [geliştirme ve test ortamlarında yayımlamak için Windows PowerShell betikleri kullanma](vs-azure-tools-publishing-using-powershell-scripts.md).

JSON yapılandırma dosyası, dağıtılması gereken ayrıntıları belirtir. Projeyi oluştururken belirttiğiniz bilgileri içerir (örneğin ad, benzeşim grubu, VHD görüntüsü ve sanal makinenin boyutu). Ayrıca sanal makinedeki uç noktaları, sağlama yapılacak veritabanlarını ve Web Dağıtım parametrelerini de içerir. Aşağıdaki kod örnek bir JSON yapılandırma dosyasını göstermektedir:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Sağlanan öğeleri değiştirmek için JSON yapılandırma dosyasını düzenleyebilirsiniz. Bir sanal makine ve bulut hizmeti gereklidir, ancak veritabanı bölümü isteğe bağlıdır.