---
title: Docker Compose projeleri için başlatma profillerini yönetme
description: Docker Compose profillerini kullanmayı öğrenin ve bu profillerde Docker Compose Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433707"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Docker Compose için başlatma profillerini yönetme

Birden çok hizmet içeren ve Docker Compose kullanan bir uygulamanız varsa, başlatma ayarlarında mevcut bir başlatma profili oluşturarak veya düzenleyerek hangi hizmetlerin Docker Compose yapılandırabilirsiniz. Başlatma profilleri, yalnızca geçerli senaryo için önemli olan hizmetleri dinamik olarak çalıştırmanıza olanak sağlar. Hata ayıklama deneyiminizi özelleştirmek ve gibi belirli başlatma eylemlerini ayarlamak için başlatma profillerini oluşturabilir ve bu profillerden seçim `Browser Launch URL` gerçekleştirebilirsiniz. Ayrıca, her bir hizmeti ayrı ayrı seçme veya çalıştıracak hizmet grubunu belirlemek için Oluştur dosyanıza da bakan bir Docker Compose profili seçerek seçeneğiniz de vardır.

Profil oluşturma hakkında Docker Compose için [bkz. Oluşturma ile profilleri kullanma.](https://docs.docker.com/compose/profiles/)
 
## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019 sürüm 16.10 veya](https://visualstudio.microsoft.com/vs/) sonraki sürümler
- Kapsayıcı Düzenleme ile [Docker Compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Başlatma ayarlarını yönetme

*docker-compose.yml Docker Compose nin* beş hizmeti ve üç Oluşturma profili (web, web1 ve web2) olduğu bir proje için aşağıdaki adımları göz önünde bulundurabilirsiniz.

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Docker Compose başlatma ayarları iletişim kutusunu açmak için birkaç seçenek vardır:
- Bu Visual Studio Başlat **Ayarları'Docker Compose**  >  **Yönet'i seçin:**

    ![Oluşturma Ayarlarını Yönet menü öğesinin Hata Ayıklama ekran görüntüsü](media/launch-settings/debug-dropdown-manage-compose.png)

- Visual Studio projesine sağ tıklayın `docker-compose` ve Başlatma **Ayarları'Docker Compose Yönet'i seçin**

    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/launch-settings-context-menu.png)

- Hızlı Başlat (**Ctrl** Q ) kullanın ve Docker Compose komutunu bulmak + için arama yazın. 

Aşağıdaki örnekte, Hizmetler listesini bu profile dahil edilen beş profilden yalnızca üçünü filtreleen Oluştur `web1` profili seçilmiştir: 

!["Başlatma ayarları iletişim kutusunun ekran görüntüsü"](media/launch-settings/launch-settings-create-profile.png)

Profil Docker Compose bölümü yalnızca *docker-compose.yml* dosyalarında tanımlanmış profiller varsa görünür.

Sonraki örnekte, Bir Oluştur profilinde hizmetlere filtrelemek yerine tek tek hizmetler arasında seçim yapmak göstermektedir. Burada, hata ayıklama ve hata ayıklama olmadan beş hizmette yalnızca iki tane başlatan adlı yeni bir başlatma profili oluşturulduğunda iletişim kutusunun nasıl `test2` `webapplication1` görüntü olacağını `webapplication2` gösterebilirsiniz.  Bu başlatma profili, uygulama başlatıldığında bir tarayıcı başlatır ve bunu giriş sayfasına `webapplication1` açar. 

![Bazı hizmetlerin seçimi kaldırılmış başlatma ayarları iletişim kutusunun ekran görüntüsü](media/launch-settings/launch-settings-selected.png)

Bu bilgiler aşağıda gösterildiği gibi *launchSettings.jsolarak* kaydedilir

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Docker Compose profili kullanan bir başlatma profili oluşturma

Ayrıca Oluşturma profillerini kullanan Visual Studio profiller oluşturarak başlatma davranışlarını daha da özelleştirebilirsiniz.

Oluştur profilini kullanan başka bir profil oluşturmak için Profil profillerini kullan'ı **Docker Compose'yi** `web1` seçin. Artık başlatma profili üç hizmet içerir: (hem hem de `webapplication1` `web` Oluştur `web1` profillerine aittir) ve `external1` `external2` . Varsayılan olarak, ve gibi kaynak kodu olmayan hizmetler `external1` hata ayıklama olmadan başlat varsayılan `external2` **eylemine sahip olur.** Kaynak koduna sahip .NET uygulamaları varsayılan olarak Hata **ayıklamayı başlat olarak ayarlar.**

> [!IMPORTANT]
> Hizmet bir Oluştur profili belirtmezseniz, bu profil tüm Oluştur profillerine örtülü olarak dahil edilir.

![Başka bir profilin oluşturulmuş olduğu başlatma ayarları iletişim kutusunun ekran görüntüsü](media/launch-settings/launch-settings-create-profile.png)

Bu bilgiler aşağıdaki kodda gösterildiği gibi kaydedilir. Varsayılan eylemi değiştirmedikçe hizmet ve varsayılan eyleminin yapılandırması kaydedlanmaz.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

Ayrıca webapplication1'in eylemlerini Hata ayıklama olmadan başlat **olarak değiştirebilirsiniz.** bulaunchSettings.js *ayarlar* aşağıdaki kod gibi olur:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Özellikler

Aşağıdaki açıklama, üzerinde yer alan *launchSettings.js:*

|Özellik| Açıklama|
| - | - |
|Commandname| Komutun adı. Varsayılan olarak "DockerCompose" kullanılır|
|commandVersion| DockerCompose başlatma profilinin şemasını yönetmek için kullanılan sürüm numarası.|
|composeProfile| Başlatma profili tanımını tanımlayan üst özellik. Alt özellikleri `includes` ve `serviceActions`|
|composeProfile - içerir | Başlatma profilini oluştur profil adlarının listesi.|
|composeProfile - serviceActions | Seçilen Oluştur profillerini, hizmetlerini ve her hizmetin başlatma eylemlerini listeler|
|serviceActions | Seçilen hizmetleri ve başlatma eylemlerini listeler.|
|composeLaunchServiceName| DockerLaunchAction veya DockerLaunchBrowser belirtilirse, DockerServiceName, başlatılan hizmetin adıdır. Dosyanın içinde hangi hizmetin başlatıla Docker Compose için bu özelliği kullanın.|
|composeLaunchAction| F5 veya Ctrl **F5** üzerinde gerçekleştirecek **başlatma** + **eylemlerini belirtir.** İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient değerleridir.|
|composeLaunchUrl| Tarayıcıyı başlatmada kullanmak üzere URL. Geçerli değiştirme belirteçleri: "{ServiceIPAddress}", "{ServicePort}" ve "{Scheme}". Örneğin: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Sonraki adımlar

Container Tools derleme ve hata ayıklamaya genel bakış Visual Studio [Container Tools'un nasıl çalıştığını öğrenebilirsiniz.](container-build.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Araçları başlatma ayarları](container-launch-settings.md)

- [Docker Compose ayarlarını yapılandırma](docker-compose-properties.md)
