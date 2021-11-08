---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: En son sürüme Visual Studio güncelleştirme hakkında bilgi edinmek için adım adım bilgi edinin.
ms.date: 09/14/2021
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
ms.openlocfilehash: 4747792137eca0745d2d005c441c6a3c045df0be
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001660"
---
# <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Bu konuda, bir istemci yüklemesini güncelleştirme işlemi Visual Studio.  BIR IT Yöneticisiyseniz ve kuruluş istemcilerini bir ağ düzeninden güncelleştirmek üzere yapılandırmak için, özellikle ağ yüklemelerini yönetme ve güncelleştirme ile ilgili bölüm olmak üzere [Visual Studio](https://aka.ms/vs/admin/guide)Yöneticiler Kılavuzu'ne [bakın.](../install/update-a-network-installation-of-visual-studio.md)

Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio bkz. [Güncelleştirme Mac için Visual Studio.](/visualstudio/mac/update) 

## <a name="before-you-update"></a>Güncelleştirmeden önce

Sanal makineleri yüklemek, güncelleştirmek Visual Studio değiştirmek için, makinede yönetici izinlerine sahip bir hesap ile oturum açmışsınızdır. Tipik bir kullanıcı olarak oturum açtıysanız ve bu komutlardan birini gerçekleştirmeyi denerseniz, sizden yönetici kimlik bilgileri isteminde bir Kullanıcı Hesabı Denetimi bildirimi alısınız. Daha fazla bilgi için bkz. [Kullanıcı İzinleri ve Visual Studio.](../ide/user-permissions-and-visual-studio.md)

Güncelleştirme gerçekleştirmeden önce çalışmanızı kaydetmenizi kesinlikle öneririz.

