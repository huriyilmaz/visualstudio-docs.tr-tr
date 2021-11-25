---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Visual Studio kurumsal bir ortamda dağıtma hakkında daha fazla bilgi edinin.
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
ms.openlocfilehash: f9c378b732d8a74f8435533958f29a785d23192d
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108679"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kurumsal ortamlarda, sistem yöneticileri genellikle son kullanıcılara bir ağ paylaşımından veya sistem yönetimi yazılımını kullanarak yükleme dağıtır. sistem yöneticilerine, yükleme varsayılanlarını önceden yapılandırmak, yükleme işlemi sırasında ürün anahtarlarını dağıtmak ve başarılı bir dağıtım sonrasında ürün güncelleştirmelerini yönetmek için bir ağ yükleme konumu oluşturma olanağı sunarak, kurumsal dağıtımı destekleyecek Visual Studio kurulum altyapısını tasarlıyoruz.

Bu Yönetici Kılavuzu, ağ ortamlarında kurumsal dağıtım için senaryo tabanlı yönergeler sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

kuruluşunuz genelinde Visual Studio dağıtmadan önce, yapmanız gereken birkaç karar vardır:

::: moniker range="=vs-2022"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/releases/2022/system-requirements)karşıladığından emin olun.

::: moniker-end

::: moniker range="=vs-2019"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/releases/2019/system-requirements)karşıladığından emin olun.

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs)karşıladığından emin olun.

::: moniker-end

::: moniker range="=vs-2019"

