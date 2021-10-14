---
title: Dağıtım güncelleştirmelerini denetleme
description: Ağdan yükleme Visual Studio güncelleştirmenin nerede göründüğünü nasıl değiştiryebilirsiniz?
ms.date: 04/06/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2a4e123e83ab8e6adbc23998a0c927e1f9e98bc0
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969508"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme

Enterprise yöneticiler genellikle bir düzen oluşturabilir ve bunu son kullanıcılarına dağıtmak için bir ağ dosya paylaşımında barındırır. Bu sayfada ağ düzeni seçeneklerinizin nasıl düzgün yapılandırıldığından emin olun.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Güncelleştirmelerin Visual Studio denetleme

**Senaryo 1: İstemci başlangıçta bir düzenden yüklenmiştir, ancak ağ düzeni konumdan veya web'den güncelleştirmeleri alacak şekilde yapılandırılmıştır**

Varsayılan olarak, Visual Studio başlangıçta bir ağ paylaşımından dağıtılmış olsa bile güncelleştirmeleri çevrimiçi aramaya devam eder. Web'de bir güncelleştirme varsa, kullanıcı bunu yükleyebilir. Ağ düzeni önbelleği ilk olarak güncelleştirilmiş ürün bitleri için incelense de, bunlar orada bulunamasa Visual Studio güncelleştirilmiş ürün bitlerini web'den alır ve indirir.

**Senaryo 2: İstemci başlangıçta yüklenmiştir ve yalnızca ağ düzeninden güncelleştirmeleri al olmalıdır**

Visual Studio istemcisinin güncelleştirmeleri nerede aray olduğunu kontrol etmek için, örneğin istemci makinenizin İnternet erişimi yoksa ve yalnızca ve her zaman düzenden yükleniyor olduğundan emin olmak için istemci yükleyicinin güncelleştirilmiş ürün bitlerini aray bulunduğu konumu yapılandırabilirsiniz. İstemci düzenden ilk yüklemeyi yapmadan önce bu ayarın doğru yapılandırıldığından emin olmak en iyisidir.

1. Çevrimdışı düzen oluşturma:

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Bunu barındırmak istediğiniz dosya paylaşımına kopyalayın:

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Düzende dosyasını ve değerini, yöneticinin denetiminde olduğu `response.json` `channelUri` channelManifest.json kopyasına işaret etmek için değiştirebilirsiniz.

   Aşağıdaki örnekte olduğu gibi değerde kaçış tireleri olduğundan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılar kurulumu bu paylaşımdan çalıştırarak Visual Studio.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

Kuruluş yöneticisi, kullanıcılarının yeni bir Visual Studio sürümüne güncelleştirme zamanı olduğunu belirlerken, düzen konumunu güncelleştirilmiş dosyaları dahil etmek için aşağıdaki gibi güncelleştirebilirler. [](update-a-network-installation-of-visual-studio.md)

1. Aşağıdaki komuta benzer bir komut kullanın:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Güncelleştirilmiş `response.json` düzende dosyanın, özellikle channelUri değişikliği gibi özelleştirmelerinizi hala içerdiğini emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Bu Visual Studio mevcut uygulama yüklemeleri, 'de güncelleştirmeleri `\\server\share\VS\ChannelManifest.json` bakar. channelManifest.json, kullanıcının yüklemiş olduğu yüklemeden daha yeniyse Visual Studio bir güncelleştirmenin kullanılabilir olduğunu kullanıcıya iletir.

İstemciden başlatılan herhangi bir yükleme güncelleştirmesi, güncelleştirme sürümünü Visual Studio doğrudan düzenden yükleyebilir.

**Senaryo 3: İstemci başlangıçta web'den yüklenmiştir, ancak şimdi yalnızca bir ağ düzeninden güncelleştirmeleri alsa**

Bazı durumlarda istemci makinesi web'den Visual Studio yüklemiş olabilir, ancak şimdi yönetici gelecekteki tüm güncelleştirmelerin yönetilen bir düzenden gelecek şekilde güncelleştirmeyi istiyor. Bunu yapmak için desteklenen tek yol, ürünün istenen sürümüyle bir ağ düzeni oluşturmak ve ardından istemci makinede düzen _konumdan_ (ör. ) önyükleyiciyi `\\server\share\vs_enterprise.exe` çalıştırmaktır. İdeal olarak, özgün istemci yüklemesi doğru yapılandırılmış ChannelURI ile ağ düzeninden önyükleyici kullanılarak güncelleştirilir, ancak güncelleştirilmiş önyükleyiciyi ağ düzeni konumdan çalıştırma da çalışır. Bu eylemlerden biri, istemci makinesine, bu düzen konumuyla bir bağlantı katıştırabilirsiniz. Bu senaryonun doğru çalışması için tek uyarı, düzenin dosyasındaki "ChannelURI"nin, özgün yükleme olduğunda istemcinin makinesine ayarlanmış ChannelURI ile aynı `response.json` olmasıdır. Büyük olasılıkla bu değer başlangıçta İnternet yayın [kanalına ayarlanmıştır.](https://aka.ms/vs/16/release/channel)

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE'de bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı Visual Studio, güncelleştirme olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ üst köşesindeki bildirim bayrağını kullanıcıya bildirebilirsiniz.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

Daha önce açıklandığı Visual Studio, güncelleştirme olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ alt köşesindeki bildirim simgesiyle kullanıcıya bunu bildirebilirsiniz.

   ![Visual Studio IDE'de bildirim simgesi](media/vs-2019/notification-bar.png &quot;Visual Studio IDE'de bildirim simgesi")

::: moniker-end

Son kullanıcılara güncelleştirmeler hakkında bildirim verilmesini istemiyorsanız bildirimleri devre dışı abilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması aracılığıyla teslim ediyorsanız bildirimleri devre dışı bırakmak istiyor olabilirsiniz.)

::: moniker range="vs-2017"

2017 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

2019 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

2022 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Dizini düzenlemek istediğiniz yüklü örnekle eş olacak şekilde değiştir emin olun.)

> [!TIP]
> İstemci [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) iş istasyonunda belirli bir Visual Studio örneğini bulmak için Visual Studio kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Örneklerde Visual Studio araçları](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
