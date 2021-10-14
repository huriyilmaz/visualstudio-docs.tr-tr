---
title: Visual Studio Enterprise kılavuzu
description: Kurumsal bir ortamda Visual Studio ayarlama ve sorun giderme.
ms.date: 04/06/2021
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
ms.openlocfilehash: 39acfccc16472215a368594b7562bb9eefa724cd
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969378"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio Enterprise kılavuzu
Şirketinizi şirket içinde çalıştırmaya başlarken zaman kazanmak Visual Studio buradan başlayabilirsiniz. Bu kurumsal kılavuz, yaygın kurumsal senaryolarda Visual Studio güncelleştirme, sorun yaşamanıza engeli kaldırma ve daha fazla yardıma ihtiyacınız olursa sorun bildirme hakkında bilgi edinme konusunda size yardımcı olacak ipuçları içerir. 

## <a name="get-started"></a>başlarken 
Ağa bağlı ve Visual Studio ortamlarda işletmenize sanal ağ dağıtımı yapmayı öğrenin.

- **[Microsoft Endpoint Configuration Manager (SCCM) kullanarak Yönetici Güncelleştirmelerini etkinleştirme.](enabling-administrator-updates.md)**  Visual Studio güncelleştirmeleri, [Microsoft Update Kataloğu'Windows](https://www.catalog.update.microsoft.com/Home.aspx) Sunucu Güncelleştirme [Hizmetleri 'ne (WSUS) dahil edilir.](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) Enterprise yöneticileri daha sonra güncelleştirmeyi indirebilir ve Visual Studio (SCCM) gibi standart dağıtım araçlarını kullanarak kuruluş genelindeki Microsoft Endpoint Configuration Manager makinelere dağıtabilirsiniz.

- **Ağa bağlı ortamlarda kurumsal dağıtım seçeneklerini anlama.** Yönetici [Visual Studio, sistem](visual-studio-administrator-guide.md) yöneticileri için senaryo tabanlı rehberlik sağlar. 

- **[Sorun giderme ipuçlarına bakın.](troubleshooting-installation-issues.md)** Bir uygulamayı yüklerken veya Visual Studio yardım edin ve engellenen bir sorunu bildirmeyi öğrenin. Bu ipuçları, çevrimiçi veya çevrimdışı yükleme sorunlarının çoğunu çözmesi gereken adım adım yönergeleri içerir. 

- **[Visual Studio'nin çevrimdışı yüklemesini oluşturun.](create-an-offline-installation-of-visual-studio.md)** İnternet'e bağlı değil veya sınırlı İnternet bağlantınız varsa, İnternet'i yükleme Visual Studio. 

- **[Önyükleyici paketleri oluşturun.](../deployment/creating-bootstrapper-packages.md)** Ürün ve paket bildirimleri oluşturarak özel önyükleyici paketleri oluşturmayı öğrenin. 

- **[ürününü dağıtırken ürün anahtarlarını otomatik Visual Studio.](automatically-apply-product-keys-when-deploying-visual-studio.md)** Ürün anahtarınızı program aracılığıyla, ürün anahtarı dağıtımını otomatikleştirmek için kullanılan bir betiğin parçası olarak Visual Studio. Ürün anahtarını, cihaz yüklemesi sırasında veya yükleme tamamlandıktan Visual Studio bir cihaza program aracılığıyla kurabilirsiniz. 

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme 

Yaygın kurumsal senaryolarda Visual Studio yükleme hakkında bilgi. 

- **[komutunu yüklemek için komut satırı Visual Studio.](use-command-line-parameters-to-install-visual-studio.md)** Uygulama yüklemenizi kontrol etmek veya özelleştirmek için çeşitli Visual Studio kullanın. Yükleme işlemini otomatikleştirin veya daha sonra kullanmak üzere yükleme dosyalarının önbelleğini oluşturun. Daha fazla bilgi için [bkz. komut satırı parametresi örnekleri.](command-line-parameter-examples.md)

- **[Visual Studio.](create-a-network-installation-of-visual-studio.md)** İlk yükleme için dosyaları ve tüm ürün güncelleştirmelerini tek bir klasöre önbelleğe alın. 

- **[Bir güvenlik duvarı Visual Studio proxy sunucusunun arkasında azure hizmetlerini ve Azure Hizmetlerini yükleyin ve kullanın.](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)** Kuruluşta güvenlik duvarı veya ara sunucu gibi güvenlik önlemleri kullanıyorsa, Visual Studio ve Azure Hizmetleri'nin yükleme ve kullanma deneyimine sahip olmak için açmak istediğiniz bir "izin verme listesine" ve bağlantı noktalarına ve protokollere eklemek istediğiniz etki alanı URL'leri vardır. 

- **[Çevrimdışı yükleme için gerekli sertifikaları yükleyin.](../install/install-certificates-for-visual-studio-offline.md)** İstemci makinesinin İnternet bağlantısı tamamen kesiliyorsa gerekli sertifikaları yükleyin.

## <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme 

Güncelleştirme sorunlarını başarıyla Visual Studio ve düzeltmeyi öğrenin. 

- **[Microsoft Endpoint Configuration Manager (SCCM) kullanarak Yönetici Güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md)** SCCM aracılığıyla Visual Studio, güvenlik ve kalite güncelleştirmelerini dağıtma hakkında bilgi alın. 

- **[Visual Studio'nin ağ tabanlı yüklemesini Visual Studio.](update-a-network-installation-of-visual-studio.md)** Visual Studio'nin ağ yükleme düzenini en son ürün güncelleştirmeleriyle güncelleştirin; böylece hem Visual Studio'nin en son güncelleştirmesi için bir yükleme noktası olarak hem de istemci iş istasyonlarına zaten dağıtılmış olan yüklemeleri korumak için kullanılabilir.

- **[Bakım Visual Studio sırasında güncelleştirme.](update-servicing-baseline.md)** Taban çizgisi üzerinde güncelleştirmenin değerini anlama ve ikincil sürümler ile bakım güncelleştirmeleri arasındaki farkı öğrenin. 

- **[En Visual Studio bir çevrimdışı düzen kullanarak güncelleştirme.](update-minimal-layout.md)** İnternet'e bağlı olan bilgisayarlar için en az düzen oluşturmak, çevrimdışı örneklerinizi güncelleştirmenin en kolay ve en Visual Studio yoludur.

- **[Güncelleştirme Visual Studio](repair-visual-studio.md) düzeltmek için güncelleştirmeleri onarın.** Bazen Visual Studio veya bozuk hale gelir. Onarım, güncelleştirmeler de dahil olmak üzere tüm yükleme işlemleri boyunca yükleme zamanı sorunlarını düzeltmek için kullanışlıdır. 

- **Güvenlik [Windows temellerini izleyin.](/windows/security/threat-protection/windows-security-baselines)** Microsoft, müşterilerine Windows 10 ve Windows Server gibi güvenli işletim sistemleri ve Microsoft Edge gibi güvenli uygulamalar sağlamayı Microsoft Edge. Microsoft, ürünlerinin güvenlik güvencesine ek olarak çeşitli yapılandırma özellikleri sağlayarak ortamlar üzerinde ince denetime sahip olur. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz. 

- [Visual Studio için üretkenlik kılavuzu](../ide/productivity-features.md)

