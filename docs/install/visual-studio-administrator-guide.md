---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Kurumsal bir ortamda Visual Studio hakkında daha fazla bilgi.
ms.date: 04/06/2021
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
ms.openlocfilehash: 94017ca1ab0d8ac7f390bcf348b2eef94ff14bfa
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453392"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio yönetici kılavuzu

Kurumsal ortamlarda sistem yöneticileri genellikle son kullanıcılara bir ağ paylaşımından veya sistem yönetimi yazılımını kullanarak yükleme dağıtır. Visual Studio kurulum altyapısını sistem yöneticilerine bir ağ yükleme konumu oluşturma, yükleme varsayılanlarını önceden yapılandırma, yükleme işlemi sırasında ürün anahtarlarını dağıtma ve başarılı bir dağıtımdan sonra ürün güncelleştirmelerini yönetme olanağı vererek kurumsal dağıtımı destekleyecek şekilde tasarladık.

Bu yönetici kılavuzu, ağa bağlı ortamlarda kurumsal dağıtım için senaryo tabanlı rehberlik sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluş genelinde Visual Studio dağıtmadan önce, tamamlanması gereken birkaç karar ve görev vardır:

::: moniker range=">=vs-2019"

* Her hedef bilgisayarın en düşük yükleme gereksinimlerini [karşılaya olduğundan emin olun.](/visualstudio/releases/2019/system-requirements/)

::: moniker-end

::: moniker range="vs-2017"

* Her hedef bilgisayarın en düşük yükleme gereksinimlerini [karşılaya olduğundan emin olun.](/visualstudio/productinfo/vs2017-system-requirements-vs/)

::: moniker-end

* Hizmet ihtiyaçlarınıza karar verin.

  Şirketinizin bir özellik kümesi üzerinde daha uzun süre kalması ama yine de düzenli bakım güncelleştirmeleri almak istiyorsa, bir bakım temeli kullanmayı planla. Daha fazla bilgi için Visual Studio yaşam döngüsü ve bakım ***sayfasının Enterprise*** ve Professional müşterileri için destek seçeneklerinin yanı sıra bakım temeli sayfasındaki [Güncelleştirme Visual Studio](update-servicing-baseline.md) bölümüne bakın. [](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)

* Güncelleştirme modeline karar verin.

  Tek tek istemci makinelerinin ürün güncelleştirmelerini nereden almak istiyorsunuz? Özellikle, istemcinin güncelleştirmeleri internetten mi yoksa şirket genelindeki bir yerel paylaşımdan mı almak istediğinize karar verin. Ardından, yerel bir paylaşım kullanmayı seçerseniz, tek tek kullanıcıların kendi istemcilerini güncelleştirip güncelleştirelerine veya bir yöneticinin istemcileri program aracılığıyla güncelleştirmesini isteyip istemediklerine karar verin. Bu kararların istemci makinede özgün yükleme öncesinden önce yapılmışsa en iyi uygulamadır. Daha fazla bilgi için, [bkz. Create a network-based installation of Visual Studio.](../install/create-a-network-installation-of-visual-studio.md)

  Visual Studio'nin ağ yükleme düzenini en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz; böylece hem Visual Studio'nin en son güncelleştirmesi için bir yükleme noktası olarak hem de istemci iş istasyonlarına dağıtılmış olan yüklemelerin bakımını yapmak için kullanılabilir. Daha fazla bilgi için [bkz. Ağ tabanlı yüklemesini güncelleştirme Visual Studio.](../install/update-a-network-installation-of-visual-studio.md)

  Kurumsal dağıtım araçlarını kullanan kuruluşlar, Visual Studio Kataloğu'Microsoft Update Sunucu Güncelleştirme Hizmetleri'Windows güncelleştirmelerinin mevcut olması avantajını kullanabilir. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md) [ve Yönetici güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md)

  İnternet'e bağlı olan bilgisayarlar için en az düzen oluşturmak, çevrimdışı örneklerinizi güncelleştirmenin en kolay ve en Visual Studio yöntemdir. Daha fazla bilgi için [bkz. En Visual Studio düzeni kullanarak güncelleştirme.](update-minimal-layout.md)

