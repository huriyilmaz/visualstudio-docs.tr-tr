---
title: Visual Studio yükleme
titleSuffix: ''
description: Visual Studio'u adım adım nasıl yükleyin öğrenin.
ms.date: 12/13/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d8e6e3a857c9bbf5577cf395f698f64cfb11bddc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302996"
---
# <a name="install-visual-studio"></a>Visual Studio yükleme

::: moniker range="vs-2019"

Visual Studio 2019'a Hoş Geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçmek ve yüklemek kolaydır. Ve azaltılmış minimum ayak izi nedeniyle, hızlı ve daha az sistem etkisi ile yükler.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio yüklemek için yeni bir yol hoş geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçmenizi ve yüklemenizi kolaylaştırdık. Ayrıca Visual Studio'nun minimum ayak izini azalttık, böylece daha hızlı ve daha az sistem etkisiyle yüklenir.

::: moniker-end

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio Yükle'ye](/visualstudio/mac/installation/)bakın.

::: moniker range="vs-2019"

Bu sürümde yeni ne hakkında daha fazla şey öğrenmek ister misiniz? Sürüm [notlarımıza](/visualstudio/releases/2019/release-notes/)bakın.

::: moniker-end

::: moniker range="vs-2017"

Bu sürümde yeni ne hakkında daha fazla şey öğrenmek ister misiniz? Sürüm [notlarımıza](/visualstudio/releasenotes/vs2017-relnotes)bakın.

::: moniker-end

Yüklemeye hazır mısınız? Adım adım sana yol bulacağız.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Adım 1 - Bilgisayarınızın Visual Studio için hazır olduğundan emin olun

Visual Studio'u yüklemeye başlamadan önce:

::: moniker range="vs-2017"

1. Sistem [gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs)kontrol edin. Bu gereksinimler, bilgisayarınızın Visual Studio 2017'yi destekleyip desteklemediğini anlamanıza yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızın Visual Studio için hem en son güvenlik güncelleştirmeleri hem de gerekli sistem bileşenlerine sahip olmasını sağlar.

1. Yeni -den başlatma. Yeniden başlatma, bekleyen yüklemelerin veya güncelleştirmelerin Visual Studio yüklemesini engellememesini sağlar.

1. Yer aç. Disk Temizleme uygulamasını çalıştırarak gereksiz dosyaları ve uygulamaları %SystemDrive%'inizden kaldırın.

::: moniker-end

::: moniker range="vs-2019"

1. Sistem [gereksinimlerini](/visualstudio/releases/2019/system-requirements)kontrol edin. Bu gereksinimler, bilgisayarınızın Visual Studio 2019'u destekleyip desteklemediğini anlamanıza yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızın Visual Studio için hem en son güvenlik güncelleştirmeleri hem de gerekli sistem bileşenlerine sahip olmasını sağlar.

1. Yeni -den başlatma. Yeniden başlatma, bekleyen yüklemelerin veya güncelleştirmelerin Visual Studio yüklemesini engellememesini sağlar.

1. Yer aç. Disk Temizleme uygulamasını çalıştırarak gereksiz dosyaları ve uygulamaları %SystemDrive%'inizden kaldırın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 ile Visual Studio'nun önceki sürümlerini yan yana çalıştırmakla ilgili sorularınız için [Visual Studio uyumluluk ayrıntılarına](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)bakın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 ile Visual Studio'nun önceki sürümlerini yan yana çalıştırmakla ilgili sorularınız için [Visual Studio 2019 Platform Hedefleme ve Uyumluluk](/visualstudio/releases/2019/compatibility/) sayfasına bakın.

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Adım 2 - Visual Studio İndir

Sonra, Visual Studio bootstrapper dosyasını indirin.

::: moniker range="vs-2017"

