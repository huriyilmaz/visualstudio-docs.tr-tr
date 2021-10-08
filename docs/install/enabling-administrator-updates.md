---
title: Microsoft Endpoint Configuration Manager Visual Studio için yönetici güncelleştirmelerini etkinleştirme
titleSuffix: ''
description: Visual Studio için yönetici güncelleştirmelerini dağıtma hakkında daha fazla bilgi edinin.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 147a244e31fab420755857f698b5a11cc6cedce2
ms.sourcegitcommit: 7a6358d7c7de0a7b9b9553801e72d91d972b0c94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2021
ms.locfileid: "129680037"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager Visual Studio için yönetici güncelleştirmelerini etkinleştirme

Microsoft Endpoint Configuration Manager (SCCM), yazılım güncelleştirme yönetimi iş akışını kullanarak, Visual Studio 2017 ve Visual Studio 2019 yönetici güncelleştirmelerini yönetebilir.

> [!NOTE]
> belge basitliği için aşağıdaki içerik, toplu olarak "Visual Studio" olarak Visual Studio 2017, Visual Studio 2019 ve Visual Studio 2022 ürünlerini ifade eder.

microsoft, Content Delivery Network (CDN) yeni bir Visual Studio güncelleştirme yayımladığında, microsoft ilgili yönetici güncelleştirme paketini aynı anda Microsoft Update sunucularına yayımlayacaktır. bu, daha sonra bir yöneticinin Visual Studio güncelleştirmesini [Microsoft Update kataloğu](https://www.catalog.update.microsoft.com/Home.aspx) (muc) veya [Windows Server update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS) aracılığıyla dağıtmasını sağlar. Configuration Manager, WSUS kataloğundaki Visual Studio yönetici güncelleştirmelerini site sunucusuna eşitlenmek üzere ayarlanabilir ve sonra, güncelleştirmeyi indirebilir ve kuruluştaki Visual Studio istemci makinelerine dağıtabilir. her bir Visual Studio sürümünde hangi düzeltmelerin mevcut olduğu hakkında daha fazla bilgi için bkz. [sürüm notları](/visualstudio/releases/2019/release-notes).

Visual Studio yönetici güncelleştirmelerini Configuration Manager aracılığıyla dağıtmak için, bu iki ilk hazırlama adımını gerçekleştirmeniz gerekir:
1. Configuration Manager Visual Studio yönetici güncelleştirme bildirimleri almasını etkinleştirin. 
2. istemci makinelerini Configuration Manager Visual Studio yönetici güncelleştirmelerini alacak şekilde etkinleştirin (veya devre dışı bırakın).

bu adımları gerçekleştirdikten sonra, Visual Studio yönetici güncelleştirmelerini dağıtmak için Configuration Manager yazılım güncelleştirme yönetimi özelliklerini kullanabilirsiniz. Visual Studio yönetici güncelleştirmelerinin farklı türleri ve özellikleri, kuruluşunuzun tamamında nasıl ve ne zaman dağıtılmaları gerektiği hakkında rehberlik sağlayan [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md)bölümünde açıklanmaktadır. Configuration Manager işlevselliği ve seçenekleri hakkında daha fazla bilgi için bkz. [Microsoft Endpoint Configuration Manager yazılım güncelleştirmelerini dağıtma](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Configuration Manager Visual Studio yönetici güncelleştirme bildirimleri almasını etkinleştir

Visual Studio yönetici güncelleştirmelerini yönetmek için Configuration Manager etkinleştirmek üzere şunları yapmanız gerekir:

* Microsoft Endpoint Configuration Manager (geçerli dal) ve Windows server Update Services (WSUS) çalıştıran Windows sunucusunun geçerli lisanslı bir sürümü. Bu güncelleştirmeleri dağıtmak için WSUS 'yi kullanamazsınız; Configuration Manager ile birlikte kullanılması gerekir.

* hiyerarşinin en üst düzey WSUS sunucusu ve en üst düzey Configuration Manager site sunucusunun, burada listelenen Visual Studio url 'ler ve bağlantı noktalarına erişimi olmalıdır: [güvenlik duvarı veya proxy sunucusunun arkasında Visual Studio ve Azure hizmetlerini yükleyip kullanın](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Microsoft Endpoint Configuration Manager, Visual Studio yönetici güncelleştirme paketleri kullanılabilir olduğunda bildirim alacak şekilde yapılandırılmalıdır.  Bunu yapmak için aşağıdaki adımları kullanın ve daha fazla bilgi için, bkz. [Microsoft Endpoint Configuration Manager yazılım güncelleştirmelerine giriş](/mem/configmgr/sum/understand/software-updates-introduction).

  1. Configuration Manager konsolunda, **Yönetim** (sol alt) öğesini seçin ve ardından **Site yapılandırması** (orta sol) ve ardından **siteler**' i seçin ve site sunucunuzu seçin.

  2. en üstteki **giriş** sekmesi şeridinde, **Ayarlar** grubu düğmesinde, **Site bileşenlerini yapılandır**' ı seçin ve ardından **yazılım güncelleştirme noktası**' nı seçin.

  3. **Yazılım güncelleştirme noktası bileşen özellikleri** iletişim kutusunda:

        * **ürünler** sekmesinde, **Geliştirici Araçları, çalışma zamanları ve yeniden dağıtılabilir** hiyerarşisi altında, eşitlenmesini istediğiniz Visual Studio sürümlerini seçin.

        * **Sınıflandırmalar** sekmesinde "güvenlik güncelleştirmeleri", "özellik paketleri" ve "Güncelleştirmeler" ' in seçildiğinden emin olun.

  4. Ardından, yazılım güncelleştirmelerini WSUS sunucusu ile eşitleyerek **yazılım kitaplığı** ' nı (sol alt tarafta) ve ardından üstteki **giriş** sekmesi şeridinde, **yazılım güncelleştirmelerini Synchronize** düğmesini seçin. yazılım güncelleştirmelerinin eşitlenmesi, kullanılabilir Visual Studio yönetici güncelleştirmelerinin, Configuration Manager konsolundan ' de görünür olmasını sağlar.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>istemci makinelerinin Configuration Manager Visual Studio yönetici güncelleştirmelerini almasına izin verme (veya devre dışı bırakma)

istemci makinenin Visual Studio yönetici güncelleştirmelerini kabul etmesine olanak tanımak için, Visual Studio istemci algılayıcı yardımcı programının düzgün yüklendiğinden emin olmanız ve istemcinin yönetici güncelleştirmelerini almasını sağlamak için bir kayıt defteri anahtarı ayarlamanız gerekir.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio İstemci algılayıcısı yardımcı programı

yönetici güncelleştirmelerinin düzgün şekilde tanınması ve alınabilmesi için istemci makinelerinde [Visual Studio istemci algılayıcısı yardımcı programı](https://support.microsoft.com/help/5001148) yüklü olmalıdır. bu yardımcı program, 12 mayıs 2020 tarihinde veya sonrasında yayınlanan tüm Visual Studio 2017 ve Visual Studio 2019 ürün güncelleştirmelerine eklenmiştir. bu, tüm Visual Studio yönetici güncelleştirmelerinde önkoşul olarak dahil edilmiştir ve ayrıca, bağımsız olarak yüklemek için [Microsoft Update kataloğunda](https://catalog.update.microsoft.com) de mevcuttur.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>İstemci makinelerde yönetici hedefini kodlama

Yönetici güncelleştirmelerini almak için istemci bilgisayarların etkinleştirilmesi gerekir. Bu adım, güncelleştirmelerin istem dışı bir istemci bilgisayara istenmeden veya yanlışlıkla itilmediğinden emin olmak için gereklidir.

 **Tınupdatesenabled**   anahtarı, yöneticinin yönetici hedefini kodlayamak üzere tasarlanmıştır. bu anahtar, [Visual Studio kurumsal dağıtımları için Set varsayılanları](/visualstudio/install/set-defaults-for-enterprise-deployments) bölümünde açıklandığı gibi standart Visual Studio konumlarından herhangi birinde olabilir. İstemci bilgisayarda yönetici erişimi, bu anahtarın değerini oluşturmak ve ayarlamak için gereklidir.

* İstemci bilgisayarı yönetici güncelleştirmelerini kabul edecek şekilde yapılandırmak için, **Tınupdatesenabled**   REG_DWORD anahtarını **1** olarak ayarlayın.
*  **Tınupdatesenabled**   REG_DWORD anahtarı **eksikse veya 0 olarak ayarlandıysa**, yönetici güncelleştirmelerinin istemci bilgisayara uygulanması engellenir.

## <a name="feedback-and-support"></a>Geri bildirim ve destek

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Visual Studio yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya güncelleştirmeleri etkileyen sorunları raporlamak için aşağıdaki yöntemleri kullanabilirsiniz:

* [yükleme ve yükseltme sorunları Visual Studio sorun giderme](../install/troubleshooting-installation-issues.md) kılavuzuna bakın.
* [Visual Studio kurulum Q ile bir Forum&](/answers/topics/vs-setup.html)topluluğa soru sorun.
* [Visual Studio destek sayfasına](https://visualstudio.microsoft.com/vs/support/)gidin ve sorunun sss bölümünde listelenip listelenmediğini denetleyin.  Sohbet yardımı için [destek bağlantısı](https://visualstudio.microsoft.com/vs/support/#talktous) düğmesini de seçebilirsiniz.
* Visual Studio ekibine, yönetici güncelleştirmelerini etkinleştirme deneyimiyle ilgili [bir sorun bildirin veya özellik geri bildirimi sağlayın](https://aka.ms/vs/wsus/feedback) .
* Microsoft için kuruluşunuzun teknik hesap yöneticisiyle iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmeleri uygulanıyor](../install/applying-administrator-updates.md)
* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Microsoft Update Catalog hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) belgeleri](/mem/configmgr)
* [Güncelleştirmeleri Microsoft kataloğundan Configuration Manager içine aktarın](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
