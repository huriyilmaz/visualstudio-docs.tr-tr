---
title: Docker Compose hizmetlerinin bir alt kümesini başlatın
description: Docker Compose başlatma profillerinin nasıl kullanılacağını ve Visual Studio Docker Compose kullandığınızda hangi hizmetlerin başlatılabildiğini nasıl denetleyeceğinizi öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 10/08/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 15861e9a22ca77267e636cb0861c97d3d41c3ab9
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001745"
---
# <a name="launch-a-subset-of-compose-services"></a>Oluşturma hizmetleri alt kümesini Başlat

Birden çok hizmetten oluşan ve Docker Compose kullanan bir uygulamanız varsa, Docker Compose başlatma ayarları ' nda var olan bir başlatma profili oluşturarak veya düzenleyerek hangi hizmetlerin çalıştırılacağını ve hata ayıklamasını yapılandırabilirsiniz. Başlatma profilleri, yalnızca geçerli senaryonuza bağlı olan hizmetleri dinamik olarak çalıştırmanızı sağlar. Hata ayıklama deneyiminizi özelleştirmek ve gibi belirli başlatma eylemlerini ayarlamak için başlatma profilleri ' nden oluşturabilir ve seçim yapabilirsiniz `Browser Launch URL` . Ayrıca, her bir hizmeti ayrı ayrı seçme ya da bir Docker Compose profili seçerek, çalıştırılacak hizmet grubunu belirlemek için oluşturma dosyanıza de bakacaksınız.

