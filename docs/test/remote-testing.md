---
title: Visual Studio'de Uzaktan Test
description: Kapsayıcılar, WSL2 veya SSH bağlantıları Visual Studio uzak ortamlardan testleri çalıştırmak için Visual Studio Test Gezgini'nde uzaktan testi kullanmayı öğrenin. Bu konu, yerel kapsayıcılar, WSL2 veya SSH bağlantıları testenvironments.jsuzaktan test yapılandırmayı kapsar.
ms.date: 08/26/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
monikerRange: '>= vs-2022'
ms.workload:
- multiple
ms.openlocfilehash: ff31dd7e6f5b45c316e3cd094a2728b085180e0b
ms.sourcegitcommit: f4e975cb5755b4a3ff207f9bde74e79f6db5c643
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2021
ms.locfileid: "123361135"
---
# <a name="remote-testing-experimental-preview"></a>Uzaktan Test (deneysel önizleme)

Uzaktan test, geliştiricilerin testleri çalıştırmaya Visual Studio hata ayıklamak için 2022'den uzak ortamlara bağlanmasını sağlar. Bu işlevsellik, farklı işletim sistemleri veya Linux işletim sistemleri gibi birden çok farklı hedef ortamına kod dağıtan platformlar Windows geliştiriciler için kullanışlıdır. Örneğin, normalde bir geliştiricinin Linux üzerinde çalışan bir testten geri bildirim almak için değişiklikleri CI işlem hattına göndermesi gerekir. Bu özellikle, Test Gezgini'ni uzak bir ortama bağlayarak Visual Studio Linux testlerini çalıştırabilirsiniz.

