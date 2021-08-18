---
title: Publish-WebApplicationVM | Microsoft Docs
description: Bir Web uygulamasını bir sanal makineye dağıtmayı öğrenin. Bu betik, mevcut değilse, Azure aboneliğinizde gerekli kaynakları oluşturur.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9443fbf7abe1098d56c41bf25dadca7ff60ced79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082315"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell betiği)
Bir sanal makineye bir Web uygulaması dağıtır. Komut dosyası, mevcut değilse, Azure aboneliğinizde gerekli kaynakları oluşturur.

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
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="subscriptionname"></a>SubscriptionName
Sanal makineyi oluşturmak istediğiniz Azure aboneliğinin adı.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |Abonelik dosyasındaki ilk aboneliği kullanır |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="webdeploypackage"></a>WebDeployPackage
Sanal makinede yayımlanacak Web dağıtım paketinin yolu. Bu paketi, Visual Studio Web 'i Yayımla Sihirbazı 'nı kullanarak oluşturabilirsiniz. Bkz. [nasıl yapılır: Visual Studio Web dağıtım paketi oluşturma](/previous-versions/aspnet/dd465323(v=vs.110)).

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="allowuntrusted"></a>Allowgüvenilmeyen
Doğru ise, güvenilen kök yetkili tarafından imzalanmamış sertifikaların kullanılmasına izin verin.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="vmpassword"></a>VMPassword
Sanal makine hesabının kimlik bilgileri. Örnek:-VMPassword @ {Name = "admin"; Password = "parola"}

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure 'da SQL veritabanının kimlik bilgileri. Örnek:-DatabaseServerPassword @ {Name = "admin"; Password = "parola"}

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yok |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakterler kabul edilsin mi? |yanlış |

### <a name="sendhostmessagestooutput"></a>Sendhostiletitooutput
Doğru ise, komut dosyasından çıkış akışına iletileri yazdırın.

| Diğer adlar | yok |
| --- | --- |
| Gerekli mi? |yanlış |
| Konum |adlandırılmış |
| Varsayılan değer |yanlış |
| İşlem hattı girişi kabul edilsin mi? |yanlış |
| Joker karakter kabul edilsin mi? |yanlış |

## <a name="remarks"></a>Açıklamalar
Geliştirme ve Test ortamları oluşturmak için betiği kullanma hakkında eksiksiz bir açıklama için, bkz. [Using Windows PowerShell Scripts to Publish to Dev and Test Environments](vs-azure-tools-publishing-using-powershell-scripts.md).

JSON yapılandırma dosyası, nelerin dağıtılacağına ilişkin ayrıntıları belirtir. Projeyi oluşturulduğunda belirttiğiniz ad, benzeşm grubu, VHD görüntüsü ve sanal makinenin boyutu gibi bilgileri içerir. Ayrıca sanal makinede uç noktaları, sağlanmayacak veritabanlarını (varsa) ve web dağıtım parametrelerini içerir. Aşağıdaki kod, örnek bir JSON yapılandırma dosyasını gösterir:

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

Sağlananları değiştirmek için JSON yapılandırma dosyasını düzenleyebilirsiniz. Sanal makine ve bulut hizmeti gereklidir, ancak veritabanı bölümü isteğe bağlıdır.