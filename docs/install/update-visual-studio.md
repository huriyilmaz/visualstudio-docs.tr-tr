---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: en son sürüme Visual Studio güncelleştirmeyi öğrenin ve adım adım.
ms.date: 12/7/2021
ms.custom: vs-acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7eb808d9863cc1ee6dd52a3c9e13ba408806b82a
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134554018"
---
# <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Bu konu, Visual Studio istemci yüklemesinin nasıl güncelleştirilmesini anlatmaktadır.  bt yöneticisiyseniz ve kuruluşunuzun istemcilerini bir ağ düzeninden güncelleştirmek üzere yapılandırmak istiyorsanız, özellikle de [bir ağ yüklemesini yönetme ve güncelleştirme](../install/update-a-network-installation-of-visual-studio.md)konusunun bölümüne [Visual Studio](https://aka.ms/vs/admin/guide)bakın.

bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update). 

## <a name="before-you-update"></a>Güncelleştirmeden önce

Visual Studio yüklemek, güncelleştirmek ya da değiştirmek için yönetici izinlerine sahip bir hesapla makinede oturum açmış olmanız gerekir. Tipik bir kullanıcı olarak oturum açtıysanız ve bu komutlardan birini gerçekleştirmeyi denerseniz, yönetici kimlik bilgileri isteyip istemediğinizi soran bir kullanıcı hesabı denetimi bildirimi alırsınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

Bir güncelleştirme gerçekleştirmeden önce işinizi kaydetmenizi kesinlikle öneririz.

güncelleştirmek için önce makinede Visual Studio yüklü olmalıdır. Microsoft tarafından barındırılan sunuculardan güncel Visual Studio sürümünü yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin. şu anda başka bir Visual Studio örneğini kullanıyorsanız, [mevcut yüklemenize yan yana Visual Studio yeni bir örneğini yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)ya da bu yenisini yüklemeden önce [önceki Visual Studio örneğini kaldırabilirsiniz](../install/uninstall-visual-studio.md) .

::: moniker range="vs-2017"