::: moniker range=">=vs-2019"

* Hangi iş [yüklerine ve bileşenlere ihtiyaç olduğuna](workload-and-component-ids.md?view=vs-2019&preserve-view=true) karar verin.

* Yanıt dosyası kullanıp [kullanmay kararını verin](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (bu, betik dosyasındaki ayrıntıları yönetmeyi basitleştiren).

::: moniker-end

::: moniker range="vs-2017"

* Hangi iş [yüklerine ve bileşenlere ihtiyaç olduğuna](workload-and-component-ids.md?view=vs-2017&preserve-view=true) karar verin.

* Yanıt dosyası kullanıp [kullanmay kararını verin](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (bu, betik dosyasındaki ayrıntıları yönetmeyi basitleştiren).

::: moniker-end

* Tek tek bilgisayarlardaki müşteri geri grup ilkesi devre dışı bırakmak için Visual Studio yapılandırmak istediğinize karar verin.

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>1. Adım - Visual Studio dosyalarını indirme

* [Yüklemek istediğiniz iş yüklerini](workload-and-component-ids.md?view=vs-2019&preserve-view=true) ve bileşenleri seçin.

* [Yeni ürün dosyaları için bir Visual Studio paylaşımı oluşturun.](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true)

## <a name="step-2---build-an-installation-script"></a>2. Adım - Yükleme betiği oluşturma

* Yüklemeyi kontrol etmek için [komut satırı parametrelerini kullanan bir yükleme](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) betiği derleme.

  >[!NOTE]
  > Bir yanıt dosyası kullanarak betikleri [basitleştirebilirsiniz.](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası sanız emin olun.

* (İsteğe bağlı) [Kullanıcıların yazılımı ayrı olarak etkinleştirmesi](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) gerekmay için yükleme betiği kapsamında bir toplu lisans ürün anahtarı uygulama.

* (İsteğe bağlı) Ürün güncelleştirmelerinin son [kullanıcılarınıza ne zaman ve nereden teslim edileceklerini kontrol etmek için ağ düzenini güncelleştirin.](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true)

* (İsteğe bağlı) Diğer sürümler veya örneklerle paylaşılan bazı Visual Studio, paketlerin önbelleğe alınıp alınmamayları gibi dağıtım ayarlarının dağıtımını etkileyen [kayıt defteri ilkeleri ayarlayın.](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true) [](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true)

* (İsteğe bağlı) Kümeyi grup ilkesi. Ayrıca, tek [tek bilgisayarlarda Visual Studio geri bildirimlerini devre dışı bırakmak için yapılandırmayı](../ide/visual-studio-experience-improvement-program.md) da yapılandırabilirsiniz.

## <a name="step-3---deploy-updates"></a>3. Adım - Güncelleştirmeleri dağıtma

Betiğinizi hedef geliştirici iş istasyonlarınıza yürütmek için tercih edilen dağıtım teknolojinizi kullanın.

* [1. adımda düzenli olarak güncelleştirilmiş](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) bileşenler eklemek için Visual Studio komutunu çalıştırarak ağ konumlarınızı en son güncelleştirmelerle yenileyin.

  Güncelleştirme betiği Visual Studio güncelleştirme betiği kullanarak bu dosyaları güncelleştirin. Bunu yapmak için komut [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) satırı parametresini kullanın.

  Windows Server Update Services'Visual Studio güncelleştirmelerini veya Microsoft Update Kataloğu'System Center Configuration Manager.  Daha fazla [bilgi için Bkz.](applying-administrator-updates.md) Yönetici güncelleştirmelerini uygulama. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>4. Adım - (İsteğe bağlı) Visual Studio doğrulama araçları kullanma

İstemci makinelerde yüklü örnekleri [algılamanıza ve yönetmenize yardımcı Visual Studio çeşitli](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) araçlarımız vardır.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio, F1 hata listesinden ve kod bağlantılarından Bing özel tür eklemeye olanak sağlar. İlkeye Visual Studio kayıt defteri anahtarının değerini değiştirerek arama mekanizmasını herhangi bir özel kullanıcı türü dahil etmek üzere devre dışı bırakmak üzere yapılandırmayı yapılandırarak şunları yapabilirsiniz:

**"PutCustomTypeInBingSearch" DWORD 0**

Kayıt defteri, özel kayıt defteri kovanının *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics \* dizininde bulunur. Kayıt defteri kovanını açma yönergeleri için bkz. kayıt [defterini bir Visual Studio düzenleme.](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>1. Adım - Visual Studio dosyalarını indirme

* [Yüklemek istediğiniz iş yüklerini](workload-and-component-ids.md?view=vs-2017&preserve-view=true) ve bileşenleri seçin.

* [Yeni ürün dosyaları için bir Visual Studio paylaşımı oluşturun.](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true)

## <a name="step-2---build-an-installation-script"></a>2. Adım - Yükleme betiği oluşturma

* Yüklemeyi kontrol etmek için [komut satırı parametrelerini kullanan bir yükleme](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) betiği derleme.

  >[!NOTE]
  > Bir yanıt dosyası kullanarak betikleri [basitleştirebilirsiniz.](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) Varsayılan yükleme seçeneğinizi içeren bir yanıt dosyası sanız emin olun.

* (İsteğe bağlı) [Kullanıcıların yazılımı ayrı olarak etkinleştirmesi](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) gerekmay için yükleme betiği kapsamında bir toplu lisans ürün anahtarı uygulama.

* (İsteğe bağlı) Ürün güncelleştirmelerinin son [kullanıcılarınıza ne zaman ve nereden teslim edileceklerini kontrol etmek için ağ düzenini güncelleştirin.](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true)

* (İsteğe bağlı) Diğer sürümler veya örneklerle paylaşılan bazı Visual Studio, paketlerin önbelleğe alınıp alınmamayları gibi dağıtım ayarlarının dağıtımını etkileyen [kayıt defteri ilkeleri ayarlayın.](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true) [](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true)

* (İsteğe bağlı) Kümeyi grup ilkesi. Ayrıca, tek [tek bilgisayarlarda Visual Studio geri bildirimlerini devre dışı bırakmak için yapılandırmayı](../ide/visual-studio-experience-improvement-program.md) da yapılandırabilirsiniz.

## <a name="step-3---deploy-updates"></a>3. Adım - Güncelleştirmeleri dağıtma

Betiğinizi hedef geliştirici iş istasyonlarınıza yürütmek için tercih edilen dağıtım teknolojinizi kullanın.

* [1. adımda düzenli olarak güncelleştirilmiş](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) bileşenler eklemek için Visual Studio komutunu çalıştırarak ağ konumlarınızı en son güncelleştirmelerle yenileyin.

  Güncelleştirme betiği Visual Studio güncelleştirme betiği kullanarak bu dosyaları güncelleştirin. Bunu yapmak için komut [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) satırı parametresini kullanın.

  Windows Server Update Services'Visual Studio güncelleştirmelerini veya Microsoft Update Kataloğu'System Center Configuration Manager. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini uygulama.](applying-administrator-updates.md)

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>4. Adım - (İsteğe bağlı) Visual Studio doğrulama araçları kullanma

İstemci makinelerde yüklü örnekleri [algılamanıza ve yönetmenize yardımcı Visual Studio çeşitli](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) araçlarımız vardır.

## <a name="advanced-configuration"></a>Gelişmiş yapılandırma

Varsayılan olarak, Visual Studio, F1 hata listesinden ve kod bağlantılarından Bing özel tür eklemeye olanak sağlar. İlkeye Visual Studio kayıt defteri anahtarının değerini değiştirerek arama mekanizmasını herhangi bir özel kullanıcı türü dahil etmek üzere devre dışı bırakmak üzere yapılandırmayı yapılandırarak şunları yapabilirsiniz:

**"PutCustomTypeInBingSearch" DWORD 0**

Kayıt defteri, özel kayıt `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` defteri kovanının dizininde bulunur. Kayıt defteri kovanını açma yönergeleri için bkz. kayıt [defterini bir Visual Studio düzenleme.](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

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
