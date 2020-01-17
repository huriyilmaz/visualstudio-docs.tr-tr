---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Visual Studio bir kuruluş ortamında dağıtma hakkında daha fazla bilgi edinin.
ms.date: 06/02/2019
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: 9f4b044cddee59254e0b4f5198e75e3fa774aab7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114212"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kurumsal ortamlarda, sistem yöneticileri genellikle son kullanıcılara bir ağ paylaşımından veya sistem yönetimi yazılımını kullanarak yükleme dağıtır. Sistem yöneticilerine, Yükleme varsayılanlarını önceden yapılandırmak, yükleme işlemi sırasında ürün anahtarlarını dağıtmak için, bir ağ yükleme konumu oluşturma olanağı sunarak, Visual Studio Kurulum altyapısını kurumsal dağıtımı destekleyecek şekilde tasarlıyoruz ve başarılı bir dağıtım sonrasında ürün güncelleştirmelerini yönetmek için.

Bu Yönetici Kılavuzu, ağa bağlı ortamlarda kurumsal dağıtım için senaryo tabanlı rehberlik sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuz genelinde Visual Studio 'Yu dağıtmadan önce, yapmanız gereken birkaç karar vardır:

::: moniker range="vs-2019"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/releases/2019/system-requirements/)karşıladığından emin olun.

* Bakım gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi daha uzun bir süre içinde kalması, ancak hala düzenli bakım güncelleştirmelerini almak istiyorsa, bir hizmet temeli kullanmayı planlayın. Daha fazla bilgi için bkz. [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) sayfasının ***Enterprise ve Professional müşterilerine yönelik destek seçenekleri*** ve [hizmet ana hat sırasında Visual Studio 'yu güncelleştirme](update-servicing-baseline.md) sayfası.

  Toplu özellik güncelleştirmeleriyle birlikte bakım güncelleştirmelerini uygulamayı planlıyorsanız en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almasını istiyorsunuz? Özellikle, güncelleştirmeleri Internet 'ten mi yoksa şirket genelindeki bir yerel paylaşımdan mı almak istediğinize karar verin. Ardından, yerel bir paylaşma kullanmayı seçerseniz, bireysel kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine karar verin ya da bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini ister misiniz?

* Şirketinizin ihtiyaç duyacağı [iş yüklerini ve bileşenleri](workload-and-component-ids.md?view=vs-2019) belirleyin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2019) kullanıp kullanmayacağınızı belirleyin (betik dosyasında ayrıntıların yönetimini basitleştirir).

* Grup ilkesi etkinleştirmek istediğinize ve Visual Studio 'Yu tek bilgisayarlarda müşteri geri bildirimini devre dışı bırakacak şekilde yapılandırmak istiyorsanız.

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın [En düşük yükleme gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs/)karşıladığından emin olun.

* Bakım gereksinimlerinize karar verin.

  Şirketinizin bir özellik kümesi daha uzun bir süre içinde kalması, ancak hala düzenli bakım güncelleştirmelerini almak istiyorsa, bir hizmet temeli kullanmayı planlayın. Daha fazla bilgi için bkz. Visual Studio [ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) sayfasının ***eski sürümleri için destek*** ve [hizmet temeli sırasında Visual Studio 'yu güncelleştirme](update-servicing-baseline.md) .

  Toplu özellik güncelleştirmeleriyle birlikte bakım güncelleştirmelerini uygulamayı planlıyorsanız en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almasını istiyorsunuz? Özellikle, güncelleştirmeleri Internet 'ten mi yoksa şirket genelindeki bir yerel paylaşımdan mı almak istediğinize karar verin. Ardından, yerel bir paylaşma kullanmayı seçerseniz, bireysel kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine karar verin ya da bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini ister misiniz?

* Şirketinizin ihtiyaç duyacağı [iş yüklerini ve bileşenleri](workload-and-component-ids.md?view=vs-2017) belirleyin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2017) kullanıp kullanmayacağınızı belirleyin (betik dosyasında ayrıntıların yönetimini basitleştirir).

* Grup ilkesi etkinleştirmek istediğinize ve Visual Studio 'Yu tek bilgisayarlarda müşteri geri bildirimini devre dışı bırakacak şekilde yapılandırmak istiyorsanız.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1-Visual Studio ürün dosyalarını Indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin](workload-and-component-ids.md?view=vs-2019) .

