---
title: Dağıtımlara yönelik güncelleştirmeleri denetleme
description: Bir ağdan yüklerken, Visual Studio 'Nun bir güncelleştirmeye baktığı yeri değiştirmeyi öğrenin.
ms.date: 04/06/2021
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
ms.openlocfilehash: 8360c48e9868f6ed5d81fffc748d050404211228
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547498"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme

Kurumsal Yöneticiler genellikle bir düzen oluşturup son kullanıcılarına dağıtmak üzere bir ağ dosya paylaşımında barındırır. Bu sayfada, ağ düzeni seçeneklerinizi doğru şekilde yapılandırma açıklanmaktadır. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio 'Nun güncelleştirmelerin nerede göründüğünü denetleme

**Senaryo 1: Istemci bir düzenden başlangıçta yüklendi, ancak ağ düzeni konumundan veya Web 'den güncelleştirmeleri alacak şekilde yapılandırıldı**

Varsayılan olarak, yükleme ilk olarak bir ağ paylaşımından dağıtılsa bile Visual Studio güncelleştirmeler için çevrimiçi görünmeye devam eder. Web üzerinde bir güncelleştirme varsa, Kullanıcı bunu yükleyebilir. Ağ düzeni önbelleği, güncelleştirilmiş herhangi bir ürün bitleri için ilk olarak incelense de, burada bulunmazsa Visual Studio, güncelleştirilmiş ürün bitlerini Web 'den bulup indirir.

**Senaryo 2: Istemci başlangıçta yüklendi ve yalnızca ağ düzeninden güncelleştirmeleri almalıdır**

Visual Studio istemcisinin güncelleştirmeleri nerede kurduğunu denetlemek istiyorsanız, örneğin, istemci makineniz Internet erişimine sahip değilse ve yalnızca ve her zaman düzenden yüklenmesini sağlamak istiyorsanız, istemci yükleyicisinin güncelleştirilmiş ürün bitlerini aradığı konumu yapılandırabilirsiniz. Bu ayarın, istemci düzenden ilk yüklemeyi yapmadan önce doğru şekilde yapılandırıldığından emin olmak en iyisidir. 

1. Çevrimdışı düzen oluşturma:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Onu barındırmak istediğiniz dosya paylaşımında kopyalayın:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. `response.json`Düzendeki dosyayı değiştirin ve `channelUri` değeri yönetici denetimlerinde channelManifest.jsbir kopyasına işaret etmek üzere değiştirin.

   Aşağıdaki örnekte olduğu gibi, değerde ters eğik çizgileri attığınızdan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Şimdi, son kullanıcılar Visual Studio 'Yu yüklemek için bu paylaşımdan kurulum 'u çalıştırabilir.

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

Bazı durumlarda, istemci makinesi Web 'den Visual Studio 'Yu zaten yüklemiş olabilir, ancak artık yönetici, gelecekteki tüm güncelleştirmelerin yönetilen bir düzenden gelmesini istiyor. Bunu yapmanın tek yolu, ürünün istenen sürümüne sahip bir ağ düzeni oluşturmak ve ardından istemci makinesinde, önyükleyici _konumundan_ (ör.), önyükleyiciyi çalıştırmanız için desteklenir `\\network\share\vs_enterprise.exe` . İdeal olarak, özgün istemci yüklemesi, doğru şekilde yapılandırılmış ChannelURI ile ağ düzeninden önyükleyici kullanılarak gerçekleşmiş olur, ancak güncelleştirilmiş önyükleyici ağ düzeni konumundan çalıştırılarak da çalışır. Bu eylemlerden biri, söz konusu düzen konumuyla bir bağlantı olan istemci makinesine katıştırılabilir. Bu senaryonun doğru çalışması için tek desteklenmediği uyarısıyla, düzen dosyasındaki "Channelurı" nin, `response.json` özgün yüklemenin gerçekleştiği sırada istemcinin makinesinde ayarlanmış olan channelurı ile aynı olması gerekir. Büyük olasılıkla bu değer ilk olarak Internet [Release kanalına](https://aka.ms/vs/16/release/channel)ayarlanmıştır. 


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

* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmeleri uygulanıyor](applying-administrator-updates.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
