---
title: Visual Studio’yu güncelleştirme
titleSuffix: ''
description: en son sürüme Visual Studio güncelleştirmeyi öğrenin ve adım adım.
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
ms.openlocfilehash: f5dfb3ec8ffd6bb05943c763611c167cfe2021d6
ms.sourcegitcommit: 022ac348337f77c899996ac81060a969ebfb64bb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2021
ms.locfileid: "128133972"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>en son sürüme Visual Studio güncelleştirme

::: moniker range="vs-2017"

en son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için Visual Studio 2017 ' in en [son sürümüne](/visualstudio/releasenotes/vs2017-relnotes/) güncelleştirmeniz önerilir.

en yeni sürümü denemek istiyorsanız, bunun yerine [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' ı indirip yüklemeyi göz önünde bulundurun.

> [!IMPORTANT]
> Visual Studio yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>güncelleştirme Visual Studio 2017 sürüm 15,6 veya üzeri

Doğrudan IDE içinden daha kolay kullanılmasını sağlamak için yükleme ve güncelleştirme deneyimini kolaylaştırdık. Sürüm 15,6 ve üzeri sürümden daha yeni Visual Studio sürümlerine nasıl güncelleştirme yapılacağı aşağıda verilmiştir.

### <a name="using-the-notifications-hub"></a>Bildirimler merkezini kullanma

Bir güncelleştirme olduğunda, Visual Studio buna karşılık gelen bir bildirim bayrağı vardır.

1. Çalışmanızı kaydedin.

1. **Bildirimler** merkezini açmak için bildirim bayrağını seçin ve ardından yüklemek istediğiniz güncelleştirmeyi seçin.

   ![Visual Studio ıde 'nin bildirim hub 'ında bir güncelleştirmeyi gösteren ekran görüntüsü.](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017'de Bildirimler hub'ı")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

    ![Visual Studio 2017 ' nin bildirimler hub 'ında başlatılan güncelleştirme iletişim kutusunda şimdi güncelleştir düğmesini gösteren ekran görüntüsü.](media/vs-update-now-from-notifications-hub.png "Visual Studio'daki Bildirimler hub'larından Güncelleştir iletişim Visual Studio")

     Kullanıcı Access Control iletişim kutusu açılırsa **Evet**' i seçin. sonra, bir "lütfen bekleyin" iletişim kutusu bir süre sonra açılabilir ve sonra Visual Studio Yükleyicisi açılarak güncelleştirmeyi başlatabilir.

     ![sürüm 15,6 ' de yeni Visual Studio Yükleyicisi deneyimini gösteren ekran görüntüsü.](media/visual-studio-15dot6-installer.png "Sürüm 15.6 Visual Studio Yükleyicisi yeni sürüm deneyimi")

     Güncelleştirmeniz devam ediyor. ardından, tamamlandığında Visual Studio yeniden başlatılır.

     > [!NOTE]
     > Visual Studio yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio el ile yeniden başlatmanız gerekir.

### <a name="using-the-ide"></a>IDE 'yi kullanma

Bir güncelleştirmeyi denetleyebilir ve ardından Visual Studio menü çubuğundan güncelleştirmeyi yükleyebilirsiniz.

1. Çalışmanızı kaydedin.

1.  > **Güncelleştirmeler için yardım denetle**' yi seçin.

     ![Visual Studio sürüm 15,6 ' deki yeni yardım menüsünü gösteren ekran görüntüsü.](media/vs-help-menu-check-for-updates.png "Sürüm 15.6 Visual Studio yeni Yardım menüsü")

1. **Güncelleştirme** iletişim kutusu açıldığında **Şimdi Güncelleştir**' i seçin.

   güncelleştirme, önceki bölümde açıklanan şekilde devam eder ve güncelleştirme başarıyla tamamlandıktan sonra yeniden başlatılır Visual Studio.

   > [!NOTE]
   > Visual Studio yönetici modunda çalıştırdığınızda, güncelleştirmeden sonra Visual Studio el ile yeniden başlatmanız gerekir.

### <a name="using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanma

Visual Studio önceki sürümlerinde olduğu gibi, bir güncelleştirmeyi yüklemek için Visual Studio Yükleyicisi kullanabilirsiniz.

1. Çalışmanızı kaydedin.

1. Yükleyiciyi açın. devam etmeden önce Visual Studio Yükleyicisi güncelleştirilmesi gerekebilir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio Yükleyicisi** olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi** olarak **d** harfi altında bulabilirsiniz.

1. yükleyicideki **ürün** sayfasında, daha önce yüklediğiniz Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi Visual Studio 2017 ' i güncelleştirmek için kullanılabilecek güncelleştirme düğmesini gösteren ekran görüntüsü.](media/update-visual-studio.png "Güncelleştirme Visual Studio 2017'de Visual Studio Yükleyicisi")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>güncelleştirme Visual Studio 2017 sürüm 15,5 veya öncesi

daha önceki bir sürümü kullanıyorsanız, Visual Studio 2017 sürüm 15,0 ' den sürüm 15,5 aracılığıyla güncelleştirme uygulama hakkında daha fazla bilgiyi burada bulabilirsiniz.

### <a name="update-by-using-the-notifications-hub"></a>Bildirimler hub 'ını kullanarak güncelleştirme

1. Güncelleştirmeler olduğunda, Visual Studio buna karşılık gelen bir bildirim bayrağı vardır.

   ![bir güncelleştirmenin kullanılabildiğini belirten Visual Studio 2017 ' de bir bildirim bayrağını gösteren ekran görüntüsü.](media/notification-flag.png "Visual Studio'da Bildirim bayrağını Visual Studio")

   **Bildirimler** merkezini açmak için bildirim bayrağını seçin.

   ![Visual Studio 2017 bildirim hub 'ını tek bir bildirimle gösteren ekran görüntüsü.](media/notifications-hub.png "Visual Studio hub'larında 2017 güncelleştirmesini güncelleştirme")

      > [!TIP]
      > Visual Studio 2017 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **uzantılar ve güncelleştirmeler** iletişim kutusunu açan **"Visual Studio güncelleştir"** i seçin.

   ![bildirim hub 'ında Visual Studio 2017 güncelleştirme bildirimi gösteren ekran görüntüsü.](media/notifications-hub-select.png "Güncelleştirme Visual Studio seçin")

1. **Uzantılar ve güncelleştirmeler** Iletişim kutusunda **Güncelleştir** düğmesini seçin.

   ![Uzantılar ve güncelleştirmeler iletişim penceresinde bir güncelleştirmeyi gösteren ekran görüntüsü.](media/notifications-extensions-and-updates.png "Visual Studio'daki Uzantılar ve Güncelleştirmeler iletişim Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio bildirimler hakkında daha fazla bilgi

Visual Studio, bir güncelleştirme Visual Studio kendisi için veya herhangi bir bileşen için kullanılabilir olduğunda ve ayrıca Visual Studio ortamında belirli olaylar gerçekleştiğinde size bildirir.

* bildirim bayrağı sarı olduğunda, yüklemek için kullanabileceğiniz bir Visual Studio ürün güncelleştirmesi vardır.
* Bildirim bayrağı kırmızı olduğunda, lisansınızın bir sorunu vardır.
* Bildirim bayrağı siyah olduğunda, gözden geçirmek için isteğe bağlı veya bilgilendirici iletiler vardır.

**Bildirimler merkezini** açmak için bildirimler bayrağını seçin ve ardından üzerinde işlem yapmak istediğiniz bildirimleri seçin. Veya bir bildirimi yoksaymayı veya kapatmak için seçin.

 ![Bildirim Hub 'ında isteğe bağlı veya bilgilendirici bir iletiyi gösteren ekran görüntüsü.](media/notification-flag-optional.png "Aşağıdaki isteğe bağlı veya bilgilendirme iletisi Bildirim Visual Studio")

bir bildirimi yok saymayı seçerseniz Visual Studio bunu göstermeyi durduruyor. yoksayılan bildirimlerin listesini sıfırlamak isterseniz, bildirimler hub 'ında **Ayarlar** düğmesini seçin.

   ![bildirim seçeneklerini görüntülemek için bildirim hub 'ında Ayarlar düğmesini gösteren ekran görüntüsü.](media/vs-notifications-hub-settings-button.png "Bildirim Ayarlar görüntülemek için Bildirimler hub'ı'nın Üst Bilgi düğmesini seçin")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanarak güncelleştirin

1. Yükleyiciyi açın. Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Böyle bir durum söz konusu olduğunda bunu yapmanız istenir.

   > [!NOTE]
   > Windows 10 çalıştıran bir bilgisayarda, yükleyiciyi **Visual Studio Yükleyicisi** olarak **V** harfi altında veya **Microsoft Visual Studio yükleyicisi** olarak **d** harfi altında bulabilirsiniz.

1. yükleyicideki **ürün** sayfasında, daha önce yüklenen Visual Studio sürümünü arayın.

1. Bir güncelleştirme varsa, bir **güncelleştirme** düğmesi görürsünüz. (Yükleyicinin bir güncelleştirmenin kullanılabilir olup olmadığını belirlemesi birkaç saniye sürebilir.)

   Güncelleştirmeleri yüklemek için **Güncelleştir** düğmesini seçin.

     ![Visual Studio 2017 güncelleştirmesi için Visual Studio Yükleyicisi güncelleştirme düğmesini gösteren ekran görüntüsü.](media/update-visual-studio.png "Visual Studio kullanarak güncelleştirme Visual Studio Yükleyicisi")

::: moniker-end

::: moniker range="vs-2019"

en son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için en [son Visual Studio sürümüne](/visualstudio/releases/2019/release-notes/) güncelleştirmeniz önerilir.

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın. şu anda farklı bir Visual Studio sürümünü kullanıyorsanız, [Visual Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)veya [önceki Visual Studio sürümlerini kaldırabilirsiniz](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Visual Studio yüklemek, güncelleştirmek veya değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

Visual Studio 2019 ' i güncelleştirme &nbsp; &nbsp; .

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

   Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.

   ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. yükleyicide, yüklediğiniz Visual Studio sürümünü arayın.

   örneğin, daha önce Visual &nbsp; Studio Community 2019 ' i yüklediyseniz &nbsp; ve bu güncelleştirme için bir güncelleştirme varsa, yükleyicide bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![kullanılabilir bir güncelleştirmeyle Visual Studio 2019 yüklemesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2019 sürümünü seçin")

1. Güncelleştirmeleri yüklemek için **Güncelleştir** ' i seçin.

    ![Visual Studio 2019 yüklemesine güncelleştirmek için kullanılabilecek Visual Studio yükleyicisindeki güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeleri yüklemek için Güncelleştir düğmesini seçin")

1. Güncelleştirme tamamlandıktan sonra bilgisayarınızı yeniden başlatmanız istenebilir. bu durumda, bunu yapın ve genellikle Visual Studio başlatın.

   bilgisayarınızı yeniden başlatmanız istenmezse, yükleyiciden Visual Studio başlatmak için **başlat** ' ı seçin.

    ![Visual Studio yükleyicisinde, Visual Studio 2019 ' i başlatmak için kullanılabilecek başlatma düğmesini gösteren ekran görüntüsü.](media/vs-2019/choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-ide"></a>IDE 'yi kullanma

bir güncelleştirmeyi denetleyebilir ve ardından menü çubuğunu veya Visual Studio 2019 ' deki arama kutusunu kullanarak yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **başlat** menüsünde **Visual Studio 2019**' i seçin.

    ![Visual Studio ıde başlangıç penceresinin sonuçlarını gösteren ekran görüntüsü Visual Studio 2019 için arama yapın.](media/vs-2019/vs-installer-visual-studio-2019.png "Visual Studio 2019'da Windows")

1. **Kullanmaya** başlayın ' ın altında, IDE 'yi açmak için herhangi bir seçeneği belirleyin.

    ![Visual Studio Yükleyicisi gösteren ekran görüntüsü.](media/vs2019-choose-option-from-get-started.png "Visual Studio Yükleyicisi")

    Visual Studio açılır. ıde 'de **Visual Studio 2019 güncelleştirme** iletisi kısaca görüntülenir.

    ![ıde 'deki ' Visual Studio 2019 güncelleştirme ' iletisini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2019 güncelleştirmesi' iletisi")

1. **Visual Studio 2019 güncelleştirme** iletisinde, **ayrıntıları görüntüle**' yi seçin.

   ![Visual Studio 2019 ıde güncelleştirme iletisindeki ayrıntıları görüntüle düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin")

1. **Güncelleştirme indirildi ve yüklemeye hazırlanıyor** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Güncelleştirme indirildi ve yüklemeye hazırlanıyor ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'İndirilen ve yüklenmeye hazır' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım**' ı seçin ve ardından **Güncelleştirmeleri denetle**' yi seçin.

     ![Yardım menüsündeki ' güncelleştirmeleri denetle 'yi gösteren ekran görüntüsü.](media/vs-2019/vs-ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

    > [!NOTE]
    > Ayrıca, güncelleştirmeleri denetlemek için IDE 'deki arama kutusunu da kullanabilirsiniz. **CTRL** + **Q** tuşlarına basın, "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2019/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. Visual Studio, çalışmanızı kaydedin.

1. **bildirimler** merkezini açmak için Visual Studio ıde 'nin sağ alt köşesinden bildirim simgesini seçin.

   ![Visual Studio ıde 'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **Ayrıntıları görüntüle**' yi seçin.

     ![Visual Studio 2019 ' de bildirim hub 'ını gösteren ekran görüntüsü.](media/vs-2019/notification-hub-update.png "Visual Studio 2019'daki Bildirim hub'ı")

      > [!TIP]
      > Visual Studio 2019 sürümüne yönelik bir güncelleştirme birikimlidir, bu nedenle her zaman en son sürüm numarasıyla yüklemeyi seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Visual Studio güncelleştirme ayarlarını, yükleme modunu değiştirerek ve otomatik indirmeleri seçerek gibi çeşitli yollarla özelleştirebilirsiniz.

Aralarından seçim yapabileceğiniz iki yükleme modu vardır:

* **İndirme sırasında yükleme**
* **Tümünü İndir, sonra Yükle**

Ayrıca, makineniz boşta kaldığında güncelleştirmelerin indirilmesine izin veren **güncelleştirme ayarlarını otomatik olarak indir** seçeneğini de belirleyebilirsiniz.

Aşağıdaki adımları uygulayın:

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Ortam**' ı genişletin ve **ürün güncelleştirmeleri**' ni seçin.

    ![Visual Studio 'daki güncelleştirme ayarlarını gösteren ekran görüntüsü.](media/vs-2019/update-settings-options.png)

1. Visual Studio güncelleştirmelerinizde, yükleme modunu ve istediğiniz otomatik indirme seçeneklerini seçin.

::: moniker-end

::: moniker range=">=vs-2022"

en son özellikleri, düzeltmeleri ve geliştirmeleri her zaman alabilmeniz için en [son Visual Studio sürümüne](/visualstudio/releases/2022/release-notes-preview) güncelleştirmeniz önerilir.

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın. şu anda farklı bir Visual Studio sürümünü kullanıyorsanız, [Visual Studio sürümlerini yan yana yükleyebilir](../install/install-visual-studio-versions-side-by-side.md)veya [önceki Visual Studio sürümlerini kaldırabilirsiniz](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Visual Studio yüklemek, değiştirmek veya güncelleştirmek için Visual Studio Yükleyicisi yönetici olarak çalıştırmanız gerekir. Visual Studio tipik bir kullanıcı olarak değiştirmeye çalışırsanız, yönetici kimlik bilgileri isteyip istemediğinizi soran bir kullanıcı hesabı denetimi bildirimi alırsınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Update Mac için Visual Studio](/visualstudio/mac/update).

Visual Studio 2022 ' i güncelleştirme.

## <a name="use-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanın

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

   Windows Başlat menüsü, "yükleyici" araması yapın ve sonra sonuçlardan **Visual Studio Yükleyicisi** ' yı seçin.

   ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2022/vs-installer.png "Arama Visual Studio Yükleyicisi")

   > [!NOTE]
   > aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenirse, istemleri izleyerek bunu yapın.

1. Visual Studio Yükleyicisi, güncelleştirmek istediğiniz Visual Studio yüklemeyi bulun. 

   örneğin, daha önce 2022 önizleme Visual Studio Community yüklediyseniz ve bu güncelleştirme için bir güncelleştirme varsa, Visual Studio Yükleyicisi bir **güncelleştirme kullanılabilir** iletisi görüntülenir.

     ![yeni bir güncelleştirme kullanılabilir olduğunda Visual Studio Yükleyicisi güncelleştirme düğmesini ve iletiyi gösteren ekran görüntüsü.](media/vs-2022/vs-installer-update-visual-studio-community.png "Güncelleştirmek istediğiniz Visual Studio 2022 sürümünü seçin")

1. Güncelleştirmeyi yüklemek için **Güncelleştir** ' i seçin.

    ![Yeni güncelleştirmeyi yüklemek için seçebileceğiniz güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-update-visual-studio-community.png "Güncelleştirmeyi yüklemek için Güncelleştir düğmesini seçin")

1. güncelleştirme tamamlandıktan sonra Visual Studio Yükleyicisi bilgisayarınızı yeniden başlatmanızı isteyebilir. bu durumda, bunu yapın ve genellikle Visual Studio başlatın.

    bilgisayarınızı yeniden başlatmanız istenmezse, Visual Studio Yükleyicisi Visual Studio başlatmak için **başlat** ' ı seçin.

    ![Visual Studio başlatmayı seçebileceğiniz başlatma düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-launch-visual-studio-community.png "Başlat düğmesini seçerek başlatmayı Visual Studio")

## <a name="use-the-visual-studio-ide"></a>Visual Studio ıde 'yi kullanma

bir güncelleştirmeyi denetleyebilir ve ardından menü çubuğunu veya Visual Studio 2022 ' deki arama kutusunu kullanarak yükleyebilirsiniz.

### <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Windows **başlat** menüsünde **Visual Studio 2022 önizleme**' yi seçin.

    ![Windows 10 Başlat menüsü Visual Studio 2022 önizleme girişinin gösterildiği ekran görüntüsü.](media/vs-2022/ide-start-menu.png "Windows'den Visual Studio 2022 Preview'Windows")

1. başlangıç penceresinde **başlarken** ' in altında, Visual Studio ıde 'yi açmak için herhangi bir seçenek belirleyin.

    ![Visual Studio ıde 'de başlangıç penceresini gösteren ekran görüntüsü.](media/vs-2022/choose-option-from-get-started.png "IDE'Visual Studio açın")

    Visual Studio açılır. Visual Studio ıde 'de, **Visual Studio 2022 güncelleştirme** iletisi kısaca görüntülenir.

    ![Visual Studio ıde 'nin sağ alt köşesinde Visual Studio 2022 için bir güncelleştirme iletisi gösteren ekran görüntüsü.](media/vs-2022/update-visual-studio-ide-message.png "IDE'de 'Visual Studio 2022 güncelleştirmesi' iletisi")

1. Visual Studio 2022 güncelleştirme iletisinde, **ayrıntıları görüntüle**' yi seçin.

   ![Visual Studio ıde 'de Visual Studio 2022 güncelleştirme bildirimi için ayrıntıları görüntüle düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-visual-studio-ide-view-details.png "Visual Studio 2022 güncelleştirme iletisinde Ayrıntıları Görüntüle düğmesini seçin")

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![Visual Studio 2022 ' deki ' kullanılabilir ' güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-ready-install-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

### <a name="in-visual-studio"></a>Visual Studio’da

1. Menü çubuğundan **Yardım**' ı seçin ve ardından **Güncelleştirmeleri denetle**' yi seçin.

     ![Yardım menüsündeki ' güncelleştirmeleri denetle ' seçeneğini gösteren ekran görüntüsü.](media/vs-2022/ide-check-updates-help-menu.png "Yardım menüsünden 'Güncelleştirmeleri Denetleme'yi seçin")

    > [!NOTE]
    > güncelleştirmeleri denetlemek için Visual Studio ıde 'deki arama kutusunu da kullanabilirsiniz. **CTRL** + **Q** tuşlarına basın, "güncelleştirmeleri denetle" yazın ve ardından eşleşen arama sonucunu seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

     ![' Kullanılabilir güncelleştirme ' iletişim kutusunda güncelleştirme düğmesini gösteren ekran görüntüsü.](media/vs-2022/update-visual-studio-community-from-ide.png "'Kullanılabilir güncelleştir' iletişim kutusunda Güncelleştir düğmesini seçin")

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

## <a name="use-the-notifications-hub"></a>Bildirimler hub 'ını kullanma

1. Visual Studio, çalışmanızı kaydedin.

1. **bildirimler** merkezini açmak için Visual Studio ıde 'nin sağ alt köşesinden bildirim simgesini seçin.

   ![Visual Studio ıde 'de bildirim simgesini gösteren ekran görüntüsü.](media/vs-2022/notification-bar.png "Visual Studio 2022'de bildirim simgesi")

1. **Bildirimler hub 'ında**, yüklemek istediğiniz güncelleştirmeyi seçin ve ardından **Ayrıntıları görüntüle**' yi seçin.

     ![Visual Studio ıde 'de bildirimler hub 'ını gösteren ekran görüntüsü.](media/vs-2022/notification-hub-update.png "Visual Studio 2022'de Bildirimler hub'ı")

      > [!TIP]
      > Visual Studio 2022 ' nin her sürümü için güncelleştirmeler birikimlidir, bu nedenle güncelleştirmeyi en son sürüm numarasıyla yüklemeyi her zaman seçin.

1. **Kullanılabilir güncelleştirme** Iletişim kutusunda **Güncelleştir**' i seçin.

   Visual Studio güncelleştirmeler, kapanır ve sonra yeniden açılır.

## <a name="customize-update-settings"></a>Güncelleştirme ayarlarını özelleştirme

Yükleme modunu değiştirerek veya otomatik Visual Studio seçerek güncelleştirme ayarlarını Visual Studio farklı şekillerde özelleştirebilirsiniz.

İki yükleme modu vardır:

* **İndirme sırasında yükleme**
* **Hepsini indirin, sonra yükleyin**

Ayrıca, makineniz **boştayken güncelleştirmeleri** indirmenize olanak Visual Studio güncelleştirmeleri otomatik olarak indir seçeneğini de belirleyin.

Aşağıdaki adımları uygulayın:

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. **Ortam'ı** genişletin ve ardından Ürün **Güncelleştirmeleri'ne tıklayın.**

    ![IDE'nin Seçenekler penceresindeki Güncelleştirmeler ayarlarını Visual Studio görüntüsü.](media/vs-2022/update-settings-options.png)

1. Uygulama güncelleştirmeleri için istediğiniz yükleme modunu ve otomatik indirme Visual Studio seçin.

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
