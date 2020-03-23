---
title: Dağıtımlar için denetim güncelleştirmeleri
description: Bir ağdan yüklediğinizde Visual Studio'nun güncelleştirmeyi nerede aradığınızı nasıl değiştireceğinizi öğrenin.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115317"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri

Kurumsal yöneticiler genellikle bir düzen oluşturur ve son kullanıcılarına dağıtmak için bir ağ dosyası paylaşımında barındırAbilir.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio'nun güncellemeleri nerede aradığına bakma

Varsayılan olarak, Visual Studio yükleme bir ağ paylaşımından dağıtılmış olsa bile güncelleştirmeleri çevrimiçi aramaya devam eder. Bir güncelleştirme varsa, kullanıcı bunu yükleyebilir. Çevrimdışı düzende bulunmayan güncelleştirilmiş içerikler web'den indirilir.

Visual Studio'nun güncelleştirmeleri nerede aradığı üzerinde doğrudan denetim istiyorsanız, konumu göründüğü yerde değiştirebilirsiniz. Kullanıcılarınızın güncelleştirilebildiği sürümü de denetleyebilirsiniz. Bunu yapmak için şu adımları uygulayın:

1. Çevrimdışı düzen oluşturun:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Barındırmak istediğiniz dosya paylaşımına kopyalayın:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Düzendeki yanıt.json dosyasını değiştirin `channelUri` ve değeri yöneticinin denetledığı channelManifest.json'Un bir kopyasına işaret edecek şekilde değiştirin.

   Aşağıdaki örnekte olduğu gibi, değerdeki ters eğik çizgilerden kurtulduğundan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılar Visual Studio'yı yüklemek için bu paylaşımdan kurulum çalıştırabilir.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Bir kuruluş yöneticisi, kullanıcılarının Visual Studio'nun daha yeni bir sürümüne güncelleştirme zamanının geldiğini belirlediğinde, güncelleştirilen dosyaları aşağıdaki gibi birleştirmek için [düzen konumunu güncelleştirebilir.](update-a-network-installation-of-visual-studio.md)

1. Aşağıdaki komuta benzer bir komut kullanın:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Güncelleştirilmiş düzendeki yanıt.json dosyasının, özellikle channelUri modifikasyonu olmak üzere özelleştirmelerinizi aşağıdaki gibi içerdiğinden emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Varolan Visual Studio bu düzenden `\\server\share\VS\ChannelManifest.json`yükler güncellemeleri için bakmak. ChannelManifest.json kullanıcının yüklediği yüklenmeden daha yeniyse, Visual Studio kullanıcıya bir güncelleştirmenin kullanılabilir olduğunu belirtir.

   Yeni yüklemeler Visual Studio'nun güncelleştirilmiş sürümünü doğrudan düzenden otomatik olarak yükler.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE'deki bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı gibi, Visual Studio herhangi bir güncelleştirme olup olmadığını görmek için ağ paylaşımı veya internet gibi yüklendiği konumu denetler. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio pencerenin sağ üst köşesinde bir bildirim bayrağı ile kullanıcıbildirir.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Daha önce açıklandığı gibi, Visual Studio herhangi bir güncelleştirme olup olmadığını görmek için ağ paylaşımı veya internet gibi yüklendiği konumu denetler. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio pencerenin sağ alt köşesinde bir bildirim simgesi ile kullanıcıbildirir.

   ![Visual Studio IDE'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE'deki bildirim simgesi")

::: moniker-end

Son kullanıcıların güncelleştirmelerden haberdar olmasını istemiyorsanız bildirimleri devre dışı kullanabilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması aracılığıyla teslim ederseniz bildirimleri devre dışı kılabilir.)

::: moniker range="vs-2017"

Visual Studio 2017 [kayıt defteri girişlerini özel bir kayıt defterine depoladığı](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)için, kayıt defterini tipik bir şekilde doğrudan olarak kaldıramazsınız. Ancak, Visual Studio `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Bildirimleri aşağıdaki komutla kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 [kayıt defteri girişlerini özel bir kayıt defterine depoladığı](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)için, kayıt defterini tipik bir şekilde doğrudan olarak kaldıramazsınız. Ancak, Visual Studio `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Bildirimleri aşağıdaki komutla kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Yüklemek istediğiniz yüklü örneği eşleştirmek için dizini değiştirdiğinden emin olun.)

> [!TIP]
> Bir istemci iş istasyonunda Visual Studio'nun belirli bir örneğini bulmak için [vswhere.exe'yi](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini yönetme araçları](tools-for-managing-visual-studio-instances.md)
* [Visual Studio ürün yaşam döngüsü ve servis](/visualstudio/releases/2019/servicing/)