en son özellikleri, güvenlik düzeltmelerini ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2017 ' in en [son sürümüne](/visualstudio/releasenotes/vs2017-relnotes/) güncelleştirmeniz önerilir. en yeni sürümü denemek isterseniz [2022 Visual Studio](https://visualstudio.microsoft.com/downloads)indirip yüklemeyi göz önünde bulundurun.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. bir güncelleştirme olduğunda, Visual Studio ıde 'nin başlık çubuğunda karşılık gelen bir bildirim bayrağı vardır. **Bildirimler** merkezini açmak için bildirim bayrağını seçin ve ardından yüklemek istediğiniz güncelleştirmeyi seçin.

   ![Visual Studio ıde 'nin bildirim hub 'ında bir güncelleştirmeyi gösteren ekran görüntüsü.](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017'de Bildirimler hub'ı")

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

    ![Visual Studio 2017 ' nin bildirimler hub 'ında başlatılan güncelleştirme iletişim kutusunda şimdi güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-update-now-from-notifications-hub.png "Visual Studio'de Bildirimler hub'larından Güncelleştir iletişim Visual Studio")

     Kullanıcı Access Control iletişim kutusu açılırsa **Evet**' i seçin. sonra, bir "lütfen bekleyin" iletişim kutusu bir süre sonra açılabilir ve sonra Visual Studio Yükleyicisi açılarak güncelleştirmeyi başlatabilir.

     ![Visual Studio Yükleyicisi deneyimini gösteren ekran görüntüsü.](media/visual-studio-15dot6-installer.png "Yeni Visual Studio Yükleyicisi deneyimi")

     güncelleştirmeniz tamamlanır ve sonra Visual Studio yeniden başlatılır.

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetle

1.  > Menü çubuğunda **güncelleştirmeler için yardım denetle** ' ye tıklayarak bir güncelleştirmenin kullanılabilir olup olmadığını kontrol edebilirsiniz.

     ![Visual Studio 'deki Yardım menüsünü gösteren ekran görüntüsü.](media/vs-help-menu-check-for-updates.png "Visual Studio'daki yeni Yardım menüsü")

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

   güncelleştirme, önceki bölümde açıklanan şekilde devam eder ve güncelleştirme başarıyla tamamlandıktan sonra yeniden başlatılır Visual Studio.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. Visual Studio önceki sürümlerinde olduğu gibi, bir güncelleştirmeyi yüklemek için Visual Studio Yükleyicisi kullanabilirsiniz.  ilk olarak, bilgisayarınızda **Visual Studio Yükleyicisi** bulun.  Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.  

1. Yükleyiciyi açın. devam etmeden önce Visual Studio Yükleyicisi güncelleştirilmesi gerekebilir.

1. yükleyicideki **ürün** sayfasında, daha önce yüklediğiniz ve şimdi güncelleştirmek istediğiniz Visual Studio sürümünü bulun.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi Visual Studio 2017 ' i güncelleştirmek için kullanılabilecek güncelleştirme düğmesini gösteren ekran görüntüsü.](media/update-visual-studio.png "Visual Studio kullanarak 2017 güncelleştirme Visual Studio Yükleyicisi")

::: moniker-end

::: moniker range="vs-2019"

en son özellikleri, güvenlik düzeltmelerini ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2019 ' in en [son sürümüne](/visualstudio/releases/2019/release-notes/) güncelleştirmeniz önerilir. en yeni sürümü denemek isterseniz [2022 Visual Studio](https://visualstudio.microsoft.com/downloads)indirip yüklemeyi göz önünde bulundurun.

Visual Studio yüklemesini güncelleştirmenin birkaç farklı yolu vardır. Visual Studio Yükleyicisi aracılığıyla güncelleştirebilirsiniz, güncelleştirmeleri denetleyebilir veya ıde 'de bildirim hub 'ını kullanabilir ya da [önyükleyici 'nin belirli bir sürümünü](/visualstudio/releases/2019/history)çalıştırarak güncelleştirebilirsiniz. &nbsp;Bu çeşitli yöntemleri kullanarak Visual Studio 2019 ' i nasıl güncelleşirsiniz &nbsp; .

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

   Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.

   ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. yükleyicide, güncelleştirmek istediğiniz Visual Studio örneğini arayın.

   örneğin, daha önce Visual &nbsp; Studio Community 2019 ' i yüklediyseniz &nbsp; ve bu güncelleştirme için bir güncelleştirme varsa, yükleyicide bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![kullanılabilir bir güncelleştirmeyle Visual Studio 2019 yüklemesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir** ' i seçin.

    ![Visual Studio 2019 yüklemesine güncelleştirmek için kullanılabilecek Visual Studio yükleyicisindeki güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. bu durumda, bunu yapın ve genellikle Visual Studio başlatın.

   bilgisayarınızı yeniden başlatmanız istenmezse, yükleyiciden Visual Studio başlatmak için **başlat** ' ı seçin.

    ![Visual Studio yükleyicisinde, Visual Studio 2019 ' i başlatmak için kullanılabilecek başlatma düğmesini gösteren ekran görüntüsü.](media/vs-2019/choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-message-box-in-the-ide"></a>IDE 'deki ileti kutusunu kullanın

1.  Visual Studio açtığınızda, ıde bir güncelleştirmenin kullanılabilir olup olmadığını denetler.  bazı durumlarda **Visual Studio 2019 güncelleştirme** iletisi kısaca görüntülenir. Şimdi güncelleştirmek istiyorsanız, **Ayrıntıları görüntüle**' yi seçin.  Visual Studio kapatana kadar güncelleştirmeyi ertelemek istiyorsanız, **kapatma sırasında güncelleştir**' i seçin.

    ![ıde 'deki ' Visual Studio 2019 güncelleştirme ' iletisini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi")

1. **Ayrıntıları görüntüle**' yi seçerseniz, daha sonra **indirilen ve yüklemeye hazır** iletişim **kutusunda Güncelleştir ' i seçerek şimdi** Güncelleştir ' i seçin.

     ![' Güncelleştirme indirildi ve yüklemeye hazırlanıyor ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetle

1. Menü çubuğundan **Yardım** ' ı seçerek ve ardından **Güncelleştirmeleri denetle**' yi seçerek bir güncelleştirmenin kullanılabilir olup olmadığını kontrol edebilirsiniz.  Arama kutusunu **CTRL** + **Q** tuşlarına basarak, "güncelleştirmeleri denetle" yazarak ve ardından eşleşen arama sonucunu seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki ' güncelleştirmeleri denetle 'yi gösteren ekran görüntüsü.](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. **bildirimler** merkezini açmak için Visual Studio ıde 'nin sağ alt köşesinden bildirim simgesini seçin.

   ![Visual Studio ıde 'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin. Şimdi güncelleştirmek istiyorsanız, **Ayrıntıları görüntüle**' yi seçin. Visual Studio kapatana kadar güncelleştirmeyi ertelemek istiyorsanız, **kapatma sırasında güncelleştir**' i seçin.

     ![Visual Studio 2019 ' de bildirim hub 'ını gösteren ekran görüntüsü.](media/vs-2019/notification-hub-update.png "Visual Studio 2019'daki Bildirim hub'ı")

1. **Ayrıntıları görüntüle**' yi seçerseniz, sonraki **güncelleştirme** iletişim kutusunda **Güncelleştir**' i seçin.

## <a name="run-a-specific-bootstrapper"></a>Belirli bir önyükleyici çalıştırma
Enterprise Professional veya müşterisiyseniz, zaten yüklü olan sürümden daha yüksek bir sürüm olduğu sürece Visual Studio 2019 örneğinizi yayınlanan belirli bir sürüme güncelleştirebilirsiniz. Visual Studio 2019 örneğinizi bu yöntem aracılığıyla güncelleştirmek için [Visual Studio 2019 sürüm geçmişi sayfasına gidin](/visualstudio/releases/2019/history), istenen güncelleştirme sürümüne karşılık gelen önyükleyici ürün yükleme dizininize indirin ve ardından güncelleştirmeyi başlatmak için çift tıklayın.  

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Güncelleştirme davranışını denetlemek için özelleştirilebilecek çeşitli farklı ayarlar vardır. bu ayarlardan bazıları Visual Studio 2019 ' ye yereldir ve ürün bitlerinin nasıl ve ne zaman indirileceği ve yüklendiği ile ilgilenir. güncelleştirmelerin kaynağını yapılandırma özelliği gibi diğer ayarlar, daha yeni Visual Studio 2022 yükleyicisinin varlığını gerektirir.  

### <a name="installation-and-download-behaviors"></a>Yükleme ve indirme davranışları

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Ortam**' ı genişletin ve **ürün güncelleştirmeleri**' ni seçin.

    ![Visual Studio 'daki güncelleştirme ayarlarını gösteren ekran görüntüsü.](media/vs-2019/update-settings-options.png)

1. Bu iletişim kutusunda ayarlanabilir yapılandırma seçeneklerini gözlemleyin. Makine boşta kaldığında güncelleştirmelerin indirilmesine izin veren **güncelleştirmeleri otomatik olarak indir** ayarını seçebilirsiniz. Aralarından seçim yapabileceğiniz iki yükleme modu da vardır: **indirme sırasında yükle** ve **Tümünü İndir, sonra Yükle**.   Visual Studio güncelleştirmelerinizin yükleme modunu ve otomatik karşıdan yükleme ayarını seçin.

### <a name="configure-source-location-of-updates"></a>Güncelleştirmelerin kaynak konumunu yapılandırma
Kurumsal bir ortamdaysanız, istemci örneklerinizin güncelleştirmeleri arama konumunu yapılandırmak mümkündür. Bu, istemcinizin bir ağ düzeninden yük olduğu ancak daha sonra istemcilerin farklı bir ağ düzeninden güncelleştirmeler almak istediğiniz durumlarda kullanışlıdır. Güncelleştirme konumlarını yapılandırma özelliği, istemci makinesine Visual Studio 2022 yükleyerek veya bir ağ düzeni aracılığıyla bunu dışarı iten bir yönetici tarafından elde edilen yeni Visual Studio 2022 yükleyicinin mevcut olması gerekir. Bu özelliği kullanma hakkında daha fazla bilgi için güncelleştirmelerin kaynak konumunu [yapılandırmaya Visual Studio 2022](/visualstudio/install/update-visual-studio?view=vs-2022&preserve-view=true#configure-source-location-of-updates-1)için bkz. . Ayrıca, en son Visual Studio 2022 yükleyicisini kullanmak için Visual Studio [2019](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-include-and-provide-the-latest-installer)düzenlerinizi yapılandırma hakkında bilgi için bkz. . 

## <a name="update-on-close"></a>Kapatmada güncelleştir

2019 Visual Studio 16.9 sürümünde Kapat üzerinde **Güncelleştirme kavramını tanıtmıştık.**  Bir güncelleştirme kullanılabilir olduğunda, IDE'de güncelleştirme bildirimi kullanıcı arabirimi, IDE'de güncelleştirmeyi isteğe bağlı olarak kapatarak güncelleştirmeyi ertelemenin bir Visual Studio. **Kapat'ta** Güncelleştir düğmesi güncelleştirme bildirimi ileti kutusunda görünür ve bildirim hub'larında da seçilebilir. Kapat **komutunda Güncelleştir** kalıcı bir ayar değildir; Yalnızca geçerli güncelleştirme için geçerlidir. Başka bir deyişle, **güncelleştirmenin kullanılabilir olduğunu** bildirimi her onaylar veya kapatırken Kapat'ta Güncelleştir ertelemesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda Kapat'ta Güncelleştir seçeneğini gösteren ekran görüntüsü.](media/vs-2019/update-on-close.png)

::: moniker-end

::: moniker range=">=vs-2022"

Her zaman en son [](/visualstudio/releases/2022/release-notes) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2022'nin en son sürümüne güncelleştirmeniz gerekir.

Bir yüklemesini güncelleştirmenin birkaç farklı yolu vardır Visual Studio. Güncelleştirmeleri uygulama Visual Studio Yükleyicisi, güncelleştirmeleri kontrol etmek veya IDE'de bildirim hub'larını kullanmak ya da önyükleyicinin belirli bir sürümünü [çalıştırarak güncelleştirebilirsiniz.](/visualstudio/releases/2022/release-history) Bu çeşitli yöntemleri kullanarak Visual &nbsp; Studio &nbsp; 2022'nin nasıl güncelleştiril burasıdır.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

   Aşağıdaki Windows Başlat menüsü "yükleyici" araması ve ardından sonuçlardan **Visual Studio Yükleyicisi'yi** seçin.

   ![Uygulamanın arama sonuçlarını Başlat menüsü ekran Visual Studio Yükleyicisi.](media/vs-2022/vs-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenirse, istemleri takip etmek için bunu yapın.

1. Aşağıdaki Visual Studio Yükleyicisi, güncelleştirmek istediğiniz Visual Studio yüklemesini bakın. 

   Örneğin, daha önce Visual Studio Community 2022'i yüklemiş ve bunun için bir  güncelleştirme varsa, kullanılabilir güncelleştirme iletisi Visual Studio Yükleyicisi.

     ![Yeni bir güncelleştirme olduğunda güncelleştirme düğmesini ve Visual Studio Yükleyicisi gösteren ekran görüntüsü.](media/vs-2022/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2022 sürümünü seçin")

1. Güncelleştirmeyi **yüklemek** için Güncelleştir'i seçin.

    ![Yeni güncelleştirmeyi yüklemek için seçerek Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeyi yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra, Visual Studio Yükleyicisi bilgisayarınızı yeniden başlatmanızı istiyor olabilir. Öyleyse, bunu yap ve ardından normal Visual Studio gibi yeni bir başlangıç yap.

    Bilgisayarınızı yeniden başlatmanız istenecekse **Başlat'ı** seçen Visual Studio başlat'ı Visual Studio Yükleyicisi.

    ![Uygulamayı başlatmak için seçerek Başlat düğmesini gösteren ekran Visual Studio.](media/vs-2022/vs-installer-choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-message-box-in-the-ide"></a>IDE'de ileti kutusunu kullanma

1. Bir güncelleştirme Visual Studio IDE tarafından kontrol edildi.  Bazı durumlarda, Visual Studio **2022 güncelleştirme** iletisi kısa bir süre görüntülenir. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.**  Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

    ![IDE'nin sağ alt köşesinde Visual Studio 2022 için güncelleştirme Visual Studio ekran görüntüsü.](media/vs-2022/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2022 güncelleştirmesi' iletisi")

1. Ayrıntıları **görüntüle'yi seçtiysanız,** sonraki Kullanılabilir **güncelleştir** iletişim kutusunda Şimdi güncelleştirmek için **Güncelleştir'i** seçin. 

     ![2022'de 'Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini Visual Studio ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğundan Yardım'ı ve ardından  Güncelleştirmeleri Kontrol Et'i seçerek bir güncelleştirmenin kullanılabilir olup **olduğunu kontrol edin.**  Arama kutusunu **Ctrl** Q tuşlarına basarak, "güncelleştirmeleri kontrol edin" yazarak ve ardından eşleşen + arama sonuçlarını seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki 'Güncelleştirmeleri Kontrol Et' seçeneğini gösteren ekran görüntüsü.](media/vs-2022/ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Bildirim hub'larını açmak için IDE'nin sağ Visual Studio simgesini **seçin.**

   ![Visual Studio IDE'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2022/notification-bar.png "Visual Studio 2022'de bildirim simgesi")

1. Bildirimler **hub'sinde,** yüklemek istediğiniz güncelleştirmeyi seçin. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.** Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

     ![IDE'de Bildirimler hub' Visual Studio ekran görüntüsü.](media/vs-2022/notification-hub-update.png "Visual Studio 2022'de Bildirimler hub'ı")

1. Ayrıntıları **görüntüle'yi seçtiysanız,** sonraki Kullanılabilir **güncelleştirme iletişim kutusunda** Güncelleştir'i **seçin.**

## <a name="run-a-specific-bootstrapper"></a>Belirli bir önyükleyiciyi çalıştırma
Enterprise veya Professional müşterisiysiniz, yüklü olandan daha yüksek bir sürüm olduğu sürece Visual Studio 2022 örneğinizi yayımlanan belirli bir sürüme güncelleştirin. bu yöntem aracılığıyla Visual Studio 2022 örneğinizi güncelleştirmek için [Visual Studio 2022](/visualstudio/releases/2022/release-history)yayın geçmişi sayfasına gidin, istenen güncelleştirme sürümüne karşılık gelen önyükleyiciyi ürün yükleme dizininize indirin ve ardından güncelleştirmeyi başlatmak için buna çift tıklayın.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Güncelleştirme davranışını kontrol etmek için ürün bitlerinin nasıl ve ne zaman indirildikten ve yükleniyorsa ya da güncelleştirme kaynağı konumunun nerede olduğu gibi özelleştirilebilen birkaç farklı ayar vardır.  

### <a name="installation-and-download-behaviors"></a>Yükleme ve indirme davranışları

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. **Ortam'ı** genişletin ve ardından Ürün **Güncelleştirmeleri'ne tıklayın.**

    ![IDE'nin Seçenekler penceresindeki Güncelleştirmeler ayarlarını Visual Studio görüntüsü.](media/vs-2022/update-settings-options.png)

1. Bu iletişim kutusunda ayarlan kullanılabilen yapılandırma seçeneklerini gözlemlemek. Makineniz **boştayken güncelleştirmelerin** indirileye izin veren Güncelleştirmeleri otomatik olarak indir ayarını seçebilirsiniz. Ayrıca iki yükleme modu da vardır: **İndirme sırasında yükle** ve Hepsini **indir'i ve ardından 'yi yükleyin.**   Uygulama güncelleştirmeleri için istediğiniz yükleme modunu ve otomatik indirme Visual Studio seçin.

### <a name="configure-source-location-of-updates"></a>Güncelleştirmelerin kaynak konumunu yapılandırma
2022'Visual Studio ile, artık istemcilerinin güncelleştirmelerini nereden edineceklerini yapılandırabilirsiniz. Bu güncelleştirme kaynağı konumları "kanallar" olarak adlandırılan bu güncelleştirmenin amacı ve kullanılabilirliği hakkında daha fazla bilgiyi [Yayın Visual Studio belgelerinde](/visualstudio/productinfo/release-rhythm) bulabilirsiniz. Microsoft hem Geçerli hem de Önizleme kanallarını herkesin kullanımına sunar ve uzun süreli bakım kanalları (LTSC' ler) hem Enterprise hem de Professional kullanılabilir. IT Yöneticileri ayrıca, istemcilerin erişmesi gereken ağ düzenleri gibi güncelleştirme kaynağı konumlarını da yapılandırabilirsiniz. Bunun nasıl [ayar Visual Studio ek seçenekler](https://aka.ms/vs/admin/guide) ve ayrıntılar için Visual Studio Yöneticileri Kılavuzu'ne bakın. 

Güncelleştirme Örneği iletişim kutusunu açmanın iki yolu Ayarlar vardır. Bu iletişim kutusu, Visual Studio güncelleştirmelerini almak için gereken kanalı değiştirmenizi sağlar. 

1. Uygulama Visual Studio açın, yapılandırmak istediğiniz örneği seçin, Diğer düğmesini **ve** ardından Ayarları güncelleştir **menü seçeneğini** belirleyin. Önceki yönergeleri izleyerek ilgili yönergeleri Visual Studio Yükleyicisi.

    ![Yükleyicide Güncelleştirmeler ayarlarını gösteren ekran görüntüsü.](media/vs-2022/installer-update-settings-menu-option.png)

2. Ayarlar Güncelleştirme iletişim kutusunu çağırmanın alternatif bir yolu, Visual Studio IDE'yi açmak, Kullanılabilir  güncelleştirme iletişim kutusunu açmaktır (Güncelleştirme bildirimiyle ilgili ayrıntıları görüntüle veya Yardım menüsünde güncelleştirmeleri kontrol et) ve Güncelleştirme ayarlarını değiştir bağlantısına tıklamaktır.    

    ![IDE'de Kullanılabilir güncelleştirme iletişim kutusunda Güncelleştirmeler ayarlarını gösteren ekran görüntüsü.](media/vs-2022/invoke-update-settings-in-the-IDE.png)
    
Ayarları **güncelleştir iletişim** kutusu aşağıdaki gibi görünür.

   ![Visual Studio 2022 IDE'de Güncelleştirmeler ayarları iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/update-settings.png)

Güncelleştirme kanalı açılan listesinde doğru **değeri** seçerek, bu güncelleştirme örneği için gelecekteki güncelleştirmelerin kaynak konumunu Visual Studio. Göz şöyledir:
 * Önizleme ve Geçerli kanallar tüm Visual Studio sürümleri için kullanılabilir ve LTSC kanalları yalnızca Professional ve Enterprise kullanılabilir. 
 * Güncelleştirme kanalı konumunu yapılandırdikten hemen Visual Studio örneğinizi güncelleştirmeyi seçebilirsiniz. Veya gerçek ürün güncelleştirmesini daha sonraya erteleyebilirsiniz. Güncelleştirme kanalını yapılandırma ve ürünü güncelleştirme eylemi iki bağımsız olaydır. 
 * Yeni bir kanala güncelleştirince, bu kanala en son sürümü yükleysiniz. Kurumsal müşteriysiniz ve belirli bir sürümü bir kanala yüklemek için daha önce açıklanan Belirli bir önyükleyiciyi çalıştırma yönergelerini izleyin. 
 * Güncelleştirme kanalını yalnızca ilgili kanalın ucunda bulunan ürünün sürümü yüklü olan  sürümden büyükse değiştirebilirsiniz. Örneğin, her zaman Geçerli kanaldan Önizleme kanalına geçesiniz, ancak Önizleme kanalından Geçerli kanala geçiş, Geçerli kanalda en son sürüm yüklü olan Önizleme sürümünü aşana kadar geçerli kanala geçesiniz. 
 * LTSC kanallarının hepsi sona erme tarihlerine sahip. LTSC'nin süresi dolsa da güncelleştirme kaynağı olarak kullanılamaz ve bu listeden kaybolur.
 * Tüm Microsoft kanalları Microsoft sunucularında barındırıldı ve İnternet erişimi gerektirir.
 * Her bir Visual Studio, kaynağını güncelleştirmeler için bağımsız olarak yapılandırma özelliğine sahip olur. Bu nedenle, 2022'Visual Studio iki örneğiniz varsa, her biri farklı bir kanaldan güncelleştirmesi olabilir. 
 * It Administrators can control the values in the **Update channel** dropdown. Örneğin, ağ düzeni konumlarını güncelleştirme kaynakları olarak ekleyebilirler. Ayrıca Microsoft tarafından barındırılan konumların güncelleştirme kaynağı seçenekleri olarak kullanılabilir olması engel olabilir. Bu işlevsellik, 2019 Visual Studio için de çalışır. Bu güncelleştirme konumlarını yapılandırma hakkında daha fazla bilgi için Visual Studio [Kılavuzu'ne bakın](https://aka.ms/vs/admin/guide)

## <a name="update-on-close"></a>Kapatmada güncelleştir

Bir güncelleştirme kullanılabilir olduğunda, IDE'de güncelleştirme bildirimi kullanıcı arabirimi, siz isteğe bağlı olarak kapatana kadar güncelleştirmeyi ertelemenin bir Visual Studio. **Kapat'ta** Güncelleştir düğmesi güncelleştirme bildirimi ileti kutusunda görünür ve Bildirim hub'larında **da seçilebilir.** Kapat **komutunda Güncelleştir** kalıcı bir ayar değildir; Yalnızca geçerli güncelleştirme için geçerlidir. Başka bir deyişle, **güncelleştirmenin kullanılabilir olduğunu** bildirimi her onaylar veya kapatırken Kapat'ta Güncelleştir ertelemesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda Kapat'ta Güncelleştir seçeneğini gösteren ekran görüntüsü.](media/vs-2022/update-on-close.png)

::: moniker-end

## <a name="administrator-updates"></a>Yönetici güncelleştirmeleri

Yazılım yüklemelerinin yönetimini merkezi hale alan bir kuruluşun parçasıysanız, kuruluş yöneticiniz makinenizi güncelleştirme Visual Studio kontrol ediyor olabilir. Makinenizin kabul edile güncelleştirme türlerini denetleme veya yapılandırma hakkında daha fazla bilgi için bkz. Yapılandırma Yöneticisi'yi kullanarak [Visual Studio.](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio Enterprise kılavuzu](visual-studio-enterprise-guide.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
