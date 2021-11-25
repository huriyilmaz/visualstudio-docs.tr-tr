---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: En son sürüme Visual Studio güncelleştirme hakkında bilgi edinmek için adım adım bilgi edinin.
ms.date: 11/23/2021
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
ms.openlocfilehash: 961561a30fa2505ad655899ef719e6d7aff15567
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133109000"
---
# <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Bu konu başlığında, bir istemci yüklemesini güncelleştirme işlemi Visual Studio.  BIR IT Yöneticisiyseniz ve kuruluş istemcilerini bir ağ düzeninden güncelleştirmek üzere yapılandırmak için, özellikle ağ yüklemelerini yönetme ve güncelleştirme ile ilgili bölüm olmak üzere [Visual Studio](https://aka.ms/vs/admin/guide)Yöneticiler Kılavuzu'ne [bakın.](../install/update-a-network-installation-of-visual-studio.md)

Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Güncelleştirme Mac için Visual Studio.](/visualstudio/mac/update) 

## <a name="before-you-update"></a>Güncelleştirmeden önce

Sanal makineleri yüklemek, güncelleştirmek Visual Studio değiştirmek için, makinede yönetici izinlerine sahip bir hesap ile oturum açmışsınızdır. Tipik bir kullanıcı olarak oturum açtıysanız ve bu komutlardan birini gerçekleştirmeyi denerseniz, sizden yönetici kimlik bilgileri istemi alan bir Kullanıcı Hesabı Denetimi bildirimini alısınız. Daha fazla bilgi için bkz. [Kullanıcı İzinleri ve Visual Studio.](../ide/user-permissions-and-visual-studio.md)

Güncelleştirme gerçekleştirmeden önce çalışmanızı kaydetmenizi kesinlikle öneririz.

