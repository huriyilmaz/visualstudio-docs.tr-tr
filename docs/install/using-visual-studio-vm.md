---
title: Azure Visual Studio Makinede sanal makine kullanma
titleSuffix: ''
description: Azure Sanal Makinesi'Visual Studio sanal makine kullanmayı öğrenin
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c27dc59e7abc477b60cc7fc10f22822fd2996350
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428172"
---
# <a name="visual-studio-images-on-azure"></a>Visual Studio Azure'da depolama

Önceden Visual Studio Bir Azure sanal makinesinde (VM) sanal makine kullanmak, hiçbir şeyden çalışan bir geliştirme ortamına gitmek için hızlı ve kolay bir yol sağlar. Farklı yapılandırma yapılandırmaları Visual Studio sistem görüntüleri, [Azure Market.](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure)

Azure’da yeni misiniz? [Ücretsiz bir Azure hesabı oluşturun.](https://azure.microsoft.com/free)

## <a name="what-configurations-and-versions-are-available"></a>Hangi yapılandırmalar ve sürümler kullanılabilir?

en son ana sürümler (Visual Studio 2019, Visual Studio 2017 ve Visual Studio 2015) için görüntüler Azure Market.  Bu sürümlerin her biri, Visual Studio Enterprise ve Visual Studio Community sunar.  Bu görüntüler en son güncelleştirmeleri ve güncelleştirmeleri dahil etmek için en Visual Studio Windows güncelleştirilir.  Görüntülerin adları aynı kalırken, her görüntünün açıklaması yüklü ürün sürümünü ve görüntünün "başlangıç" tarihini içerir.

| Sürüm sürümü                                                                                                                                                | Sürümler              | Ürün sürümü       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019: En Son (Sürüm 16.11)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Sürüm 16.11        |
| [Visual Studio 2017: En son (Sürüm 15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Sürüm 15.9      |
| [Visual Studio 2015: En son (Güncelleştirme 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Sürüm 14.0.25431.01 |

> [!NOTE]
> Microsoft hizmet ilkesine uygun olarak, Visual Studio 2015'in ilk yayımlanan (RTW) sürümü bakım süresi doldu. Visual Studio 2015 Güncelleştirme 3, Visual Studio 2015 ürün satırı için sunulan tek sürümdür.

Daha fazla bilgi için [bkz. Visual Studio İlkesi.](/visualstudio/productinfo/vs-servicing-vs)

## <a name="what-features-are-installed"></a>Hangi özellikler yüklenir?

Her görüntü, bu sürüm için önerilen özellik Visual Studio içerir. Genellikle, yükleme şunları içerir:

* Her iş yükünün önerilen isteğe bağlı bileşenleri de dahil olmak üzere tüm kullanılabilir iş yükleri
* .NET 4.6.2 ve .NET 4.7 SDK'ları, Hedefleme Paketleri ve Geliştirici Araçları
* Visual F#
* Visual Studio için GitHub Uzantısı
* LINQ to SQL Araçları

Görüntülerin ne zaman Visual Studio yüklemek için aşağıdaki komut satırı kullanıyoruz:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Görüntülerde ihtiyaç Visual Studio özelliği yoksa, sayfanın sağ üst köşesindeki geri bildirim aracı aracılığıyla geri bildirim gönderin.

## <a name="what-size-vm-should-i-choose"></a>Hangi boyutta VM seçmem gerekir?

Azure, çok çeşitli sanal makine boyutları sunar. Visual Studio güçlü, çok iş parçacıklı bir uygulama olduğundan, en az iki işlemci ve 7 GB bellek içeren bir VM boyutuna sahip olmak istersiniz. Sanal makine görüntüleri için aşağıdaki VM Visual Studio öneririz:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

En son makine boyutları hakkında daha fazla bilgi için [bkz. Azure'Windows sanal makinelerin boyutları.](/azure/virtual-machines/windows/sizes)

Azure ile, VM'yi yeniden boyutlandırma yoluyla ilk seçiminizi yeniden dengelersiniz. Daha uygun bir boyuta sahip yeni bir VM s sağlama veya mevcut VM'nizi farklı temel alınan donanıma yeniden boyutlandırma. Daha fazla bilgi için [bkz. Vm'Windows boyutlandırma.](/azure/virtual-machines/windows/resize-vm)

## <a name="after-the-vm-is-running-whats-next"></a>VM çalıştır çalıştırktan sonra ne olacak?

Visual Studio Azure'da "kendi lisansını getir" modelini izler. Özel donanıma yapılan bir yüklemede olduğu gibi, ilk adımlardan biri de özel donanım Visual Studio lisanslamadır. Bir Visual Studio açmak için:

* Bir Microsoft hesabı aboneliğiyle ilişkili bir Visual Studio oturum açma
* İlk Visual Studio ile birlikte gelen ürün anahtarıyla kilit açma

Daha fazla bilgi için [bkz. Visual Studio'da oturum açma](../ide/signing-in-to-visual-studio.md) [ve Visual Studio.](../ide/how-to-unlock-visual-studio.md)

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Nasıl yaparım? VM'yi gelecekte veya takım kullanımı için kaydedecek misiniz?

Geliştirme ortamlarının yelpazesi çok büyük ve daha karmaşık ortamların geliştirilmesiyle ilişkili gerçek bir maliyet vardır. Ortamınız yapılandırmasına bakılmaksızın, yapılandırılan VM'nizi gelecekteki kullanımlar veya takımınız için "temel görüntü" olarak kaydedebilir veya yakalayabilirsiniz. Ardından, yeni bir VM'yi önyüklerken, vm'yi sanal makine görüntüsü yerine Azure Market sağlar.

Hızlı bir özet: Sistem Hazırlama aracını (Sysprep) kullanın, çalışan  VM'yi kapatın ve ardından vm'yi kullanıcı arabirimi üzerinden görüntü olarak Azure portal. Azure, `.vhd` görüntüyü içeren dosyayı seçtiğiniz depolama hesabına kaydeder. Yeni görüntü daha sonra aboneliğinizin kaynak listesinde Görüntü kaynağı olarak görünür.

![Azure portal kullanıcı arabirimi aracılığıyla görüntü yakalama](media/capture-vm.png)

*(Şekil 1) Azure portal kullanıcı arabirimi aracılığıyla bir görüntü yakalama.*

Daha fazla bilgi için [bkz. Azure'da genelleştirilmiş bir VM'nin yönetilen görüntüsünü oluşturma.](/azure/virtual-machines/windows/capture-image-resource)

> [!IMPORTANT]
> VM'yi hazırlamak için Sysprep kullanmayı unutmayın. Bu adımı kaçırırsanız, Azure görüntüden vm sağ aşamaz.

> [!NOTE]
> Görüntülerin depolanması için yine de bazı maliyetler ödemezsiniz, ancak bu artımlı maliyet, vm'yi ihtiyacı olan her ekip üyesi için sıfırdan yeniden oluşturmak için gereken ek yük maliyetlerine kıyasla önemsiz olabilir. Örneğin, bir ay boyunca 127 GB'lık bir görüntü oluşturmak ve depolamak, tüm takımınız tarafından yeniden kullanılabilir. Ancak bu maliyetler, her çalışanın bireysel kullanım için düzgün yapılandırılmış bir geliştirme kutusu oluşturmak ve doğrulamak için yatırım yaptıkları saatlerle karşılaştırıldığında önemsizdir.

Ayrıca, geliştirme görevleriniz veya teknolojileriniz, geliştirme yapılandırmaları ve birden çok makine yapılandırması gibi daha fazla ölçek gerektirebilir. "Altın Azure DevTest Labs" oluşturma _işlemini otomatikleştiren_ tarifler oluşturmak için Azure DevTest Labs'i kullanabilirsiniz. DevTest Labs'i, takımınız tarafından çalıştırilen VM'lere yönelik ilkeleri yönetmek için de kullanabilirsiniz. [Geliştiriciler Azure DevTest Labs devtest labs](/azure/devtest-lab/devtest-lab-developer-lab) hakkında daha fazla bilgi için en iyi kaynaktır.

## <a name="next-steps"></a>Sonraki adımlar

Önceden yapılandırılmış sanal makine görüntüleri hakkında bilgi Visual Studio bir sonraki adım yeni bir VM oluşturmaktır:

* [Sanal makine aracılığıyla VM Azure portal](/azure/virtual-machines/windows/quick-create-portal)
* [Windows Sanal Makinelere genel bakış](/azure/virtual-machines/windows/overview)