Uzaktan testin bu deneysel sürümünü kullanma gereksinimleri:
* Visual Studio 2022 Güncelleştirme 17.0 Önizleme 3 veya sonraki bir sürümü
* Yalnızca .NET testlerinde kullanılabilir.
  * Diğer diller için uzaktan test desteğiyle ilgileniyorsanız lütfen bir [öneri kaydedin](/visualstudio/ide/suggest-a-feature) veya mevcut öneriyi oy kullanın. [C++ uzaktan test desteği.](https://developercommunity.visualstudio.com/t/run-c-unit-tests-on-linux-with-visual-studio/1403357)
* Şu anda ortamın sağlanmasının büyük bir kısmını kullanıcının belirtimleri bırakmaktadır. Kullanıcının hedef ortamınıza gerekli bağımlılıkları yüklemesi gerekir. Örneğin, testleriniz .NET 5.0'ı hedeflese kapsayıcıda Dockerfile dosyanız aracılığıyla .NET 5.0 yüklü olduğundan emin olun. Testleri uzaktan çalıştırmak ve bulmak için gereken uzak ortama .NET Core yüklemek için bir istem olabilir. 
* Çıkış Ve Testler bölmesini kullanarak uzak ortama bağlantı durumunu > plan olun. Örneğin, kapsayıcı durdurulmuşsa Çıkış ve Testler bölmesinde > görünür. Tüm senaryoları algılamayabilirsiniz, bu nedenle bağlantının kaybedildi gibi görünüyorsa çıkışınızı denetlemeyi planla. Özellikle, Çıkış bölmesi "Test" olarak ayarlanmasa, iletiyi hemen görenemebilirsiniz. Bağlantı kaybolursa, bağlantıyı yerel ortamınıza geri ayarlamak için Test Gezgini'nde ortam açılır öğesini kullanabilir ve bağlantıyı yeniden başlatacak uzak ortamı yeniden seçin.

## <a name="set-up-the-remote-testing-environment"></a>Uzaktan test ortamını ayarlama

Ortamlar, `testenvironments.json` çözümünün kökünde kullanılarak belirtilir. JSON dosya yapısı burada açıklanan şemaya uyar:
```json
{
    "version": "1", // value must be 1
    "environments": [
        { "name": "<unique name>", ... },
        ...
    ]
}
```

### <a name="local-container-connections"></a>Yerel kapsayıcı bağlantıları

Yerel olarak çalışan bir kapsayıcıya bağlanmak için yerel makinede [Docker](https://www.docker.com/products/docker-desktop) Desktop'ınız olması gerekir. İsteğe bağlı olarak, [daha iyi performans için WSL2](/windows/wsl/install-win10) tümleştirmeyi etkinleştirin.

Dockerfile için, ortamı çözümünün `testEnvironments.json` kökünde belirtilebilir. Burada açıklanan özellikleri kullanır.
```json
    {
    "name": "<name>",
    "localRoot": "<path to local environment>", // optional
    "type": "docker",
    "dockerImage": "<docker image tag>",
    }
```

Aşağıdaki örnek adlı yerel `testenvironments.json` bir kapsayıcı görüntüsü için \<mcr.microsoft.com/dotnet/core/sdk\> gösterir.
```json
{
"version": "1",
"environments": [
    {
    "name": "linux dotnet-core-sdk-3.1",
    "type": "docker",
    "dockerImage": "mcr.microsoft.com/dotnet/core/sdk"
    }
]
}
```

Aşağıdaki örnekte. .NET 5.0'ı hedef alan testleri çalıştırmaya yönelik bir Dockerfile yer a gösterir. İkinci satır, hata ayıklayıcının kapsayıcınıza bağlana ve kapsayıcıda çalıştırana kadar devamını sağlar.
```
FROM mcr.microsoft.com/dotnet/core/sdk:5.0

RUN wget https://aka.ms/getvsdbgsh && \
    sh getvsdbgsh -v latest  -l /vsdbg
```

Kapsayıcının yerel makineniz üzerinde yerleşik bir görüntüsü olması gerekir. Aşağıdaki komutu kullanarak (sonundaki "." dahil) bir kapsayıcıyı derlemek için: `docker build -t <docker image name> -f <path to Dockerfile> .`

### <a name="local-wsl2-connections"></a>Yerel WSL2 bağlantıları
WSL2'de testleri uzaktan çalıştırmak için yerel [makineniz üzerinde WSL2 tümleştirmeyi](/windows/wsl/install-win10) etkinleştirmeniz gerekir.

Ortam, aşağıdaki şema kullanılarak çözümünün kökünde belirtilebilir ve yerine hangi `testEnvironments.json` \<Ubuntu\> WSL2 Dağıtımını yüklemiş olursanız kullanın.
```json
{
"version": "1",
"environments": [
    {
    "name": "WSL-Ubuntu",
    "type": "wsl",
    "wslDistribution": "Ubuntu"
    }
]
}
```

### <a name="ssh-connections"></a>SSH bağlantıları
 Araçlar ve Seçenekler'de SSH bağlantıları ekleyebilir veya **> Platformlar > SSH bağlantılarını > Bağlantı Yöneticisi.** "Ekle"yi seçmek konak adını, bağlantı noktasını ve ihtiyacınız olan kimlik bilgilerini girmenize olanak sağlar.

Ortam, aşağıdaki şema kullanılarak çözümünün kökünde belirtilebilir ve yerine `testEnvironments.json` `\<ssh://user@hostname:22\>` SSH remoteUri'nizi kullanabilirsiniz.
```json
{
"version": "1",
"environments": [
    {
    "name": "ssh-remote",
    "type": "ssh",
    "remoteUri": "ssh://user@hostname:22"
    }
]
}
```

## <a name="use-the-test-explorer-to-run-and-debug-remote-tests"></a>Uzak testleri çalıştırmak ve hata ayıklamak için Test Gezgini'ni kullanma
* Etkin ortam, Test Gezgini araç çubuğundaki bir açılan liste aracılığıyla seçilir. Şu anda aynı anda yalnızca bir test ortamı etkin olabilir.

  ![Test Gezgini'nde uzaktan test ortamı açılan listesinde](media/remote_test_drop_down.png)

* Ortam seçildikten sonra testler yeni ortamda keşfedilecek ve çalıştırilecek.

  ![Testler uzak ortamlarda keşfedildi ve yürütülür](media/remote_test_linux_discovery.png)

* Artık testlerinizi uzak ortamda çalıştırabilir ve ortamlarda testlerinizi ayıkabilirsiniz!

  ![Test gezgininde uzak ortamdan test sonuçlarını görüntüleme](media/remote_test_linux_passing.png)

* Test Gezgini bazı eksik ortam önkoşullarını yükleme ve eksik bağımlılıkları yükleme denemesi istendiğinde. Ancak, uzak ortamın sağlanmasının büyük bir kısmını kullanıcının belirtimleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