* Güvenlik ve uyumluluk gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi üzerinde kalması, ancak yine de düzenli bakım güvenlik güncelleştirmeleri almak istiyorsa, bir hizmet temeli kullanmayı planlamanız gerekir. daha fazla bilgi için bkz. [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing-vs2019#support-options-for-enterprise-and-professional-customers) sayfasının ***Enterprise ve Professional müşterileri için destek seçenekleri ve*** [hizmet temeli sayfasında güncelleştirme Visual Studio](update-servicing-baseline.md) .
  
::: moniker-end

::: moniker range=">=vs-2022"

* Güvenlik ve uyumluluk gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi üzerinde kalması, ancak yine de düzenli bakım güvenlik güncelleştirmeleri almak istiyorsa, bir hizmet temeli kullanmayı planlamanız gerekir. daha fazla bilgi için bkz. [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing-vs2022#support-options-for-enterprise-and-professional-customers) sayfasının ***Enterprise ve Professional müşterileri için destek seçenekleri ve*** [hizmet temeli sayfasında güncelleştirme Visual Studio](update-servicing-baseline.md) .
  
::: moniker-end  

* Güncelleştirme modeline karar verin.

  Tek tek [istemci makinelerin ürün güncelleştirmelerini nereden almasını](/visualstudio/install/update-a-network-installation-of-visual-studio)istiyorsunuz? Özellikle, istemcinin [Şirket genelinde bir ağ düzeninden](/visualstudio/install/create-a-network-installation-of-visual-studio) veya internet 'ten güncelleştirme almasını isteyip istemediğinize karar verin.
  
  Ayrıca, bireysel kullanıcıların kendi istemcilerini güncelleştirebilir mi yoksa bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini istediğinizi de belirlemeniz gerekir. Güncelleştirmenin başlatanın, makinede yönetici ayrıcalıklarına sahip olması gerekir. Bu kararların, istemci makinesinde özgün yükleme gerçekleştirilmeden önce yapılması en iyisidir. 

  en son Visual Studio güncelleştirmesi için bir yükleme noktası olarak ve ayrıca istemci iş istasyonlarına zaten dağıtılan yüklemeleri sürdürmek için [Visual Studio bir ağ düzeninin](/visualstudio/install/create-a-network-installation-of-visual-studio#update-or-modify-your-layout) en son ürün güncelleştirmeleriyle güncelleştirilmesi mümkündür. 

  kurumsal dağıtım araçlarını kullanan kuruluşlar, Visual Studio güncelleştirmelerinin Microsoft Update kataloğu ve Windows Server Update Services üzerinde kullanılabildiği gerçeden faydalanabilir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](/visualstudio/install/enabling-administrator-updates) ve [yönetici güncelleştirmelerini uygulama](/visualstudio/install/applying-administrator-updates).

  internet 'e bağlı olmayan bilgisayarlar için, [istemciyi programlı bir şekilde güncelleştirebilir ve internet erişimini engelleyebilir](/visualstudio/install/update-a-network-installation-of-visual-studio#programatically-update-a-client-that-doesnt-have-internet-access)veya [en az düzen kullanarak Visual Studio güncelleştirebilirsiniz](update-minimal-layout.md). 

* Şirketinizin ihtiyaç duyacağı [iş yüklerini ve bileşenleri](workload-and-component-ids.md) belirleyin.

* Yükleme varsayılanlarını ayarlamanıza olanak tanıyan bir [yanıt dosyası](automated-installation-with-response-file.md)kullanıp kullanmayacağınızı belirleyin.

* grup ilkesi etkinleştirmek istediğinize ve tek bilgisayarlarda müşteri geri bildirimini devre dışı bırakacak Visual Studio yapılandırmak istiyorsanız belirleyin.

## <a name="step-1---download-visual-studio-product-files"></a>1. adım-Visual Studio ürün dosyalarını indirme

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin](workload-and-component-ids.md) .

* [Visual Studio ürün dosyaları için bir ağ düzeni oluşturun](create-a-network-installation-of-visual-studio.md).

## <a name="step-2---build-an-installation-script"></a>2. adım-yükleme betiği oluşturma

* [bir ağ düzeninden istemci makinesine Visual Studio yüklemek] için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md) kullanan bir yükleme betiği oluşturun] (/visualstudio/install/create-a-network-installation-of-visual-studio # install-Visual-Studio-to-a-client-machıne

* Seçim Kullanıcıların yazılımı ayrı olarak etkinleştirmesine gerek kalmaması için yükleme komut dosyasının parçası olarak [bir toplu lisans ürün anahtarı uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md) .

* Seçim diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği, bu paketlerin nerede ve önbelleğe alındığı, yönetici güncelleştirmesinin etkinleştirilmesi veya nasıl uygulanması gerektiği, hangi güncelleştirme kanallarının kullanılabildiği ve bunların istemciye nasıl sunulduğu ve bildirimlerin nasıl göründüğü veya görünmediği gibi [Visual Studio dağıtım ve davranışlarını etkileyen kayıt defteri ilkeleri ayarlayın](set-defaults-for-enterprise-deployments.md) .

* Seçim Grup ilkesi ayarlayın. ayrıca, her bir bilgisayarda [müşteri geri bildirimini devre dışı bırakmak için Visual Studio yapılandırabilirsiniz](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy-updates"></a>3. adım-güncelleştirmeleri dağıtma

Komut dosyanızı hedef geliştirici iş istasyonlarınızda yürütmek için tercih ettiğiniz dağıtım teknolojinizi kullanın.  

* [Ağ düzeninizi istenen Visual Studio sürümü ile güncelleştirin](/visualstudio/install/create-a-network-installation-of-visual-studio.md#update-or-modify-your-layout)

* Visual Studio için [en son güncelleştirmelerle istemci makinenizi yenileyin](/visualstudio/install/update-a-network-installation-of-visual-studio) .

* Windows Server Update Services veya Microsoft Update kataloğundan Visual Studio güncelleştirmelerini System Center Configuration Manager gibi araçlarla dağıtabilirsiniz. Daha fazla bilgi için [yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md) bölümüne bakın. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>4. adım-(isteğe bağlı) yüklemeyi doğrulamak için Visual Studio araçları kullanın

istemci makinelerde [yüklü Visual Studio örneklerini tespit etmenize ve yönetmenize](tools-for-managing-visual-studio-instances.md) yardımcı olacak çeşitli araçlar sunulmaktadır.

::: moniker range="vs-2019"

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Visual Studio yükleme, varsayılan olarak, hata listesi F1 ve kod bağlantıları 'ndaki Bing aramalarına özel tür ekleme imkanı sunar. ilke ile aşağıdaki kayıt defteri anahtarının değerini değiştirerek, arama mekanizmasını herhangi bir özel kullanıcı türünü dahil ederek devre dışı bırakmak için Visual Studio yapılandırabilirsiniz:

**"Putcustomtypeınbingsearch" DWORD 0**

Kayıt defteri, `Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\` özel kayıt defteri kovanın dizininde bulunur. kayıt defteri kovanının nasıl açılacağı hakkında yönergeler için bkz. [Visual Studio örneği için kayıt defterini düzenlemeyle](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Visual Studio yükleme, varsayılan olarak, hata listesi F1 ve kod bağlantıları 'ndaki Bing aramalarına özel tür ekleme imkanı sunar. ilke ile aşağıdaki kayıt defteri anahtarının değerini değiştirerek, arama mekanizmasını herhangi bir özel kullanıcı türünü dahil ederek devre dışı bırakmak için Visual Studio yapılandırabilirsiniz:

**"Putcustomtypeınbingsearch" DWORD 0**

Kayıt defteri, `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` özel kayıt defteri kovanın dizininde bulunur. kayıt defteri kovanının nasıl açılacağı hakkında yönergeler için bkz. [Visual Studio örneği için kayıt defterini düzenlemeyle](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmeleri uygulanıyor](applying-administrator-updates.md)
* [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Yükleme yapılandırmasını içeri veya dışarı aktarma](import-export-installation-configurations.md)
* [Visual Studio kurulum arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [ürün yaşam döngüsü ve bakım Visual Studio](/visualstudio/releases/2019/servicing/)
* [Zaman uyumlu oto yükleme ayarları](../extensibility/synchronously-autoloaded-extensions.md)
