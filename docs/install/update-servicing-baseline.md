---
title: Bakım temeli sırasında Visual Studio’yu güncelleştirme
description: hizmet temeli üzerinde kalarak Visual Studio güncelleştirme hakkında bilgi edinin.
ms.date: 11/23/2021
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
ms.openlocfilehash: 342da7abdf898f15216694dba4a200b9f0263556
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108657"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Bakım temeli sırasında Visual Studio’yu güncelleştirme

Visual Studio ürün yaşam döngüsü boyunca sıklıkla güncelleştiririz. İki tür güncelleştirme vardır:

* **Küçük sürüm güncelleştirmeleri** &mdash; Örneğin, &mdash; yeni özellikleri ve bileşenleri içeren 16,0 16,1 ' dir.  
* **Bakım güncelleştirmeleri**— Örneğin, 16.0.4 to 16.0.5 — yalnızca kritik sorunlara yönelik hedeflenen düzeltmeleri içerir.

Enterprise yöneticileri, istemcilerinin bir hizmet ana çizgisi üzerinde tutulmasını seçebilirler. Bir hizmet ana çizgisi, bir sonraki hizmet temelinin sürümünden önceki bir yıla yönelik güncelleştirme Bakımı ile desteklenir.

Hizmet temeli seçeneği, geliştiricilere ve yöneticilere yeni küçük güncelleştirmelere dahil olan yeni özellikleri, hata düzeltmelerini veya bileşenleri benimsemek için daha fazla esneklik sağlar. İlk hizmet temeli 16.0. x ' dir. Daha fazla bilgi için bkz. [Enterprise ve Professional müşterileri Için destek seçenekleri](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Hizmet temeline nasıl ulaşın

bir hizmet ana temelini kullanmaya başlamak için [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)adresinden bir sabit sürüm Visual Studio yükleyicisi önyükleyici indirin. Bootstrap'in bu belirli sürüme yönelik ürün yapılandırmalarına, iş yüklerine ve bileşenlerine bağlantıları vardır.

> [!NOTE]
> Sabit sürümlü önyükleyici ve standart bootstrapdenetleyicileri arasında ayrım yapmanız konusunda dikkatli olun. Standart Bootstrap, Visual Studio en son kullanılabilir sürümünü kullanacak şekilde yapılandırılır. Standart önyükleyici, My.VisualStudio.com adresinden İndirildiklerinde dosya adında bir sayı (örneğin, vs_enterprise__123456789-123456789.exe) sahiptir.

Yükleme sırasında, Kuruluş yöneticilerinin istemcilerinin en son sürüme güncelleştirilmesini engellemek için istemcilerini yapılandırması gerekir. Bunu yapmak için çeşitli yollar vardır:
- [ `channelUri` Yanıt yapılandırma dosyasındaki ayarı](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) , düzen veya yerel klasörde bir kanal bildirimi kullanacak şekilde değiştirin.
- [Komut satırı yürütme yoluyla channelUri 'yi,](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) varolmayan bir dosya kullanacak şekilde değiştirin.
- İstemcilerin kendi kendine güncelleştirilmesini engellemek için, [güncelleştirmeleri devre dışı bırakmak üzere istemci sisteminde Ilke ayarlayın](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating).

### <a name="install-a-servicing-baseline-on-a-network"></a>Bir ağa hizmet temeli yükler

Bir ağ düzeni yüklemesi kullanan yöneticiler, `channelUri` mizanpajda *Response. JSON* dosyasındaki değeri aynı klasörde olan *channelmanifest. JSON* dosyasını kullanacak şekilde değiştirmeli. gerçekleştirilecek adımlar için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). Değerin değiştirilmesi, `channelUri` istemcilerin düzen konumundaki güncelleştirmeleri bakmalarını sağlar.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Internet üzerinden bir hizmet temeli yüklemesi

Internet tabanlı yükleme için, `--channelUri` Kurulum 'u başlatmak için kullanılan komut satırına mevcut olmayan bir kanal bildirimini ekleyin. bu, Visual Studio bir güncelleştirme için en son kullanılabilir sürümü kullanmasını devre dışı bırakır. Aşağıda bir örnek verilmiştir:

```shell
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>İstemcilerin güncelleştirilmesini devre dışı bırakmak için ilke ayarlarını kullanma

İstemci üzerindeki güncelleştirmeleri denetlemek için başka bir seçenek de [güncelleştirme bildirimlerini kapatıncaya](controlling-updates-to-visual-studio-deployments.md). Yükleme sırasında channelUri değeri değiştirilmediyseniz bu seçeneği kullanın. İstemcinin kullanılabilir en son sürüme bağlantı almasını devre dışı bırakır. Bir sabit sürümlü önyükleyici, istemci üzerindeki belirli bir sürüme güncelleştirmek için hala gereklidir.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Hizmet temeli üzerinde kal

Hizmet temeli için bir güncelleştirme kullanılabilir olduğunda, [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)adresindeki bakım güncelleştirmesi için sabit sürümlü önyükleyici dosyaları kullanılabilir hale getirilir.

Ağ düzeni yüklemesi kullanarak dağıtan Yöneticiler için, yöneticinin [Düzen konumunu](create-a-network-installation-of-visual-studio.md#update-or-modify-your-layout)güncelleştirmesi gerekir. Konumdan yüklenen istemciler, güncelleştirme bildirimleri alır. Güncelleştirmenin istemcilere dağıtılması gerekiyorsa, [Bu yönergeleri](update-a-network-installation-of-visual-studio.md)izleyin. Bir güncelleştirme için ' Response. json ' öğesini değiştirdiğinizde ek iş yükleri, bileşenler veya diller eklemeyin. Bu ayarların yönetilmesi, ürün güncelleştirildikten sonra ' Değiştir ' dağıtımı olarak yapılmalıdır.

Internet tabanlı bir yükleme için, `--channelUri` istemcideki mevcut olmayan bir kanal bildirimini işaret eden parametresiyle yeni bir sabit sürüm önyükleyici çalıştırın. Güncelleştirme sessiz veya pasif modda dağıtılmışsa, iki ayrı komut kullanın:

1. Visual Studio yükleyicisini güncelleştirin:

    ```shell
    vs_enterprise.exe --quiet --update
    ```

::: moniker range="vs-2019"
 
2. Visual Studio uygulamasının kendisini güncelleştirin:
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

::: moniker range=">=vs-2022"

2. Visual Studio uygulamasının kendisini güncelleştirin:
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
* [Yanıt dosyasındaki ayarları tanımlama](automated-installation-with-response-file.md)
* [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [ürün yaşam döngüsü ve bakım Visual Studio](/visualstudio/releases/2019/servicing/)
