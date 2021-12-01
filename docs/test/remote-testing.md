---
title: Visual Studio uzaktan test
description: Visual Studio Test gezgini 'nde kapsayıcılar, WSL2 veya SSH bağlantıları üzerinden uzak ortamlardan testleri çalıştırmak için uzaktan test etmeyi nasıl kullanacağınızı öğrenin. Bu konu, yerel kapsayıcılar, WSL2 veya SSH bağlantıları için testortamlarını. JSON ile uzaktan testi yapılandırmayı ele alır.
ms.date: 08/26/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
monikerRange: '>= vs-2022'
ms.workload:
- multiple
ms.openlocfilehash: 7b756ac42a7747d1d9011b5e3e84f75731b38a7e
ms.sourcegitcommit: 263703af9c4840e0e0876aa99df6dd7455c43519
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "133387487"
---
# <a name="remote-testing-experimental-preview"></a>Uzaktan test (deneysel Önizleme)

uzaktan test, geliştiricilerin çalışan ve hata ayıklama testleri için uzak ortamlara 2022 Visual Studio bağlanmasına olanak sağlar. bu işlevsellik, farklı Windows veya Linux işletim sistemleri gibi birden çok farklı hedef ortama kod dağıtan platformlar arası geliştiriciler için yararlıdır. Örneğin, normalde bir geliştiricinin Linux üzerinde çalışan bir testten geri bildirim almak için değişiklikleri bir CI ardışık düzenine göndermek zorunda olması gerekir. bu özellikle, Test gezginini uzak bir ortama bağlayarak Visual Studio Linux testlerini doğrudan çalıştırabilirsiniz.

