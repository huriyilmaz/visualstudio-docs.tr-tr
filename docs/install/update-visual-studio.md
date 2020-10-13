---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: Visual Studio 'Yu en son sürüme güncelleştirme, adım adım yönergeler hakkında bilgi edinin.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
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
ms.openlocfilehash: 01bc8fe18ff32d5da3f56eb39465b3fc696239b4
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007178"
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

1. **Help** > **Güncelleştirmeler için yardım denetle**' yi seçin.

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
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio yükleyicisi**olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi**olarak **d** harfi altında bulabilirsiniz.

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
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio yükleyicisi**olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi**olarak **d** harfi altında bulabilirsiniz.

1. Yükleyicideki **ürün** sayfasında, daha önce yüklenen Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi kullanarak Visual Studio 2017 ' i güncelleştirin](media/update-visual-studio.png "Visual Studio Yükleyicisi kullanarak Visual Studio 'Yu güncelleştirme")

::: moniker-end

::: moniker range="vs-2019"

En son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2019 ' in en [son sürümüne](/visualstudio/releases/2019/release-notes/) güncelleştirmeniz önerilir.

Visual Studio 2019 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın. Şu anda farklı bir Visual Studio sürümü kullanıyorsanız, Visual [Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)ya da [Visual Studio 'nun önceki sürümlerini kaldırabilirsiniz](../install/uninstall-visual-studio.md).

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

    ![Visual Studio 'Yu başlatmak için Başlat düğmesini seçin](media/vs-2019/choose-launch-visual-studio-community.png "Visual Studio 'Yu başlatmak için Başlat düğmesini seçin")

## <a name="use-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve ardından menü çubuğunu veya Visual Studio 2019 arama kutusunu kullanarak yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **Başlat** menüsünde **Visual Studio 2019**' ı seçin.

    ![Visual Studio 2019 'yi açın](media/vs-2019/vs-installer-visual-studio-2019.png "Windows 'dan Visual Studio 2019 'yi açın")

1. **Kullanmaya**başlayın ' ın altında, IDE 'yi açmak için herhangi bir seçeneği belirleyin.

    ![Visual Studio Yükleyicisi açın](media/vs2019-choose-option-from-get-started.png "Visual Studio Yükleyicisi açın")

    Visual Studio açılır. IDE 'de bir **Visual Studio 2019 güncelleştirme** iletisi görüntülenir.

    ![IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi](media/vs-2019/update-visual-studio-ide-message.png "IDE 'deki ' Visual Studio 2019 Güncelleştirmesi ' iletisi")

1. **Visual Studio 2019 güncelleştirme** Iletisinde **Ayrıntıları görüntüle**' yi seçin.

   ![Visual Studio 2019 IDE güncelleştirme iletisinde ayrıntıları görüntüle düğmesini seçin](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisindeki ayrıntıları görüntüle düğmesini seçin")

1. **Güncelleştirme indirildi ve yüklemeye hazırlanıyor** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "' Güncelleştirme indirilmiş ve yüklenmeye hazırlanıyor ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım**' ı seçin ve ardından **Güncelleştirmeleri denetle**' yi seçin.

     ![Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden ' güncelleştirmeleri denetle 'yi seçin")

    > [!NOTE]
    > Ayrıca, güncelleştirmeleri denetlemek için IDE 'deki arama kutusunu da kullanabilirsiniz. **CTRL** + **Q**tuşlarına basın, "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin](media/vs-2019/update-visual-studio-community-from-ide.png "' Kullanılabilir güncelleştirme ' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeleri, kapanır ve sonra yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. Visual Studio 'da çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak Için VISUAL Studio IDE 'nin sağ alt köşesindeki bildirim simgesini seçin.

   ![Visual Studio IDE 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE 'deki bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **Ayrıntıları görüntüle**' yi seçin.

     ![Visual Studio 2019 ' de Bildirim Hub 'ı](media/vs-2019/notification-hub-update.png "Visual Studio 2019 ' de Bildirim Hub 'ı")

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürümlerini yan yana yükleme](install-visual-studio-versions-side-by-side.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
