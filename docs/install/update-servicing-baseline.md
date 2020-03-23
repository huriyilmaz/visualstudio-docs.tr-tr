---
title: Bakım temeli sırasında Visual Studio’yu güncelleştirme
description: Servis taban çizgisinde kalırken Visual Studio'yı nasıl güncelleştirteceklerini öğrenin.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9f31a3f7ae5e0e0ca4150d88870b9e48493bffcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114967"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Bakım temeli sırasında Visual Studio’yu güncelleştirme

Visual Studio'yı ürün yaşam döngüsü sırasında sık sık güncelliyoruz. İki tür güncelleştirme vardır: 

* **Minor release updates**&mdash;Örneğin, yeni özellikler ve bileşenler içeren 16.0 ile 16.1&mdash;küçük sürüm güncelleştirmeleri.  
* **Yalnızca**kritik sorunlar için hedeflenen düzeltmeleri içeren (örneğin, 16.0.4 ila 16.0.5) hizmet güncelleştirmeleri.

Kurumsal yöneticiler, istemcilerini hizmet taban çizgisinde tutmayı seçebilirler. Servis taban çizgisi, bir sonraki hizmet taban çizgisinin yayımlanmasından önceki bir yıl boyunca servis güncelleştirmeleriyle desteklenir.

Servis taban çizgisi seçeneği, geliştiricilere ve yöneticilere yeni küçük güncelleştirmelerde bulunan yeni özellikleri, hata düzeltmelerini veya bileşenleri benimsemeleri için daha fazla esneklik sağlar. İlk servis taban çizgisi 16.0.x'tir. Daha fazla bilgi [için, kurumsal ve profesyonel müşteriler için Destek seçeneklerine](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)bakın.

## <a name="how-to-get-onto-a-servicing-baseline"></a>Servis taban çizgisine nasıl ulaşılabilirsiniz?

Servis taban çizgisini kullanmaya başlamak için, [My.VisualStudio.com'dan](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)sabit sürüm Visual Studio yükleyici bootstrapper indirin. Bootstrappers ürün yapılandırmaları, iş yükleri ve belirli bir sürüm için bileşenleri bağlantılar var.

> [!NOTE]
> Sabit sürüm bootstrapper ve standart bootstrappers arasında ayrım yapmaya dikkat edin. Standart bootstrappers Visual Studio en son sürümü kullanmak için yapılandırılmıştır. Standart boostrappers dosya adı (örneğin, vs_enterprise__123456789-123456789.exe) onlar My.VisualStudio.com indirilen bir numara var.

Yükleme sırasında, kurumsal yöneticilerin istemcilerin en son sürüme güncellenmesini önlemek için istemcilerini yapılandırmaları gerekir. Bunu yapmanın birkaç yolu vardır:
- Düzende veya yerel klasörde bir kanal bildirimi kullanmak için [yanıt yapılandırma dosyasındaki `channelUri` ayarı değiştirin.](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network)
- Var olmayan bir dosyayı kullanmak için [channelUri'yi komut satırı yürütme yoluyla değiştirin.](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet)
- [İstemci sistemindeki ilkeleri, istemcilerin](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)kendi kendini güncelleştirmesini önlemek için güncelleştirmeleri devre dışı bırakabilmek için ayarlayın.

### <a name="install-a-servicing-baseline-on-a-network"></a>Ağa servis taban çizgisi yükleme

Ağ düzeni yüklemesi kullanan `channelUri` yöneticiler, aynı klasördeki *channelmanifest.json* dosyasını kullanmak için düzendeki *yanıt.json* dosyasındaki değeri değiştirmelidir. Atılacak adımlar [için, ağ tabanlı Visual Studio dağıtımlarında Denetim güncelleştirmelerine](controlling-updates-to-visual-studio-deployments.md)bakın. Değeri `channelUri` değiştirmek, istemcilerin düzen konumundagüncelleştirmeleri aramasını sağlar.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Internet üzerinden servis taban çizgisi yükleme

Internet tabanlı yükleme için, `--channelUri` kurulum başlatmak için kullanılan komut satırına var olmayan bir kanal bildirimi ekleyin. Bu, Visual Studio'nun bir güncelleştirme için mevcut en son sürümü kullanmasını devre dışı kılabilir. Bir örneği aşağıda verilmiştir:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>İstemcileri güncelleştirmeyi devre dışı kalmak için ilke ayarlarını kullanma

İstemci deki güncelleştirmeleri denetlemek için başka bir seçenek de [güncelleştirme bildirimlerini kapatmaktır.](controlling-updates-to-visual-studio-deployments.md) Yüklemede channelUri değeri değiştirilmediyse bu seçeneği kullanın. İstemciyi en son sürümdeki bağlantıları almaktan devre dışı bırakacaktır. Sabit sürüm bootstrapper istemci üzerinde belirli bir sürüme güncelleştirmek için hala gereklidir.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Servis taban çizgisinde nasıl kalın?

Bir servis taban çizgisi için bir güncelleştirme kullanılabilir olduğunda, [My.VisualStudio.com'daki](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)servis güncelleştirmesi için sabit sürüm bootstrapper dosyaları kullanıma sunulur.

Ağ düzeni yüklemesini kullanarak dağıtan yöneticiler için, yöneticinin [düzen konumunu](update-a-network-installation-of-visual-studio.md)güncelleştirmesi gerekir. Konumdan yüklenen istemciler güncelleştirme bildirimleri alır. Güncelleştirmeistemcilere dağıtılmalısa, [aşağıdaki yönergeleri](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines)izleyin. Bir güncelleştirme için 'response.json'u değiştirdiğinizde, ek iş yükleri, bileşenler veya diller eklemeyin. Bu ayarların yönetilmesi, ürün güncelleştirildikten sonra 'değiştir' dağıtımı olarak yapılmalıdır.

Internet tabanlı bir yükleme için, istemcide var olmayan `--channelUri` bir kanal bildirimini gösteren parametre ile yeni sabit sürüm bootstrapper çalıştırın. Güncelleştirme sessiz veya pasif modda dağıtılırsa, iki ayrı komut kullanın:

1. Visual Studio yükleyicisini güncelleyin:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Visual Studio uygulamasının kendisini güncelleyin:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasındaki ayarlar nasıl tanımlanır?](automated-installation-with-response-file.md)
* [Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve servis](/visualstudio/releases/2019/servicing/)