Uzaktan test 'in bu deneysel sürümünü kullanma gereksinimleri:
* Visual Studio 2022 güncelleştirme 17,0 Preview 3 veya üzeri
* Yalnızca .NET testleri için kullanılabilir.
  * Diğer diller için uzaktan test desteğiyle ilgileniyorsanız lütfen [bir öneri](/visualstudio/ide/suggest-a-feature) gönderin veya mevcut bir öneriyi oylayın. [C++ uzaktan sınamasını destekleme](https://developercommunity.visualstudio.com/t/run-c-unit-tests-on-linux-with-visual-studio/1403357).
* şu anda, uzak ortamda yalnızca Windows, ubuntu ve de, görüntülerini destekliyoruz. 
* Şu anda ortamın sağlanması, kullanıcının belirtimine ayrılmakta. Kullanıcının hedef ortamınıza gerekli bağımlılıkları yüklemesi gerekir. Örneğin, testleriniz .NET 6,0 ' i hedefliyorsanız, kapsayıcının Dockerfile ile .NET 6,0 yüklendiğinden emin olmanız gerekir. Uzak ortama .NET Core yüklemek için bir istem olabilir. Bu, testleri uzaktan çalıştırmak ve saptamak için gereklidir. 
* Çıkış > testleri bölmesini kullanarak bağlantı durumunuzu uzak ortama izlemeyi planlayın. Örneğin, kapsayıcı durdurulmuşsa çıktı > testleri bölmesinde bir ileti görüntülenir. Tüm senaryoları algılayamıyoruz, bu nedenle bağlantı kaybedildiği gibi görünüyorsa çıktınızdan emin olun. Özellikle, çıkış bölmesi "test" olarak ayarlanmamışsa iletiyi hemen görmeyebilirsiniz. Bağlantı kaybolursa, bağlantıyı yerel ortamınıza geri ayarlamak için test Gezgini 'ndeki ortam açılır öğesini kullanabilir ve sonra bağlantıyı yeniden başlatmak için uzak ortamı yeniden seçebilirsiniz.

## <a name="set-up-the-remote-testing-environment"></a>Uzaktan test ortamını ayarlama

Ortamlar `testenvironments.json` , çözümünüzün kökünde kullanılarak belirtilir. JSON dosya yapısı, burada açıklanan şemayı izler:
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

Yerel olarak çalışan bir kapsayıcıya bağlanmak için yerel makinenizde [Docker Desktop](https://www.docker.com/products/docker-desktop) 'a sahip olmanız gerekir. İsteğe bağlı olarak, daha iyi performans için [WSL2 tümleştirmesini etkinleştirin](/windows/wsl/install-win10) .

Dockerfile için, ortam `testEnvironments.json` çözümünüzün kökünde içinde belirtilebilir. Burada açıklanan özellikleri kullanır.
```json
    {
    "name": "<name>",
    "localRoot": "<path to local environment>", // optional
    "type": "docker",
    "dockerImage": "<docker image tag>",
    }
```

Aşağıdaki örnekte `testenvironments.json` adlı yerel bir kapsayıcı görüntüsü gösterilmektedir \<mcr.microsoft.com/dotnet/core/sdk\> .
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

Aşağıdaki örnekte, .NET 5,0 ' i hedefleyen testlerin çalıştırılması için bir Dockerfile gösterilmektedir. İkinci satır, hata ayıklayıcının kapsayıcınıza bağlanıp çalıştırmasına emin olur.
```
FROM mcr.microsoft.com/dotnet/core/sdk:5.0

RUN wget https://aka.ms/getvsdbgsh && \
    sh getvsdbgsh -v latest  -l /vsdbg
```

Kapsayıcının yerel makinenizde oluşturulmuş bir görüntüsü olmalıdır. Aşağıdaki komutu kullanarak bir kapsayıcı oluşturabilirsiniz (sonunda "." de dahil): `docker build -t <docker image name> -f <path to Dockerfile> .`

### <a name="local-wsl2-connections"></a>Yerel WSL2 bağlantıları
Testleri WSL2 üzerinde uzaktan çalıştırmak için yerel makinenizde [WSL2 tümleştirmesini etkinleştirmeniz](/windows/wsl/install-win10) gerekir.

Ortam, `testEnvironments.json` çözümünüzün kökünde, aşağıdaki şemayı kullanarak ve \<Ubuntu\> yüklemiş olduğunuz HERHANGI bir WSL2 dağıtımı ile değiştirilerek belirlenebilir.
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
 **Araçlar > seçeneklerinde, platformlar arası > bağlantı yöneticisi >** SSH bağlantıları ekleyebilir veya kaldırabilirsiniz. "Ekle" seçeneğinin belirlenmesi, ana bilgisayar adı, bağlantı noktası ve ihtiyacınız olan tüm kimlik bilgilerini girmenize olanak sağlar.

Ortam, `testEnvironments.json` çözümünüzün kökünde, aşağıdaki şemayı kullanarak belirtilebilir ve bunu `\<ssh://user@hostname:22\>` SSH remoteUri 'niz ile değiştirerek.
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

#### <a name="prerequisites-for-a-remote-windows-environment"></a>uzak Windows ortamı önkoşulları
1. [Windows tasarlanan dosya sisteminin](/windows/win32/projfs/enabling-windows-projected-file-system) etkinleştirildiğinden emin olun. Bunu etkinleştirmek için bir yönetici PowerShell penceresinden şunları çalıştırabilirsiniz:

   ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Client-ProjFS -NoRestart
   ```

   Gerekirse, lütfen ortamı yeniden başlatın.
2. SSH ayarının ayarlandığından emin olun. [OpenSSH 'Yi Install](/windows-server/administration/openssh/openssh_install_firstuse#install-openssh-using-powershell)adımlarını gözden geçirebilirsiniz. Bir yönetici PowerShell penceresinde aşağıdaki komutu çalıştırarak SSH sunucusunu başlatın:
   ```powershell
   Start-Service sshd
   ```

3. Testleriniz için gerekli olan uygun .NET çalışma zamanının yüklü olduğundan emin olun. İndirilenler [burada](https://dotnet.microsoft.com/download)bulunabilir.
4. Testlerin hata ayıklaması için:
   1. Uzak [Araçlar SKU](/visualstudio/debugger/remote-debugging?view=vs-2022&preserve-view=true) 'sunu uzak ortama lütfen yüklersiniz. 
   2. Uzaktan hata ayıklayıcıyı yönetici olarak başlatın ve VS kullanıcısının bağlanma izinlerine sahip olduğundan emin olun.

#### <a name="prerequisites-for-a-remote-linux-environment"></a>Uzak Linux ortamı için Önkoşullar
1. SSH 'nin yapılandırıldığından ve çalıştığından emin olun.
2. `fuse3`Paket Yöneticisi kullanarak yükler.
3. Testlerinizin gerektirdiği uygun .NET çalışma zamanının uzak ortamda yüklü olduğundan emin olun.

## <a name="use-the-test-explorer-to-run-and-debug-remote-tests"></a>Test Gezginini kullanarak uzak testleri çalıştırma ve hatalarını ayıklama
* Etkin ortam, test Gezgini araç çubuğunda açılan bir açılır pencere aracılığıyla seçilir. Şu anda tek seferde yalnızca bir test ortamı etkin olabilir.

  ![Test Gezgini 'nde uzaktan test ortamı açılır](media/remote-test-drop-down.png)

* Bir ortam seçildikten sonra, testler yeni ortamda keşfedilir ve çalıştırılır.

  ![Testler uzak ortamlarda keşfedilir ve yürütülür](media/remote-test-linux-discovery.png)

* Artık testlerinizi uzak ortamda çalıştırabilir ve testlerde ortamınızda hata ayıklaması yapabilirsiniz!

  ![Test Gezgini 'nde uzak ortamdan test sonuçlarını görüntüleme](media/remote-test-linux-passing.png)

* Test Gezgini, bazı eksik ortam önkoşullarını yüklemenizi ve eksik bağımlılıkları yüklemeyi denemesini isteyebilir. Ancak, uzak ortamı sağlamanın toplu işlemi, kullanıcının belirtimine göre yapılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