Visual Studio 2017 için bir bootstrapper almak için, nasıl yapılacağını hakkında ayrıntılı bilgi için [Visual Studio önceki sürümleri](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Bunu yapmak için aşağıdaki düğmeyi seçin, Istediğiniz Visual Studio sürümünü seçin, **Kaydet'i**seçin ve ardından **Klasörü Aç'ı**seçin.

 > [!div class="button"]
 > [Visual Studio’yu İndir](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Adım 3 - Visual Studio yükleyicisini yükleyin

Visual Studio Installer'ı yüklemek için bootstrapper dosyasını çalıştırın. Bu yeni hafif yükleyici, Visual Studio'yı yüklemek ve özelleştirmek için ihtiyacınız olan her şeyi içerir.

1. **İndirilenler** klasörünüzden, aşağıdaki dosyalarla eşleşen veya benzer olan bootstrapper'ı çift tıklatın:

   * Visual Studio Community için **vs_community.exe**
   * Visual Studio Professional için **vs_professional.exe**
   * Visual Studio Enterprise için **vs_enterprise.exe**

   Bir Kullanıcı Hesabı Denetimi bildirimi **alırsanız, Evet'i**seçin.

2. Microsoft [Lisans Koşullarını](https://visualstudio.microsoft.com/license-terms/) ve Microsoft [Gizlilik Bildirimi'ni](https://privacy.microsoft.com/privacystatement)kabul etmenizi isteriz. **Devam**'ı seçin.

   ![Lisans Koşulları ve Gizlilik Bildirimi](media/privacy-and-license-terms.png "Microsoft Lisans Koşulları ve Gizlilik Bildirimi")

## <a name="step-4---choose-workloads"></a>Adım 4 - İş yüklerini seçin

Yükleyici yüklendikten sonra, istediğiniz özellik kümelerini veya iş yüklerini seçerek yüklemenizi özelleştirmek için kullanabilirsiniz. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. **Visual Studio Yükleyici'de**istediğiniz iş yükünü bulun.

   ![Visual Studio 2017: İş yükü yükleyin](../install/media/vs-installer-installing-workloads.png)

     Örneğin, ".NET masaüstü geliştirme" iş yükünü seçin. 20'den fazla dil için temel kod düzenleme desteği, proje gerektirmeden herhangi bir klasörden kod açma ve düzenleme olanağı ve tümleşik kaynak kodu denetimi içeren varsayılan çekirdek düzenleyicisi ile birlikte gelir.

1. İstediğiniz iş yükünü(ler) seçtikten sonra **Yükle'yi**seçin.

    Ardından, Visual Studio yüklemenizin ilerlemesini gösteren durum ekranları görüntülenir.

 ::: moniker-end

::: moniker range="vs-2019"

1. **Visual Studio Yükleyici'de**istediğiniz iş yükünü bulun.

   ![Visual Studio 2019: İş yükü yükleyin](../install/media/vs-2019/vs-installer-workloads.png)

     Örneğin, "ASP.NET ve web geliştirme" iş yükünü seçin. 20'den fazla dil için temel kod düzenleme desteği, proje gerektirmeden herhangi bir klasörden kod açma ve düzenleme olanağı ve tümleşik kaynak kodu denetimi içeren varsayılan çekirdek düzenleyicisi ile birlikte gelir.

1. İstediğiniz iş yükünü(ler) seçtikten sonra **Yükle'yi**seçin.

    Ardından, Visual Studio yüklemenizin ilerlemesini gösteren durum ekranları görüntülenir.

 ::: moniker-end

> [!TIP]
> Yüklemeden sonra istediğiniz zaman, başlangıçta yüklemediğiniz iş yüklerini veya bileşenleri yükleyebilirsiniz. Visual Studio açıksa, **Araçlar** > **Al Araçları ve Özellikleri...** Veya Başlat menüsünden **Visual Studio Installer'ı** açın. Buradan, yüklemek istediğiniz iş yüklerini veya bileşenleri seçebilirsiniz. Ardından **Değiştir'i**seçin.

## <a name="step-5---choose-individual-components-optional"></a>Adım 5 - Tek tek bileşenleri seçin (İsteğe bağlı)

Visual Studio yüklemenizi özelleştirmek için İş Yükleri özelliğini kullanmak istemiyorsanız veya iş yükü yüklemelerinden daha fazla bileşen eklemek istiyorsanız, bunu **Tek tek bileşenler** sekmesinden tek tek bileşenleri yükleyerek veya ekleyerek yapabilirsiniz.

::: moniker range="vs-2017"

  ![Visual Studio 2017 - Tek tek bileşenleri yükleyin](media/vs-installer-installing-components.png "Visual Studio'ya tek tek bileşenleri yükleyin")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 - Tek tek bileşenleri yükleyin](media/vs-2019/vs-installer-individual-components.png "Visual Studio'ya tek tek bileşenleri yükleyin")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Adım 6 - Dil paketlerini yükleyin (İsteğe bağlı)

Varsayılan olarak, yükleyici programı ilk kez çalıştığında işletim sisteminin dilini eşleştirmeye çalışır. Visual Studio'yu seçtiğiniz bir dilde yüklemek için Visual Studio Installer'dan **Dil paketleri** sekmesini seçin ve ardından istemleri izleyin.

::: moniker range="vs-2017"

  ![Visual Studio 2017 - Dil paketlerini yükleyin](media/vs-installer-installing-language-packs.png "Visual Studio dil paketlerini yükleyin")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 - Dil paketlerini yükleyin](media/vs-2019/vs-installer-language-packs.png "Visual Studio dil paketlerini yükleyin")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Yükleyici dilini komut satırından değiştirme

Varsayılan dili değiştirmenin başka bir yolu da yükleyiciyi komut satırından çalıştırmaktır. Örneğin, aşağıdaki komutu kullanarak yükleyiciyi İngilizce olarak çalıştırmaya zorlayabilirsiniz: `vs_installer.exe --locale en-US`. Yükleyici, bir sonraki çalıştırıldığında bu ayarı hatırlar. Yükleyici aşağıdaki dil belirteçlerini destekler: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru ve tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Adım 7 - Yükleme konumunu seçin (İsteğe bağlı)

::: moniker range="vs-2017"

**15.7'de Yeni**: Artık Visual Studio'nun sistem sürücünüzdeki kurulum ayak izini azaltabilirsiniz. İndirme önbelleğini, paylaşılan bileşenleri, SDK'ları ve araçları farklı sürücülere taşımayı seçebilir ve Visual Studio'yu en hızlı çalıştıran sürücüde tutabilirsiniz.

  ![Visual Studio 2017 - Kurulum yerlerini değiştir](media/installation-options-by-location.png "Yükleme konumunu değiştirme")

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'nun sistem sürücünüzdeki kurulum ayak izini azaltabilirsiniz. İndirme önbelleğini, paylaşılan bileşenleri, SDK'ları ve araçları farklı sürücülere taşımayı seçebilir ve Visual Studio'yu en hızlı çalıştıran sürücüde tutabilirsiniz.

  ![Visual Studio 2019 - Yükleme konumlarını seçin](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin")

::: moniker-end

> [!IMPORTANT]
> Farklı bir sürücüyü yalnızca Visual Studio'yı ilk yüklediğinizde seçebilirsiniz. Zaten yüklediyseniz ve sürücüleri değiştirmek istiyorsanız, Visual Studio'yı kaldırmanız ve sonra yeniden yüklemeniz gerekir.

Daha fazla bilgi için [yükleme konumlarını seç](change-installation-locations.md) sayfasına bakın.

## <a name="step-8---start-developing"></a>Adım 8 - Geliştirmeye başlayın

::: moniker range="vs-2017"

1. Visual Studio yüklemesi tamamlandıktan sonra Visual Studio ile geliştirmeye başlamak için **Başlat** düğmesini seçin.

2. **Dosya'yı**seçin ve ardından **Yeni Proje'yi**seçin.

3. Proje türünü seçin.

   Örneğin, [bir C++ uygulaması oluşturmak](/cpp/get-started/tutorial-console-cpp)için **Installed**' i seçin , **Visual C++**'yı genişletin ve ardından oluşturmak istediğiniz C++ proje türünü seçin.

   [C# uygulaması oluşturmak](../get-started/csharp/tutorial-console.md)için **Installed,** Expand **Visual C#** seçeneğini belirleyin ve ardından oluşturmak istediğiniz C# proje türünü seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio yüklemesi tamamlandıktan sonra Visual Studio ile geliştirmeye başlamak için **Başlat** düğmesini seçin.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

1. Arama kutusuna, kullanılabilir şablonların listesini görmek için oluşturmak istediğiniz uygulama türünü girin. Şablonlar listesi, yükleme sırasında seçtiğiniz iş yüküne bağlıdır. Farklı şablonları görmek için farklı iş yüklerini seçin.

   **Ayrıca, Dil** açılır listesini kullanarak belirli bir programlama dili için aramanıza filtre uygulayabilirsiniz. **Platform** listesini ve **Proje türü** listesini de kullanarak filtre uygulayabilirsiniz.

1. Visual Studio yeni projenizi açıyor ve kodlamaya hazırsınız!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Visual Studio'nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Mac için Visual Studio’yu yükleyin](/visualstudio/mac/installation)
