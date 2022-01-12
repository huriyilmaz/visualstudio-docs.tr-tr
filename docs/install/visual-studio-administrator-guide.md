---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Kurumsal bir ortamda Visual Studio hakkında daha fazla bilgi.
ms.date: 11/23/2021
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e22cbc20ddd6c6d16a8cfc17a71bcb3fd47d45e6
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135533980"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kurumsal ortamlarda sistem yöneticileri genellikle son kullanıcılara bir ağ paylaşımından veya sistem yönetimi yazılımını kullanarak yükleme dağıtır. Visual Studio kurulum altyapısını sistem yöneticilerine bir ağ yükleme konumu oluşturma, yükleme varsayılanlarını önceden yapılandırma, yükleme işlemi sırasında ürün anahtarlarını dağıtma ve başarılı bir dağıtımdan sonra ürün güncelleştirmelerini yönetme olanağı vererek kurumsal dağıtımı destekleyecek şekilde tasarladık.

Bu yönetici kılavuzu, ağa bağlı ortamlarda kurumsal dağıtım için senaryo tabanlı rehberlik sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluş genelinde Visual Studio dağıtmadan önce, tamamlanması gereken birkaç karar ve görev vardır:

::: moniker range="=vs-2022"

* Her hedef bilgisayarın en düşük yükleme gereksinimlerini [karşılaya olduğundan emin olun.](/visualstudio/releases/2022/system-requirements)

::: moniker-end

::: moniker range="=vs-2019"

* Her hedef bilgisayarın en düşük yükleme gereksinimlerini [karşılaya olduğundan emin olun.](/visualstudio/releases/2019/system-requirements)

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın en düşük yükleme gereksinimlerini [karşılaya olduğundan emin olun.](/visualstudio/productinfo/vs2017-system-requirements-vs)

::: moniker-end

::: moniker range="=vs-2019"