Visual Studio önce makineye yüklenmiş olması gerekir. Microsoft tarafından barındırılan sunuculardan Visual Studio sürümünü yüklemek için Visual Studio [sayfasına](https://visualstudio.microsoft.com/downloads) gidin. Şu anda başka bir Visual Studio örneği kullanıyorsanız, [Visual Studio'nin](../install/install-visual-studio-versions-side-by-side.md)yeni bir örneğini mevcut yüklemenize yan yana yükleyebilir veya bu yeni örneği yüklemeden önce [Visual Studio'nin](../install/uninstall-visual-studio.md) önceki örneğini kaldırabilirsiniz.

::: moniker range="vs-2017"

Her zaman en son [](/visualstudio/releasenotes/vs2017-relnotes/) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2017'nin en son sürümüne güncelleştirmeniz gerekir. En yeni sürümü denemek için [2022](https://visualstudio.microsoft.com/downloads)sürümünü indirip Visual Studio düşünün.

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Güncelleştirme olduğunda, IDE'nin başlık çubuğunda karşılık gelen bir bildirim Visual Studio vardır. Notifications hub'ı **açmak için bildirim** bayrağını seçin ve ardından yüklemek istediğiniz güncelleştirmeyi seçin.

   ![Visual Studio IDE'nin Bildirim hub' Visual Studio ekran görüntüsü.](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017 ' deki bildirimler hub 'ı")

1. Güncelleştir iletişim **kutusu** açıldığında Şimdi **Güncelleştir'i seçin.**

    ![Visual Studio 2017'nin Bildirimler hub'larından başlatılan Güncelleştir iletişim kutusundaki Şimdi Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-update-now-from-notifications-hub.png "Visual Studio 'de bildirimler hub 'ından güncelleştirme iletişim kutusu")

     User Access Control iletişim kutusu açılırsa Evet'i **seçin.** Ardından bir "Lütfen bekleyin" iletişim kutusu açabilirsiniz ve ardından Visual Studio Yükleyicisi başlatmak için açılır.

     ![En iyi deneyimi Visual Studio Yükleyicisi ekran görüntüsü.](media/visual-studio-15dot6-installer.png "yeni Visual Studio Yükleyicisi deneyimi")

     Güncelleştirmeniz tamamlanır ve Visual Studio yeniden başlatılır.

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğunda Güncelleştirmeleri Denetleme Yardımı'nın seçerek **bir** > **güncelleştirmenin kullanılabilir olup** olduğunu kontrol edin.

     ![Visual Studio'daki Yardım menüsünü gösteren Visual Studio.](media/vs-help-menu-check-for-updates.png "Visual Studio yeni Yardım menüsü")

1. Güncelleştir iletişim **kutusu** açıldığında Şimdi **Güncelleştir'i seçin.**

   Güncelleştirme önceki bölümde açıklandığı gibi devam eder ve güncelleştirme Visual Studio tamamlandıktan sonra yeniden başlatılır.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Visual Studio'ın önceki sürümlerinde olduğu gibi, Visual Studio Yükleyicisi'i kullanarak güncelleştirmeyi yükleyebilirsiniz.  İlk olarak, **Visual Studio Yükleyicisi** bilgisayarınıza yükleyin.  Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.  

1. Yükleyiciyi açın. Devam Visual Studio Yükleyicisi önce güncelleştirme gerektir.

1. Yükleyicinin **Ürün** sayfasında, daha önce yüklemiş Visual Studio şimdi güncelleştirmek istediğiniz uygulamanın sürümünü bulun.

1. Bir güncelleştirme varsa bir Güncelleştir **düğmesiyle karşınız.** (Yükleyicinin bir güncelleştirme olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri **yüklemek** için Güncelleştir düğmesini seçin.

     ![2017'de Visual Studio Yükleyicisi güncelleştirme için kullanılan Güncelleştirme düğmesini Visual Studio ekran görüntüsü.](media/update-visual-studio.png "Visual Studio Yükleyicisi kullanarak 2017 Visual Studio güncelleştirin")

::: moniker-end

::: moniker range="vs-2019"

Her zaman en son [](/visualstudio/releases/2019/release-notes/) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2019'un en son sürümüne güncelleştirmeniz gerekir. En yeni sürümü denemek için [2022](https://visualstudio.microsoft.com/downloads)sürümünü indirip Visual Studio düşünün.

Bir yüklemesini güncelleştirmenin birkaç farklı yolu vardır Visual Studio. Güncelleştirmeleri, Visual Studio Yükleyicisi IDE'de bildirim hub'larını kullanabilir veya önyükleyicinin belirli bir sürümünü çalıştırarak [güncelleştirebilirsiniz.](/visualstudio/releases/2019/history) Bu çeşitli yöntemleri kullanarak Visual &nbsp; Studio &nbsp; 2019'un nasıl güncelleştirilecekleri burada açıklandı.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

   Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.

   ![Bir uygulamanın, Başlat menüsü aramanın sonuçlarını gösteren Visual Studio Yükleyicisi.](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, güncelleştirmek istediğiniz Visual Studio örneğine bakın.

   Örneğin, Daha önce Visual &nbsp; Studio Community &nbsp; 2019 yüklemiş  ve bunun için bir güncelleştirme varsa yükleyicide Kullanılabilir güncelleştirme iletisi görüntülenir.

     ![Kullanılabilir bir güncelleştirmeyle Visual Studio 2019 yüklemesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-update-visual-studio-community.png "güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri **yüklemek** için Güncelleştir'i seçin.

    ![Visual Studio 2019 yüklemesinde bir sürüme güncelleştirmek için kullanılan Visual Studio gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilirsiniz. Öyleyse, bunu yap ve ardından normal Visual Studio gibi yeni bir başlangıç yap.

   Bilgisayarınızı yeniden başlatmanız istenecekse başlat'ı **seçen** yükleyiciden Visual Studio başlat'ı seçin.

    ![2019'Visual Studio başlatmak için kullanılan Visual Studio ekran görüntüsü.](media/vs-2019/choose-launch-visual-studio-community.png "Başlamak için Başlat düğmesini seçin Visual Studio")

## <a name="use-the-message-box-in-the-ide"></a>IDE'de ileti kutusunu kullanma

1.  Bir güncelleştirme Visual Studio IDE tarafından güncelleştirmeyi denetler.  Bazı durumlarda, Visual Studio **2019 güncelleştirme** iletisi kısa bir süre görüntülenir. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.**  Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

    ![IDE'de 'Visual Studio 2019 güncelleştirmesi' iletiyi gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-ide-message.png "ıde 'deki ' Visual Studio 2019 güncelleştirme ' iletisi")

1. Ayrıntıları **görüntüle'yi seçerseniz,** sonraki İndirilen güncelleştirme **ve yüklenmeye hazır** iletişim kutusunda Şimdi güncelleştirmek için **Güncelleştir'i** seçin.

     !['İndirilen ve yüklenmeye hazır' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğundan Yardım'ı ve ardından  Güncelleştirmeleri Kontrol Et'i seçerek bir güncelleştirmenin kullanılabilir olup **olduğunu kontrol edin.**  Arama kutusunu **Ctrl** Q tuşlarına basarak, "güncelleştirmeleri kontrol edin" yazarak ve ardından eşleşen + arama sonuçlarını seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki 'Güncelleştirmeleri Denetleme' seçeneğini gösteren ekran görüntüsü.](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin")

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Bildirim hub'larını açmak için IDE'nin Visual Studio sağ alt **köşesindeki bildirim simgesini** seçin.

   ![Visual Studio IDE'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2019/notification-bar.png "Visual Studio ıde 'deki bildirim simgesi")

1. Bildirimler **hub'sinde,** yüklemek istediğiniz güncelleştirmeyi seçin. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.** Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

     ![Visual Studio 2019'daki Bildirim hub'larını gösteren ekran görüntüsü.](media/vs-2019/notification-hub-update.png "Visual Studio 2019 ' deki bildirim hub 'ı")

1. Ayrıntıları **görüntüle'yi seçtiysanız,** sonraki Kullanılabilir **güncelleştirme iletişim kutusunda** Güncelleştir'i **seçin.**

## <a name="run-a-specific-bootstrapper"></a>Belirli bir önyükleyiciyi çalıştırma
Enterprise veya Professional müşterisiysiniz, yüklü olandan daha yüksek bir sürüm olduğu sürece Visual Studio 2019 örneğinizi yayımlanan belirli bir sürüme güncelleştirin. Visual Studio 2019 örneğinizi bu yöntemle güncelleştirmek için [Visual Studio 2019](/visualstudio/releases/2019/history)yayın geçmişi sayfasına gidin, istenen güncelleştirme sürümüne karşılık gelen önyükleyiciyi ürün yükleme dizininize indirin ve ardından güncelleştirmeyi başlatmak için buna çift tıklayın.  

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Güncelleştirme davranışını kontrol etmek için özelleştirebileceğiniz birkaç farklı ayar vardır. Bu ayarlardan birkaçı 2019'Visual Studio yereldir ve ürün bitlerinin nasıl ve ne zaman yükleniyor olduğuyla ilgilenilir. Güncelleştirmelerin kaynağını yapılandırma gibi diğer ayarlar, 2022 yükleyicisi için Visual Studio gerektirir.  

### <a name="installation-and-download-behaviors"></a>Yükleme ve indirme davranışları

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. **Ortam'ı** genişletin ve ardından Ürün **Güncelleştirmeleri'ne tıklayın.**

    ![Güncelleştirmeler sayfasındaki güncelleştirme ayarlarını gösteren Visual Studio.](media/vs-2019/update-settings-options.png)

1. Bu iletişim kutusunda ayarlan kullanılabilen yapılandırma seçeneklerini gözlemlemek. Makineniz **boştayken güncelleştirmelerin** indirileye izin veren Güncelleştirmeleri otomatik olarak indir ayarını seçebilirsiniz. Ayrıca iki yükleme modu da vardır: **İndirme sırasında yükle** ve Hepsini indir ve sonra **yükle.**   Güncelleştirmeleri yüklemek için istediğiniz yükleme modunu ve otomatik indirme Visual Studio seçin.

### <a name="configure-source-location-of-updates"></a>Güncelleştirmelerin kaynak konumunu yapılandırın
Kurumsal ortamındaysanız, istemci örneklerinizin güncelleştirmeler için baktığı konumu yapılandırmak mümkündür. Bu, istemcinizin bir ağ düzeninden yüklendiği durumlarda, ancak daha sonra istemcilerin farklı bir ağ düzeninden güncelleştirme almasını istediğinizde yararlıdır. güncelleştirme konumlarını yapılandırma özelliği, istemci makinesine Visual Studio 2022 yüklenerek veya bir ağ düzeni üzerinden göndererek bir yönetici tarafından elde edilen yeni Visual Studio 2022 yükleyicisinin varlığını gerektirir. bu senaryonun nasıl yapılandırılacağı hakkında daha fazla bilgi için, [Visual Studio yöneticileri kılavuzuna](https://aka.ms/vs/admin/guide) bakın.

## <a name="update-on-close"></a>Yakın güncelleştirme

Visual Studio 2019 sürüm 16,9 ' de, **güncelleştirme kavramını yakın** bir şekilde kullanıma sunduk.  Bir güncelleştirme kullanılabilir olduğunda, IDE 'deki güncelleştirme bildirimi Kullanıcı arabirimi, Visual Studio gönüllü olarak kapattığınızda güncelleştirmeyi ertelemenizi sağlayan bir yol sağlar. **Kapat** düğmesi güncelleştirme bildirim iletisi kutusunda görünür ve Bildirim Hub 'ında de seçilebilir. **Kapat komutuyla güncelleştirme** kalıcı bir ayar değildir; yalnızca geçerli güncelleştirme için geçerlidir. Diğer bir deyişle, güncelleştirmenin kullanılabilir olduğu bildirimi her onayladığınızda veya **kapaışınızda kapatma** erteleme ertelemeal güncelleştirmesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda kapana güncelleştirme seçeneğini gösteren ekran görüntüsü.](media/vs-2019/update-on-close.png)

::: moniker-end

::: moniker range=">=vs-2022"

en son özellikleri, güvenlik düzeltmelerini ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2022 ' in en [son sürümüne](/visualstudio/releases/2022/release-notes) güncelleştirmeniz önerilir.

Visual Studio yüklemesini güncelleştirmenin birkaç farklı yolu vardır. Visual Studio Yükleyicisi aracılığıyla güncelleştirebilirsiniz, güncelleştirmeleri denetleyebilir veya ıde 'de bildirim hub 'ını kullanabilir ya da [önyükleyici 'nin belirli bir sürümünü](/visualstudio/releases/2022/release-history)çalıştırarak güncelleştirebilirsiniz. &nbsp;Bu çeşitli yöntemleri kullanarak Visual Studio 2022 ' i nasıl güncelleşirsiniz &nbsp; .

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

   Windows Başlat menüsü, "yükleyici" araması yapın ve sonra sonuçlardan **Visual Studio Yükleyicisi** ' yı seçin.

   ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2022/vs-installer.png "Visual Studio Yükleyicisi arayın")

   devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenirse, istemleri izleyerek bunu yapın.

1. Visual Studio Yükleyicisi, güncelleştirmek istediğiniz Visual Studio yüklemeyi bulun. 

   örneğin, daha önce 2022 önizleme Visual Studio Community yüklediyseniz ve bu güncelleştirme için bir güncelleştirme varsa, Visual Studio Yükleyicisi bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![yeni bir güncelleştirme kullanılabilir olduğunda Visual Studio Yükleyicisi güncelleştirme düğmesini ve iletiyi gösteren ekran görüntüsü.](media/vs-2022/vs-installer-update-visual-studio-community.png "güncelleştirmek istediğiniz Visual Studio 2022 sürümünü seçin")

1. Güncelleştirmeyi yüklemek için **Güncelleştir** ' i seçin.

    ![Yeni güncelleştirmeyi yüklemek için seçebileceğiniz güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeyi yüklemek için Güncelleştir düğmesini seçin")

1. güncelleştirme tamamlandıktan sonra Visual Studio Yükleyicisi bilgisayarınızı yeniden başlatmanızı isteyebilir. bu durumda, bunu yapın ve genellikle Visual Studio başlatın.

    bilgisayarınızı yeniden başlatmanız istenmezse, Visual Studio Yükleyicisi Visual Studio başlatmak için **başlat** ' ı seçin.

    ![Visual Studio başlatmayı seçebileceğiniz başlatma düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-launch-visual-studio-community.png "Başlamak için Başlat düğmesini seçin Visual Studio")

## <a name="use-the-message-box-in-the-ide"></a>IDE 'deki ileti kutusunu kullanın

1. Visual Studio açtığınızda, ıde bir güncelleştirmenin kullanılabilir olup olmadığını denetler.  bazı durumlarda **Visual Studio 2022 güncelleştirme** iletisi kısaca görüntülenir. Şimdi güncelleştirmek istiyorsanız, **Ayrıntıları görüntüle**' yi seçin.  Visual Studio kapatana kadar güncelleştirmeyi ertelemek istiyorsanız, **kapatma sırasında güncelleştir**' i seçin.

    ![Visual Studio ıde 'nin sağ alt köşesinde Visual Studio 2022 için bir güncelleştirme iletisi gösteren ekran görüntüsü.](media/vs-2022/update-visual-studio-ide-message.png "ıde 'deki ' Visual Studio 2022 güncelleştirme ' iletisi")

1. **Ayrıntıları görüntüle**' yi seçerseniz, sonraki **güncelleştirme** iletişim kutusunda, şimdi güncelleştirmek için **Güncelleştir** ' i seçin. 

     ![Visual Studio 2022 ' deki ' kullanılabilir ' güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetle

1. Menü çubuğundan **Yardım** ' ı seçerek ve ardından **Güncelleştirmeleri denetle**' yi seçerek bir güncelleştirmenin kullanılabilir olup olmadığını kontrol edebilirsiniz.  Arama kutusunu **CTRL** + **Q** tuşlarına basarak, "güncelleştirmeleri denetle" yazarak ve ardından eşleşen arama sonucunu seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki ' güncelleştirmeleri denetle ' seçeneğini gösteren ekran görüntüsü.](media/vs-2022/ide-check-updates-help-menu.png "Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin")

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. **bildirimler** merkezini açmak için Visual Studio ıde 'nin sağ alt köşesinden bildirim simgesini seçin.

   ![Visual Studio ıde 'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2022/notification-bar.png "Visual Studio 2022 ' deki bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin. Şimdi güncelleştirmek istiyorsanız, **Ayrıntıları görüntüle**' yi seçin. Visual Studio kapatana kadar güncelleştirmeyi ertelemek istiyorsanız, **kapatma sırasında güncelleştir**' i seçin.

     ![Visual Studio ıde 'de bildirimler hub 'ını gösteren ekran görüntüsü.](media/vs-2022/notification-hub-update.png "Visual Studio 2022 ' deki bildirimler hub 'ı")

1. **Ayrıntıları görüntüle**' yi seçerseniz, sonraki **güncelleştirme** iletişim kutusunda **Güncelleştir**' i seçin.

## <a name="run-a-specific-bootstrapper"></a>Belirli bir önyükleyici çalıştırma
Enterprise Professional veya müşterisiyseniz, zaten yüklü olan sürümden daha yüksek bir sürüm olduğu sürece Visual Studio 2022 örneğinizi yayınlanan belirli bir sürüme güncelleştirebilirsiniz. Visual Studio 2022 örneğinizi bu yöntem aracılığıyla güncelleştirmek için [Visual Studio 2022 sürüm geçmişi sayfasına gidin](/visualstudio/releases/2022/release-history), istenen güncelleştirme sürümüne karşılık gelen önyükleyici ürün yükleme dizininize indirin ve ardından bu güncelleştirmeyi başlatmak için çift tıklayın.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Ürün bitlerinin nasıl ve ne zaman indirileceği, ne zaman ve güncelleştirme kaynak konumunun olduğu gibi, güncelleştirme davranışını denetlemek için özelleştirilebilecek birkaç farklı ayar vardır.  

### <a name="installation-and-download-behaviors"></a>Yükleme ve indirme davranışları

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Ortam**' ı genişletin ve **ürün güncelleştirmeleri**' ni seçin.

    ![Visual Studio ıde 'nin seçenekler penceresinde güncelleştirmeler ayarlarını gösteren ekran görüntüsü.](media/vs-2022/update-settings-options.png)

1. Bu iletişim kutusunda ayarlanabilir yapılandırma seçeneklerini gözlemleyin. Makine boşta kaldığında güncelleştirmelerin indirilmesine izin veren **güncelleştirmeleri otomatik olarak indir** ayarını seçebilirsiniz. Aralarından seçim yapabileceğiniz iki yükleme modu da vardır: **indirme sırasında yükle** ve **Tümünü İndir, sonra Yükle**.   Visual Studio güncelleştirmelerinizin yükleme modunu ve otomatik karşıdan yükleme ayarını seçin.

### <a name="configure-source-location-of-updates"></a>Güncelleştirmelerin kaynak konumunu yapılandırın
Visual Studio 2022 ile, artık istemcilerinizin güncelleştirmelerinin nereden alınacağını yapılandırabilirsiniz. bu güncelleştirme kaynak konumlarına "kanallar" adı verilir ve [Visual Studio Release rhythd](/visualstudio/productinfo/release-rhythm) belgelerinde kanal amacı ve kullanılabilirliği hakkında daha fazla bilgi edinebilirsiniz. Microsoft, hem geçerli hem de önizleme kanallarını herkese açık hale getirir ve uzun süreli bakım kanalları (ltscs) Enterprise ve Professional müşterileri tarafından kullanılabilir. BT yöneticileri, istemcilerin erişimi olması gereken ağ düzenleri gibi güncelleştirme kaynak konumlarını da yapılandırabilir. bunun nasıl ayarlanacağı hakkında ek seçenekler ve ayrıntılar için [Visual Studio yöneticileri kılavuzuna](https://aka.ms/vs/admin/guide) bakın. 

Visual Studio örneğinizin güncelleştirmelerini alması gereken kanalı değiştirmenize olanak sağlayan güncelleştirme Ayarlar iletişim kutusunu açmak için iki yol vardır. 

1. Visual Studio yükleyicisini açın, yapılandırmak istediğiniz örneği seçin, **daha fazla düğmesini** seçin ve ardından **güncelleştirme ayarları** menü seçeneğini belirleyin. Visual Studio Yükleyicisi nasıl bulacağınızı öğrenmek için önceki yönergelere bakın.

    ![Yükleyicideki güncelleştirme ayarlarını gösteren ekran görüntüsü.](media/vs-2022/installer-update-settings-menu-option.png)

2. güncelleştirme Ayarlar iletişim kutusunu çağırmak için alternatif bir yol Visual Studio ıde 'yi açmak, güncelleştirme ile ilgili **ayrıntıları görüntülemek** veya yardım menüsünde **güncelleştirmeleri denetlemek** ya da güncelleştirme ayarlarını değiştir bağlantısına tıklamanız gerekir.   

    ![IDE 'deki güncelleştirme kullanılabilir iletişim kutusunda güncelleştirme ayarlarını gösteren ekran görüntüsü.](media/vs-2022/invoke-update-settings-in-the-IDE.png)
    
**Güncelleştirme ayarları** iletişim kutusu şuna benzeyecektir.

   ![Visual Studio 2022 ıde 'de güncelleştirme ayarları iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/update-settings.png)

**Güncelleştirme kanalı** açılan menüsünde doğru değeri seçerek bu Visual Studio örneği için gelecekteki güncelleştirmelerin kaynak konumunu kontrol edebilirsiniz. Göz önünde bulundurmanız gereken ek şeyler şunlardır:
 * önizleme ve geçerli kanallar tüm Visual Studio sürümleri için kullanılabilir ve ltsc kanalları yalnızca Professional ve Enterprise müşterileri için kullanılabilir. 
 * Visual Studio örneğinizi güncelleştirme kanalı konumunu yapılandırdıktan hemen sonra güncelleştirmeyi seçebilirsiniz. Ya da gerçek ürün güncelleştirmesini bir süre sonra erteleyebilirsiniz. Güncelleştirme kanalını yapılandırma ve ürünü güncelleştirme eylemi, iki bağımsız olaydır. 
 * Yeni bir kanala güncelleştirdiğinizde en son sürümü bu kanala yüklersiniz. Kurumsal müşteriyseniz ve belirli bir sürümü bir kanala yüklemek istiyorsanız, daha önce açıklanan belirli bir önyükleyici talimatlarını çalıştırın. 
 * Güncelleştirme kanalını yalnızca, söz konusu kanalın ipucunda bulunan ürünün sürümü yüklemiş olduğunuz sürümden **fazlaysa** değiştirebilirsiniz. Örneğin, her zaman geçerli kanaldan önizleme kanalına geçiş yapabilirsiniz, ancak geçerli kanalın en son sürümü yüklediğiniz önizleme sürümünü geçirene kadar önizleme kanalından geçerli kanala geçiş yapamazsınız. 
 * LTSC kanalları için süre sonu tarihleri vardır. LTSC 'nin süresi dolduktan sonra, güncelleştirme kaynağı olarak kullanılamaz ve bu listeden kaybolacaktır.
 * Tüm Microsoft kanalları Microsoft sunucularında barındırılır ve internet erişimi gerektirir.
 * her Visual Studio örneği, güncelleştirme kaynağını bağımsız olarak yapılandırma özelliğine sahiptir. bu nedenle, Visual Studio 2022 ' nin iki örneği yüklüyse, her biri farklı bir kanaldan güncelleştirebilir. 
 * BT yöneticileri **güncelleştirme kanalı** açılan menüsündeki değerleri denetleyebilir. Örneğin, güncelleştirme kaynakları olarak ağ düzeni konumları ekleyebilirler. Ayrıca, Microsoft tarafından barındırılan konumların güncelleştirme kaynağı seçenekleri olarak kullanılabilmesini de engelleyebilir. bu işlevsellik Visual Studio 2019 yüklemesi için de geçerlidir. bu güncelleştirme konumlarını yapılandırma hakkında daha fazla bilgi için, [Visual Studio yöneticileri kılavuzuna](https://aka.ms/vs/admin/guide) bakın.

## <a name="update-on-close"></a>Yakın güncelleştirme

Bir güncelleştirme kullanılabilir olduğunda, IDE 'deki güncelleştirme bildirimi Kullanıcı arabirimi, Visual Studio gönüllü olarak kapatana kadar güncelleştirmeyi ertelemenizi sağlayan bir yol sağlar. **Kapat** düğmesi güncelleştirme bildirim iletisi kutusunda görünür ve **bildirim** hub 'ında de seçilebilir. **Kapat komutuyla güncelleştirme** kalıcı bir ayar değildir; yalnızca geçerli güncelleştirme için geçerlidir. Diğer bir deyişle, güncelleştirmenin kullanılabilir olduğu bildirimi her onayladığınızda veya **kapaışınızda kapatma** erteleme ertelemeal güncelleştirmesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda kapana güncelleştirme seçeneğini gösteren ekran görüntüsü.](media/vs-2022/update-on-close.png)

::: moniker-end

## <a name="administrator-updates"></a>Yönetici güncelleştirmeleri

yazılım yüklemelerinin yönetimini merkezileştiren bir kuruluşun parçasıysa, kuruluş yöneticiniz Visual Studio makinenizi nasıl güncelleştirçalıştığını denetleyebilir. makinenizin kabul edebileceği güncelleştirme türlerini denetleme veya yapılandırma hakkında daha fazla bilgi için bkz. [Visual Studio güncelleştirmelerini dağıtmak için Configuration Manager kullanma](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio Enterprise kılavuzu](visual-studio-enterprise-guide.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
