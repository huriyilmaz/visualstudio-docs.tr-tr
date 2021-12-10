---
title: Microsoft Endpoint Configuration Manager ile Visual Studio güncelleştirmelerini etkinleştirme
titleSuffix: ''
description: Yöneticilere yönetici güncelleştirmeleri dağıtma hakkında daha fazla Visual Studio.
ms.date: 12/7/2021
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7db34d7f43bc90bdd3e49e698d0eddab28646ed4
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134553888"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager ile Visual Studio güncelleştirmelerini etkinleştirme

Microsoft Endpoint Configuration Manager (SCCM), yazılım güncelleştirmesi Visual Studio 2017 ve Visual Studio 2019 yönetici güncelleştirmelerini yazılım güncelleştirmelerini yönetebilir.

> [!NOTE]
> Belge basitliği için aşağıdaki içerikler Visual Studio 2017, Visual Studio 2019 ve Visual Studio 2022 ürünlerini topluca "Visual Studio" olarak ifade edecek.

Microsoft, yeni bir Visual Studio güncelleştirmesini Content Delivery Network (CDN) yayımlarsa, Microsoft ilgili yönetici güncelleştirme paketini aynı anda Microsoft Update yayımlar. Bu, yöneticinin güncelleştirme güncelleştirmesini Visual Studio Kataloğu (MUC) [veya Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) Sunucu Güncelleştirme Hizmetleri (WSUS) [Windows dağıtmalarını](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) sağlar. Yapılandırma Yöneticisi, WSUS kataloğundan Visual Studio yönetici güncelleştirmelerini site sunucusuna eşitlemek için ayarlanır ve ardından güncelleştirmeyi indirebilir ve kuruluş genelinde Visual Studio istemci makinelerine dağıtabilirsiniz. Her bir sürümde hangi düzeltmelerin mevcut olduğu hakkında daha fazla bilgi Visual Studio sürüm [notlarına bakın.](/visualstudio/releases/2019/release-notes)

