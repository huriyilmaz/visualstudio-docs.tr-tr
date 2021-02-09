---
title: Dağıtımlara yönelik güncelleştirmeleri denetleme
description: Bir ağdan yüklerken, Visual Studio 'Nun bir güncelleştirmeye baktığı yeri değiştirmeyi öğrenin.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ffa088de8852b0d5884cd4d9db5e65e1c179164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868549"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme

Kurumsal Yöneticiler genellikle son kullanıcılara dağıtmak üzere bir düzen oluşturup bir ağ dosya paylaşımında barındırır.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio 'Nun güncelleştirmelerin nerede göründüğünü denetleme

Varsayılan olarak, yükleme bir ağ paylaşımından dağıtılsa bile Visual Studio güncelleştirmeler için çevrimiçi görünmeye devam eder. Bir güncelleştirme varsa, Kullanıcı bunu yükleyebilir. Çevrimdışı düzende bulunmayan güncelleştirilmiş içerikler Web 'den indirilir.

Visual Studio 'Nun güncelleştirmeleri aradığı yerde doğrudan denetim istiyorsanız, konumunu değiştirmek için değişiklik yapabilirsiniz. Kullanıcılarınızın güncelleştirilme sürümünü de denetleyebilirsiniz. Bunu yapmak için aşağıdaki adımları izleyin:

1. Çevrimdışı düzen oluşturma:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Onu barındırmak istediğiniz dosya paylaşımında kopyalayın:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Düzendeki dosyadaki response.jsdeğiştirin ve `channelUri` değeri yönetici denetimlerinde channelManifest.jsbir kopyasına işaret etmek üzere değiştirin.

   Aşağıdaki örnekte olduğu gibi, değerde ters eğik çizgileri attığınızdan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılar Visual Studio 'Yu yüklemek için bu paylaşımdan kurulum 'u çalıştırabilir.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Bir Kurumsal Yönetici, kullanıcıların Visual Studio 'nun daha yeni bir sürümüne güncelleştirilmesi için zaman olduğunu belirlediğinde, [Düzen konumunu](update-a-network-installation-of-visual-studio.md) güncelleştirilmiş dosyaları içerecek şekilde güncelleştirebilir.

1. Aşağıdaki komuta benzer bir komut kullanın:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Güncelleştirilmiş düzendeki dosyadaki response.js, özelleştirmelerinizi, özellikle de channelUri değişikliğini şu şekilde içerdiğinden emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Bu düzenden var olan Visual Studio yüklemeleri, ' de güncelleştirmeleri arar `\\server\share\VS\ChannelManifest.json` . channelManifest.js, kullanıcının yüklemiş olduğu sürümden daha yeniyse, Visual Studio kullanıcıya bir güncelleştirme olduğunu bildirir.

   Yeni Yüklemeler, Visual Studio 'nun güncelleştirilmiş sürümünü doğrudan düzenden otomatik olarak yükler.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE 'de bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı gibi, Visual Studio herhangi bir güncelleştirmenin kullanılabilir olup olmadığını görmek için bir ağ veya Internet gibi yüklendiği Konumu kontrol eder. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio kullanıcıya pencerenin sağ üst köşesinde bir bildirim bayrağı bildirir.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Daha önce açıklandığı gibi, Visual Studio herhangi bir güncelleştirmenin kullanılabilir olup olmadığını görmek için bir ağ veya Internet gibi yüklendiği Konumu kontrol eder. Bir güncelleştirme kullanılabilir olduğunda, Visual Studio kullanıcıya pencerenin sağ alt köşesinde bir bildirim simgesiyle bilgilendirir.

   ![Visual Studio IDE 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE 'deki bildirim simgesi")

::: moniker-end

Son kullanıcılara güncelleştirmelerin bildirilmesini istemiyorsanız bildirimleri devre dışı bırakabilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması üzerinden sunmanız durumunda bildirimleri devre dışı bırakmak isteyebilirsiniz.)

::: moniker range="vs-2017"

Visual Studio 2017, [kayıt defteri girdilerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. Ancak Visual Studio, `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Aşağıdaki komutla bildirimleri devre dışı bırakabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019, [kayıt defteri girdilerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. Ancak Visual Studio, `vsregedit.exe` Visual Studio ayarlarını değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Aşağıdaki komutla bildirimleri devre dışı bırakabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Dizini, düzenlemek istediğiniz yüklü örnekle eşleşecek şekilde değiştirdiğinizden emin olun.)

> [!TIP]
> Bir istemci iş istasyonunda belirli bir Visual Studio örneğini bulmak için [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
