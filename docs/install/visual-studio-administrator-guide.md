---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Visual Studio 'Yu kurumsal bir ortamda dağıtma hakkında daha fazla bilgi edinin.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: db1e57097b492a8847be6d96719054a6b917e4bd
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425413"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kurumsal ortamlarda, sistem yöneticileri genellikle son kullanıcılara bir ağ paylaşımından veya sistem yönetimi yazılımını kullanarak yükleme dağıtır. Sistem yöneticilerine bir ağ yükleme konumu oluşturma, Yükleme varsayılanlarını önceden yapılandırma, yükleme işlemi sırasında ürün anahtarlarını dağıtma ve başarılı bir dağıtım sonrasında ürün güncelleştirmelerini yönetme olanağı sunarak, kurumsal dağıtımı desteklemek için Visual Studio Kurulum altyapısını tasarladık.

Bu Yönetici Kılavuzu, ağ ortamlarında kurumsal dağıtım için senaryo tabanlı yönergeler sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuz genelinde Visual Studio 'Yu dağıtmadan önce, yapmanız gereken birkaç karar vardır:

::: moniker range="vs-2019"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/releases/2019/system-requirements/)karşıladığından emin olun.

* Bakım gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi daha uzun bir süre içinde kalması, ancak hala düzenli bakım güncelleştirmelerini almak istiyorsa, bir hizmet temeli kullanmayı planlayın. Daha fazla bilgi için, [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) sayfasının ***Enterprise ve Professional müşterilerinin destek seçeneklerine*** ve [hizmet ana hat üzerinde Visual Studio 'yu güncelleştirme](update-servicing-baseline.md) bölümüne bakın.

  Toplu özellik güncelleştirmeleriyle birlikte bakım güncelleştirmelerini uygulamayı planlıyorsanız en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almasını istiyorsunuz? Özellikle, güncelleştirmeleri Internet 'ten mi yoksa şirket genelindeki bir yerel paylaşımdan mı almak istediğinize karar verin. Ardından, yerel bir paylaşma kullanmayı seçerseniz, bireysel kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine karar verin ya da bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini ister misiniz?

  Visual Studio 'nun bir ağ yükleme düzeninin en son ürün güncelleştirmeleriyle güncelleştirilmesi olasıdır. böylece, Visual Studio 'nun en son güncelleştirmesi için bir yükleme noktası olarak ve ayrıca istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](../install/update-a-network-installation-of-visual-studio.md).

  İnternet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur. Daha fazla bilgi için bkz. [Visual Studio 'yu en düşük düzeyde çevrimdışı düzen kullanarak güncelleştirme](update-minimal-layout.md).

* Şirketinizin ihtiyaç duyacağı [iş yüklerini ve bileşenleri](workload-and-component-ids.md?view=vs-2019) belirleyin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2019) kullanıp kullanmayacağınızı belirleyin (betik dosyasında ayrıntıların yönetimini basitleştirir).

* Grup ilkesi etkinleştirmek istediğinize ve Visual Studio 'Yu tek bilgisayarlarda müşteri geri bildirimini devre dışı bırakacak şekilde yapılandırmak istiyorsanız.

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs/)karşıladığından emin olun.