Bu Visual Studio güncelleştirmelerini Yapılandırma Yöneticisi dağıtmak için şu iki başlangıç hazırlık adımını atabilirsiniz:
1. Yönetici Yapılandırma Yöneticisi bildirimlerini Visual Studio için yöneticiyi etkinleştirin. 
2. İstemci makinelerinden yönetici güncelleştirmelerini almak için istemci Visual Studio etkinleştirin (veya devre dışı Yapılandırma Yöneticisi.

Bu adımları gerçekleştirdikten sonra, yönetici güncelleştirmelerini dağıtmak için Yapılandırma Yöneticisi güncelleştirme yönetimi Visual Studio kullanabilirsiniz. Yönetici güncelleştirmelerinin farklı türleri Visual Studio özellikleri, kuruluş [](../install/applying-administrator-updates.md)genelinde nasıl ve ne zaman dağıtılmaları gerektiği konusunda rehberlik sağlayan Yönetici güncelleştirmelerini uygulama konusunda açıklanmıştır. İşlevsellik ve Yapılandırma Yöneticisi daha fazla bilgi için [bkz. Yazılım güncelleştirmelerini Microsoft Endpoint Configuration Manager.](/mem/configmgr/sum/deploy-use/deploy-software-updates)

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Yönetici Yapılandırma Yöneticisi bildirimlerini Visual Studio için yöneticiyi etkinleştirme

Yönetici güncelleştirmelerini Yapılandırma Yöneticisi için Visual Studio sağlamak için şunları gerekir:

* Windows Server Update Services (WSUS) Microsoft Endpoint Configuration Manager (geçerli dal) ve Windows çalıştıran geçerli lisanslı bir sürüm. Bu güncelleştirmeleri dağıtmak için WSUS'nin kendisini kullanamazsınız; bu, verilerle birlikte Yapılandırma Yöneticisi.

* Yönetici Microsoft Endpoint Configuration Manager paketleri kullanılabilir olduğunda bildirim almak için Visual Studio yapılandırmanız gerekir.  Bunu yapmak için aşağıdaki adımları kullanın ve daha fazla bilgi için [bkz.](/mem/configmgr/sum/understand/software-updates-introduction)Microsoft Endpoint Configuration Manager .

  1. Yapılandırma Yöneticisi konsolunda Yönetim **(sol** alt) seçeneğini, ardından **Site** Yapılandırması (orta sol), Siteler'i **ve** ardından site sunucunuz'ı seçin.

  2. Üstteki **Giriş** sekmesi şeridinde, site **grubu Ayarlar** **Site** Bileşenlerini Yapılandır'ı ve ardından Yazılım Güncelleştirme **Noktası'ı seçin.**

  3. Yazılım **Güncelleştirme Noktası Bileşen Özellikleri iletişim** kutusunda:

        * Ürünler **sekmesinde,** **Geliştirici Araçları, Çalışma** Zamanları ve Yeniden Dağıtılabilirler hiyerarşisinin altında, eşitlemek istediğiniz Visual Studio sürümlerini seçin.

        * Sınıflandırmalar **sekmesinde** "Güvenlik Güncelleştirmeleri", "Özellik Paketleri" ve "Güncelleştirmeler"in seçildiğinden emin olun.

  4. Ardından, Yazılım **Kitaplığı(sol** alt) seçeneğini ve ardından üstteki Giriş sekmesi  şeridinde Yazılım Güncelleştirmelerini Eşitle düğmesini seçerek yazılım güncelleştirmelerini WSUS **sunucusuyla eşitleyebilirsiniz.** Yazılım Güncelleştirmelerinin Eşitlenmesi, Visual Studio yönetici güncelleştirmelerinin görünür hale gelir ve Yapılandırma Yöneticisi konsolundan dağıtılabilir.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>İstemci makinelerinin yönetici güncelleştirmelerini yönetici güncelleştirmelerini Visual Studio (veya devre dışı bırakma) Yapılandırma Yöneticisi

Bir istemci makinesinin Visual Studio yönetici güncelleştirmelerini kabul etmelerini sağlamak için, Visual Studio İstemci Algılayıcısı Yardımcı Programı'nın düzgün şekilde yüklü olduğundan emin olun ve istemcinin yönetici güncelleştirmelerini aldırması için bir kayıt defteri anahtarı ayarlamanız gerekir.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio Algılayıcı yardımcı programı

Yönetici [Visual Studio düzgün tanınması](https://support.microsoft.com/help/5001148) ve alın olması için istemci makinelerde İstemci Algılayıcısı Yardımcı Programı'nın yüklü olması gerekir. Bu yardımcı program tüm Visual Studio 2017 ve 12 Mayıs 2020'de veya sonrasında yayımlanan Visual Studio 2019 ürün güncelleştirmelerine dahil edildi, tüm Visual Studio yönetici güncelleştirmelerinin önkul olarak dahil edildi ve bağımsız olarak yüklemek için [Microsoft Update Kataloğu'da](https://catalog.update.microsoft.com) da kullanılabilir.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>İstemci makinelerde yönetici amacı kodlama

Yönetici güncelleştirmelerini almak için istemci bilgisayarların etkinleştirilmesi gerekir. Bu adım, güncelleştirmelerin yanlışlıkla veya yanlışlıkla şüpheli istemci bilgisayarlara doğru şekilde ertelenmemelerini sağlar.

 **AdministratorUpdatesEnabled**   anahtarı, yöneticinin yönetici amacını kodlaması için tasarlanmıştır. Bu anahtar, Kuruluş dağıtımları için varsayılanları Visual Studio ayarlama belgelerinde açıklandığı gibi standart Visual Studio [olabilir.](/visualstudio/install/set-defaults-for-enterprise-deployments) Bu anahtarın değerini oluşturmak ve ayarlamak için istemci bilgisayarda yönetici erişimi gerekir.

* İstemci bilgisayarı Yönetici Güncelleştirmelerini kabul etmek üzere yapılandırmak için **AdministratorUpdatesEnabled**   REG_DWORD **1 olarak ayarlayın.**
*  **AdministratorUpdatesEnabled** REG_DWORD anahtarı eksikse veya 0 olarak ayarlanırsa, yönetici güncelleştirmelerinin istemci bilgisayara   uygulanması engellenir. 

## <a name="feedback-and-support"></a>Geri bildirim ve destek

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya Visual Studio sorunları rapor etmek için aşağıdaki yöntemleri kullanabilirsiniz:

* Yükleme ve yükseltme [Visual Studio sorunlarını giderme kılavuzuna](../install/troubleshooting-installation-issues.md) bakın.
* Soru-Cevap Kurulumu'nda [Visual Studio topluluk&sorun.](/answers/topics/vs-setup.html)
* destek sayfasına [Visual Studio ve soruna](https://visualstudio.microsoft.com/vs/support/)SSS sayfasında listelenmiş olup olmadığını kontrol edin.  Sohbet yardımı için Destek [Bağlantısı düğmesini](https://visualstudio.microsoft.com/vs/support/#talktous) de seçin.
* [Yönetici güncelleştirmelerini etkinleştirme deneyimiyle ilgili olarak](https://aka.ms/vs/wsus/feedback) özellik geri bildirimi Visual Studio sorun bildirin.
* Microsoft için kuruluşun teknik hesap yöneticisine ulaşın.

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md)
* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Microsoft Update Kataloğu hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) belgeleri](/mem/configmgr)
* [Güncelleştirmeleri Microsoft Kataloğu'dan Yapılandırma Yöneticisi](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
