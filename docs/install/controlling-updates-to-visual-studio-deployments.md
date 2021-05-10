---
title: Dağıtım güncelleştirmelerini denetleme
description: Ağdan yükleme Visual Studio güncelleştirmenin nerede göründüğünü nasıl değiştiryebilirsiniz?
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3504e866a7f89de8fa38f92a8bfea501ddd952c9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666802"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme

Kuruluş yöneticileri genellikle bir düzen oluşturabilir ve bunu son kullanıcılarına dağıtmak için bir ağ dosya paylaşımında barındırır. Bu sayfada ağ düzeni seçeneklerinizin nasıl düzgün yapılandırıldığından emin olun. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Güncelleştirmelerin Visual Studio denetleme

**Senaryo 1: İstemci başlangıçta bir düzenden yüklenir, ancak ağ düzeni konumdan veya web'den güncelleştirmeleri alacak şekilde yapılandırılır**

Varsayılan olarak, Visual Studio başlangıçta bir ağ paylaşımından dağıtılmış olsa bile güncelleştirmeleri çevrimiçi olarak aramaya devam eder. Web'de bir güncelleştirme varsa, kullanıcı bunu yükleyebilir. Ağ düzeni önbelleği ilk olarak güncelleştirilmiş ürün bitleri için incelense de, bunlar orada bulunamasa Visual Studio güncelleştirilmiş ürün bitlerini web'den alır ve indirir.

**Senaryo 2: İstemci başlangıçta yüklenmiştir ve yalnızca ağ düzeninden güncelleştirmeleri al olmalıdır**

Visual Studio istemcisinin güncelleştirmeleri nerede aray olduğunu kontrol etmek için, örneğin istemci makinenizin İnternet erişimi yoksa ve yalnızca ve her zaman düzenden yükleniyor olduğundan emin olmak istiyorsanız, istemci yükleyicisi güncelleştirilmiş ürün bitlerini arama konumunu yapılandırabilirsiniz. İstemci düzenden ilk yüklemeyi yapmadan önce bu ayarın doğru yapılandırıldığından emin olmak en iyisidir. 

1. Çevrimdışı düzen oluşturma:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Bunu barındırmak istediğiniz dosya paylaşımına kopyalayın:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Düzende dosyasını değiştirebilir ve değeri yöneticinin denetiminde olduğu channelManifest.js`response.json` `channelUri` kopyaya işaret etmek için değiştirebilirsiniz.

   Aşağıdaki örnekte olduğu gibi değerde kaçış tireleri olduğundan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılar bu paylaşımdan kurulumu çalıştırarak Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Bir Kurumsal Yönetici, kullanıcıların Visual Studio 'nun daha yeni bir sürümüne güncelleştirilmesi için zaman olduğunu belirlediğinde, [Düzen konumunu](update-a-network-installation-of-visual-studio.md) güncelleştirilmiş dosyaları içerecek şekilde güncelleştirebilir.

1. Aşağıdaki komuta benzer bir komut kullanın:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. `response.json`Güncelleştirilmiş düzendeki dosyanın özelleştirmelerinizi, özellikle de channelUri değişikliğini şu şekilde içerdiğinden emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Bu düzenden var olan Visual Studio yüklemeleri, ' de güncelleştirmeleri arar `\\server\share\VS\ChannelManifest.json` . channelManifest.js, kullanıcının yüklemiş olduğu sürümden daha yeniyse, Visual Studio kullanıcıya bir güncelleştirme olduğunu bildirir.

İstemciden başlatılan tüm yükleme güncelleştirmeleri otomatik olarak Visual Studio 'nun güncelleştirilmiş sürümünü doğrudan düzenden yükler.

**Senaryo 3: Istemci, başlangıçta Web 'den yüklendi, ancak şimdi yalnızca bir ağ düzeninden güncelleştirmeler almalıdır**

Bazı durumlarda, istemci makinesi Web 'den Visual Studio 'Yu zaten yüklemiş olabilir, ancak artık yönetici, gelecekteki tüm güncelleştirmelerin yönetilen bir düzenden gelmesini istiyor. Bunu yapmanın tek yolu, ürünün istenen sürümüne sahip bir ağ düzeni oluşturmak ve ardından istemci makinesinde, önyükleyici _konumundan_ (ör.), önyükleyiciyi çalıştırmanız için desteklenir `\\server\share\vs_enterprise.exe` . İdeal olarak, özgün istemci yüklemesi, doğru şekilde yapılandırılmış ChannelURI ile ağ düzeninden önyükleyici kullanılarak gerçekleşmiş olur, ancak güncelleştirilmiş önyükleyici ağ düzeni konumundan çalıştırılarak da çalışır. Bu eylemlerden biri, söz konusu düzen konumuyla bir bağlantı olan istemci makinesine katıştırılabilir. Bu senaryonun doğru çalışması için tek desteklenmediği uyarısıyla, düzen dosyasındaki "Channelurı" nin, `response.json` özgün yüklemenin gerçekleştiği sırada istemcinin makinesinde ayarlanmış olan channelurı ile aynı olması gerekir. Büyük olasılıkla bu değer ilk olarak Internet [Release kanalına](https://aka.ms/vs/16/release/channel)ayarlanmıştır. 


## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE 'de bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı Visual Studio, güncelleştirmelerin kullanılabilir olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ üst köşesindeki bildirim bayrağını kullanıcıya iletir.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019&quot;

Daha önce açıklandığı Visual Studio, güncelleştirmelerin kullanılabilir olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ alt köşesindeki bildirim simgesiyle kullanıcıya bunu bildirebilirsiniz.

   ![Visual Studio IDE'de bildirim simgesi](media/vs-2019/notification-bar.png &quot;Visual Studio IDE 'deki bildirim simgesi")

::: moniker-end

Son kullanıcılara güncelleştirmelerin bildirilmesi istemiyorsanız bildirimleri devre dışı abilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması aracılığıyla teslim ediyorsanız bildirimleri devre dışı bırakmak istiyor olabilirsiniz.)

::: moniker range="vs-2017"

2017 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

2019 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Dizini düzenlemek istediğiniz yüklü örnekle eş olacak şekilde değiştir emin olun.)

> [!TIP]
> İstemci [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) iş istasyonundaki belirli bir Visual Studio örneğini bulmak için Visual Studio kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Örneklerde Visual Studio araçları](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