* [Visual Studio ürün dosyaları için bir ağ paylaşma oluşturun](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>2\. adım-yükleme betiği oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) kullanan bir yükleme betiği oluşturun.

  >[!NOTE]
  > Komut dosyalarını bir [yanıt dosyası](automated-installation-with-response-file.md?view=vs-2019)kullanarak basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* Seçim Kullanıcıların yazılımı ayrı olarak etkinleştirmesine gerek kalmaması için yükleme komut dosyasının parçası olarak [bir toplu lisans ürün anahtarı uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) .

* Seçim [Ürün güncelleştirmelerinin Son kullanıcılarınıza ne zaman ve nereden teslim edildiğini denetlemek](controlling-updates-to-visual-studio-deployments.md?view=vs-2019)için ağ yerleşimini güncelleştirin.

* Seçim Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe](set-defaults-for-enterprise-deployments.md?view=vs-2019) alındığı veya [paketlerin önbelleğe alınıp alınmayacağı](disable-or-move-the-package-cache.md?view=vs-2019)gibi, Visual Studio 'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* Seçim Grup ilkesi ayarlayın. [Visual Studio 'yu, tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakmak için de yapılandırabilirsiniz](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>3\. adım-dağıtma

* Komut dosyanızı hedef geliştirici iş istasyonlarınızda yürütmek için tercih ettiğiniz dağıtım teknolojinizi kullanın.

## <a name="step-4---deploy-updates"></a>4\. adım-güncelleştirmeleri dağıtma

* [En son güncelleştirmeleri içeren ağ konumunuza Yenile](update-a-network-installation-of-visual-studio.md?view=vs-2019) Visual Studio, kullandığınız komutunu çalıştırarak güncelleştirilmiş bileşenleri eklemek için düzenli olarak adım 1.

  Visual Studio 'Yu bir güncelleştirme betiği kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>5\. adım-(Isteğe bağlı) Visual Studio araçlarını kullanma

Yardımcı olacak çeşitli araçlar sunuyoruz [algılamak ve yüklü Visual Studio Örnekleri yönetme](tools-for-managing-visual-studio-instances.md?view=vs-2019) istemci makinelerinde.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1-Visual Studio ürün dosyalarını Indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin](workload-and-component-ids.md?view=vs-2017) .

* [Visual Studio ürün dosyaları için bir ağ paylaşma oluşturun](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>2\. adım-yükleme betiği oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) kullanan bir yükleme betiği oluşturun.

  >[!NOTE]
  > Komut dosyalarını bir [yanıt dosyası](automated-installation-with-response-file.md?view=vs-2017)kullanarak basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* Seçim Kullanıcıların yazılımı ayrı olarak etkinleştirmesine gerek kalmaması için yükleme komut dosyasının parçası olarak [bir toplu lisans ürün anahtarı uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) .

* Seçim [Ürün güncelleştirmelerinin Son kullanıcılarınıza ne zaman ve nereden teslim edildiğini denetlemek](controlling-updates-to-visual-studio-deployments.md?view=vs-2017)için ağ yerleşimini güncelleştirin.

* Seçim Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe](set-defaults-for-enterprise-deployments.md?view=vs-2019) alındığı veya [paketlerin önbelleğe alınıp alınmayacağı](disable-or-move-the-package-cache.md?view=vs-2017)gibi, Visual Studio 'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* Seçim Grup ilkesi ayarlayın. [Visual Studio 'yu, tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakmak için de yapılandırabilirsiniz](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>3\. adım-dağıtma

* Komut dosyanızı hedef geliştirici iş istasyonlarınızda yürütmek için tercih ettiğiniz dağıtım teknolojinizi kullanın.

## <a name="step-4---deploy-updates"></a>4\. adım-güncelleştirmeleri dağıtma

* [En son güncelleştirmeleri içeren ağ konumunuza Yenile](update-a-network-installation-of-visual-studio.md?view=vs-2017) Visual Studio, kullandığınız komutunu çalıştırarak güncelleştirilmiş bileşenleri eklemek için düzenli olarak adım 1.

  Visual Studio 'Yu bir güncelleştirme betiği kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>5\. adım-(Isteğe bağlı) Visual Studio araçlarını kullanma

Yardımcı olacak çeşitli araçlar sunuyoruz [algılamak ve yüklü Visual Studio Örnekleri yönetme](tools-for-managing-visual-studio-instances.md?view=vs-2017) istemci makinelerinde.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio'yu çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Yükleme yapılandırmasını içeri veya dışarı aktarma](import-export-installation-configurations.md)
* [Visual Studio Kurulum arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
* [Zaman uyumlu oto yükleme ayarları](../extensibility/synchronously-autoloaded-extensions.md)
