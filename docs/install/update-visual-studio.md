---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: Visual Studio 'Yu en son sürüme güncelleştirme, adım adım yönergeler hakkında bilgi edinin.
ms.date: 04/06/2021
ms.custom: acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b541568da45c9bd8dda7258534193371e7e9f04b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306845"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Visual Studio 'Yu en son sürüme güncelleştirme

::: moniker range="vs-2017"

En son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2017 ' in en [son sürümüne](/visualstudio/releasenotes/vs2017-relnotes/) güncelleştirmeniz önerilir.

En yeni sürümü denemek istiyorsanız bunun yerine [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' i indirip yüklemeyi göz önünde bulundurun.

> [!IMPORTANT]
> Visual Studio 'Yu yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Visual Studio 2017 sürüm 15,6 veya üstünü Güncelleştir

Doğrudan IDE içinden daha kolay kullanılmasını sağlamak için yükleme ve güncelleştirme deneyimini kolaylaştırdık. Sürüm 15,6 ve sonrasında Visual Studio 'nun yeni sürümlerine nasıl güncelleştirme yapılacağı aşağıda verilmiştir.

### <a name="using-the-notifications-hub"></a>Bildirimler merkezini kullanma

Bir güncelleştirme olduğunda, Visual Studio 'da karşılık gelen bir bildirim bayrağı vardır.

1. Çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak için bildirim bayrağını seçin ve ardından yüklemek istediğiniz güncelleştirmeyi seçin.

   ![Bildirim Hub 'ını kullanarak Visual Studio 2017 'yi güncelleştirme](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017 ' de bildirimler hub 'ı")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

    ![Bildirimler hub 'ından güncelleştirme iletişim kutusunu kullanarak Visual Studio 2017 'yi güncelleştirme](media/vs-update-now-from-notifications-hub.png "Visual Studio 'da bildirimler hub 'ından güncelleştirme iletişim kutusu")

     Kullanıcı Access Control iletişim kutusu açılırsa **Evet**' i seçin. Sonra, bir "lütfen bekleyin" iletişim kutusu bir süre sonra açılabilir ve sonra Visual Studio Yükleyicisi açılarak güncelleştirmeyi başlatabilir.

     ![Sürüm 15,6 ' de yeni Visual Studio Yükleyicisi deneyimi](media/visual-studio-15dot6-installer.png "Sürüm 15,6 ' de yeni Visual Studio Yükleyicisi deneyimi")

     Güncelleştirmeniz devam ediyor. Ardından, tamamlandığında Visual Studio yeniden başlatılır.

     > [!NOTE]
     > Visual Studio 'Yu yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio 'Yu el ile yeniden başlatmanız gerekir.

### <a name="using-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve sonra Visual Studio 'daki menü çubuğundan güncelleştirmeyi yükleyebilirsiniz.

1. Çalışmanızı kaydedin.

1.  > **Güncelleştirmeler için yardım denetle**' yi seçin.

     ![Visual Studio sürüm 15,6 ' deki yeni Yardım menüsü](media/vs-help-menu-check-for-updates.png "Visual Studio sürüm 15,6 ' deki yeni Yardım menüsü")

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

   Güncelleştirme, önceki bölümde açıklanan şekilde devam eder ve güncelleştirme başarıyla tamamlandıktan sonra Visual Studio yeniden başlatılır.

   > [!NOTE]
   > Visual Studio 'Yu yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio 'Yu el ile yeniden başlatmanız gerekir.

### <a name="using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanma

Visual Studio 'nun önceki sürümlerinde olduğu gibi, bir güncelleştirmeyi yüklemek için Visual Studio Yükleyicisi kullanabilirsiniz.

1. Çalışmanızı kaydedin.

1. Yükleyiciyi açın. Devam etmeden önce Visual Studio Yükleyicisi güncelleştirilmesi gerekebilir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio yükleyicisi** olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi** olarak **d** harfi altında bulabilirsiniz.

1. Yükleyicideki **ürün** sayfasında, daha önce yüklediğiniz Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin](media/update-visual-studio.png "Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Visual Studio 2017 sürüm 15,5 veya öncesini güncelleştirme

Önceki bir sürümü kullanıyorsanız, Visual Studio 2017 sürüm 15,0 ' den sürüm 15,5 aracılığıyla bir güncelleştirme uygulama hakkında daha fazla bilgiyi burada bulabilirsiniz.

### <a name="update-by-using-the-notifications-hub"></a>Bildirimler hub 'ını kullanarak güncelleştirme

1. Güncelleştirmeler olduğunda, Visual Studio 'da karşılık gelen bir bildirim bayrağı vardır.

   ![Visual Studio 2017 bildirim bayrağını Güncelleştir](media/notification-flag.png "Visual Studio 'da güncelleştirme bildirimi bayrağı")

   **Bildirimler** merkezini açmak için bildirim bayrağını seçin.

   ![Bildirim Hub 'ında Visual Studio 2017 güncelleştirmesi](media/notifications-hub.png "Bildirim Hub 'ında Visual Studio 2017 güncelleştirmesi")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Uzantılar ve güncelleştirmeler** iletişim kutusunu açan **"Visual Studio Update"** i seçin.

   ![Visual Studio güncelleştirmesini seçin](media/notifications-hub-select.png "Visual Studio güncelleştirmesini seçin")

1. **Uzantılar ve güncelleştirmeler** Iletişim kutusunda **Güncelleştir** düğmesini seçin.

   ![Uzantılar ve güncelleştirmeler iletişim kutusunda Güncelleştir ' i seçin](media/notifications-extensions-and-updates.png "Visual Studio 'da Uzantılar ve güncelleştirmeler iletişim kutusu")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio bildirimleri hakkında daha fazla bilgi

Visual Studio, Visual Studio 'nun kendisi için veya herhangi bir bileşen için kullanılabilir olduğunda ve ayrıca Visual Studio ortamında belirli olaylar gerçekleştiğinde size bildirir.

* Bildirim bayrağı sarı olduğunda, yüklemek için kullanabileceğiniz bir Visual Studio ürün güncelleştirmesi vardır.
* Bildirim bayrağı kırmızı olduğunda, lisansınızın bir sorunu vardır.
* Bildirim bayrağı siyah olduğunda, gözden geçirmek için isteğe bağlı veya bilgilendirici iletiler vardır.

**Bildirimler merkezini** açmak için bildirimler bayrağını seçin ve ardından üzerinde işlem yapmak istediğiniz bildirimleri seçin. Veya bir bildirimi yoksaymayı veya kapatmak için seçin.

 ![Bildirim Hub 'ında isteğe bağlı veya bilgilendirici bir ileti görüntüleme](media/notification-flag-optional.png "Visual Studio 'da isteğe bağlı veya bilgilendirici ileti bildirim bayrağı")

Bir bildirimi yok saymayı seçerseniz, Visual Studio bunu göstermeyi durduruyor. Yoksayılan bildirimlerin listesini sıfırlamak isterseniz, bildirimler hub 'ında **Ayarlar** düğmesini seçin.

   ![Bildirim seçeneklerini görüntülemek için bildirimler hub 'ında ayarlar düğmesini seçin](media/vs-notifications-hub-settings-button.png "Bildirim seçeneklerini görüntülemek için bildirimler hub 'ında ayarlar düğmesini seçin")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanarak güncelleştirin

1. Yükleyiciyi açın. Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Böyle bir durum söz konusu olduğunda bunu yapmanız istenir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio yükleyicisi** olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi** olarak **d** harfi altında bulabilirsiniz.

1. Yükleyicideki **ürün** sayfasında, daha önce yüklenen Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin](media/update-visual-studio.png "Visual Studio Yükleyicisi kullanarak Visual Studio 'Yu güncelleştirme")

::: moniker-end

::: moniker range="vs-2019"

En son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için Visual Studio 'nun en [son sürümüne](/visualstudio/releases/2019/release-notes/) güncelleştirmeniz önerilir.

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın. Şu anda farklı bir Visual Studio sürümü kullanıyorsanız, Visual [Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)ya da [Visual Studio 'nun önceki sürümlerini kaldırabilirsiniz](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Visual Studio 'Yu yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

Visual Studio 2019 ' i güncelleştirme &nbsp; &nbsp; .

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

   Windows Başlat menüsünde, "yükleyici" için arama yapabilirsiniz.

   ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın.

   Örneğin, daha önce Visual &nbsp; Studio Community 2019 ' i yüklediyseniz &nbsp; ve bu güncelleştirme için bir güncelleştirme varsa, yükleyicide bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir** ' i seçin.

    ![Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. Varsa, bunu yapın ve ardından Visual Studio 'Yu genellikle yaptığınız gibi başlatın.

   Bilgisayarınızı yeniden başlatmanız istenmezse, yükleyiciden Visual Studio 'yu başlatmak için **Başlat** ' ı seçin.

    ![Başlat düğmesini seçerek başlatmayı Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Visual Studio 'Yu başlatmak için Başlat düğmesini seçin")

## <a name="use-the-ide"></a>IDE kullanma

2019'da menü çubuğunu veya arama kutusunu kullanarak bir güncelleştirmeyi Visual Studio yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows Başlat **menüsünden** **2019'Visual Studio seçin.**

    ![Open Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Windows 'dan Visual Studio 2019 'yi açın")

1. Bu **Kullanmaya başlayın** IDE'yi açmak için herhangi bir seçeneği belirleyin.

    ![Dosyayı Visual Studio Yükleyicisi](media/vs2019-choose-option-from-get-started.png "Visual Studio Yükleyicisi açın")

    Visual Studio açılır. IDE'de, **Visual Studio 2019 güncelleştirme** iletisi görüntülenir.

    ![IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi](media/vs-2019/update-visual-studio-ide-message.png "IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi")

1. **2019 Visual Studio iletisinde** Ayrıntıları **görüntüle'yi seçin.**

   ![Visual Studio 2019 IDE güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisindeki ayrıntıları görüntüle düğmesini seçin")

1. İndirilen **ve yüklenmeye hazır olan güncelleştirme iletişim** kutusunda Güncelleştir'i **seçin.**

     !['İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio, kapanır ve yeniden açar.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan Yardım'ı **ve ardından** Güncelleştirmeleri Kontrol **Et'i seçin.**

     ![Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin")

    > [!NOTE]
    > Güncelleştirmeleri kontrol etmek için IDE'de arama kutusunu da kullanabilirsiniz. **Ctrl** + **Q tuşlarına** basın, "güncelleştirmeleri denetleme" yazın ve ardından eşleşen arama sonuçlarını seçin.

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio, kapanır ve yeniden açar.

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Bu Visual Studio çalışmanızı kaydedin.

1. IDE'nin sağ alt köşesindeki bildirim simgesini Visual Studio **Hub'ı açın.**

   ![Visual Studio IDE'de bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE 'deki bildirim simgesi")

1. Bildirimler **hub'sinde** yüklemek istediğiniz güncelleştirmeyi seçin ve ardından Ayrıntıları **görüntüle'yi seçin.**

     ![Visual Studio 2019'da Bildirim hub'ı](media/vs-2019/notification-hub-update.png "Visual Studio 2019 ' de Bildirim Hub 'ı")

      > [!TIP]
      > Visual Studio 2019 sürümünün güncelleştirmesi birikmelidir, bu nedenle her zaman en son sürüm numarasına sahip sürümü yükleyin.

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

   Visual Studio, kapanır ve yeniden açar.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Güncelleştirme ayarlarını, yükleme modunu Visual Studio ve otomatik indirmeleri seçerek gibi birkaç farklı şekilde özelleştirebilirsiniz.

İki yükleme modu vardır:

* **İndirme sırasında yükleme**
* **Hepsini indirin, sonra yükleyin**

Ayrıca, makineniz **boştayken güncelleştirmelerin** indirileye izin veren Güncelleştirmeleri otomatik olarak indir ayarını da seçebilirsiniz.

Aşağıdaki adımları uygulayın:

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

2. **Ortam'ı** genişletin ve ardından Ürün **Güncelleştirmeleri'ne tıklayın.**

    ![Visual Studio'de ayarları Visual Studio](media/vs-2019/update-settings-options.png)

3. Güncelleştirmeleri yüklemek için istediğiniz yükleme modunu ve otomatik indirme Visual Studio seçin.

::: moniker-end

::: moniker range=">=vs-2022"

Her zaman en son [özelliklere,](/visualstudio/releases/2022/release-notes/) düzeltmelere ve geliştirmelere sahip olmak için Visual Studio en son sürümüne güncelleştirmeniz teşvik edilecektir.

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin. Şu anda farklı bir Visual Studio sürümünü kullanıyorsanız, Visual Studio [](../install/install-visual-studio-versions-side-by-side.md)sürümlerini yan yana yükleyebilir veya önceki sürümlerini [Visual Studio.](../install/uninstall-visual-studio.md)

> [!IMPORTANT]
> Bu hesabı yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapta oturum Visual Studio. Daha fazla bilgi için bkz. [Kullanıcı İzinleri ve Visual Studio.](../ide/user-permissions-and-visual-studio.md)
>
> [!NOTE]
> Bu konu Windows'Visual Studio için geçerlidir. Daha Mac için Visual Studio için [bkz. Güncelleştirme Mac için Visual Studio.](/visualstudio/mac/update)

Visual &nbsp; Studio &nbsp; 2022'nin nasıl güncelleştiril burasıdır.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

   Windows Başlat menüsü", "yükleyici" için arama da kullanabilirsiniz.

   ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklemiş Visual Studio sürümünü ara.

   Örneğin, daha önce Visual &nbsp; Studio Community &nbsp; 2022 yüklemiş  ve bunun için bir güncelleştirme varsa yükleyicide Kullanılabilir güncelleştirme iletisi görüntülenir.

     ![Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri **yüklemek** için Güncelleştir'i seçin.

    ![Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilirsiniz. Öyleyse, bunu yap ve ardından normal Visual Studio gibi yeni bir başlangıç yap.

   Bilgisayarınızı yeniden başlatmanız istenecekse Başlat'ı **seçen** Visual Studio başlat'ı seçin.

    ![Başlat düğmesini seçerek başlatmayı Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Visual Studio 'Yu başlatmak için Başlat düğmesini seçin")

## <a name="use-the-ide"></a>IDE kullanma

2022'de menü çubuğunu veya arama kutusunu kullanarak bir güncelleştirmeyi Visual Studio yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows Başlat **menüsünden** **2022'Visual Studio seçin.**

    ![Open Visual Studio 2022](media/vs-2019/vs-installer-visual-studio-2019.png "Windows 'dan Visual Studio 2019 'yi açın")

1. Bu **Kullanmaya başlayın** IDE'yi açmak için herhangi bir seçeneği belirleyin.

    ![Dosyayı Visual Studio Yükleyicisi](media/vs2019-choose-option-from-get-started.png "Visual Studio Yükleyicisi açın")

    Visual Studio açılır. IDE'de, **Visual Studio 2022 güncelleştirme iletisi** görüntülenir.

    ![IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi](media/vs-2019/update-visual-studio-ide-message.png "IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi")

1. **2022 Visual Studio iletisinde** Ayrıntıları **görüntüle'yi seçin.**

   ![Visual Studio 2019 IDE güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisindeki ayrıntıları görüntüle düğmesini seçin")

1. İndirilen **ve yüklenmeye hazır olan güncelleştirme iletişim** kutusunda Güncelleştir'i **seçin.**

     !['İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio, kapanır ve yeniden açar.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan Yardım'ı **ve ardından** Güncelleştirmeleri Kontrol **Et'i seçin.**

     ![Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin")

    > [!NOTE]
    > Güncelleştirmeleri kontrol etmek için IDE'de arama kutusunu da kullanabilirsiniz. **Ctrl** + **Q tuşlarına** basın, "güncelleştirmeleri denetleme" yazın ve ardından eşleşen arama sonuçlarını seçin.

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

     !['Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio, kapanır ve yeniden açar.

## <a name="use-the-notifications-hub"></a>Bildirimler hub'larını kullanma

1. Bu Visual Studio çalışmanızı kaydedin.

1. IDE'nin sağ alt köşesindeki bildirim simgesini Visual Studio **Hub'ı açın.**

   ![Visual Studio IDE'de bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE 'deki bildirim simgesi")

1. Bildirimler **hub'sinde** yüklemek istediğiniz güncelleştirmeyi seçin ve ardından Ayrıntıları **görüntüle'yi seçin.**

     ![Visual Studio 2019'da Bildirim hub'ı](media/vs-2019/notification-hub-update.png "Visual Studio 2019 ' de Bildirim Hub 'ı")

      > [!TIP]
      > Visual Studio 2022 sürümünün güncelleştirmesi birikmelidir, bu nedenle her zaman en son sürüm numarasına sahip sürümü yükleyin.

1. Kullanılabilir güncelleştir **iletişim kutusunda** Güncelleştir'i **seçin.**

   Visual Studio, kapanır ve yeniden açar.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Visual Studio 'daki güncelleştirme ayarlarını, yükleme modunu değiştirerek ve otomatik indirmeleri seçerek gibi çeşitli yollarla özelleştirebilirsiniz.

Aralarından seçim yapabileceğiniz iki yükleme modu vardır:

* **İndirme sırasında yükleme**
* **Tümünü İndir, sonra Yükle**

Ayrıca, makineniz boşta kaldığında güncelleştirmelerin indirilmesine izin veren **güncelleştirme ayarlarını otomatik olarak indir** seçeneğini de belirleyebilirsiniz.

Aşağıdaki adımları uygulayın:

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve **ürün güncelleştirmeleri**' ni seçin.

    ![Visual Studio 'da güncelleştirme ayarları](media/vs-2019/update-settings-options.png)

3. Visual Studio güncelleştirmelerinizde yükleme modunu ve otomatik indirme seçeneklerini belirleyin.
::: moniker-end

## <a name="administrator-updates"></a>Yönetici güncelleştirmeleri

Yazılım yüklemelerinin yönetimini merkezileştiren bir kuruluşun parçasıysa kuruluş yöneticiniz, Visual Studio 'Nun makinenizde güncelleştirilmesine neden olabilir. Makinenizin kabul edebileceği güncelleştirme türlerini denetleme veya yapılandırma hakkında daha fazla bilgi için bkz. [Using Configuration Manager, Visual Studio güncelleştirmelerini dağıtmak için](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio Enterprise kılavuzu](visual-studio-enterprise-guide.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
