---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: Visual Studio'yu en son sürümde adım adım nasıl güncelleştirteceklerini öğrenin.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19da163c76724ae56c0e3d83f1ed795333d081d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77453401"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Visual Studio'yu en son sürümle güncelleştirin

::: moniker range="vs-2017"

Visual Studio 2017'nin en [son sürümüne](/visualstudio/releasenotes/vs2017-relnotes/) güncellemenizi öneririz, böylece her zaman en son özellikleri, düzeltmeleri ve iyileştirmeleri elde elabilirsiniz.

En yeni sürümüdenemek isterseniz Visual [Studio 2019'u](https://visualstudio.microsoft.com/downloads) indirmeyi ve yüklemeyi düşünün.

> [!IMPORTANT]
> Visual Studio'yı yüklemek, güncelleştirmek veya değiştirmek için yönetim izinleri olan bir hesapla oturum açmanız gerekir. Daha fazla bilgi için [Kullanıcı İzinleri ve Visual Studio'ya](../ide/user-permissions-and-visual-studio.md)bakın.
>
> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'yı güncelleştir'e](/visualstudio/mac/update)bakın.

## <a name="update-visual-studio-2017-version-156-or-later"></a>Visual Studio 2017 sürümünü 15.6 veya sonrası güncelle

Doğrudan IDE içinden kullanımı kolaylaştırmak için yükleme ve güncelleme deneyimini kolaylaştırdık. Sürüm 15.6'dan visual studio'nun daha yeni sürümlerine nasıl güncellenir?

### <a name="using-the-notifications-hub"></a>Bildirimler merkezini kullanma

Bir güncelleştirme olduğunda, Visual Studio'da karşılık gelen bir bildirim bayrağı vardır.

1. Çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak için bildirim bayrağını seçin ve sonra yüklemek istediğiniz güncelleştirmeyi seçin.

   ![Bildirim merkezini kullanarak Visual Studio 2017'yi güncelleştirin](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017'de Bildirimler merkezi")

      > [!TIP]
      > Visual Studio 2017 sürümü için bir güncelleştirme kümülatiftir, bu nedenle her zaman en son sürüm numarasına sahip sürümü yüklemeyi seçin.

1. **Güncelleştir** iletişim kutusu açıldığında, **Şimdi Güncelleştir'i**seçin.

    ![Bildirimler hub'ından Güncelle iletişim kutusunu kullanarak Visual Studio 2017'yi güncelleştirin](media/vs-update-now-from-notifications-hub.png "Visual Studio'daki Bildirimler hub'ından Güncelleştirme iletişim kutusu")

     Kullanıcı Erişim Denetimi iletişim kutusu açılırsa **Evet'i**seçin. Ardından, bir an için "Lütfen bekleyin" iletişim kutusu açılır ve güncelleştirmeyi başlatmak için Visual Studio Installer açılır.

     ![Sürüm 15.6 yeni Visual Studio Installer deneyimi](media/visual-studio-15dot6-installer.png "Sürüm 15.6 yeni Visual Studio Installer deneyimi")

     Güncelleştirmeniz devam ediyor. Sonra, tamamlandığında, Visual Studio yeniden başlatılır.

     > [!NOTE]
     > Visual Studio'yu yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio'yu el ile yeniden başlatmanız gerekir.

### <a name="using-the-ide"></a>IDE'yi kullanma

Güncelleştirmeyi denetleyebilir ve ardından Visual Studio'daki menü çubuğundan güncelleştirmeyi yükleyebilirsiniz.

1. Çalışmanızı kaydedin.

1. **Güncelleştirmeler için** **Yardım** > Denetimi'ni seçin.

     ![Visual Studio sürüm 15.6'daki yeni Yardım menüsü](media/vs-help-menu-check-for-updates.png "Visual Studio sürüm 15.6'daki yeni Yardım menüsü")

1. **Güncelleştir** iletişim kutusu açıldığında, **Şimdi Güncelleştir'i**seçin.

   Güncelleştirme önceki bölümde açıklandığı gibi devam eder ve güncelleştirme başarıyla tamamlandıktan sonra Visual Studio yeniden başlatılır.

   > [!NOTE]
   > Visual Studio'yu yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio'yu el ile yeniden başlatmanız gerekir.

### <a name="using-the-visual-studio-installer"></a>Visual Studio Yükleyicisini Kullanma

Visual Studio'nun önceki sürümlerinde olduğu gibi, bir güncelleştirme yüklemek için Visual Studio Installer'ı kullanabilirsiniz.

1. Çalışmanızı kaydedin.

1. Yükleyiciyi açın. Visual Studio Yükleyici devam etmeden önce güncelleştirme gerekebilir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, Yükleyici'yi **Visual Studio Installer**olarak **V** harfinin altında veya Microsoft Visual Studio **Installer**olarak **M** harfinin altında bulabilirsiniz.

1. Yükleyicideki **Ürün** sayfasında, daha önce yüklediğiniz Visual Studio sürümünü arayın.

1. Güncelleştirme varsa, **bir Güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Installer'ı kullanarak Visual Studio 2017'yi güncelleyin](media/update-visual-studio.png "Visual Studio Installer'ı kullanarak Visual Studio 2017'yi güncelleyin")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Visual Studio 2017 sürümünü 15.5 veya daha önce güncelleştirin

Daha önceki bir sürümü kullanıyorsanız, Visual Studio 2017 sürüm 15.0 sürümünden sürüm 15.5'e nasıl bir güncelleştirme uygulayabilirsiniz.

### <a name="update-by-using-the-notifications-hub"></a>Bildirimler merkezini kullanarak güncelleştirme

1. Güncelleştirmeler olduğunda, Visual Studio'da karşılık gelen bir bildirim bayrağı vardır.

   ![Bildirim merkezini kullanarak Visual Studio 2017'yi güncelleştirin](media/notification-flag.png "Visual Studio'da güncelleştirme Bildirimi bayrağı")

   **Bildirimler** merkezini açmak için bildirim bayrağını seçin.

   ![Bildirim merkezini kullanarak Visual Studio 2017'yi güncelleştirin](media/notifications-hub.png "Visual Studio'da Bildirimler merkezi")

      > [!TIP]
      > Visual Studio 2017 sürümü için bir güncelleştirme kümülatiftir, bu nedenle her zaman en son sürüm numarasına sahip sürümü yüklemeyi seçin.

1. **Uzantıları ve Güncelleştirmeleri** iletişim kutusunu açan **"Visual Studio Update" seçeneğini**belirleyin.

   ![Bildirimler merkezini kullanarak Visual Studio 2017'yi güncelleştirin](media/notifications-hub-select.png "Visual Studio'da Bildirimler merkezi")

1. **Uzantılar ve Güncelleştirmeler** iletişim kutusunda **Güncelleştir** düğmesini seçin.

   ![Bildirimler merkezini kullanarak Visual Studio 2017'yi güncelleştirin](media/notifications-extensions-and-updates.png "Visual Studio'daki Uzantılar ve Güncellemeler iletişim kutusu")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio bildirimleri hakkında daha fazla şey

Visual Studio, Visual Studio'nun kendisi veya herhangi bir bileşen için bir güncelleştirme olduğunda ve ayrıca Visual Studio ortamında belirli olayların meydana geldiğini size haber verirken sizi iyi bilir.

* Bildirim bayrağı sarı olduğunda, yüklemeniz gereken bir Visual Studio ürün güncelleştirmesi vardır.
* Bildirim bayrağı kırmızı olduğunda, lisansınızda bir sorun vardır.
* Bildirim bayrağı siyah olduğunda, gözden geçirilmesi gereken isteğe bağlı veya bilgilendirilen iletiler vardır.

**Bildirimler** merkezini açmak için bildirimler bayrağını seçin ve ardından harekete geçebilmek istediğiniz bildirimleri seçin. Veya bir bildirimi yoksaymayı veya reddetmeyi seçin.

 ![Bildirim hub'ında isteğe bağlı veya bilgilendirici bir iletiyi görüntüleme](media/notification-flag-optional.png "Visual Studio'da isteğe bağlı veya bilgilendirici mesaj Bildirimi bayrağı")

Bir bildirimi yoksaymayı seçerseniz, Visual Studio bildirimi göstermeyi durdurur. Yoksayılan bildirimler listesini sıfırlamak istiyorsanız, Bildirimler hub'ındaki **Ayarlar** düğmesini seçin.

   ![Bildirim seçeneklerini görüntülemek için Bildirimler bmerkezindeki Ayarlar düğmesini seçin](media/vs-notifications-hub-settings-button.png "Bildirim seçeneklerini görüntülemek için Bildirimler bmerkezindeki Ayarlar düğmesini seçin")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio Installer'ı kullanarak güncelleştirin

1. Yükleyiciyi açın. Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, bunu yapmanız istenir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, Yükleyici'yi **Visual Studio Installer**olarak **V** harfinin altında veya Microsoft Visual Studio **Installer**olarak **M** harfinin altında bulabilirsiniz.

1. Yükleyicideki **Ürün** sayfasında, daha önce yüklenen Visual Studio sürümünü arayın.

1. Güncelleştirme varsa, **bir Güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Installer'ı kullanarak Visual Studio 2017'yi güncelleyin](media/update-visual-studio.png "Visual Studio Installer'ı kullanarak Visual Studio'yu güncelleştirin")

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019'un en [son sürümüne](/visualstudio/releases/2019/release-notes/) güncellemenizi öneririz, böylece her zaman en son özellikleri, düzeltmeleri ve iyileştirmeleri elde elabilirsiniz.

Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin. Şu anda Visual Studio'nun farklı bir sürümünü kullanıyorsanız, [Visual Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)veya [Visual Studio'nun önceki sürümlerini kaldırabilirsiniz.](../install/uninstall-visual-studio.md)

> [!IMPORTANT]
> Visual Studio'yı yüklemek, güncelleştirmek veya değiştirmek için yönetim izinleri olan bir hesapla oturum açmanız gerekir. Daha fazla bilgi için [Kullanıcı İzinleri ve Visual Studio'ya](../ide/user-permissions-and-visual-studio.md)bakın.
>
> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'yı güncelleştir'e](/visualstudio/mac/update)bakın.

Visual&nbsp;Studio&nbsp;2019'u şu şekilde güncelleyebilirim.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisini Kullanma

1. Yükleyiciyi açın.

     ![Windows'tan Visual Studio Yükleyicisini Açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisini Açın")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın.

   Örneğin, Visual&nbsp;Studio Community&nbsp;2019'u daha önce yüklediyseniz ve bunun için bir güncelleştirme varsa, yükleyicide bir Güncelleştirme **kullanılabilir** iletisi görüntülenir.

     ![Güncellemek istediğiniz Visual Studio 2019 sürümünü seçin](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncellemek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir'i** seçin.

    ![Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. Eğer öyleyse, bunu yapın ve sonra genellikle olduğu gibi Visual Studio başlatın.

   Bilgisayarınızı yeniden başlatmanız istenmiyorsa, Yükleyiciden Visual Studio'yu başlatmak için **Başlat'ı** seçin.

    ![Visual Studio'yu başlatmak için Başlat düğmesini seçin](media/vs-2019/choose-launch-visual-studio-community.png "Visual Studio'yu başlatmak için Başlat düğmesini seçin")

## <a name="use-the-ide"></a>IDE'yi kullanma

Visual Studio 2019'daki menü çubuğunu veya arama kutusunu kullanarak bir güncelleştirmeyi denetleyebilir ve sonra yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **Başlat** menüsünden **Visual Studio 2019'u**seçin.

    ![Açık Görsel Stüdyo 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Windows'dan Görsel Stüdyo 2019'u Aç")

1. **Başlat'ın**altında, IDE'yi açmak için herhangi bir seçenek seçin.

    ![Visual Studio Yükleyicisini Açın](media/vs2019-choose-option-from-get-started.png "Visual Studio Yükleyicisini Açın")

    Visual Studio açılır. IDE'de Visual **Studio 2019 güncelleştirme** iletisi görüntülenir.

    ![IDE'de 'Visual Studio 2019 güncellemesi' mesajı](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncellemesi' mesajı")

1. Visual **Studio 2019 güncelleştirme** iletisinde **ayrıntıları görüntüle'yi**seçin.

   ![Visual Studio 2019 IDE güncelleme iletisinde Ayrıntıları Görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleme iletisinde Ayrıntıları Görüntüle düğmesini seçin")

1. **İndirilen ve yüklenmeye hazır Güncelleştirme** iletişim kutusunda **Güncelleştir'i**seçin.

     !['İndirilen ve yüklemeye hazır' iletişim kutusundaki Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklemeye hazır' iletişim kutusundaki Güncelleştir düğmesini seçin")

   Visual Studio günceller, kapanır ve yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım'ı**seçin ve ardından **Güncelleştirmeleri Denetle'yi**seçin.

     ![Yardım menüsünden 'Güncelleştirmeleri Denetle' seçeneğini belirleyin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetle' seçeneğini belirleyin")

    > [!NOTE]
    > Güncelleştirmeleri denetlemek için IDE'deki arama kutusunu da kullanabilirsiniz. **Ctrl**+**Q**tuşuna basın , "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. Kullanılabilir **güncelleştirme** iletişim kutusunda **Güncelleştir'i**seçin.

     !['İndirilen ve yüklemeye hazır' iletişim kutusundaki Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "'İndirilen ve yüklemeye hazır' iletişim kutusundaki Güncelleştir düğmesini seçin")

   Visual Studio günceller, kapanır ve yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler merkezini kullanma

1. Visual Studio'da, çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak için Visual Studio IDE'nin sağ alt köşesinden bildirim simgesini seçin.

   ![Visual Studio IDE'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE'deki bildirim simgesi")

1. **Bildirimler**hub'ında, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **ayrıntıları görüntüle'yi**seçin.

     ![Visual Studio 2019'da Bildirim merkezi](media/vs-2019/notification-hub-update.png "Visual Studio 2019'da Bildirim merkezi")

      > [!TIP]
      > Visual Studio 2019 sürümü için bir güncelleştirme kümülatiftir, bu nedenle her zaman en son sürüm numarasına sahip sürümü yüklemeyi seçin.

1. Kullanılabilir **güncelleştirme** iletişim kutusunda **Güncelleştir'i**seçin.

   Visual Studio günceller, kapanır ve yeniden açılır.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Visual Studio'daki güncelleştirme ayarlarını yükleme modunu değiştirerek ve otomatik indirmeleri seçerek birkaç farklı şekilde özelleştirebilirsiniz.

Aralarından seçim yapabileceğiniz iki yükleme modu vardır:

* **İndirirken yükleme**
* **Tümlerini indirin, sonra yükleyin**

Makineniz boştayken güncelleştirmelerin karşıdan yüklemesine olanak tanıyan **Otomatik olarak indirgüncelleştirmeleri** ayarını da seçebilirsiniz.

Bunu yapmak için:

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Ortamı**Genişletin ve ardından **Ürün Güncelleştirmeleri'ni**seçin.

    ![Visual Studio'da ayarları güncelleştirir](media/vs-2019/update-settings-options.png)

3. Visual Studio güncellemeleriniz için yükleme modunu ve istediğiniz otomatik indirme seçeneklerini seçin.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