Visual Studio önce makineye yüklenmiş olması gerekir. Microsoft tarafından barındırılan sunuculardan Visual Studio sürümünü yüklemek için Visual Studio [sayfasına](https://visualstudio.microsoft.com/downloads) gidin. Şu anda başka bir Visual Studio örneği kullanıyorsanız, [Visual Studio'nin](../install/install-visual-studio-versions-side-by-side.md)yeni bir örneğini mevcut yüklemenize yan yana yükleyebilir veya bu yeni örneği yüklemeden önce [önceki Visual Studio](../install/uninstall-visual-studio.md) örneğini kaldırabilirsiniz.

::: moniker range="vs-2017"

Her zaman en son [](/visualstudio/releasenotes/vs2017-relnotes/) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2017'nin en son sürümüne güncelleştirmeniz gerekir. En yeni sürümü denemek için [2022 sürümünü indirip Visual Studio 2022'yi deneyin.](https://visualstudio.microsoft.com/downloads)

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Güncelleştirme olduğunda, IDE'nin başlık çubuğunda karşılık gelen bir bildirim Visual Studio vardır. Bildirimler hub'larını **açmak için bildirim** bayrağını seçin ve ardından yüklemek istediğiniz güncelleştirmeyi seçin.

   ![IDE'nin Bildirim hub'larında bir güncelleştirmeyi Visual Studio görüntüsü.](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017'de Bildirimler hub'ı")

1. Güncelleştir iletişim **kutusu** açıldığında Şimdi **Güncelleştir'i seçin.**

    ![Visual Studio 2017'nin Bildirimler hub'larından başlatılan Güncelleştir iletişim kutusundaki Şimdi Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-update-now-from-notifications-hub.png "Visual Studio'daki Bildirimler hub'larından Güncelleştir iletişim Visual Studio")

     User Access Control iletişim kutusu açılırsa Evet'i **seçin.** Ardından, bir süre için "Lütfen bekleyin" iletişim kutusu açabilirsiniz ve ardından Visual Studio Yükleyicisi başlatmak için yeni iletişim kutusu açılır.

     ![En iyi deneyimi Visual Studio Yükleyicisi ekran görüntüsü.](media/visual-studio-15dot6-installer.png "Yeni Visual Studio Yükleyicisi deneyimi")

     Güncelleştirmeniz tamamlanır ve Visual Studio yeniden başlatılır.

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğunda Güncelleştirmeleri Denetleme Yardımı'nın seçerek **bir** > **güncelleştirmenin kullanılabilir olup** olduğunu kontrol edin.

     ![Web'de Yardım menüsünü gösteren Visual Studio.](media/vs-help-menu-check-for-updates.png "Visual Studio'daki yeni Yardım Visual Studio")

1. Güncelleştir iletişim **kutusu** açıldığında Şimdi **Güncelleştir'i seçin.**

   Güncelleştirme önceki bölümde açıklandığı gibi devam eder ve güncelleştirme Visual Studio tamamlandıktan sonra yeniden başlatılır.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Visual Studio'nin önceki sürümlerinde olduğu gibi, Visual Studio Yükleyicisi yüklemek için kullanabilirsiniz.  İlk olarak, **Visual Studio Yükleyicisi** bilgisayarınıza yükleyin.  Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.  

1. Yükleyiciyi açın. Devam Visual Studio Yükleyicisi önce güncelleştirme gerektir.

1. Yükleyicinin **Ürün** sayfasında, daha önce yüklemiş Visual Studio şimdi güncelleştirmek istediğiniz uygulamanın sürümünü bulun.

1. Bir güncelleştirme varsa, bir Güncelleştir **düğmesiyle karşınız.** (Yükleyicinin bir güncelleştirme olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri **yüklemek** için Güncelleştir düğmesini seçin.

     ![2017'de Visual Studio Yükleyicisi güncelleştirme için kullanılan Güncelleştirme düğmesini Visual Studio ekran görüntüsü.](media/update-visual-studio.png "Visual Studio kullanarak 2017 güncelleştirme Visual Studio Yükleyicisi")

::: moniker-end

::: moniker range="vs-2019"

Her zaman en son [](/visualstudio/releases/2019/release-notes/) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2019'un en son sürümüne güncelleştirmeniz gerekir. En yeni sürümü denemek için [2022 sürümünü indirip Visual Studio 2022'yi deneyin.](https://visualstudio.microsoft.com/downloads)

Bir yüklemesini güncelleştirmenin birkaç farklı yolu vardır Visual Studio. Güncelleştirmeleri Visual Studio Yükleyicisi, güncelleştirmeleri kontrol etmek veya IDE'de Bildirim hub'larını kullanmak ya da önyükleyicinin belirli bir sürümünü [çalıştırarak güncelleştirebilirsiniz.](/visualstudio/releases/2019/history) Bu çeşitli yöntemleri kullanarak Visual &nbsp; Studio &nbsp; 2019'un nasıl güncelleştirilecekleri burada açıklandı.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

   Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.

   ![Uygulamanın arama sonuçlarını Başlat menüsü ekran Visual Studio Yükleyicisi.](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, güncelleştirmek istediğiniz Visual Studio örneğine bakın.

   Örneğin, Daha önce Visual &nbsp; Studio Community &nbsp; 2019'a  yüklemiş ve bunun için bir güncelleştirme varsa yükleyicide Kullanılabilir güncelleştirme iletisi görüntülenir.

     ![Kullanılabilir güncelleştirme ile Visual Studio 2019 yüklemesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri **yüklemek** için Güncelleştir'i seçin.

    ![Visual Studio 2019 yüklemesinde bir sürüme güncelleştirmek için kullanılan Visual Studio gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilirsiniz. Öyleyse, bunu yap ve ardından normal Visual Studio gibi yeni bir başlangıç yap.

   Bilgisayarınızı yeniden başlatmanız istenecekse başlat'ı **seçen** Visual Studio başlat'ı seçin.

    ![2019'da Visual Studio için kullanılan Başlat düğmesini gösteren Visual Studio görüntüsü.](media/vs-2019/choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-message-box-in-the-ide"></a>IDE'de ileti kutusunu kullanma

1.  Bir güncelleştirme Visual Studio IDE tarafından güncelleştirmeyi denetler.  Bazı durumlarda, Visual Studio **2019 güncelleştirme** iletisi kısa bir süre görüntülenir. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.**  Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

    ![IDE'de 'Visual Studio 2019 güncelleştirmesi' iletiyi gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi")

1. Ayrıntıları **görüntüle'yi seçtiysanız,** sonraki güncelleştirme **indirildi ve** yüklenmeye hazır iletişim kutusunda Şimdi güncelleştirmek için **Güncelleştir'i** seçin.

     !['İndirilen ve yüklenmeye hazır' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğundan Yardım'ı ve ardından  Güncelleştirmeleri Kontrol Et'i seçerek bir güncelleştirmenin kullanılabilir olup **olduğunu kontrol edin.**  Arama kutusunu **Ctrl** Q tuşlarına basarak, "güncelleştirmeleri kontrol edin" yazarak ve ardından eşleşen + arama sonuçlarını seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki 'Güncelleştirmeleri Denetleme' seçeneğini gösteren ekran görüntüsü.](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. IDE'nin sağ alt köşesindeki bildirim simgesini Visual Studio **Hub'ı açmak için** seçin.

   ![Visual Studio IDE'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

1. Bildirimler **hub'sinde,** yüklemek istediğiniz güncelleştirmeyi seçin. Şimdi güncelleştirmek için Ayrıntıları **görüntüle'yi seçin.** Güncelleştirmeyi kapatana kadar ertelemek Visual Studio **Kapat'ta Güncelleştir'i seçin.**

     ![Visual Studio 2019'daki Bildirim hub'larını gösteren ekran görüntüsü.](media/vs-2019/notification-hub-update.png "Visual Studio 2019'daki Bildirim hub'ı")

1. Ayrıntıları **görüntüle'yi seçtiysanız,** sonraki Kullanılabilir **güncelleştirme iletişim kutusunda** Güncelleştir'i **seçin.**

## <a name="run-a-specific-bootstrapper"></a>Belirli bir önyükleyiciyi çalıştırma
Enterprise veya Professional müşterisiysiniz, yüklü olandan daha yüksek bir sürüm olduğu sürece Visual Studio 2019 örneğinizi yayımlanan belirli bir sürüme güncelleştirin. Visual Studio 2019 örneğinizi bu yöntemle güncelleştirmek için [Visual Studio 2019](/visualstudio/releases/2019/history)yayın geçmişi sayfasına gidin, istenen güncelleştirme sürümüne karşılık gelen önyükleyiciyi ürün yükleme dizininize indirin ve ardından güncelleştirmeyi başlatmak için buna çift tıklayın.  

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Güncelleştirme davranışını kontrol etmek için özelleştirebileceğiniz birkaç farklı ayar vardır. Bu ayarlardan birkaçı Visual Studio 2019'da yereldir ve ürün bitlerinin nasıl ve ne zaman yükleniyor olduğuyla ilgilenilir. Güncelleştirmelerin kaynağını yapılandırma gibi diğer ayarlar, 2022 yükleyicisi için yeni Visual Studio gerektirir.  

### <a name="installation-and-download-behaviors"></a>Yükleme ve indirme davranışları

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. **Ortam'ı** genişletin ve ardından Ürün **Güncelleştirmeleri'ne tıklayın.**

    ![Güncelleştirmeler sayfasındaki güncelleştirme ayarlarını gösteren Visual Studio.](media/vs-2019/update-settings-options.png)

1. Bu iletişim kutusunda ayarlan kullanılabilen yapılandırma seçeneklerini gözlemlemek. Makineniz **boştayken güncelleştirmelerin** indirileye izin veren Güncelleştirmeleri otomatik olarak indir ayarını seçebilirsiniz. Ayrıca iki yükleme modu da vardır: **İndirme sırasında yükle** ve Hepsini **indir'i ve ardından 'yi yükleyin.**   Uygulama güncelleştirmeleri için istediğiniz yükleme modunu ve otomatik indirme Visual Studio seçin.

### <a name="configure-source-location-of-updates"></a>Güncelleştirmelerin kaynak konumunu yapılandırma
Kurumsal bir ortamdaysanız, istemci örneklerinizin güncelleştirmeleri arama konumunu yapılandırmak mümkündür. Bu, istemcinizin bir ağ düzeninden yük olduğu ancak daha sonra istemcilerin farklı bir ağ düzeninden güncelleştirmeler almak istediğiniz durumlarda kullanışlıdır. Güncelleştirme konumlarını yapılandırma özelliği, istemci makinesine Visual Studio 2022 yükleyerek veya bir ağ düzeni aracılığıyla bunu dışarı iten bir yönetici tarafından elde edilen yeni Visual Studio 2022 yükleyicinin mevcut olması gerekir. Bu özelliğin kullanımı hakkında daha fazla bilgi için güncelleştirmelerin kaynak konumunu [yapılandırma hakkında Visual Studio 2022'ye](/visualstudio/install/update-visual-studio?view=vs-2022&preserve-view=true#configure-source-location-of-updates-1)ilişkin Visual Studio belgelerine bakın. Ayrıca, en son Visual Studio 2022 yükleyicisini kullanmak için Visual Studio [2019](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-use-the-latest-installer)düzenlerinizi yapılandırma hakkında bilgi için bkz. . 

## <a name="update-on-close"></a>Kapatmada güncelleştir

2019 Visual Studio 16.9 sürümünde, Kapat üzerinde **Güncelleştirme kavramını tanıtmıştık.**  Bir güncelleştirme kullanılabilir olduğunda, IDE'de güncelleştirme bildirimi kullanıcı arabirimi, IDE'de güncelleştirmeyi isteğe bağlı olarak kapatarak güncelleştirmeyi ertelemenin bir Visual Studio. **Kapat'ta** Güncelleştir düğmesi güncelleştirme bildirimi ileti kutusunda görünür ve bildirim hub'larında da seçilebilir. Kapat **komutunda Güncelleştir** kalıcı bir ayar değildir; Yalnızca geçerli güncelleştirme için geçerlidir. Başka bir deyişle, **güncelleştirmenin kullanılabilir olduğunu** bildirimi her onaylar veya kapatırken Kapat'ta Güncelleştir ertelemesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda Kapat'ta Güncelleştir seçeneğini gösteren ekran görüntüsü.](media/vs-2019/update-on-close.png)

::: moniker-end

::: moniker range=">=vs-2022"

Her zaman en son [](/visualstudio/releases/2022/release-notes) özellikleri, güvenlik düzeltmelerini ve geliştirmeleri elde etmek için Visual Studio 2022'nin en son sürümüne güncelleştirmeniz gerekir.

Bir yüklemesini güncelleştirmenin birkaç farklı yolu Visual Studio. Güncelleştirmeleri Visual Studio Yükleyicisi, güncelleştirmeleri kontrol etmek veya IDE'de bildirim hub'larını kullanmak ya da önyükleyicinin belirli bir sürümünü [çalıştırarak güncelleştirebilirsiniz.](/visualstudio/releases/2022/release-history) Bu çeşitli yöntemleri kullanarak Visual &nbsp; Studio &nbsp; 2022'nin nasıl güncelleştiril burasıdır.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

   Aşağıdaki Windows Başlat menüsü "yükleyici" araması ve ardından sonuçlardan **Visual Studio Yükleyicisi'yi** seçin.

   ![Bir uygulamanın, Başlat menüsü aramanın sonuçlarını gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenirse, istemleri takip etmek için bunu yapın.

1. Bu Visual Studio Yükleyicisi, güncelleştirmek istediğiniz Visual Studio yüklemesini bakın. 

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

     ![Visual Studio 2022'de 'Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="manually-check-for-updates"></a>Güncelleştirmeleri el ile denetleme

1. Menü çubuğundan Yardım'ı ve ardından  Güncelleştirmeleri Kontrol Et'i seçerek bir güncelleştirmenin kullanılabilir olup **olduğunu kontrol edin.**  Arama kutusunu **Ctrl** Q tuşlarına basarak, "güncelleştirmeleri kontrol edin" yazarak ve ardından eşleşen + arama sonuçlarını seçerek de kullanabilirsiniz. 

     ![Yardım menüsündeki 'Güncelleştirmeleri Kontrol Et' seçeneğini gösteren ekran görüntüsü.](media/vs-2022/ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusundaki Güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. IDE'nin sağ alt köşesindeki bildirim simgesini Visual Studio **hub'larını açın.**

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

2. Güncelleştirme Ayarlar iletişim kutusunu çağırmanın alternatif bir yolu, Visual Studio IDE'yi açmak, Kullanılabilir güncelleştirme  iletişim kutusunu açmaktır  (güncelleştirme bildirimiyle ilgili ayrıntıları görüntüle veya Yardım menüsünde güncelleştirmeleri kontrol et) ve Güncelleştirme ayarlarını değiştir bağlantısına tıklamaktır.   

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
 * It Administrators can control the values in the **Update channel** dropdown. Örneğin, ağ düzeni konumlarını güncelleştirme kaynakları olarak ekleyebilirler. Ayrıca Microsoft tarafından barındırılan konumların güncelleştirme kaynağı seçenekleri olarak kullanılabilir olması engel olabilir. Bu işlevsellik, 2019 Visual Studio için de çalışır. Bu güncelleştirme konumlarını yapılandırma hakkında bilgi için Bkz. [Visual Studio Yönetici Kılavuzu](https://aka.ms/vs/admin/guide)

## <a name="update-on-close"></a>Kapatmada güncelleştir

Bir güncelleştirme kullanılabilir olduğunda, IDE'de güncelleştirme bildirimi kullanıcı arabirimi, siz isteğe bağlı olarak kapatana kadar güncelleştirmeyi ertelemenin bir Visual Studio. **Kapat'ta** Güncelleştir düğmesi güncelleştirme bildirimi ileti kutusunda görünür ve Bildirim hub'larında **da seçilebilir.** Kapat **komutunda Güncelleştir** kalıcı bir ayar değildir; Yalnızca geçerli güncelleştirme için geçerlidir. Başka bir deyişle, **güncelleştirmenin kullanılabilir olduğunu** bildirimi her onaylar veya kapatırken Kapat'ta Güncelleştir ertelemesi seçilmelidir.

   ![Güncelleştirme bildirimi ileti kutusunda Kapat'ta Güncelleştir seçeneğini gösteren ekran görüntüsü.](media/vs-2022/update-on-close.png)

::: moniker-end

## <a name="administrator-updates"></a>Yönetici güncelleştirmeleri

Yazılım yüklemelerinin yönetimini merkezi hale alan bir kuruluşun parçasıysanız, kuruluş yöneticiniz makinenizi güncelleştirme Visual Studio kontrol ediyor olabilir. Makinenizin kabul edile güncelleştirme türlerini denetleme veya yapılandırma hakkında daha fazla bilgi için bkz. Yapılandırma Yöneticisi [güncelleştirmelerini dağıtmak için Visual Studio kullanma.](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio Enterprise kılavuzu](visual-studio-enterprise-guide.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
