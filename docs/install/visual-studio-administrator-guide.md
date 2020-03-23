---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Visual Studio'nun kurumsal ortamda nasıl dağıtılabildiğini öğrenin.
ms.date: 03/09/2020
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
ms.openlocfilehash: bda9a73a7a1aabb2d288653ff4d7b20b1c40db8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79190284"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kuruluş ortamlarında, sistem yöneticileri genellikle yüklemeleri ağ paylaşımından veya sistem yönetim yazılımı kullanarak son kullanıcılara dağıtır. Sistem yöneticilerine ağ yükleme konumu oluşturma, yükleme varsayılanlarını önceden yapılandırma, yükleme işlemi sırasında ürün anahtarlarını dağıtma olanağı sağlayarak kurumsal dağıtımı destekleyecek Visual Studio kurulum motorunu tasarladık ve başarılı bir ürün lansmanından sonra ürün güncelleştirmelerini yönetmek için.

Bu yönetici kılavuzu, ağ ortamlarında kurumsal dağıtım için senaryo tabanlı yönerge sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Visual Studio'yı kuruluşunuz genelinde dağıtmadan önce, karar vermeniz ve tamamlamanız gereken görevler vardır:

::: moniker range="vs-2019"

* Her hedef bilgisayarın minimum [yükleme gereksinimlerini](/visualstudio/releases/2019/system-requirements/)karşıladığından emin olun.

* Servis ihtiyaçlarınızı belirleyin.

  Şirketinizin bir özellik setinde daha uzun kalması gerekiyorsa ancak yine de düzenli servis güncelleştirmeleri almak istiyorsa, servis taban çizgisini kullanmayı planlayın. Daha fazla bilgi ***için*** Visual Studio ürün yaşam [döngüsü ve servis](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) sayfasının Kurumsal ve Profesyonel müşteriler için Destek seçenekleri nin yanı sıra servis taban çizgisi sayfasında [Visual Studio'yu nasıl güncelleyin](update-servicing-baseline.md) bölümüne bakın.

  Hizmet güncelleştirmelerini kümülatif özellik güncelleştirmeleriyle birlikte uygulamayı planlıyorsanız, en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almak istediğini? Özellikle, internetten veya şirket çapında yerel bir paylaşımdan güncelleme almak isteyip istemediğinizkarar verin. Ardından, yerel bir paylaşım kullanmayı seçerseniz, tek tek kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine veya bir yöneticinin istemcileri programlı olarak güncelleştirmesini isteyip istemediğinizi belirleyin.

* Şirketinizin hangi [iş yüklerine ve bileşenlere](workload-and-component-ids.md?view=vs-2019) ihtiyacı olduğuna karar verin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2019) kullanıp kullanmamaya karar verin (komut dosyası dosyasındaki ayrıntıları yönetmeyi kolaylaştırır).

* Grup İlkesi'ni etkinleştirmek isteyip istemediğinizi ve Visual Studio'yı tek tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakıp, visual studio'u yapılandırmak isteyip istemediğinizi belirleyin.

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın minimum [yükleme gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs/)karşıladığından emin olun.

