---
title: Dağıtımları yönelik güncelleştirmeleri denetleme
description: Burada bir ağdan yüklediğinizde Visual Studio güncelleştirmesi görünümünü değiştirme konusunda bilgi edinin.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2cdf4d4e6fb90b18c8141d1d176629539a0a4f8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570589"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme

Kurumsal yöneticiler genellikle bir düzen oluşturmak ve kendi son kullanıcılara dağıtmak için bir ağ dosya paylaşımında bir ana bilgisayar.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio güncelleştirmeleri nerede arar denetleme

Varsayılan olarak, Visual Studio yükleme bir ağ paylaşımından olsa bile güncelleştirmeleri çevrimiçi ara devam eder. Bir güncelleştirme varsa, kullanıcı bunu yükleyebilirsiniz. Web'den çevrimdışı düzeninde bulunamadı güncelleştirilmiş içerik indirildi.

Visual Studio güncelleştirmeleri nerede arar üzerinde doğrudan denetim istiyorsanız, nerede göründüğüne konumu değiştirebilirsiniz. Kullanıcılarınız için güncelleştirilmiş sürümü de denetleyebilirsiniz. Bunu yapmak için aşağıdaki adımları izleyin:

1. Çevrimdışı bir düzen oluşturma:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Sitemi barındırmak istediğiniz dosya paylaşımına kopyalayın:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Düzeni ve değişiklik response.json dosyasında değişiklik `channelUri` yönetim denetimleri channelManifest.json bir kopyasına işaret edecek şekilde değeri.

   Aşağıdaki örnekte olduğu gibi değeri ters eğik çizgi kaçış emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılara bu paylaşımdan Visual Studio'yu yüklemek için kurulumu çalıştırabilirsiniz.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Kuruluş Yöneticisi Visual Studio'nun daha yeni bir sürüme güncelleştirmek kullanıcıları için zaman olduğunu belirlediğinde, yapabilirler [düzen konumunu güncelleştirme](update-a-network-installation-of-visual-studio.md) güncelleştirilmiş dosyaları gibi birleştirmek için.

1. Aşağıdaki komutu benzeyen bir komut kullanın:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Güncelleştirilmiş düzenini response.json dosyasında yine de özellikle Channelurı değişiklik, özelleştirmelerinizi gibi içerdiğinden emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Varolan bir Visual Studio yükler güncelleştirmeleri bu düzen arayın gelen `\\server\share\VS\ChannelManifest.json`. Visual Studio channelManifest.json kullanıcı yüklü olduğu daha yeniyse, bir güncelleştirme kullanılabilir kullanıcıya bildirir.

   Yeni yüklemeler, düzenden doğrudan Visual Studio'nun güncelleştirilmiş sürümü otomatik olarak yükler.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE'de bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı gibi Visual Studio içinden, bir ağ paylaşımına veya herhangi bir güncelleştirme kullanılabilir olup olmadığını görmek için Internet gibi yüklenmiş olduğu konum denetler. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio pencerenin sağ üst köşesinde bir bildirim bayrağı ile kullanıcıyı uyarır.

   ![Güncelleştirmeleri için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Daha önce açıklandığı gibi Visual Studio içinden, bir ağ paylaşımına veya herhangi bir güncelleştirme kullanılabilir olup olmadığını görmek için Internet gibi yüklenmiş olduğu konum denetler. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio kullanıcıya pencerenin sağ alt köşesinde bir bildirim simgesiyle bilgilendirir.

   ![Visual Studio IDE 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE 'deki bildirim simgesi")

::: moniker-end

Son kullanıcılar, güncelleştirmeleri almak istemiyorsanız bildirimleri devre dışı bırakabilirsiniz. (Örneğin, güncelleştirmeleri bir yazılım merkezi dağıtım mekanizması teslim ediyorsanız bildirimleri devre dışı bırakmak isteyebilirsiniz.)

::: moniker range="vs-2017"

Çünkü Visual Studio 2017 [kayıt defteri girdileri özel bir kayıt defterinde depolar](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), normal şekilde kayıt defterini doğrudan düzenleyemezsiniz. Ancak, Visual Studio içeren bir `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz yardımcı programı. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019, [kayıt defteri girdilerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio içeren bir `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz yardımcı programı. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Dizin düzenlemek istediğiniz yüklü örnekle eşleşecek şekilde değiştirdiğinizden emin olun.)

> [!TIP]
> Kullanım [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) istemci iş istasyonunda Visual Studio'nun belirli bir örneği bulunamadı.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini yönetmek için Araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