Docker Compose profilleri hakkında daha fazla bilgi için bkz. [oluşturma ile profilleri kullanma](https://docs.docker.com/compose/profiles/).

## <a name="prerequisites"></a>Önkoşullar

:::moniker range="vs-2019"
- [Visual Studio 2019 sürüm 16,10](https://visualstudio.microsoft.com/vs/) veya üzeri
- [Docker Compose Ile kapsayıcı düzenlemesi](tutorial-multicontainer.md) olan bir .NET çözümü
:::moniker-end
:::moniker range=">=vs-2022"
- [Visual Studio 2022](https://visualstudio.microsoft.com/downloads) veya [Visual Studio 2019 sürüm 16,10](https://visualstudio.microsoft.com/vs/) veya üzeri
- [Docker Compose Ile kapsayıcı düzenlemesi](tutorial-multicontainer.md) olan bir .NET çözümü
:::moniker-end

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
- Visual Studio,   >  **yönetim Docker Compose başlatma Ayarlar** hata ayıkla ' yı seçin:

    :::moniker range="<=vs-2019"
    ![hata ayıklama oluşturma Ayarlar menü öğesini yönetme ekran görüntüsü](media/launch-settings/debug-dropdown-manage-compose.png)
    :::moniker-end
    :::moniker range=">=vs-2022"
    ![hata ayıklama oluşturma Ayarlar menü öğesini yönetme ekran görüntüsü](media/tutorial-multicontainer/vs-2022/debug-dropdown-manage-compose.png)
    :::moniker-end

- Visual Studio projesine sağ tıklayın `docker-compose` ve **Docker Compose başlatmayı yönet** ' i seçin Ayarlar

    :::moniker range="<=vs-2019"
    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/launch-settings-context-menu.png)
    :::moniker-end
    :::moniker range=">=vs-2022"
    ![Bağlam menüsü öğesinin ekran görüntüsü](media/launch-settings/vs-2022/launch-settings-context-menu.png)
    :::moniker-end

- Hızlı Başlat (**CTRL** + **Q**) kullanın ve aynı komutu bulmak için **Docker Compose** arayın.

Aşağıdaki örnekte, `web1` Oluştur profili seçilidir ve bu profil, **Hizmetler** listesini yalnızca bu profilde bulunan üç beş tanesi ile filtreliyor:

!["Başlatma ayarları iletişim kutusunun ekran görüntüsü"](media/launch-settings/launch-settings-create-profile.png)

>[!NOTE]
> Docker Compose profilleri bölümü yalnızca *Docker-Compose. yıml* dosyalarınızda tanımlanmış profiller varsa görüntülenir.

Sonraki örnekte, bir oluşturma profilindeki hizmetlere filtre uygulamak yerine bireysel hizmetler arasında seçim gösterilmektedir. Burada, `test2` hata ayıklama ve hata ayıklama olmadan beş hizmetten oluşan iki hizmetten oluşan adlı yeni bir başlatma profili oluşturduysanız, iletişim kutusunun nasıl görünebileceği gösterilmektedir `webapplication1` `webapplication2` .  Bu başlatma profili ayrıca uygulama başlatıldığında bir tarayıcı başlatır ve giriş sayfasında açar `webapplication1` . 

![Bazı hizmetler seçili değilken başlatma ayarları iletişim kutusunun ekran görüntüsü](media/launch-settings/launch-settings-selected.png)

Bu bilgiler, aşağıda gösterildiği gibi *Launchsettings. JSON* dosyasında kaydedilecek

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

ayrıca, oluşturma profillerini kullanan Visual Studio başlatma profilleri oluşturarak başlatma davranışlarını daha da özelleştirebilirsiniz.

Oluşturma profilini kullanan başka bir profil oluşturmak için **Docker Compose profillerini kullan** ' ı seçin ve öğesini seçin `web1` . Şimdi başlatma profili üç hizmet içerir: `webapplication1` (hem hem de `web` oluşturma profillerine ait olan `web1` ) `external1` ve `external2` . Varsayılan olarak, ve gibi kaynak kodu olmayan hizmetler, `external1`  `external2` **hata ayıklama olmadan Başlat** varsayılan eylemine sahiptir. Kaynak kodlu .NET uygulamaları, **hata ayıklamayı başlatmak** için varsayılan olarak kullanılır.

> [!IMPORTANT]
> Bir hizmet bir oluşturma profili belirtmezse, tüm oluşturma profillerine örtülü olarak dahil edilir.

![Başka bir profille oluşturulan başlatma ayarları iletişim kutusunun ekran görüntüsü](media/launch-settings/launch-settings-create-profile.png)

Bu bilgiler, aşağıdaki kodda gösterildiği gibi kaydedilir. Varsayılan eylemi değiştirmediğiniz müddetçe hizmetin yapılandırması ve varsayılan eylemi kaydedilmez.

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

Ayrıca, WebApplication1 eylemini **hata ayıklama olmadan başlayacak** şekilde değiştirebilirsiniz. *Launchsettings. JSON* dosyasındaki ayarlar daha sonra aşağıdaki koda benzer şekilde görünür:

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

*Launchsettings. JSON* içindeki her bir özelliğin açıklaması aşağıdadır:

|Özellik| Açıklama|
| - | - |
|Name| Komutun adı. Varsayılan olarak "DockerCompose"|
|commandVersion| DockerCompose başlatma profili şemasını yönetmek için kullanılan sürüm numarası.|
|composeProfile| Başlatma profili tanımını tanımlayan Parent özelliği. Alt özellikleri `includes` ve `serviceActions`|
|composeProfile-şunları içerir | Bir başlatma profili oluşturan oluşturma profili adlarının listesi.|
|composeProfile-serviceActions | Her hizmetin seçili oluşturma profillerini, hizmetlerini ve başlatma eylemini listeler|
|serviceActions | Seçilen hizmetleri ve başlatma eylemini listeler.|
|composeLaunchAction| **F5** veya **CTRL** F5 üzerinde gerçekleştirilecek başlatma eylemini belirtir + . İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient 'Tur.|
|composeLaunchUrl 'Si| Tarayıcı başlatılırken kullanılacak URL. Geçerli değiştirme belirteçleri şunlardır "{Serviceıpaddress}", "{ServicePort}" ve "{Scheme}". Örneğin: {Scheme}: ı{serviceipaddress}: {ServicePort}|
|composeLaunchServiceName| ComposeLaunchUrl 'Sindeki belirteçleri değiştirmek için kullanılan hizmeti belirtir.|

## <a name="next-steps"></a>Sonraki adımlar

kapsayıcı araçlarının nasıl çalıştığı hakkında daha fazla bilgi edinin [Visual Studio kapsayıcı araçları derleme ve hata ayıklama genel bakış](container-build.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

- [Docker Compose derleme ayarları](docker-compose-properties.md)
