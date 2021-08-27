---
title: Visual Studio Enterprise kılavuzu
description: kurumsal ortamda Visual Studio ayarlama ve sorun giderme.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 16624eb602b5ef02d7871ba579e0e2bdc5bdb337
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981017"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio Enterprise kılavuzu
şirketinizi Visual Studio çalışırken zamandan tasarruf ediyorsanız, buradan başlayın. bu kurumsal kılavuz, yaygın kurumsal senaryolarda Visual Studio yüklemenize ve güncelleştirmenize yardımcı olabilecek ipuçları ve daha fazla yardıma ihtiyacınız varsa bir sorunu nasıl bildirebileceğinizi öğrenmek içerir. 

## <a name="get-started"></a>başlarken 
kuruluşunuzun ağa ve çevrimdışı ortamlarda Visual Studio dağıtmayı öğrenin.

- **[Microsoft Endpoint Configuration Manager (SCCM) kullanarak yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)**.  Visual Studio güncelleştirmeler [Microsoft Update kataloğuna](https://www.catalog.update.microsoft.com/Home.aspx) ve [Windows Server Update Services 'a (WSUS)](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)dahildir. Enterprise yöneticiler daha sonra güncelleştirmeyi indirebilir ve Microsoft Endpoint Configuration Manager (SCCM) gibi standart dağıtım araçlarını kullanarak kuruluş genelinde Visual Studio istemci makinelerine dağıtabilir.

- **Ağ ortamlarında kurumsal dağıtım seçeneklerini anlayın**. [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md) , sistem yöneticileri için senaryo tabanlı yönergeler sağlar. 

- **[Sorun giderme Ipuçları alın](troubleshooting-installation-issues.md)**. Visual Studio yüklerken veya güncelleştirirken yardım alın ve bloke olduğunuzda bir sorunu nasıl bildirebileceğinizi öğrenin. Bu ipuçları, çoğu çevrimiçi veya çevrimdışı yükleme sorununu çözmek için adım adım yönergeleri içerir. 

- **[Visual Studio çevrimdışı yüklemesi oluşturun](create-an-offline-installation-of-visual-studio.md)**. Internet 'e bağlı değilseniz veya sınırlı Internet bağlantısına sahipseniz Visual Studio yükleme seçeneklerini bulun. 

- **[Önyükleyici paketleri oluşturun](../deployment/creating-bootstrapper-packages.md)**. Ürün ve paket bildirimleri oluşturarak özel önyükleyici paketleri oluşturmayı öğrenin. 

- **[Visual Studio dağıtımı sırasında ürün anahtarlarını otomatik olarak uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Visual Studio dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak ürün anahtarınızı programlı bir şekilde uygulayabilirsiniz. bir Visual Studio yüklemesi sırasında veya bir yükleme tamamlandıktan sonra, bir cihazdaki ürün anahtarını programlı bir şekilde ayarlayabilirsiniz. 

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme 

Visual Studio ortak kurumsal senaryolara nasıl yükleyeceğinizi öğrenin. 

- **[Visual Studio yüklemek için komut satırı parametrelerini kullanın](use-command-line-parameters-to-install-visual-studio.md)**. Visual Studio yüklemenizi denetlemek veya özelleştirmek için çeşitli parametreleri kullanın. Yükleme işlemini otomatikleştirin veya daha sonra kullanmak üzere yükleme dosyalarının bir önbelleğini oluşturun. Daha fazla bilgi için bkz. [komut satırı parametre örnekleri](command-line-parameter-examples.md).

- **[Visual Studio ağ yüklemesi oluşturun](create-a-network-installation-of-visual-studio.md)**. Tüm ürün güncelleştirmeleriyle birlikte, ilk yüklemenin dosyalarını tek bir klasöre önbelleğe alma. 

- **[Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanın](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. kuruluşunuz güvenlik duvarı veya ara sunucu gibi güvenlik önlemleri kullanıyorsa, Visual Studio ve Azure hizmetlerini yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "allowlist" ve bağlantı noktaları ve protokoller eklemek isteyebileceğiniz etki alanı url 'leri vardır. 

- **[Çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)**. İstemci makinenin internet bağlantısı tamamen kesildiğinde gerekli sertifikaları yükler.

## <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme 

Visual Studio başarıyla güncelleştirme ve güncelleştirme sorunlarını giderme hakkında bilgi edinin. 

- **[Microsoft Endpoint Configuration Manager (SCCM) kullanarak yönetici güncelleştirmelerini uygulayın](../install/applying-administrator-updates.md)**. SCCM aracılığıyla Visual Studio özellik, güvenlik ve kalite güncelleştirmeleri dağıtma hakkında bilgi edinin. 

- **[Visual Studio ağ tabanlı yüklemesini güncelleştirin](update-a-network-installation-of-visual-studio.md)**. Visual Studio bir ağ yüklemesi mizanpajını en son ürün güncelleştirmeleriyle güncelleştirin ve bu sayede, Visual Studio en son güncelleştirmesi için bir yükleme noktası olarak ve ayrıca istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapmak için kullanılabilir.

- **[hizmet ana temeliyle Visual Studio güncelleştirin](update-servicing-baseline.md)**. Bir taban çizgisi güncelleştirme sırasında değeri anlayın ve küçük yayınlar ile bakım güncelleştirmeleri arasındaki farkı öğrenin. 

- **[en düşük düzeyde çevrimdışı düzen kullanarak Visual Studio güncelleştirin](update-minimal-layout.md)**. internet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur.

- **güncelleştirme sorunlarını gidermek için [Visual Studio onarın](repair-visual-studio.md)**. bazen Visual Studio yüklemeniz hasar görmüşse veya bozulmuş olur. Güncelleştirme, güncelleştirmeleri de dahil olmak üzere tüm yük işlemlerinde karşıya yüklenmeye yönelik sorunları düzeltmek için faydalıdır. 

- **[Windows güvenlik temellerini](/windows/security/threat-protection/windows-security-baselines)izleyin**. Microsoft, müşterilerine Windows 10 ve Windows sunucusu gibi güvenli işletim sistemleri ve Microsoft Edge gibi güvenli uygulamalar sağlamaya ayrılmıştır. Microsoft, ürünlerinin güvenlik güvencesine ek olarak çeşitli yapılandırma özellikleri sunarak ortamlarınız üzerinde ince denetim sağlamanıza da imkan sağlar. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz. 

- [Visual Studio için üretkenlik Kılavuzu](../ide/productivity-features.md)

