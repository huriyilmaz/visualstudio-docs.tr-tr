---
title: Microsoft uç noktası ile Visual Studio için yönetici güncelleştirmelerini etkinleştirme Configuration Manager
titleSuffix: ''
description: Yönetici güncelleştirmelerini Visual Studio 'ya dağıtma hakkında daha fazla bilgi edinin.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307459"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Microsoft uç noktası ile Visual Studio için yönetici güncelleştirmelerini etkinleştirme Configuration Manager

Microsoft uç nokta Configuration Manager (SCCM), yazılım güncelleştirme yönetimi iş akışını kullanarak Visual Studio 2017 ve Visual Studio 2019 yönetici güncelleştirmelerini yönetebilir.

> [!NOTE]
> Belge basitliği için aşağıdaki içerik, toplu olarak "Visual Studio" olarak Visual Studio 2017, Visual Studio 2019 ve Visual Studio 2022 ürünlerine başvuracaktır.

Microsoft, Content Delivery Network (CDN) için yeni bir Visual Studio Güncelleştirmesi yayımladığında, Microsoft aynı anda ilgili yönetici güncelleştirme paketini Microsoft Update sunucularına yayımlayacaktır. Böylece, bir yöneticinin Visual Studio güncelleştirmesini [Microsoft Update katalogu](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) veya [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS) aracılığıyla dağıtması etkinleştirilir. Configuration Manager, Visual Studio Yönetici güncelleştirmelerini WSUS kataloğundan site sunucusuna eşitlenmek üzere ayarlanabilir ve sonra, güncelleştirmeyi indirebilir ve kuruluştaki Visual Studio istemci makinelerine dağıtabilir. Visual Studio 'nun her sürümünde hangi düzeltmelerin bulunduğu hakkında daha fazla bilgi için [sürüm notlarına](/visualstudio/releases/2019/release-notes)bakın.

Configuration Manager aracılığıyla Visual Studio Yönetici güncelleştirmelerini dağıtmak için, bu iki ilk hazırlama adımını gerçekleştirmeniz gerekir:
1. Visual Studio Yönetici güncelleştirme bildirimlerini almak için Configuration Manager etkinleştirin. 
2. Configuration Manager 'den Visual Studio Yönetici güncelleştirmelerini almak için istemci makinelerini etkinleştirin (veya devre dışı bırakın).

