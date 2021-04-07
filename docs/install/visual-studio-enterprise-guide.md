---
title: Visual Studio Enterprise kılavuzu
description: Visual Studio 'Yu bir kurumsal ortamda ayarlayın ve sorun giderin.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e5e8a28ac89c2bea85aee8323060bf948266ad2e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547394"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio Enterprise kılavuzu
Şirket Visual Studio 'da çalışır durumdayken zamandan tasarruf ediyorsanız, buradan başlayın. Bu kurumsal kılavuz, Visual Studio 'Yu ortak kurumsal senaryolarda yüklemenize ve güncelleştirmenize yardımcı olabilecek ipuçları ve daha fazla yardıma ihtiyacınız varsa bir sorunu nasıl bildirebileceğinizi öğrenmek içerir. 

## <a name="get-started"></a>başlarken 
Ağa bağlı ve çevrimdışı ortamlarda Visual Studio 'Yu kuruluşunuza dağıtmayı öğrenin.

- **[Microsoft uç nokta Configuration Manager (SCCM) kullanarak yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)**.  Visual Studio güncelleştirmeleri [Microsoft Update kataloğuna](https://www.catalog.update.microsoft.com/Home.aspx) ve [Windows Server Update SERVICES 'a (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)dahildir. Kurumsal Yöneticiler daha sonra güncelleştirmeyi indirebilir ve Microsoft uç nokta Configuration Manager (SCCM) gibi standart dağıtım araçlarını kullanarak kuruluş genelinde Visual Studio istemci makinelerine dağıtabilir.

- **Ağ ortamlarında kurumsal dağıtım seçeneklerini anlayın**. [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md) , sistem yöneticileri için senaryo tabanlı yönergeler sağlar. 

- **[Sorun giderme Ipuçları alın](troubleshooting-installation-issues.md)**. Visual Studio 'Yu yüklerken veya güncelleştirirken yardım alın ve bloke olduğunuzda bir sorunu nasıl bildirebileceğinizi öğrenin. Bu ipuçları, çoğu çevrimiçi veya çevrimdışı yükleme sorununu çözmek için adım adım yönergeleri içerir. 

- **[Visual Studio 'nun çevrimdışı yüklemesini oluşturun](create-an-offline-installation-of-visual-studio.md)**. Internet 'e bağlı değilseniz veya sınırlı Internet bağlantısına sahipseniz, Visual Studio yükleme seçeneklerini bulun. 

- **[Önyükleyici paketleri oluşturun](../deployment/creating-bootstrapper-packages.md)**. Ürün ve paket bildirimleri oluşturarak özel önyükleyici paketleri oluşturmayı öğrenin. 

- **[Visual Studio 'yu dağıttığınızda ürün anahtarlarını otomatik olarak uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Ürün anahtarınızı, Visual Studio 'nun dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak programlı bir şekilde uygulayabilirsiniz. Bir Visual Studio yüklemesi sırasında veya bir yükleme tamamlandıktan sonra bir cihazda program aracılığıyla bir ürün anahtarı ayarlayabilirsiniz. 

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme 

Visual Studio 'Yu ortak kurumsal senaryolara nasıl yükleyeceğinizi öğrenin. 

- **[Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanın](use-command-line-parameters-to-install-visual-studio.md)**. Visual Studio yüklemenizi denetlemek veya özelleştirmek için çeşitli parametreleri kullanın. Yükleme işlemini otomatikleştirin veya daha sonra kullanmak üzere yükleme dosyalarının bir önbelleğini oluşturun. Daha fazla bilgi için bkz. [komut satırı parametre örnekleri](command-line-parameter-examples.md).

- **[Visual Studio 'nun bir ağ yüklemesini oluşturun](create-a-network-installation-of-visual-studio.md)**. Tüm ürün güncelleştirmeleriyle birlikte, ilk yüklemenin dosyalarını tek bir klasöre önbelleğe alma. 

- **[Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanın](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Kuruluşunuz bir güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, Visual Studio ve Azure hizmetlerini yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "allowlist" ve bağlantı noktaları ve protokoller eklemek isteyebileceğiniz etki alanı URL 'Leri vardır. 

- **[Çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)**. İstemci makinenin internet bağlantısı tamamen kesildiğinde gerekli sertifikaları yükler.

## <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme 

Visual Studio 'Yu başarıyla güncelleştirme ve güncelleştirme sorunlarını giderme hakkında bilgi edinin. 

- **[Microsoft uç noktası Configuration Manager (SCCM) kullanarak yönetici güncelleştirmelerini uygulayın](../install/applying-administrator-updates.md)**. SCCM aracılığıyla Visual Studio özelliği, güvenlik ve kalite güncelleştirmeleri dağıtma hakkında bilgi edinin. 

- **[Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirin](update-a-network-installation-of-visual-studio.md)**. Visual Studio 'nun bir ağ yükleme yerleşimini en son ürün güncelleştirmeleriyle güncelleştirin, böylece hem Visual Studio 'nun en son güncelleştirmesi için bir yükleme noktası hem de istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapabilirsiniz.

- **[Bakım temel alınarak Visual Studio 'Yu güncelleştirin](update-servicing-baseline.md)**. Bir taban çizgisi güncelleştirme sırasında değeri anlayın ve küçük yayınlar ile bakım güncelleştirmeleri arasındaki farkı öğrenin. 

- **[En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio 'Yu güncelleştirin](update-minimal-layout.md)**. İnternet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur.

- **Güncelleştirme sorunlarını gidermek Için [Visual Studio 'yu onarın](repair-visual-studio.md)**. Bazen Visual Studio yüklemenizin hasar görmüş veya bozuk hale gelir. Güncelleştirme, güncelleştirmeleri de dahil olmak üzere tüm yük işlemlerinde karşıya yüklenmeye yönelik sorunları düzeltmek için faydalıdır. 

- **[Windows Güvenlik temellerini](/windows/security/threat-protection/windows-security-baselines)izleyin**. Microsoft, müşterilerine Windows 10 ve Windows Server gibi güvenli işletim sistemleri ve Microsoft Edge gibi güvenli uygulamalar sağlamak için ayrılmıştır. Microsoft, ürünlerinin güvenlik güvencesine ek olarak çeşitli yapılandırma özellikleri sunarak ortamlarınız üzerinde ince denetim sağlamanıza da imkan sağlar. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz. 

- [Visual Studio için üretkenlik Kılavuzu](../ide/productivity-features.md)