* Bakım gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi daha uzun bir süre içinde kalması, ancak hala düzenli bakım güncelleştirmelerini almak istiyorsa, bir hizmet temeli kullanmayı planlayın. Daha fazla bilgi için, Visual Studio [ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) sayfası 'nın yanı sıra [bir hizmet ana hat üzerinde Visual Studio 'yu güncelleştirme](update-servicing-baseline.md) bölümünde yer alan Visual ***Studio 'nun eski sürümleri için destek*** bölümüne bakın.

  Toplu özellik güncelleştirmeleriyle birlikte bakım güncelleştirmelerini uygulamayı planlıyorsanız en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almasını istiyorsunuz? Özellikle, güncelleştirmeleri Internet 'ten mi yoksa şirket genelindeki bir yerel paylaşımdan mı almak istediğinize karar verin. Ardından, yerel bir paylaşma kullanmayı seçerseniz, bireysel kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine karar verin ya da bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini ister misiniz?

  Visual Studio 'nun bir ağ yükleme düzeninin en son ürün güncelleştirmeleriyle güncelleştirilmesi olasıdır. böylece, Visual Studio 'nun en son güncelleştirmesi için bir yükleme noktası olarak ve ayrıca istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](../install/update-a-network-installation-of-visual-studio.md).

  İnternet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur. Daha fazla bilgi için bkz. [Visual Studio 'yu en düşük düzeyde çevrimdışı düzen kullanarak güncelleştirme](update-minimal-layout.md).

* Şirketinizin ihtiyaç duyacağı [iş yüklerini ve bileşenleri](workload-and-component-ids.md?view=vs-2017) belirleyin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2017) kullanıp kullanmayacağınızı belirleyin (betik dosyasında ayrıntıların yönetimini basitleştirir).

* Grup ilkesi etkinleştirmek istediğinize ve Visual Studio 'Yu tek bilgisayarlarda müşteri geri bildirimini devre dışı bırakacak şekilde yapılandırmak istiyorsanız.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1-Visual Studio ürün dosyalarını Indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin](workload-and-component-ids.md?view=vs-2019) .

* [Visual Studio ürün dosyaları için bir ağ paylaşma oluşturun](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>2. adım-yükleme betiği oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) kullanan bir yükleme betiği oluşturun.

  >[!NOTE]
  > Komut dosyalarını bir [yanıt dosyası](automated-installation-with-response-file.md?view=vs-2019)kullanarak basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* Seçim Kullanıcıların yazılımı ayrı olarak etkinleştirmesine gerek kalmaması için yükleme komut dosyasının parçası olarak [bir toplu lisans ürün anahtarı uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) .

* Seçim [Ürün güncelleştirmelerinin Son kullanıcılarınıza ne zaman ve nereden teslim edildiğini denetlemek](controlling-updates-to-visual-studio-deployments.md?view=vs-2019)için ağ yerleşimini güncelleştirin.