* Servis ihtiyaçlarınızı belirleyin.

  Şirketinizin bir özellik setinde daha uzun kalması gerekiyorsa ancak yine de düzenli servis güncelleştirmeleri almak istiyorsa, servis taban çizgisini kullanmayı planlayın. Daha fazla bilgi için Visual Studio ürün yaşam [döngüsü ve servis](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) ***sayfasının Visual Studio bölümünün eski sürümleri için destek*** ve servis taban çizgisi [sayfasındayken Visual Studio'yu Nasıl Güncelleyin bölümüne](update-servicing-baseline.md) bakın.

  Hizmet güncelleştirmelerini kümülatif özellik güncelleştirmeleriyle birlikte uygulamayı planlıyorsanız, en son bitleri seçebilirsiniz.

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin güncelleştirmeleri nereden almak istediğini? Özellikle, internetten veya şirket çapında yerel bir paylaşımdan güncelleme almak isteyip istemediğinizkarar verin. Ardından, yerel bir paylaşım kullanmayı seçerseniz, tek tek kullanıcıların kendi istemcilerini güncelleştirip güncelleştiremeyeceğine veya bir yöneticinin istemcileri programlı olarak güncelleştirmesini isteyip istemediğinizi belirleyin.

* Şirketinizin hangi [iş yüklerine ve bileşenlere](workload-and-component-ids.md?view=vs-2017) ihtiyacı olduğuna karar verin.

* [Yanıt dosyası](automated-installation-with-response-file.md?view=vs-2017) kullanıp kullanmamaya karar verin (komut dosyası dosyasındaki ayrıntıları yönetmeyi kolaylaştırır).

* Grup İlkesi'ni etkinleştirmek isteyip istemediğinizi ve Visual Studio'yı tek tek bilgisayarlarda müşteri geri bildirimlerini devre dışı bırakıp, visual studio'u yapılandırmak isteyip istemediğinizi belirleyin.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1 - Visual Studio ürün dosyalarını indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin.](workload-and-component-ids.md?view=vs-2019)

* [Visual Studio ürün dosyaları için ağ paylaşımı oluşturun.](create-a-network-installation-of-visual-studio.md?view=vs-2019)

## <a name="step-2---build-an-installation-script"></a>Adım 2 - Yükleme komut dosyası oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) kullanan bir yükleme komut dosyası oluşturun.

  >[!NOTE]
  > Yanıt [dosyalarını](automated-installation-with-response-file.md?view=vs-2019)kullanarak komut dosyalarını basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* (İsteğe bağlı) Kullanıcıların yazılımı ayrı olarak etkinleştirmelerine gerek kalmaması için yükleme komut dosyasının bir parçası olarak [toplu lisans ürün anahtarı uygulayın.](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019)

* (İsteğe bağlı) [Ürün güncelleştirmelerinin son kullanıcılarınıza ne zaman ve nereden teslim edilecek](controlling-updates-to-visual-studio-deployments.md?view=vs-2019)lerini denetlemek için ağ düzenini güncelleştirin.

* (İsteğe bağlı) Diğer sürümlerle veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe alınıp alınmadığı](set-defaults-for-enterprise-deployments.md?view=vs-2019) veya [paketlerin önbelleğe alınıp alınmadığı](disable-or-move-the-package-cache.md?view=vs-2019)gibi Visual Studio'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* (İsteğe bağlı) Grup İlkesi ayarlayın. Ayrıca Visual Studio'yı tek tek bilgisayarlardaki [müşteri geri bildirimlerini devre dışı kılabilir](../ide/visual-studio-experience-improvement-program.md) şekilde yapılandırabilirsiniz.

## <a name="step-3---deploy"></a>Adım 3 - Dağıt

* Komut dosyanızı hedef geliştirici iş istasyonlarınıza çalıştırmak için seçtiğiniz dağıtım teknolojisini kullanın.

## <a name="step-4---deploy-updates"></a>Adım 4 - Güncellemeleri dağıt

* Güncelleştirilmiş bileşenler eklemek için adım 1'de kullandığınız komutu düzenli olarak çalıştırarak Visual Studio'daki [en son güncellemelerle ağ konumunuzu yenileyin.](update-a-network-installation-of-visual-studio.md?view=vs-2019)

  Visual Studio'yu bir güncelleştirme komut dosyası kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>Adım 5 - (İsteğe Bağlı) Visual Studio araçlarını kullanın

İstemci makinelerinde [yüklü Visual Studio örneklerini algılamanıza ve yönetmenize](tools-for-managing-visual-studio-instances.md?view=vs-2019) yardımcı olacak çeşitli araçlar mevcuttur.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio yüklemehata listesi F1 ve kod bağlantıları bing aramalarında özel tür ekleme sağlar. Aşağıdaki kayıt defteri anahtarının değerini ilke ile değiştirerek, Visual Studio'yu arama mekanizmasını belirli kullanıcı türlerini dahil etme durumunda devre dışı düşürecek şekilde yapılandırabilirsiniz:

**"PutCustomTypeinbingSearch" DWORD 0**

Kayıt defteri , özel kayıt defteri kovanının *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* dizininde yer alır. Kayıt defteri kovanının nasıl açIleceğine ilişkin talimatlar [için, Visual Studio örneği için kayıt defterini düzenlemeye](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance)bakın.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Adım 1 - Visual Studio ürün dosyalarını indirin

