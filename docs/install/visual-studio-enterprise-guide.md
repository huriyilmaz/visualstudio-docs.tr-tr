---
title: Visual Studio Enterprise kılavuzu
description: Visual Studio 'Yu bir kurumsal ortamda ayarlayın ve sorun giderin.
ms.date: 07/29/2020
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
ms.openlocfilehash: e653d7ae5f2408fd8438cbdf69a28648c6bcc446
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967117"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio Enterprise kılavuzu
Şirket Visual Studio 'da çalışır durumdayken zamandan tasarruf ediyorsanız, buradan başlayın. Bu kurumsal kılavuz, Visual Studio 'Yu ortak kurumsal senaryolarda yüklemenize ve güncelleştirmenize yardımcı olabilecek ipuçları ve daha fazla yardıma ihtiyacınız varsa bir sorunu nasıl bildirebileceğinizi öğrenmek içerir. 

## <a name="get-started"></a>başlarken 
Ağa bağlı ve çevrimdışı ortamlarda Visual Studio 'Yu kuruluşunuza dağıtmayı öğrenin. 

- **Ağ ortamlarında kurumsal dağıtım seçeneklerini anlayın**. [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md) , sistem yöneticileri için senaryo tabanlı yönergeler sağlar. 

- **[Sorun giderme Ipuçları alın](troubleshooting-installation-issues.md)**. Visual Studio 'Yu yüklerken veya güncelleştirirken yardım alın ve bloke olduğunuzda bir sorunu nasıl bildirebileceğinizi öğrenin. Bu ipuçları, çoğu çevrimiçi veya çevrimdışı yükleme sorununu çözmek için adım adım yönergeleri içerir. 

- **[Visual Studio 'nun çevrimdışı yüklemesini oluşturun](create-an-offline-installation-of-visual-studio.md)**. Internet 'e bağlı değilseniz veya sınırlı Internet bağlantısına sahipseniz, Visual Studio yükleme seçeneklerini bulun. 

- **[Önyükleyici paketleri oluşturun](../deployment/creating-bootstrapper-packages.md)**. Ürün ve paket bildirimleri oluşturarak özel önyükleyici paketleri oluşturmayı öğrenin. 

- **[Visual Studio 'yu dağıttığınızda ürün anahtarlarını otomatik olarak uygulayın](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Ürün anahtarınızı, Visual Studio 'nun dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak programlı bir şekilde uygulayabilirsiniz. Bir Visual Studio yüklemesi sırasında veya bir yükleme tamamlandıktan sonra bir cihazda program aracılığıyla bir ürün anahtarı ayarlayabilirsiniz. 

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme 

Visual Studio 'Yu ortak kurumsal senaryolara nasıl yükleyeceğinizi öğrenin. 

- **[Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanın](use-command-line-parameters-to-install-visual-studio.md)**. Visual Studio yüklemenizi denetlemek veya özelleştirmek için çeşitli parametreleri kullanın. Yükleme işlemini otomatikleştirin veya daha sonra kullanmak üzere yükleme dosyalarının bir önbelleğini oluşturun. 

- **Bkz. [Visual Studio yüklemesi için komut satırı parametresi örnekleri](command-line-parameter-examples.md)**. Visual Studio 'Yu yüklemek için komut satırı parametrelerinin nasıl kullanılacağını göstermek için, gereksinimlerinize uyacak şekilde özelleştirebileceğiniz çeşitli örnekleri görüntüleyin. 

- **[Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanın](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Kuruluşunuz bir güvenlik duvarı veya proxy sunucu gibi güvenlik önlemleri kullanıyorsa, Visual Studio ve Azure hizmetlerini yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "izin verilenler listesine" ve bağlantı noktalarına ve protokollere eklemek isteyebileceğiniz etki alanı URL 'Leri vardır. 

- **[Visual Studio 'nun bir ağ yüklemesini oluşturun](create-a-network-installation-of-visual-studio.md)**. Tüm ürün güncelleştirmeleriyle birlikte, ilk yüklemenin dosyalarını tek bir klasöre önbelleğe alma.  

## <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme 

Visual Studio 'Yu başarıyla güncelleştirme ve güncelleştirme sorunlarını giderme hakkında bilgi edinin. 

- **[Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirin](update-a-network-installation-of-visual-studio.md)**. Visual Studio 'nun bir ağ yükleme yerleşimini en son ürün güncelleştirmeleriyle güncelleştirin, böylece hem Visual Studio 'nun en son güncelleştirmesi için bir yükleme noktası hem de istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapabilirsiniz.

- **[Bakım temel alınarak Visual Studio 'Yu güncelleştirin](update-servicing-baseline.md)**. Bir taban çizgisi güncelleştirme sırasında değeri anlayın ve küçük yayınlar ile bakım güncelleştirmeleri arasındaki farkı öğrenin. 

- **[En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio 'Yu güncelleştirin](update-minimal-layout.md)**. İnternet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur.

- **Güncelleştirme sorunlarını gidermek Için [Visual Studio 'yu onarın](repair-visual-studio.md)**. Bazen Visual Studio yüklemenizin hasar görmüş veya bozuk hale gelir. Güncelleştirme, güncelleştirmeleri de dahil olmak üzere tüm yük işlemlerinde karşıya yüklenmeye yönelik sorunları düzeltmek için faydalıdır. 

- **[Windows Güvenlik temellerini](/windows/security/threat-protection/windows-security-baselines)izleyin**. Microsoft, müşterilerine Windows 10 ve Windows Server gibi güvenli işletim sistemleri ve Microsoft Edge gibi güvenli uygulamalar sağlamak için ayrılmıştır. Microsoft, ürünlerinin güvenlik güvencesine ek olarak çeşitli yapılandırma özellikleri sunarak ortamlarınız üzerinde ince denetim sağlamanıza da imkan sağlar. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz. 

- [Visual Studio için üretkenlik Kılavuzu](../ide/productivity-features.md)