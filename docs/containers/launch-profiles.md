---
title: Docker Compose projeleri için başlatma profillerini yönetme
description: Docker Compose başlatma profillerinin nasıl kullanılacağını ve Visual Studio 'da Docker Compose kullandığınızda hangi hizmetlerin başlatılabildiğini nasıl denetleyeceğinizi öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 003205525f883b010f897e6e47d4cab92a31b8a1
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110018549"
---
# <a name="manage-launch-profiles-for-docker-compose-preview"></a>Docker Compose için başlatma profillerini yönetme (Önizleme)

Birden çok hizmetten oluşan ve Docker Compose kullanan bir uygulamanız varsa, Docker Compose başlatma ayarları ' nda var olan bir başlatma profili oluşturarak veya düzenleyerek hangi hizmetlerin çalıştırılacağını ve hata ayıklamasını yapılandırabilirsiniz. Başlatma profilleri, yalnızca geçerli senaryonuza bağlı olan hizmetleri dinamik olarak çalıştırmanızı sağlar. Hata ayıklama deneyiminizi özelleştirmek ve gibi belirli başlatma eylemlerini ayarlamak için başlatma profilleri ' nden oluşturabilir ve seçim yapabilirsiniz `Browser Launch URL` . Ayrıca, her bir hizmeti ayrı ayrı seçme ya da bir Docker Compose profili seçerek, çalıştırılacak hizmet grubunu belirlemek için oluşturma dosyanıza de bakacaksınız.

Docker Compose profilleri hakkında daha fazla bilgi için bkz. [oluşturma ile profilleri kullanma](https://docs.docker.com/compose/profiles/).
 
## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019 sürüm 16,10 Önizleme](https://visualstudio.microsoft.com/vs/preview/) veya üzeri
- [Docker Compose Ile kapsayıcı düzenlemesi](tutorial-multicontainer.md) olan bir çözüm

## <a name="manage-launch-settings"></a>Başlatma ayarlarını yönetme

*Docker-Compose. yıml* 'nin beş hizmet ve üç oluşturma profili (Web, Web1 ve web2) sahip olduğu aşağıdaki Docker Compose projeyi göz önünde bulundurun.

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
- Visual Studio 'da, **Hata Ayıkla**  >  **Docker Compose başlatma ayarları**' nı seçin:

    ![Hata ayıklama oluşturma ayarlarını yönetme menü öğesi ekran görüntüsü](media/launch-settings/debug-dropdown-manage-compose.png)

- Visual Studio projesine sağ tıklayın `docker-compose` ve **Docker Compose başlatma ayarlarını yönet** ' i seçin.

    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/launch-settings-context-menu.png)

- Hızlı Başlatma ' yı (**CTRL** + **Q**) kullanın ve **Docker Compose** için arama yapın ve belirtilen komutu bulun.

Aşağıdaki örnekte, `web1` Oluştur profili seçilidir ve bu profil, **Hizmetler** listesini yalnızca bu profilde bulunan üç beş tanesi ile filtreliyor:

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

Ayrıca webapplication1'in eylemlerini Hata ayıklama olmadan başlat **olarak değiştirebilirsiniz.** BulaunchSettings.js *ayarlar* aşağıdaki kod gibi olur:

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
|composeLaunchUrl| Tarayıcı başlatılırken kullanılacak URL. Geçerli değiştirme belirteçleri şunlardır "{Serviceıpaddress}", "{ServicePort}" ve "{Scheme}". Örneğin: {Scheme}: ı{serviceipaddress}: {ServicePort}|

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio kapsayıcı araçları derleme ve hata ayıklamayla genel bakış](container-build.md)aracılığıyla kapsayıcı araçlarının nasıl çalıştığı hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

- [Docker Compose derleme ayarları](docker-compose-properties.md)