Bu adımları gerçekleştirdikten sonra, Visual Studio Yönetici güncelleştirmelerini dağıtmak için Configuration Manager yazılım güncelleştirme yönetimi özelliklerini kullanabilirsiniz. Visual Studio yönetici güncelleştirmelerinin farklı türleri ve özellikleri, kuruluşunuzun tamamında nasıl ve ne zaman dağıtılmaları gerektiği hakkında rehberlik sağlayan [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md)bölümünde açıklanmaktadır. Configuration Manager işlevselliği ve seçenekleri hakkında daha fazla bilgi için bkz. [Microsoft uç noktası 'nda yazılım güncelleştirmelerini dağıtma Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Visual Studio Yönetici güncelleştirme bildirimlerini almak için Configuration Manager etkinleştirme

Visual Studio Yönetici güncelleştirmelerini yönetmek için Configuration Manager etkinleştirmek üzere şunları yapmanız gerekir:

* Microsoft uç noktası Configuration Manager (geçerli dal) ve Windows Server Update Services (WSUS) çalıştıran Windows Server 'ın geçerli bir lisanslı sürümü. Bu güncelleştirmeleri dağıtmak için WSUS 'yi kullanamazsınız; Configuration Manager ile birlikte kullanılması gerekir.

* Hiyerarşinin en üst düzey WSUS sunucusu ve en üst düzey Configuration Manager site sunucusu, Visual Studio URL 'Lerine ve bu bağlantı noktalarına aşağıda listelenen bağlantı noktalarına erişebilmelidir: [bir güvenlik duvarı veya proxy sunucusunun arkasında Visual Studio ve Azure hizmetlerini yükleyip kullanın](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Microsoft uç noktası Configuration Manager, Visual Studio Yönetici güncelleştirme paketleri kullanılabilir olduğunda bildirim alacak şekilde yapılandırılmalıdır.  Bunu yapmak için aşağıdaki adımları kullanın ve daha fazla bilgi için bkz. [Microsoft uç nokta Configuration Manager yazılım güncelleştirmelerine giriş](/mem/configmgr/sum/understand/software-updates-introduction).

  1. Configuration Manager konsolunda, **Yönetim** (sol alt) öğesini seçin ve ardından **Site yapılandırması** (orta sol) ve ardından **siteler**' i seçin ve site sunucunuzu seçin.

  2. En üstteki **giriş** sekmesi şeridinde, **Ayarlar** grubu düğmesinde, **site bileşenlerini Yapılandır**' ı seçin ve ardından **yazılım güncelleştirme noktası**' nı seçin.

  3. **Yazılım güncelleştirme noktası bileşen özellikleri** iletişim kutusunda:

        * **Ürünler** sekmesinde, **Geliştirici araçları, çalışma zamanları ve yeniden dağıtılabilir** hiyerarşisi altında, eşitlenmek istediğiniz Visual Studio sürümlerini seçin.

        * **Sınıflandırmalar** sekmesinde "güvenlik güncelleştirmeleri", "özellik paketleri" ve "Güncelleştirmeler" ' in seçildiğinden emin olun.

  4. Ardından, yazılım güncelleştirmelerini WSUS sunucusu ile eşitleyerek **yazılım kitaplığı** ' nı (sol alt tarafta) ve ardından üstteki **giriş** sekmesi şeridinde, **yazılım güncelleştirmelerini Synchronize** düğmesini seçin. Yazılım güncelleştirmelerinin eşitlenmesi, kullanılabilir Visual Studio yönetici güncelleştirmelerinin ' de görünür olmasını ve Configuration Manager konsolundan dağıtılmasını sağlar.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>İstemci makinelerinin Configuration Manager Visual Studio Yönetici güncelleştirmelerini almasına izin verme (veya devre dışı bırakma)

Bir istemci makinenin Visual Studio Yönetici güncelleştirmelerini kabul etmesine olanak tanımak için, Visual Studio Istemci algılayıcısı yardımcı programının düzgün yüklendiğinden emin olmanız ve istemcinin yönetici güncelleştirmelerini almasını sağlamak için bir kayıt defteri anahtarı ayarlamanız gerekir.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio Istemci algılayıcısı yardımcı programı

Yönetici güncelleştirmelerinin düzgün şekilde tanınması ve alınabilmesi için, istemci makinelerde [Visual Studio Istemci algılayıcısı yardımcı programı](https://support.microsoft.com/help/5001148) yüklü olmalıdır. Bu yardımcı program, 12 Mayıs 2020 tarihinde veya bu tarihten sonra yayınlanan tüm Visual Studio 2017 ve Visual Studio 2019 ürün güncelleştirmelerine eklenmiştir. Bu, tüm Visual Studio Yönetici güncelleştirmelerinde önkoşul olarak dahildir ve ayrıca, bağımsız olarak yüklemek için [Microsoft Update kataloğunda](https://catalog.update.microsoft.com) de mevcuttur.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>İstemci makinelerde yönetici hedefini kodlama

Yönetici güncelleştirmelerini almak için istemci bilgisayarların etkinleştirilmesi gerekir. Bu adım, güncelleştirmelerin istem dışı bir istemci bilgisayara istenmeden veya yanlışlıkla itilmediğinden emin olmak için gereklidir.

 **Tınupdatesenabled**   anahtarı, yöneticinin yönetici hedefini kodlayamak üzere tasarlanmıştır. Bu anahtar, [Visual Studio 'nun kurumsal dağıtımları için Varsayılanları Ayarla](/visualstudio/install/set-defaults-for-enterprise-deployments) belgelerinin açıklandığı gibi standart Visual Studio konumlarından herhangi birinde olabilir. İstemci bilgisayarda yönetici erişimi, bu anahtarın değerini oluşturmak ve ayarlamak için gereklidir.

* İstemci bilgisayarı yönetici güncelleştirmelerini kabul edecek şekilde yapılandırmak için, **Tınupdatesenabled**   REG_DWORD anahtarını **1** olarak ayarlayın.
*  **Tınupdatesenabled**   REG_DWORD anahtarı **eksikse veya 0 olarak ayarlandıysa**, yönetici güncelleştirmelerinin istemci bilgisayara uygulanması engellenir.

## <a name="feedback-and-support"></a>Geri bildirim ve destek

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Visual Studio yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya güncelleştirmeleri etkileyen sorunları bildirmek için aşağıdaki yöntemleri kullanabilirsiniz:

* [Visual Studio yükleme ve yükseltme sorunlarını giderme](../install/troubleshooting-installation-issues.md) kılavuzuna bakın.
* [Visual Studio Kurulumu soru-cevap&](/answers/topics/vs-setup.html)topluluğa soru sorun.
* [Visual Studio destek sayfasına](https://visualstudio.microsoft.com/vs/support/)gidin ve sorunun SSS bölümünde listelenip listelenmediğini denetleyin.  Sohbet yardımı için [destek bağlantısı](https://visualstudio.microsoft.com/vs/support/#talktous) düğmesini de seçebilirsiniz.
* Yönetici güncelleştirmelerini etkinleştirme deneyimiyle ilgili olarak, [özellik geri bildirimi sağlayın veya Visual Studio ekibine bir sorun bildirin](https://aka.ms/vs/wsus/feedback) .
* Microsoft için kuruluşunuzun teknik hesap yöneticisiyle iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmeleri uygulanıyor](../install/applying-administrator-updates.md)
* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Microsoft Update Catalog hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft uç nokta Configuration Manager (SCCM) belgeleri](/mem/configmgr)
* [Güncelleştirmeleri Microsoft kataloğundan Configuration Manager içine aktarın](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
