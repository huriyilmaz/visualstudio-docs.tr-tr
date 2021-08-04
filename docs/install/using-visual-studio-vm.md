---
title: Azure sanal makinesinde Visual Studio kullanma
titleSuffix: ''
description: Azure sanal makinesinde Visual Studio kullanmayı öğrenin
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
ms.openlocfilehash: 16cbe08f48d5d64d1213fb0422d2482f192309e8
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094547"
---
# <a name="visual-studio-images-on-azure"></a>Azure 'da görüntüleri Visual Studio

önceden yapılandırılmış bir Azure sanal makinesinde (VM) Visual Studio kullanmak, herhangi bir şey için bir veya çalışan bir geliştirme ortamına kadar hızlı ve kolay bir yoldur. farklı Visual Studio yapılandırmalarına sahip sistem görüntüleri [Azure marketi](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure)'nde kullanılabilir.

Azure’da yeni misiniz? [Ücretsiz bir Azure hesabı oluşturun](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Hangi yapılandırma ve sürümler mevcuttur?

en son ana sürümlere ait görüntüler, Visual Studio 2019 Visual Studio 2017 ve Visual Studio 2015 Azure marketi 'nde bulunabilir.  Yayınlanan her ana sürüm için, başlangıçta "Web 'e Yayınlandı" (RTW) sürümü ve en son güncelleştirilmiş sürümleri görürsünüz.  bu sürümlerin her biri, Visual Studio Enterprise ve Visual Studio Community sürümlerini sunar.  en son Visual Studio ve Windows güncelleştirmeleri dahil olmak üzere bu görüntüler en az her ay güncellenir.  Görüntülerin adları aynı olmaya devam ederken, her bir görüntünün açıklaması yüklü ürün sürümünü ve görüntünün "itibariyle" tarihini içerir.

| Yayın sürümü                                                                                                                                                | Sürümler              | Ürün sürümü       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019: en son (sürüm 16,8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Sürüm 16.8.0        |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Kurumsal            | Sürüm 16.0.20       |
| [Visual Studio 2017: en son (sürüm 15,9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Sürüm 15.9.29       |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | Sürüm 15.0.28       |
| [Visual Studio 2015: en son (güncelleştirme 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Sürüm 14.0.25431.01 |

> [!NOTE]
> Microsoft hizmet ilkesine uygun olarak, Visual Studio 2015 ' nin ilk yayınlanan (RTW) sürümü bakım için sona ermiştir. Visual Studio 2015 güncelleştirme 3, Visual Studio 2015 ürün satırı için sunulan tek sürümdür.

daha fazla bilgi için bkz. [hizmet ilkesi Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Hangi özellikler yüklendi?

her görüntü, bu Visual Studio sürümü için önerilen özellik kümesini içerir. Genellikle, yükleme şunları içerir:

* Her iş yükünün önerilen isteğe bağlı bileşenleri dahil tüm kullanılabilir iş yükleri
* .NET 4.6.2 ve .NET 4,7 SDK 'Ları, hedeflenen paketleri ve Geliştirici Araçları
* Visual F#
* Visual Studio için GitHub Uzantısı
* LINQ to SQL Aracı

görüntüleri oluştururken Visual Studio yüklemek için aşağıdaki komut satırını kullanıyoruz:

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

görüntüler ihtiyacınız olan bir Visual Studio özelliği içermiyorsa, sayfanın sağ üst köşesindeki geri bildirim aracı aracılığıyla geri bildirim sağlayın.

## <a name="what-size-vm-should-i-choose"></a>Hangi boyutta VM 'yi seçmem gerekir?

Azure, sanal makine boyutlarının tam bir aralığını sunar. Visual Studio güçlü, çok iş parçacıklı bir uygulama olduğundan, en az iki işlemci ve 7 GB bellek içeren bir VM boyutu istersiniz. Visual Studio görüntüleri için aşağıdaki VM boyutlarını öneririz:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

en son makine boyutları hakkında daha fazla bilgi için bkz. [Azure 'da Windows sanal makineler için boyutlar](/azure/virtual-machines/windows/sizes).

Azure ile, sanal makineyi yeniden boyutlandırarak başlangıç seçiminizi yeniden dengelemeniz sağlayabilirsiniz. Daha uygun bir boyuta sahip yeni bir VM sağlayabilir veya mevcut sanal makineyi farklı temel donanımla yeniden boyutlandırabilirsiniz. daha fazla bilgi için bkz. [Windows VM 'yi yeniden boyutlandırma](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>VM çalışmaya başladıktan sonra ne var?

Visual Studio, Azure 'daki "kendi lisansını getir" modelini izler. özel donanım yüklemesinde olduğu gibi, ilk adımlardan biri Visual Studio yüklemenizi lisanslandır. Visual Studio kilidini açmak için aşağıdakilerden birini yapın:

* Visual Studio abonelikle ilişkili bir Microsoft hesabı oturum açın
* Visual Studio, ilk satın alımınızla birlikte gelen ürün anahtarıyla açın

daha fazla bilgi için bkz. [Visual Studio oturum açma](../ide/signing-in-to-visual-studio.md) ve [Visual Studio kilidini açma](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Geliştirme sanal makinesini gelecekteki veya ekip kullanımı için Nasıl yaparım? kaydetmek istiyor musunuz?

Geliştirme ortamlarının yelpazesi çok büyük ve daha karmaşık ortamları oluşturmaya ilişkin gerçek maliyet vardır. Ortamınızın yapılandırmasına bakılmaksızın, yapılandırılmış sanal makineyi gelecekte kullanılmak üzere veya takımınızın diğer üyeleri için "temel görüntü" olarak kaydedebilir veya yakalayabilirsiniz. Ardından, yeni bir VM 'yi önyüklerken Azure Market görüntüsü yerine temel görüntüden temin edersiniz.

Hızlı Özet: Sistem Hazırlama Aracı 'nı (Sysprep) kullanın ve çalışan VM 'yi kapatın ve ardından Azure portal VM 'yi bir görüntü olarak *(Şekil 1)* sanal makine aracılığıyla yakalayın. Azure `.vhd` , görüntüyü içeren dosyayı seçtiğiniz depolama hesabına kaydeder. Yeni görüntü daha sonra, aboneliğinizin kaynak listesinde bir görüntü kaynağı olarak gösterilir.

![Azure portal kullanıcı arabiriminden bir görüntü yakala](media/capture-vm.png)

*(Şekil 1) Azure portal kullanıcı arabiriminden bir görüntü yakalayın.*

Daha fazla bilgi için bkz. [Azure 'da Genelleştirilmiş BIR VM 'nin yönetilen görüntüsünü oluşturma](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> VM 'yi hazırlamak için Sysprep 'ı kullanmayı unutmayın. Bu adımı kaçırırsanız Azure görüntüden bir VM sağlayamaz.

> [!NOTE]
> Görüntülerin depolanması için yine de bazı maliyetlerle karşılaşmanız gerekir, ancak bu artımlı maliyet, bir tane gerektiren her ekip üyesi için VM 'nin sıfırdan yeniden derlenmesi için ek gider maliyetlerine kıyasla çok önemli olabilir. Örneğin, tüm ekibiniz tarafından yeniden kullanılabilen bir ayda 127 GB görüntüsünü oluşturmak ve depolamak için birkaç dolar maliyeti vardır. Ancak, bu maliyetler her bir çalışanın, bireysel kullanımları için düzgün yapılandırılmış bir dev kutusunu oluşturmak ve doğrulamak üzere her çalışanın yatırım yaptıkları saatlere kıyasla önem altına alınır.

Ayrıca, geliştirme görevleriniz veya teknolojilerinizin, geliştirme yapılandırmalarının ve birden çok makine yapılandırmasının değişen özellikleri gibi daha fazla ölçeği olması gerekebilir. "altın görüntü" oluşturmayı otomatikleştiren _tarifler_ oluşturmak için Azure DevTest Labs kullanabilirsiniz. Takımınızın çalışan VM 'Lerinin ilkelerini yönetmek için DevTest Labs de kullanabilirsiniz. [geliştiriciler için Azure DevTest Labs kullanmak](/azure/devtest-lab/devtest-lab-developer-lab) , devtest Labs hakkında daha fazla bilgi için en iyi kaynaktır.

## <a name="next-steps"></a>Sonraki adımlar

önceden yapılandırılmış Visual Studio görüntülerini öğrenmiş olduğunuza göre, sonraki adım yeni bir VM oluşturmaktır:

* [Azure portal aracılığıyla VM oluşturma](/azure/virtual-machines/windows/quick-create-portal)
* [Windows Sanal makinelere genel bakış](/azure/virtual-machines/windows/overview)