* Güvenlik ve uyumluluk ihtiyaçlarına karar verin.

  Şirketinizin bir özellik kümesi üzerinde daha uzun süre kalması ama yine de düzenli bakım güvenlik güncelleştirmeleri almak istiyorsa, bir bakım temeli kullanmayı planlamanız gerekir. Daha fazla bilgi ***için, Visual Studio*** ürün yaşam döngüsü ve bakım [](/visualstudio/releases/2019/servicing-vs2019#support-options-for-enterprise-and-professional-customers) sayfasının Enterprise ve Professional müşterileri için destek seçeneklerinin yanı sıra bakım temeli sayfasındaki [Güncelleştirme Visual Studio](update-servicing-baseline.md) bölümüne bakın.
  
::: moniker-end

::: moniker range=">=vs-2022"

* Güvenlik ve uyumluluk ihtiyaçlarına karar verin.

  Şirketinizin bir özellik kümesi üzerinde daha uzun süre kalması ama yine de düzenli bakım güvenlik güncelleştirmeleri almak istiyorsa, bir bakım temeli kullanmayı planlamanız gerekir. Daha fazla bilgi ***için, Visual Studio*** ürün yaşam döngüsü ve bakım [](/visualstudio/releases/2022/servicing-vs2022#enterprise-professional-and-build-tools-editions-support) sayfasının Enterprise ve Professional müşterileri için destek seçeneklerinin yanı sıra bakım temeli sayfasındaki [Güncelleştirme Visual Studio](update-servicing-baseline.md) bölümüne bakın.
  
::: moniker-end  

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin [ürün güncelleştirmelerini nereden almak istiyorsunuz?](update-a-network-installation-of-visual-studio.md) Özellikle, istemcinin güncelleştirmeleri şirket genelindeki bir ağ düzeninden mi yoksa İnternet'den mi [almak istediğinize](create-a-network-installation-of-visual-studio.md) karar verin.
  
  Ayrıca tek tek kullanıcıların kendi istemcilerini güncelleştirip güncelleştirelerine veya bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini isteyip istemediklerine de karar verebilirsiniz. Güncelleştirmeyi başlatan kişinin makinede yönetici ayrıcalıklarına sahip olması gerekir. Bu kararların, istemci makinede özgün yükleme öncesinden önce almaları en iyisidir. 

  [Visual Studio'nin](create-a-network-installation-of-visual-studio.md#update-or-modify-your-layout) bir ağ düzenini en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz; böylece hem Visual Studio'ın en son güncelleştirmesi için bir yükleme noktası olarak hem de istemci iş istasyonlarına dağıtılmış olan yüklemeleri korumak için kullanılabilir. 

  Kurumsal dağıtım araçlarını kullanan kuruluşlar, Visual Studio Kataloğu'Microsoft Update Sunucu Güncelleştirme Hizmetleri'Windows güncelleştirmelerinin mevcut olması avantajını kullanabilir. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md) [ve Yönetici güncelleştirmelerini uygulama.](applying-administrator-updates.md)

  İnternet'e bağlı olan bilgisayarlar için, istemciyi program aracılığıyla güncelleştirebilirsiniz ve [İnternet](update-a-network-installation-of-visual-studio.md#programatically-update-a-client-that-doesnt-have-internet-access)erişimini önlenebilir veya en az Visual Studio kullanarak istemciyi [güncelleştirebilirsiniz.](update-minimal-layout.md) 

* Hangi iş [yüklerine ve bileşenlere ihtiyaç olduğuna](workload-and-component-ids.md) karar verin.

* Yükleme varsayılanlarını [ayarlamaya olanak sağlayan bir](automated-installation-with-response-file.md)yanıt dosyası kullanıp kullanmay karar verin.

* Tek tek bilgisayarlardaki müşteri geri grup ilkesi devre dışı bırakmak için Visual Studio yapılandırmak istediğinize karar verin.

## <a name="step-1---download-visual-studio-product-files"></a>1. Adım : Visual Studio dosyalarını indirme

* [Yüklemek istediğiniz iş yüklerini](workload-and-component-ids.md) ve bileşenleri seçin.

* [Ürün dosyaları için bir Visual Studio düzeni oluşturun.](create-a-network-installation-of-visual-studio.md)

## <a name="step-2---build-an-installation-script"></a>2. Adım - Yükleme betiği oluşturma

* Bir ağ düzeninden istemci [makinesine komut satırı](use-command-line-parameters-to-install-visual-studio.md) [Visual Studio komut satırı parametrelerini kullanan bir yükleme betiği derleme.](create-a-network-installation-of-visual-studio.md#install-visual-studio-onto-a-client-machine-from-a-network-installation)

* (İsteğe bağlı) [Kullanıcıların yazılımı ayrı olarak etkinleştirmesi](automatically-apply-product-keys-when-deploying-visual-studio.md) gerekmay için yükleme betiği kapsamında bir toplu lisans ürün anahtarı uygulama.

* (İsteğe bağlı) [Visual Studio'nin](set-defaults-for-enterprise-deployments.md) dağıtımını ve davranışını etkileyen, diğer sürümler veya örneklerle paylaşılan bazı paketlerin nerede yüklü olduğu, paketlerin nerede ve önbelleğe alınıp alınacağı, yönetici güncelleştirmelerinin nasıl etkinleştirilmesi gerektiği, hangi güncelleştirme kanallarının kullanılabilir olduğu ve istemciye nasıl sunuldukları ve bildirimlerin nasıl görüntülediği ya da görünme şekli gibi, Visual Studio'nin dağıtımını ve davranışını etkileyen kayıt defteri ilkeleri ayarlayın.

* (İsteğe bağlı) Kümeyi grup ilkesi. Ayrıca, tek [tek bilgisayarlarda Visual Studio geri bildirimlerini devre dışı bırakmak için yapılandırmayı](../ide/visual-studio-experience-improvement-program.md) da yapılandırabilirsiniz.

## <a name="step-3---deploy-updates"></a>3. Adım - Güncelleştirmeleri dağıtma

Betiğinizi hedef geliştirici iş istasyonlarınıza yürütmek için tercih edilen dağıtım teknolojinizi kullanın.  

* [Ağ düzeninizi istenen sürümle güncelleştirin Visual Studio](create-a-network-installation-of-visual-studio.md#update-or-modify-your-layout)

* [İstemci makinenizi en son güncelleştirmelerle yenileyin](update-a-network-installation-of-visual-studio.md) Visual Studio.

* Windows Server Update Services Visual Studio den veya Microsoft Update Kataloğu'System Center Configuration Manager. Daha fazla [bilgi için Bkz.](applying-administrator-updates.md) Yönetici güncelleştirmelerini uygulama. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>4. Adım - (İsteğe bağlı) Visual Studio doğrulama araçlarını kullanma

İstemci makinelerde yüklü örnekleri [algılamanıza ve yönetmenize yardımcı Visual Studio çeşitli](tools-for-managing-visual-studio-instances.md) araçlarımız vardır.

::: moniker range="vs-2019"

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio, F1 hata listesinden ve kod bağlantılarından Bing özel tür eklemeye olanak sağlar. İlkeye Visual Studio kayıt defteri anahtarının değerini değiştirerek arama mekanizmasını devre dışı bırakmak için özel kullanıcı türlerini dahil etmek üzere yapılandırmayı yapılandırmış olursunuz:

**"PutCustomTypeInBingSearch" DWORD 0**

Kayıt defteri, özel kayıt `Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\` defteri kovanının dizininde bulunur. Kayıt defteri kovanını açma yönergeleri için bkz. kayıt [defterini Visual Studio düzenleme.](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

::: moniker-end

::: moniker range="vs-2017"

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio, F1 hata listesinden ve kod bağlantılarından Bing özel tür eklemeye olanak sağlar. İlkeye Visual Studio kayıt defteri anahtarının değerini değiştirerek arama mekanizmasını devre dışı bırakmak için özel kullanıcı türlerini dahil etmek üzere yapılandırmayı yapılandırmış olursunuz:

**"PutCustomTypeInBingSearch" DWORD 0**

Kayıt defteri, özel kayıt `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` defteri kovanının dizininde bulunur. Kayıt defteri kovanını açma yönergeleri için bkz. kayıt [defterini Visual Studio düzenleme.](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md)
* [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Çevrimdışı yükleme için Visual Studio sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Yükleme yapılandırmasını içeri veya dışarı aktarma](import-export-installation-configurations.md)
* [Visual Studio Kurulum Arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
* [Zaman uyumlu otomatik yükleme ayarları](../extensibility/synchronously-autoloaded-extensions.md)
