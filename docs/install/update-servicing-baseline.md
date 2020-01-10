---
title: Bakım temeli sırasında Visual Studio’yu güncelleştirme
description: Visual Studio 'Yu bir hizmet ana hat üzerinde kalarak güncelleştirme hakkında bilgi edinin.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4c33420e715f2164f767ba57ff149a409d7d3627
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776179"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Bakım temeli sırasında Visual Studio’yu güncelleştirme

Visual Studio 'Yu genellikle ürün yaşam döngüsü boyunca güncelleştiririz. İki tür güncelleştirme vardır: 

* **Küçük yayın güncelleştirmeleri**&mdash;Örneğin, yeni özellikler ve bileşenler içeren 16,0 16,1&mdash;.  
* **Bakım güncelleştirmeleri**— Örneğin, 16.0.4 to 16.0.5 — yalnızca kritik sorunlara yönelik hedeflenen düzeltmeleri içerir.

Kurumsal Yöneticiler, istemcilerinin bir hizmet ana hat üzerinde tutulmasını tercih edebilir. Bir hizmet ana çizgisi, bir sonraki hizmet temelinin sürümünden önceki bir yıla yönelik güncelleştirme Bakımı ile desteklenir.

Hizmet temeli seçeneği, geliştiricilere ve yöneticilere yeni küçük güncelleştirmelere dahil olan yeni özellikleri, hata düzeltmelerini veya bileşenleri benimsemek için daha fazla esneklik sağlar. İlk hizmet temeli 16.0. x ' dir. Daha fazla bilgi için bkz. [Enterprise ve Professional müşterileri Için destek seçenekleri](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Hizmet temeline nasıl ulaşın

Bir hizmet temeli kullanmaya başlamak için, [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)adresinden sabit sürümlü bir Visual Studio yükleyicisi önyükleyici indirin. Bootstrap'in bu belirli sürüme yönelik ürün yapılandırmalarına, iş yüklerine ve bileşenlerine bağlantıları vardır.

> [!NOTE]
> Sabit sürümlü önyükleyici ve standart bootstrapdenetleyicileri arasında ayrım yapmanız konusunda dikkatli olun. Standart bootstrapdenetleyicileri, Visual Studio 'nun en son sürümünü kullanacak şekilde yapılandırılmıştır. Standart önyükleyici, My.VisualStudio.com ' den İndirildiklerinde dosya adında bir sayı (örneğin, vs_enterprise__123456789 -123456789. exe) vardır.

Yükleme sırasında, Kuruluş yöneticilerinin istemcilerinin en son sürüme güncelleştirilmesini engellemek için istemcilerini yapılandırması gerekir. Bunu yapmak için çeşitli yollar vardır:
- [Yanıt yapılandırma dosyasında `channelUri` ayarını](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) , düzen veya yerel klasörde bir kanal bildirimi kullanacak şekilde değiştirin.
- [Komut satırı yürütme yoluyla channelUri 'yi,](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) varolmayan bir dosya kullanacak şekilde değiştirin.
- İstemcilerin kendi kendine güncelleştirilmesini engellemek için, [güncelleştirmeleri devre dışı bırakmak üzere istemci sisteminde Ilke ayarlayın](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating).

### <a name="install-a-servicing-baseline-on-a-network"></a>Bir ağa hizmet temeli yükler

Bir ağ düzeni yüklemesi kullanan yöneticiler aynı klasörde bulunan *channelmanifest. JSON* dosyasını kullanmak için mizanpajda *Response. JSON* dosyasındaki `channelUri` değerini değiştirmeli. Gerçekleştirilecek adımlar için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). `channelUri` değerini değiştirmek, istemcilerin düzen konumundaki güncelleştirmeleri bakmalarını sağlar.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Internet üzerinden bir hizmet temeli yüklemesi

Internet tabanlı yükleme için, kurulum 'u başlatmak için kullanılan komut satırına mevcut olmayan bir kanal bildirimi ile `--channelUri` ekleyin. Bu, Visual Studio 'Nun bir güncelleştirme için kullanılabilir en son sürümü kullanmasını devre dışı bırakır. Örnek buradadır:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>İstemcilerin güncelleştirilmesini devre dışı bırakmak için ilke ayarlarını kullanma

İstemci üzerindeki güncelleştirmeleri denetlemek için başka bir seçenek de [güncelleştirme bildirimlerini kapatıncaya](controlling-updates-to-visual-studio-deployments.md). Yükleme sırasında channelUri değeri değiştirilmediyseniz bu seçeneği kullanın. İstemcinin kullanılabilir en son sürüme bağlantı almasını devre dışı bırakır. Bir sabit sürümlü önyükleyici, istemci üzerindeki belirli bir sürüme güncelleştirmek için hala gereklidir.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Hizmet temeli üzerinde kal

Hizmet temeli için bir güncelleştirme kullanılabilir olduğunda, [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)adresindeki bakım güncelleştirmesi için sabit sürümlü önyükleyici dosyaları kullanılabilir hale getirilir.

Ağ düzeni yüklemesi kullanarak dağıtan Yöneticiler için, yöneticinin [Düzen konumunu](update-a-network-installation-of-visual-studio.md)güncelleştirmesi gerekir. Konumdan yüklenen istemciler, güncelleştirme bildirimleri alır. Güncelleştirmenin istemcilere dağıtılması gerekiyorsa, [Bu yönergeleri](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines)izleyin. Bir güncelleştirme için ' Response. json ' öğesini değiştirdiğinizde ek iş yükleri, bileşenler veya diller eklemeyin. Bu ayarların yönetilmesi, ürün güncelleştirildikten sonra ' Değiştir ' dağıtımı olarak yapılmalıdır.

Internet tabanlı bir yüklemede, istemci üzerindeki var olmayan bir kanal bildirimini işaret eden `--channelUri` parametresi ile yeni bir sabit sürüm önyükleyici çalıştırın. Güncelleştirme sessiz veya pasif modda dağıtılmışsa, iki ayrı komut kullanın:

1. Visual Studio yükleyicisini güncelleştirin:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Visual Studio uygulamasını güncelleştirin:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasındaki ayarları tanımlama](automated-installation-with-response-file.md)
* [Ağ tabanlı Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
