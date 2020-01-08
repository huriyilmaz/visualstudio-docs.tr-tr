---
title: Visual Studio Yükle
titleSuffix: ''
description: Visual Studio, adım adım yüklemeyi öğrenin.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 078c54a680fccda0d7d6af88446b709765f277a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590130"
---
# <a name="install-visual-studio"></a>Visual Studio Yükle

::: moniker range="vs-2019"

Visual Studio 2019 'e hoş geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçmek ve yüklemek çok kolay. En düşük minimum kaplama nedeniyle, hızlı bir şekilde ve daha az sistem etkisinden yüklenir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio'yu yüklemek için yeni bir yolunu Hoş Geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçip yüklemenizi daha kolay hale geçirdik. Daha hızlı ve daha önce hiç olmadığı kadar sistemi daha az etkileyerek yükler, böylece biz de Visual Studio'nun minimum ayak kısalttık.

::: moniker-end

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Else bu sürümdeki yenilikler hakkında daha fazla bilgi edinmek istiyorsunuz? Bkz. bizim [sürüm notları](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Else bu sürümdeki yenilikler hakkında daha fazla bilgi edinmek istiyorsunuz? Bkz. bizim [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Yüklenmeye hazır? Biz, bunu, adım adım konusunda rehberlik edelim.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>1\. adım: bilgisayarınızın Visual Studio'ya hazır olduğundan emin olun

Visual Studio yükleme başlamadan önce:

::: moniker range="vs-2017"

1. Denetleme [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs). Bu gereksinimleri bilgisayarınıza Visual Studio 2017 destekleyip desteklemediğini bilmenize yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızda Visual Studio için en son güvenlik güncelleştirmelerini hem gerekli sistem bileşenlerine sahip olun.

1. Yeniden başlatma. Yeniden başlatma bekleyen yükleme veya güncelleştirmelerin Visual Studio yüklemesini engellememesini sağlar.

1. Alan boşaltın. Gereksiz dosyaları ve uygulamalar, % SYSTEMDRIVE %, örneğin, Disk Temizleme uygulamayı çalıştıran kaldırın.

::: moniker-end

::: moniker range="vs-2019"

1. Denetleme [sistem gereksinimleri](/visualstudio/releases/2019/system-requirements). Bu gereksinimler, bilgisayarınızın Visual Studio 2019 ' i destekleyip desteklemediğini bilmenizi sağlamaya yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızda Visual Studio için en son güvenlik güncelleştirmelerini hem gerekli sistem bileşenlerine sahip olun.

1. Yeniden başlatma. Yeniden başlatma bekleyen yükleme veya güncelleştirmelerin Visual Studio yüklemesini engellememesini sağlar.

1. Alan boşaltın. Gereksiz dosyaları ve uygulamalar, % SYSTEMDRIVE %, örneğin, Disk Temizleme uygulamayı çalıştıran kaldırın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 ile yan yana Visual Studio'nun önceki sürümlerini çalıştıran hakkında sorular için bkz [Visual Studio uyumluluk ayrıntıları](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun önceki sürümlerini Visual Studio 2019 ile yan yana çalıştırma hakkında sorularınız için [Visual studio 2019 Platform hedefleme ve uyumluluk](/visualstudio/releases/2019/compatibility/) sayfasına bakın.

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Adım 2 - Visual Studio indirme

Ardından, Visual Studio önyükleyicisi dosyasını indirin.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Bunu yapmak için, aşağıdaki düğmeyi seçin, istediğiniz Visual Studio sürümünü seçin, **Kaydet**' i seçin ve sonra **klasörü aç**' ı seçin.

 > [!div class="button"]
 > [Visual Studio 'Yu indirin](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>3\. adım - Visual Studio Yükleyicisi'ni yükleme

Visual Studio Yükleyicisi yüklemek için önyükleyici dosyasını çalıştırın. Bu yeni basit yükleyici, Visual Studio 'Yu yüklemek ve özelleştirmek için ihtiyacınız olan her şeyi içerir.

1. Öğesinden, **indirir** klasöründe eşleşen veya benzer bir aşağıdaki dosyalar önyükleyici çift tıklayın:

   * **vs_community.exe** Visual Studio Community için
   * **vs_professional.exe** Visual Studio Professional
   * **vs_enterprise.exe** için Visual Studio Enterprise

   Bir kullanıcı hesabı denetimi bildirimi alırsanız **Evet**' i seçin.

2. Microsoft onaylamak için isteriz [lisans koşulları](https://visualstudio.microsoft.com/license-terms/) ve Microsoft [gizlilik bildirimi](https://privacy.microsoft.com/privacystatement). Seçin **devam**.

   ![Lisans koşulları ve gizlilik bildirimi](media/privacy-and-license-terms.png "Microsoft lisans koşulları ve gizlilik bildirimi")

## <a name="step-4---choose-workloads"></a>4\. adım-iş yüklerini seçin

Yükleyici yüklendikten sonra bu özellik kümeleri seçerek yüklemenizi özelleştirmek için kullanabilirsiniz — veya iş yükleriniz — istediğiniz. İşte nasıl.

 ::: moniker range="vs-2017"

1. **Visual Studio yükleyicisi**istediğiniz iş yükünü bulun.

   ![Visual Studio 2017: iş yükü yüklemesi](../install/media/vs-installer-installing-workloads.png)

     Örneğin, ".NET masaüstü geliştirme" iş yükünü seçin. Bu, temel kod düzenleme açın ve projeye gerek kalmadan herhangi bir klasörden kodu düzenleme olanağı 20'den dil için destek içerir ve tümleşik kaynak kod denetimi varsayılan çekirdek Düzenleyicisi ile birlikte gelir.

1. İstediğiniz iş yüklerini seçtikten sonra, **yükler**' i seçin.

    Ardından, durum ekranları, Visual Studio yüklemenizin ilerleme durumunu gösteren görünür.

 ::: moniker-end

::: moniker range="vs-2019"

1. **Visual Studio yükleyicisi**istediğiniz iş yükünü bulun.

   ![Visual Studio 2019: iş yükü yüklemesi](../install/media/vs-2019/vs-installer-workloads.png)

     Örneğin, "ASP.NET ve Web geliştirme" iş yükünü seçin. Bu, temel kod düzenleme açın ve projeye gerek kalmadan herhangi bir klasörden kodu düzenleme olanağı 20'den dil için destek içerir ve tümleşik kaynak kod denetimi varsayılan çekirdek Düzenleyicisi ile birlikte gelir.

1. İstediğiniz iş yüklerini seçtikten sonra, **yükler**' i seçin.

    Ardından, durum ekranları, Visual Studio yüklemenizin ilerleme durumunu gösteren görünür.

 ::: moniker-end

> [!TIP]
> Yüklemeden sonra herhangi bir zamanda iş yükleri veya başlangıçta yüklenmedi bileşenleri yükleyebilirsiniz. Visual Studio'nun varsa **Araçları** > **araçları ve özellikleri Al...**  Visual Studio yükleyicisi açılır. Veya açık **Visual Studio yükleyicisi** Başlat menüsünden. Buradan, yüklemek istediğiniz iş yüklerini veya bileşenleri seçebilirsiniz. Ardından **Değiştir**' i seçin.

## <a name="step-5---choose-individual-components-optional"></a>5\. adım-tek tek bileşenleri seçin (Isteğe bağlı)

Visual Studio yüklemenizi özelleştirmek için Iş yükleri özelliğini kullanmak istemiyorsanız veya bir iş yükü yüklemesinden daha fazla bileşen eklemek istiyorsanız, **tek** tek bileşenler sekmesinden tek tek bileşenleri yükleyerek veya ekleyerek bunu yapabilirsiniz. istediğinizi seçin ve ardından istemleri takip edin.

::: moniker range="vs-2017"

  ![Visual Studio 2017-ayrı bileşenleri yükler](media/vs-installer-installing-components.png "Visual Studio bireysel bileşenlerini yükler")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-ayrı bileşenleri yükler](media/vs-2019/vs-installer-individual-components.png "Visual Studio bireysel bileşenlerini yükler")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>6\. adım - yükleme dil paketleri (isteğe bağlı)

Varsayılan olarak, yükleyici programı ilk kez çalıştığında işletim sisteminin dilini eşleştirmeye çalışır. Visual Studio 'Yu seçtiğiniz bir dilde yüklemek için Visual Studio Yükleyicisi **dil paketleri** sekmesini seçin ve ardından istemleri izleyin.

::: moniker range="vs-2017"

  ![Visual Studio 2017-dil paketlerini yükler](media/vs-installer-installing-language-packs.png "Visual Studio dil paketlerini yükler")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-dil paketlerini yükler](media/vs-2019/vs-installer-language-packs.png "Visual Studio dil paketlerini yükler")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Komut satırından yükleyici dilini değiştirme

Varsayılan dilini değiştirme başka bir komut satırından yükleyiciyi çalıştırarak yoludur. Örneğin, aşağıdaki komutu kullanarak İngilizce olarak çalıştırmak için yükleyici zorlayabilirsiniz: `vs_installer.exe --locale en-US`. Yükleyici, sonraki açışınızda çalıştırdığınızda bu ayar hatırlanır. Aşağıdaki Dil belirteçler yükleyici destekler: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-IT, ja-jp, ko-kr, pl-pl, pt-br, ru-ru ve tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>7\. adım-yükleme konumunu seçin (Isteğe bağlı)

::: moniker range="vs-2017"

**15.7 sürümündeki yeni**: artık Visual Studio yükleme ayak izini sistem sürücünüzde azaltabilir. İndirme önbelleğini, paylaşılan bileşenler, SDK'ları ve araçları farklı sürücülere taşıma ve Visual Studio en hızlı çalışan sürücüde korumak seçebilirsiniz.

  ![Visual Studio 2017-yükleme konumlarını değiştirme](media/installation-options-by-location.png "Yükleme konumunu değiştirme")

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun yükleme ayak izini sistem sürücünüzde azaltabilirsiniz. İndirme önbelleğini, paylaşılan bileşenler, SDK'ları ve araçları farklı sürücülere taşıma ve Visual Studio en hızlı çalışan sürücüde korumak seçebilirsiniz.

  ![Visual Studio 2019-yükleme konumlarını seçme](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin")

::: moniker-end

> [!IMPORTANT]
> Yalnızca Visual Studio 'Yu ilk kez yüklediğinizde, farklı bir sürücü seçebilirsiniz. Zaten yüklediyseniz ve sürücüleri değiştirmek istiyorsanız, Visual Studio 'Yu kaldırmalı ve ardından yeniden yüklemeniz gerekir.

Daha fazla bilgi için bkz. [yükleme konumlarını seçme](change-installation-locations.md) sayfası.

## <a name="step-8---start-developing"></a>8\. adım - geliştirmeye başlayın

::: moniker range="vs-2017"

1. Visual Studio yüklemesi tamamlandıktan sonra, Visual Studio ile geliştirmeye başlamak için **Başlat** düğmesini seçin.

2. **Dosya**' yı ve ardından **Yeni proje**' yi seçin.

3. Bir proje türü seçin.

   Örneğin, [bir C++ uygulama oluşturmak](/cpp/get-started/tutorial-console-cpp)için, **yüklendi**, **görsel C++** ' i seçin ve ardından derlemek istediğiniz C++ proje türünü seçin.

   [Bir C# uygulama oluşturmak](../get-started/csharp/tutorial-console.md)için, **yüklü**, **görsel C#** ' i seçin ve ardından derlemek istediğiniz C# proje türünü seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio yüklemesi tamamlandıktan sonra, Visual Studio ile geliştirmeye başlamak için **Başlat** düğmesini seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. Arama kutusuna, kullanılabilir şablonların listesini görmek için oluşturmak istediğiniz uygulamanın türünü girin. Şablon listesi, yükleme sırasında seçtiğiniz iş yüküne bağlıdır. Farklı şablonları görmek için farklı iş yükleri seçin.

   Ayrıca, **dil** açılan listesini kullanarak, aramanızı belirli bir programlama diline göre filtreleyebilirsiniz. **Platform** listesini ve **Proje türü** listesini kullanarak filtre uygulayabilirsiniz.

1. Visual Studio yeni projenizi açar ve kodlamaya hazırsınız!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Mac için Visual Studio'yu yükleyin](/visualstudio/mac/installation)
