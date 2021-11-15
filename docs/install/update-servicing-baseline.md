---
title: Bakım temeli sırasında Visual Studio’yu güncelleştirme
description: Bakım temel çizgisinde Visual Studio güncelleştirme hakkında bilgi öğrenin.
ms.date: 07/17/2019
ms.topic: conceptual
ms.assetid: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: bca4ca6872532a16b1328707c1a11ecd4935fab9
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453990"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Bakım temeli sırasında Visual Studio’yu güncelleştirme

Ürün yaşam Visual Studio sık sık güncelleştirmeler sunuyoruz. İki tür güncelleştirme vardır:

* **İkincil sürüm güncelleştirmeleri** &mdash; Örneğin, yeni özellikler ve bileşenler içeren 16.0 ile 16.1 &mdash; arasında.  
* **Bakım güncelleştirmeleri**(örneğin, 16.0.4'den 16.0.5'e) yalnızca kritik sorunlar için hedeflenen düzeltmeleri içerir.

Enterprise yöneticileri istemcilerini bakım temellerinde tutmayı seçebilir. Bakım temeli, sonraki bakım temeli yayından bir yıl önce yapılan bakım güncelleştirmeleriyle birlikte de desteklemektedir.

Bakım temeli seçeneği, geliştiricilere ve yöneticilere yeni küçük güncelleştirmelerde yer alan yeni özellikleri, hata düzeltmelerini veya bileşenleri benimseme konusunda daha fazla esneklik sağlar. İlk bakım temeli 16.0.x'tir. Daha fazla bilgi için [bkz. Kurumsal ve profesyonel müşteriler için destek seçenekleri.](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)

## <a name="how-to-get-onto-a-servicing-baseline"></a>Bakım temel çizgisine nasıl binersiniz?

Bakım temeli kullanmaya başlamak için, My.VisualStudio.com'dan bir sabit Visual Studio yükleyici [önyükleyicisi indirin.](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) Önyükleyiciler, ilgili sürüme yönelik ürün yapılandırmalarına, iş yüklerine ve bileşenlere bağlantılar içerir.

> [!NOTE]
> Sabit sürüm önyükleyici ile standart önyükleyicileri birbirinden ayırt etmek için dikkatli olun. Standart önyükleyiciler, Visual Studio'nin en son kullanılabilir sürümünü Visual Studio. Standart boostrapper'ların dosya adı (örneğin, vs_enterprise__123456789-123456789.exe) My.VisualStudio.com.

Yükleme sırasında, kuruluş yöneticilerinin istemcilerini istemcilerinin en son sürüme güncelleştirmesini önlemek için yapılandırmaları gerekir. Bunu yapmak için çeşitli yollar vardır:
- [Yanıt `channelUri` yapılandırma dosyasındaki ayarı düzende](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) veya yerel klasörde bir kanal bildirimi kullanmak için değiştirebilirsiniz.
- [ChannelUri'yi komut satırı yürütmesi aracılığıyla,](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) var olmayan bir dosya kullanmak için değiştirme.
- [İstemcilerin kendi kendini güncelleştirmesini önlemek için güncelleştirmeleri](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)devre dışı bırakmak için istemci sisteminde ilkeler ayarlayın.

### <a name="install-a-servicing-baseline-on-a-network"></a>Bir ağa hizmet temeli yükleme

Ağ düzeni yüklemesi kullanan yöneticiler, aynı klasörde yer alan `channelUri` *channelmanifest.json* dosyasını kullanmak için düzendeki *response.json* dosyasındaki değeri değiştirmeli. Atılması gereken adımlar için [bkz. Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio.](controlling-updates-to-visual-studio-deployments.md) Değerin `channelUri` değiştirilmesi, istemcilerin düzen konumu içinde güncelleştirmeleri alar.

### <a name="install-a-servicing-baseline-via-the-internet"></a>İnternet üzerinden hizmet temeli yükleme

İnternet tabanlı bir yükleme için, kurulumu başlatmak için kullanılan komut satırına mevcut `--channelUri` olmayan bir kanal bildirimi ekleyin. Bu, Visual Studio için kullanılabilir en son sürümü kullanmasını devre dışı bırakmanızı sağlar. Aşağıda bir örnek verilmiştir:

```shell
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>İstemcilerin güncelleştirmesini devre dışı bırakmak için ilke ayarlarını kullanma

bir istemcide güncelleştirmeleri denetlemenin bir diğer seçeneği [de güncelleştirme bildirimlerini kapatmaktır.](controlling-updates-to-visual-studio-deployments.md) Yüklemede channelUri değeri değişmemişse bu seçeneği kullanın. İstemcinin kullanılabilir en son sürümün bağlantılarını almasını devre dışı bıraktır. İstemcide belirli bir sürüme güncelleştirmek için sabit sürüm önyükleyici hala gereklidir.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Bakım temel çizgisine bağlı kalma

Bakım temeli için bir güncelleştirme kullanılabilir olduğunda, hizmet güncelleştirmesi için sabit sürüm önyükleyici dosyaları [My.VisualStudio.com.](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)

Ağ düzeni yüklemesi kullanarak dağıtım yapan yöneticiler için, yöneticinin düzen konumunu [güncelleştirmesi gerekir.](update-a-network-installation-of-visual-studio.md) Konumdan yüklü istemciler güncelleştirme bildirimleri alır. Güncelleştirmenin istemcilere dağıtılması gerekirse bu [yönergeleri izleyin.](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines) Bir güncelleştirme için 'response.json' değiştirerek başka iş yükleri, bileşenler veya diller eklemeyebilirsiniz. Bu ayarların yönetilmesi, ürün güncelleştirildikten sonra 'değişiklik' dağıtımı olarak yapılması gerekir.

İnternet tabanlı bir yükleme için, parametresi istemcide mevcut olmayan bir kanal bildirimine işaret ediyor olan yeni sabit sürüm `--channelUri` önyükleyicisini çalıştırın. Güncelleştirme sessiz veya pasif modda dağıtılırsa iki ayrı komut kullanın:

1. Visual Studio güncelleştirin:

    ```shell
    vs_enterprise.exe --quiet --update
    ```

::: moniker range="vs-2019"
 
2. Uygulamanın Visual Studio güncelleştirin:
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

::: moniker range=">=vs-2022"

2. Uygulamanın Visual Studio güncelleştirin:
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasında ayarları tanımlama](automated-installation-with-response-file.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