* Yüklemek istediğiniz [iş yüklerini ve bileşenleri seçin.](workload-and-component-ids.md?view=vs-2017)

* [Visual Studio ürün dosyaları için ağ paylaşımı oluşturun.](create-a-network-installation-of-visual-studio.md?view=vs-2017)

## <a name="step-2---build-an-installation-script"></a>Adım 2 - Yükleme komut dosyası oluşturma

* Yüklemeyi denetlemek için [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) kullanan bir yükleme komut dosyası oluşturun.

  >[!NOTE]
  > Yanıt [dosyalarını](automated-installation-with-response-file.md?view=vs-2017)kullanarak komut dosyalarını basitleştirebilirsiniz. Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası oluşturduğunuzdan emin olun.

* (İsteğe bağlı) Kullanıcıların yazılımı ayrı olarak etkinleştirmelerine gerek kalmaması için yükleme komut dosyasının bir parçası olarak [toplu lisans ürün anahtarı uygulayın.](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017)

* (İsteğe bağlı) [Ürün güncelleştirmelerinin son kullanıcılarınıza ne zaman ve nereden teslim edilecek](controlling-updates-to-visual-studio-deployments.md?view=vs-2017)lerini denetlemek için ağ düzenini güncelleştirin.

* (İsteğe bağlı) Diğer sürümlerle veya örneklerle paylaşılan bazı paketlerin yüklendiği, [paketlerin önbelleğe alınıp alınmadığı](set-defaults-for-enterprise-deployments.md?view=vs-2019) veya [paketlerin önbelleğe alınıp alınmadığı](disable-or-move-the-package-cache.md?view=vs-2017)gibi Visual Studio'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayın.

* (İsteğe bağlı) Grup İlkesi ayarlayın. Ayrıca Visual Studio'yı tek tek bilgisayarlardaki [müşteri geri bildirimlerini devre dışı kılabilir](../ide/visual-studio-experience-improvement-program.md) şekilde yapılandırabilirsiniz.

## <a name="step-3---deploy"></a>Adım 3 - Dağıt

* Komut dosyanızı hedef geliştirici iş istasyonlarınıza çalıştırmak için seçtiğiniz dağıtım teknolojisini kullanın.

## <a name="step-4---deploy-updates"></a>Adım 4 - Güncellemeleri dağıt

* Güncelleştirilmiş bileşenler eklemek için adım 1'de kullandığınız komutu düzenli olarak çalıştırarak Visual Studio'daki [en son güncellemelerle ağ konumunuzu yenileyin.](update-a-network-installation-of-visual-studio.md?view=vs-2017)

  Visual Studio'yu bir güncelleştirme komut dosyası kullanarak güncelleştirebilirsiniz. Bunu yapmak için [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) komut satırı parametresini kullanın.

## <a name="step-5---optional-use-visual-studio-tools"></a>Adım 5 - (İsteğe Bağlı) Visual Studio araçlarını kullanın

İstemci makinelerinde [yüklü Visual Studio örneklerini algılamanıza ve yönetmenize](tools-for-managing-visual-studio-instances.md?view=vs-2017) yardımcı olacak çeşitli araçlar mevcuttur.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio yüklemehata listesi F1 ve kod bağlantıları bing aramalarında özel tür ekleme sağlar. Aşağıdaki kayıt defteri anahtarının değerini ilke ile değiştirerek, Visual Studio'yu arama mekanizmasını belirli kullanıcı türlerini dahil etme durumunda devre dışı düşürecek şekilde yapılandırabilirsiniz:

**"PutCustomTypeinbingSearch" DWORD 0**

Kayıt defteri , özel kayıt defteri kovanının *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\* dizininde yer alır. Kayıt defteri kovanının nasıl açIleceğine ilişkin talimatlar [için, Visual Studio örneği için kayıt defterini düzenlemeye](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance)bakın.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio çevrimdışı yüklemesi için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Yükleme yapılandırmasını içeri veya dışarı aktarma](import-export-installation-configurations.md)
* [Visual Studio Kurulum Arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio ürün yaşam döngüsü ve servis](/visualstudio/releases/2019/servicing/)
* [Senkron otomatik yükleme ayarları](../extensibility/synchronously-autoloaded-extensions.md)
