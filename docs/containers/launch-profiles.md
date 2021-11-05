---
title: Docker Compose hizmetlerinin bir alt kümesini başlatma
description: Docker Compose profillerini kullanmayı ve Docker Compose'i kullanarak hangi hizmetlerin Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 10/08/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a7d3b70e2c8ce4f761e1ec6dff25a0cd3a989e9a
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662626"
---
# <a name="launch-a-subset-of-compose-services"></a>Oluşturma hizmetlerinin bir alt kümesini başlatma

Birden çok hizmet içeren ve Docker Compose kullanan bir uygulamanız varsa, başlatma ayarlarında mevcut bir başlatma profili oluşturarak veya düzenleyerek hangi hizmetlerin Docker Compose yapılandırabilirsiniz. Başlatma profilleri, yalnızca geçerli senaryo için önemli olan hizmetleri dinamik olarak çalıştırmanıza olanak sağlar. Hata ayıklama deneyiminizi özelleştirmek ve gibi belirli başlatma eylemlerini ayarlamak için başlatma profillerini oluşturabilir ve bu profillerden seçim `Browser Launch URL` gerçekleştirebilirsiniz. Ayrıca, her bir hizmeti ayrı ayrı seçme veya çalıştıracak hizmet grubunu belirlemek için Oluştur dosyanıza da bakan bir Docker Compose profili seçerek seçeneğiniz de vardır.

Profil oluşturma hakkında Docker Compose için [bkz. Oluşturma ile profilleri kullanma.](https://docs.docker.com/compose/profiles/)

## <a name="prerequisites"></a>Önkoşullar

:::moniker range="vs-2019"
- [Visual Studio 2019 sürüm 16.10 veya](https://visualstudio.microsoft.com/vs/) sonraki sürümler
- Docker Compose ile [Kapsayıcı Düzenleme ile bir](tutorial-multicontainer.md) .NET Docker Compose
:::moniker-end
:::moniker range=">=vs-2022"
- [Visual Studio 2022 RC](https://visualstudio.microsoft.com/downloads) [veya Visual Studio 2019 sürüm 16.10](https://visualstudio.microsoft.com/vs/) veya sonrası
- Docker Compose ile [Kapsayıcı Düzenleme ile bir](tutorial-multicontainer.md) .NET Docker Compose
:::moniker-end

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
- Bu Visual Studio Başlat ve **Başlat'ı**  >  **seç Docker Compose Yönet'Ayarlar:**

    :::moniker range="<=vs-2019"
    ![Oluştur ve Oluştur menü öğesinin Ayarlar Hata Ayıklama ekran görüntüsü](media/launch-settings/debug-dropdown-manage-compose.png)
    :::moniker-end
    :::moniker range=">=vs-2022"
    ![Oluştur ve Oluştur menü öğesinin Ayarlar Hata Ayıklama ekran görüntüsü](media/tutorial-multicontainer/vs-2022/debug-dropdown-manage-compose.png)
    :::moniker-end

- Visual Studio projesine sağ tıklayın `docker-compose` ve Başlat'ı **Docker Compose'yi Ayarlar**

    :::moniker range="<=vs-2019"
    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/launch-settings-context-menu.png)
    :::moniker-end
    :::moniker range=">=vs-2022"
    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/vs-2022/launch-settings-context-menu.png)
    :::moniker-end

- Hızlı Başlat (**Ctrl** Q ) kullanın ve aynı +  **Docker Compose** için arama yazın.

Aşağıdaki örnekte, Hizmetler listesini bu profile dahil edilen beş profilden yalnızca üçünü filtreleen Oluştur `web1` profili seçilmiştir: 

!["Başlatma ayarları iletişim kutusunun ekran görüntüsü"](media/launch-settings/launch-settings-create-profile.png)

>[!NOTE]
> Profil Docker Compose bölümü yalnızca *docker-compose.yml* dosyalarında tanımlanmış profiller varsa görünür.

Sonraki örnekte, Bir Oluştur profilinde hizmetlere filtrelemek yerine tek tek hizmetler arasında seçim yapmak göstermektedir. Burada, hata ayıklama ve hata ayıklama olmadan beş hizmette yalnızca iki tane başlatan adlı yeni bir başlatma profili oluşturulduğunda iletişim kutusunun nasıl `test2` `webapplication1` görüntü olacağını `webapplication2` gösterebilirsiniz.  Bu başlatma profili, uygulama başlatıldığında bir tarayıcı başlatır ve bunu giriş sayfasına `webapplication1` açar. 

![Bazı hizmetlerin seçimi kaldırılmış başlatma ayarları iletişim kutusunun ekran görüntüsü](media/launch-settings/launch-settings-selected.png)

Bu bilgiler aşağıda gösterildiği gibi *launchSettings.json'a* kaydedilir

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

Ayrıca Oluşturma profillerini kullanan Visual Studio profillerini oluşturarak başlatma davranışlarını daha da özelleştirebilirsiniz.

Oluştur profilini kullanan başka bir profil oluşturmak için Profil profillerini **kullan'ı Docker Compose'yi** `web1` seçin. Artık başlatma profili üç hizmet içerir: (hem hem de `webapplication1` `web` Oluştur `web1` profillerine aittir) ve `external1` `external2` . Varsayılan olarak, ve gibi kaynak kodu olmayan hizmetler `external1` hata ayıklama olmadan başlat varsayılan `external2` **eylemine sahip olur.** Kaynak koduna sahip .NET uygulamaları varsayılan olarak Hata **ayıklamayı başlat olarak ayarlar.**

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

Ayrıca webapplication1'in eylemlerini Hata ayıklama olmadan başlat **olarak değiştirebilirsiniz.** *LaunchSettings.json'daki* ayarlar aşağıdaki koda benzer:

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

*launchSettings.json'daki her özelliğin açıklaması şu şekildedir:*

|Özellik| Açıklama|
| - | - |
|Commandname| Komutun adı. Varsayılan olarak "DockerCompose" kullanılır|
|commandVersion| DockerCompose başlatma profilinin şemasını yönetmek için kullanılan sürüm numarası.|
|composeProfile| Başlatma profili tanımını tanımlayan üst özellik. Alt özellikleri `includes` ve `serviceActions`|
|composeProfile - içerir | Başlatma profilini oluştur profil adlarının listesi.|
|composeProfile - serviceActions | Seçilen Oluştur profillerini, hizmetlerini ve her hizmetin başlatma eylemlerini listeler|
|serviceActions | Seçilen hizmetleri ve başlatma eylemlerini listeler.|
|composeLaunchAction| F5 veya Ctrl **F5** üzerinde gerçekleştirecek **başlatma** + **eylemlerini belirtir.** İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient değerleridir.|
|composeLaunchUrl| Tarayıcıyı başlatmada kullanmak üzere URL. Geçerli değiştirme belirteçleri: "{ServiceIPAddress}", "{ServicePort}" ve "{Scheme}". Örneğin: {Scheme}://{ServiceIPAddress}:{ServicePort}|
|composeLaunchServiceName| composeLaunchUrl içinde belirteçleri değiştirmek için kullanılan hizmeti belirtir.|

## <a name="next-steps"></a>Sonraki adımlar

Container Tools derleme ve hata ayıklamaya genel bakış Visual Studio [Container Tools'un nasıl çalıştığını öğrenebilirsiniz.](container-build.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Kapsayıcı Araçları başlatma ayarları](container-launch-settings.md)

- [Docker Compose ayarları oluşturma](docker-compose-properties.md)
