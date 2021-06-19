---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: Visual Studio 'Yu en son sürüme güncelleştirme, adım adım yönergeler hakkında bilgi edinin.
ms.date: 04/06/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: 8414d745b63eb0e9145208dca97ce9f117c5cf2c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387963"
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

   ![Bildirim Hub 'ını kullanarak Visual Studio 2017 'yi güncelleştirme](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017'de Bildirimler hub'ı")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

    ![Bildirimler hub 'ından güncelleştirme iletişim kutusunu kullanarak Visual Studio 2017 'yi güncelleştirme](media/vs-update-now-from-notifications-hub.png "Visual Studio'daki Bildirimler hub'larından Güncelleştir iletişim Visual Studio")

     Kullanıcı Access Control iletişim kutusu açılırsa **Evet**' i seçin. Sonra, bir "lütfen bekleyin" iletişim kutusu bir süre sonra açılabilir ve sonra Visual Studio Yükleyicisi açılarak güncelleştirmeyi başlatabilir.

     ![Sürüm 15,6 ' de yeni Visual Studio Yükleyicisi deneyimi](media/visual-studio-15dot6-installer.png "Sürüm 15.6 Visual Studio Yükleyicisi yeni sürüm deneyimi")

     Güncelleştirmeniz devam ediyor. Ardından, tamamlandığında Visual Studio yeniden başlatılır.

     > [!NOTE]
     > Visual Studio 'Yu yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio 'Yu el ile yeniden başlatmanız gerekir.

### <a name="using-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve sonra Visual Studio 'daki menü çubuğundan güncelleştirmeyi yükleyebilirsiniz.

1. Çalışmanızı kaydedin.

1.  > **Güncelleştirmeler için yardım denetle**' yi seçin.

     ![Visual Studio sürüm 15,6 ' deki yeni Yardım menüsü](media/vs-help-menu-check-for-updates.png "Sürüm 15.6 Visual Studio yeni Yardım menüsü")

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

     ![Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin](media/update-visual-studio.png "Visual Studio 2017 güncelleştirmesini Visual Studio Yükleyicisi")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Visual Studio 2017 sürüm 15,5 veya öncesini güncelleştirme

Önceki bir sürümü kullanıyorsanız, Visual Studio 2017 sürüm 15,0 ' den sürüm 15,5 aracılığıyla bir güncelleştirme uygulama hakkında daha fazla bilgiyi burada bulabilirsiniz.

### <a name="update-by-using-the-notifications-hub"></a>Bildirimler hub 'ını kullanarak güncelleştirme

1. Güncelleştirmeler olduğunda, Visual Studio 'da karşılık gelen bir bildirim bayrağı vardır.

   ![Visual Studio 2017 bildirim bayrağını Güncelleştir](media/notification-flag.png "Visual Studio'de Bildirim güncelleştirme bayrağı")

   **Bildirimler** merkezini açmak için bildirim bayrağını seçin.

   ![Bildirim Hub 'ında Visual Studio 2017 güncelleştirmesi](media/notifications-hub.png "Visual Studio hub'larında 2017 güncelleştirmesini güncelleştirme")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Uzantılar ve güncelleştirmeler** iletişim kutusunu açan **"Visual Studio Update"** i seçin.

   ![Visual Studio güncelleştirmesini seçin](media/notifications-hub-select.png "Güncelleştirme Visual Studio seçin")

1. **Uzantılar ve güncelleştirmeler** Iletişim kutusunda **Güncelleştir** düğmesini seçin.

   ![Uzantılar ve güncelleştirmeler iletişim kutusunda Güncelleştir ' i seçin](media/notifications-extensions-and-updates.png "Visual Studio'daki Uzantılar ve Güncelleştirmeler iletişim Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio bildirimleri hakkında daha fazla bilgi

Visual Studio, Visual Studio 'nun kendisi için veya herhangi bir bileşen için kullanılabilir olduğunda ve ayrıca Visual Studio ortamında belirli olaylar gerçekleştiğinde size bildirir.

* Bildirim bayrağı sarı olduğunda, yüklemek için kullanabileceğiniz bir Visual Studio ürün güncelleştirmesi vardır.
* Bildirim bayrağı kırmızı olduğunda, lisansınızın bir sorunu vardır.
* Bildirim bayrağı siyah olduğunda, gözden geçirmek için isteğe bağlı veya bilgilendirici iletiler vardır.

**Bildirimler merkezini** açmak için bildirimler bayrağını seçin ve ardından üzerinde işlem yapmak istediğiniz bildirimleri seçin. Veya bir bildirimi yoksaymayı veya kapatmak için seçin.

 ![Bildirim Hub 'ında isteğe bağlı veya bilgilendirici bir ileti görüntüleme](media/notification-flag-optional.png "Visual Studio'daki isteğe bağlı veya bilgilendirme iletisi Bildirim bayrağı")

Bir bildirimi yok saymayı seçerseniz, Visual Studio bunu göstermeyi durduruyor. Yoksayılan bildirimlerin listesini sıfırlamak isterseniz, bildirimler hub 'ında **Ayarlar** düğmesini seçin.

   ![Bildirim seçeneklerini görüntülemek için bildirimler hub 'ında ayarlar düğmesini seçin](media/vs-notifications-hub-settings-button.png "Bildirim seçeneklerini görüntülemek için Bildirimler hub'larında Ayarlar düğmesini seçin")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanarak güncelleştirin

1. Yükleyiciyi açın. Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Böyle bir durum söz konusu olduğunda bunu yapmanız istenir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio yükleyicisi** olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi** olarak **d** harfi altında bulabilirsiniz.

1. Yükleyicideki **ürün** sayfasında, daha önce yüklenen Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin](media/update-visual-studio.png "Visual Studio kullanarak güncelleştirme Visual Studio Yükleyicisi")

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

   ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın.

   Örneğin, daha önce Visual &nbsp; Studio Community 2019 ' i yüklediyseniz &nbsp; ve bu güncelleştirme için bir güncelleştirme varsa, yükleyicide bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir** ' i seçin.

    ![Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. Varsa, bunu yapın ve ardından Visual Studio 'Yu genellikle yaptığınız gibi başlatın.

   Bilgisayarınızı yeniden başlatmanız istenmezse, yükleyiciden Visual Studio 'yu başlatmak için **Başlat** ' ı seçin.

    ![Visual Studio 'Yu başlatmak için Başlat düğmesini seçin](media/vs-2019/choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve ardından menü çubuğunu veya Visual Studio 2019 arama kutusunu kullanarak yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **Başlat** menüsünde **Visual Studio 2019**' ı seçin.

    ![Visual Studio 2019 'yi açın](media/vs-2019/vs-installer-visual-studio-2019.png "Windows'Visual Studio 2019'u açın")

1. **Kullanmaya** başlayın ' ın altında, IDE 'yi açmak için herhangi bir seçeneği belirleyin.

    ![Visual Studio Yükleyicisi açın](media/vs2019-choose-option-from-get-started.png "Dosyayı Visual Studio Yükleyicisi")

    Visual Studio açılır. IDE 'de bir **Visual Studio 2019 güncelleştirme** iletisi görüntülenir.

    ![IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi")

1. **Visual Studio 2019 güncelleştirme** Iletisinde **Ayrıntıları görüntüle**' yi seçin.

   ![Visual Studio 2019 IDE güncelleştirme iletisinde ayrıntıları görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin")

1. **Güncelleştirme indirildi ve yüklemeye hazırlanıyor** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım**' ı seçin ve ardından **Güncelleştirmeleri denetle**' yi seçin.

     ![Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

    > [!NOTE]
    > Ayrıca, güncelleştirmeleri denetlemek için IDE 'deki arama kutusunu da kullanabilirsiniz. **CTRL** + **Q** tuşlarına basın, "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. Visual Studio 'da çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak Için VISUAL Studio IDE 'nin sağ alt köşesindeki bildirim simgesini seçin.

   ![Visual Studio IDE 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **Ayrıntıları görüntüle**' yi seçin.

     ![Visual Studio 2019 ' de Bildirim Hub 'ı](media/vs-2019/notification-hub-update.png "Visual Studio 2019'da Bildirim hub'ı")

      > [!TIP]
      > Visual Studio 2019 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

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

::: moniker range=">=vs-2022"

En son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için Visual Studio 'nun en [son sürümüne](/visualstudio/releases/2022/release-notes/) güncelleştirmeniz önerilir.

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın. Şu anda farklı bir Visual Studio sürümü kullanıyorsanız, Visual [Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)ya da [Visual Studio 'nun önceki sürümlerini kaldırabilirsiniz](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Visual Studio 'Yu yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

Visual Studio 2022 ' i güncelleştirme &nbsp; &nbsp; .

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

   Windows Başlat menüsünde, "yükleyici" için arama yapabilirsiniz.

   ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın.

   Örneğin, daha önce Visual &nbsp; Studio Community 2022 ' i yüklediyseniz &nbsp; ve bu güncelleştirme için bir güncelleştirme varsa, yükleyicide bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir** ' i seçin.

    ![Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. Varsa, bunu yapın ve ardından Visual Studio 'Yu genellikle yaptığınız gibi başlatın.

   Bilgisayarınızı yeniden başlatmanız istenmezse, yükleyiciden Visual Studio 'yu başlatmak için **Başlat** ' ı seçin.

    ![Visual Studio 'Yu başlatmak için Başlat düğmesini seçin](media/vs-2019/choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve ardından menü çubuğunu veya Visual Studio 2022 arama kutusunu kullanarak yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **Başlat** menüsünde **Visual Studio 2022**' ı seçin.

    ![Visual Studio 2022 'yi açın](media/vs-2019/vs-installer-visual-studio-2019.png "Windows'Visual Studio 2019'u açın")

1. **Kullanmaya** başlayın ' ın altında, IDE 'yi açmak için herhangi bir seçeneği belirleyin.

    ![Visual Studio Yükleyicisi açın](media/vs2019-choose-option-from-get-started.png "Dosyayı Visual Studio Yükleyicisi")

    Visual Studio açılır. IDE 'de bir **Visual Studio 2022 güncelleştirme** iletisi görüntülenir.

    ![IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi")

1. **Visual Studio 2022 güncelleştirme** Iletisinde **Ayrıntıları görüntüle**' yi seçin.

   ![Visual Studio 2019 IDE güncelleştirme iletisinde ayrıntıları görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin")

1. **Güncelleştirme indirildi ve yüklemeye hazırlanıyor** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım**' ı seçin ve ardından **Güncelleştirmeleri denetle**' yi seçin.

     ![Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

    > [!NOTE]
    > Ayrıca, güncelleştirmeleri denetlemek için IDE 'deki arama kutusunu da kullanabilirsiniz. **CTRL** + **Q** tuşlarına basın, "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. Visual Studio 'da çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak Için VISUAL Studio IDE 'nin sağ alt köşesindeki bildirim simgesini seçin.

   ![Visual Studio IDE 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **Ayrıntıları görüntüle**' yi seçin.

     ![Visual Studio 2019 ' de Bildirim Hub 'ı](media/vs-2019/notification-hub-update.png "Visual Studio 2019'da Bildirim hub'ı")

      > [!TIP]
      > Visual Studio 2022 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

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

## <a name="administrator-updates"></a>Yönetici güncelleştirmeleri

Yazılım yüklemelerinin yönetimini merkezi hale alan bir kuruluşun parçasıysanız, kuruluş yöneticiniz makinenize güncelleştirme Visual Studio neden olabilir. Makinenizin hangi tür güncelleştirmeleri kabul edilesini denetleme veya yapılandırma hakkında daha fazla bilgi için bkz. [Yapılandırma Yöneticisi'yi Visual Studio.](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio Enterprise kılavuzu](visual-studio-enterprise-guide.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