* Seçim Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe](set-defaults-for-enterprise-deployments.md?view=vs-2019) alındığı veya [paketlerin önbelleğe alınıp alınmayacağı](disable-or-move-the-package-cache.md?view=vs-2019)gibi, Visual Studio 'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* Seçim Grup ilkesi ayarlayın. [Visual Studio 'yu, tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakmak için de yapılandırabilirsiniz](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>3. adım-dağıtma

* Komut dosyanızı hedef geliştirici iş istasyonlarınızda yürütmek için tercih ettiğiniz dağıtım teknolojinizi kullanın.

## <a name="step-4---deploy-updates"></a>4. adım-güncelleştirmeleri dağıtma

* Güncelleştirilmiş bileşenleri eklemek için düzenli olarak 1. adımda kullandığınız komutu çalıştırarak, Visual Studio 'Nun [en son güncelleştirmeleriyle ağ konumunuzu yenileyin](update-a-network-installation-of-visual-studio.md?view=vs-2019) .

  Visual Studio 'Yu bir güncelleştirme betiği kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>5. adım-(Isteğe bağlı) Visual Studio araçlarını kullanma

İstemci makinelerde [yüklü Visual Studio örneklerini tespit etmenize ve yönetmenize](tools-for-managing-visual-studio-instances.md?view=vs-2019) yardımcı olacak çeşitli araçlar sunulmaktadır.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio yüklemesi, hata listesi F1 ve kod bağlantıları 'ndaki Bing aramalarına özel tür ekleme imkanı sunar. Visual Studio 'Yu, ilke ile aşağıdaki kayıt defteri anahtarının değerini değiştirerek, arama mekanizmanın herhangi bir özel kullanıcı türünü dahil etme özelliğini devre dışı bırakacak şekilde yapılandırabilirsiniz:

**"Putcustomtypeınbingsearch" DWORD 0**

Kayıt defteri, özel kayıt kovanının * Software\Microsoft\VisualStudio\16.0_ {InstanceId} \ Roslyn\ınternal\diagnostics \* dizininde bulunur. Kayıt defteri kovanının nasıl açılacağı hakkında yönergeler için bkz. [Visual Studio örneği için kayıt defterini düzenlemeyle](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1-Visual Studio ürün dosyalarını Indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin](workload-and-component-ids.md?view=vs-2017) .

* [Visual Studio ürün dosyaları için bir ağ paylaşma oluşturun](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>2. adım-yükleme betiği oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) kullanan bir yükleme betiği oluşturun.

  >[!NOTE]
  > Komut dosyalarını bir [yanıt dosyası](automated-installation-with-response-file.md?view=vs-2017)kullanarak basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* Seçim Kullanıcıların yazılımı ayrı olarak etkinleştirmesine gerek kalmaması için yükleme komut dosyasının parçası olarak [bir toplu lisans ürün anahtarı uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) .

* Seçim [Ürün güncelleştirmelerinin Son kullanıcılarınıza ne zaman ve nereden teslim edildiğini denetlemek](controlling-updates-to-visual-studio-deployments.md?view=vs-2017)için ağ yerleşimini güncelleştirin.

* Seçim Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe](set-defaults-for-enterprise-deployments.md?view=vs-2019) alındığı veya [paketlerin önbelleğe alınıp alınmayacağı](disable-or-move-the-package-cache.md?view=vs-2017)gibi, Visual Studio 'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* Seçim Grup ilkesi ayarlayın. [Visual Studio 'yu, tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakmak için de yapılandırabilirsiniz](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>3. adım-dağıtma

* Komut dosyanızı hedef geliştirici iş istasyonlarınızda yürütmek için tercih ettiğiniz dağıtım teknolojinizi kullanın.

## <a name="step-4---deploy-updates"></a>4. adım-güncelleştirmeleri dağıtma

* Güncelleştirilmiş bileşenleri eklemek için düzenli olarak 1. adımda kullandığınız komutu çalıştırarak, Visual Studio 'Nun [en son güncelleştirmeleriyle ağ konumunuzu yenileyin](update-a-network-installation-of-visual-studio.md?view=vs-2017) .

  Visual Studio 'Yu bir güncelleştirme betiği kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>5. adım-(Isteğe bağlı) Visual Studio araçlarını kullanma

İstemci makinelerde [yüklü Visual Studio örneklerini tespit etmenize ve yönetmenize](tools-for-managing-visual-studio-instances.md?view=vs-2017) yardımcı olacak çeşitli araçlar sunulmaktadır.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio yüklemesi, hata listesi F1 ve kod bağlantıları 'ndaki Bing aramalarına özel tür ekleme imkanı sunar. Visual Studio 'Yu, ilke ile aşağıdaki kayıt defteri anahtarının değerini değiştirerek, arama mekanizmanın herhangi bir özel kullanıcı türünü dahil etme özelliğini devre dışı bırakacak şekilde yapılandırabilirsiniz:

**"Putcustomtypeınbingsearch" DWORD 0**

Kayıt defteri, özel kayıt kovanının * Software\Microsoft\VisualStudio\15.0_ {InstanceId} \ Roslyn\ınternal\diagnostics \* dizininde bulunur. Kayıt defteri kovanının nasıl açılacağı hakkında yönergeler için bkz. [Visual Studio örneği için kayıt defterini düzenlemeyle](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Yükleme yapılandırmasını içeri veya dışarı aktarma](import-export-installation-configurations.md)
* [Visual Studio Kurulum arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
* [Zaman uyumlu oto yükleme ayarları](../extensibility/synchronously-autoloaded-extensions.md)
