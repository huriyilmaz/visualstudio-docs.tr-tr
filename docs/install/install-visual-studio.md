---
title: Visual Studio'yu yükleme
titleSuffix: ''
description: Visual Studio 'Yu nasıl yükleyeceğinizi adım adım öğrenin.
ms.date: 12/13/2019
ms.custom: contperf-fy21q1
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
ms.openlocfilehash: 2c3302499ec44d7a97ca66532428e0af117e3a7e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903785"
---
# <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2019"

Visual Studio 2019 'e hoş geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçmek ve yüklemek çok kolay. En düşük minimum kaplama nedeniyle, hızlı bir şekilde ve daha az sistem etkisinden yüklenir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'Yu yüklemek için yeni bir yola hoş geldiniz! Bu sürümde, yalnızca ihtiyacınız olan özellikleri seçip yüklemenizi daha kolay hale geçirdik. Ayrıca, Visual Studio 'nun en küçük ayak izini daha hızlı bir şekilde ve daha az sistem etkisinden daha önce hiç olmadığı kadar azalttık.

::: moniker-end

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Install Mac için Visual Studio](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Bu sürümdeki yenilikler hakkında daha fazla bilgi edinmek istiyor musunuz? [Sürüm notlarımıza](/visualstudio/releases/2019/release-notes/)bakın.

::: moniker-end

::: moniker range="vs-2017"

Bu sürümdeki yenilikler hakkında daha fazla bilgi edinmek istiyor musunuz? [Sürüm notlarımıza](/visualstudio/releasenotes/vs2017-relnotes)bakın.

::: moniker-end

Yüklenmeye hazırlanıyor mi? Adım adım size kılavuzluk ederiz.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>1. adım-bilgisayarınızın Visual Studio için hazırlanmaya çalıştığından emin olun

Visual Studio 'Yu yüklemeye başlamadan önce:

::: moniker range="vs-2017"

1. [Sistem gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs)denetleyin. Bu gereksinimler, bilgisayarınızın Visual Studio 2017 ' i destekleyip desteklemediğini bilmenizi sağlamaya yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızda hem en son güvenlik güncelleştirmelerinin hem de Visual Studio için gerekli sistem bileşenlerinin bulunduğundan emin olun.

1. Makine. Yeniden başlatma, bekleyen yükleme veya güncelleştirmelerin Visual Studio yüklemesini desteklemez.

1. Boş alan açın. % SystemDrive% öğesinden gereksiz dosya ve uygulamaları, örneğin, disk temizleme uygulamasını çalıştırmak için kaldırın.

::: moniker-end

::: moniker range="vs-2019"

1. [Sistem gereksinimlerini](/visualstudio/releases/2019/system-requirements)denetleyin. Bu gereksinimler, bilgisayarınızın Visual Studio 2019 ' i destekleyip desteklemediğini bilmenizi sağlamaya yardımcı olur.

1. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızda hem en son güvenlik güncelleştirmelerinin hem de Visual Studio için gerekli sistem bileşenlerinin bulunduğundan emin olun.

1. Makine. Yeniden başlatma, bekleyen yükleme veya güncelleştirmelerin Visual Studio yüklemesini desteklemez.

1. Boş alan açın. % SystemDrive% öğesinden gereksiz dosya ve uygulamaları, örneğin, disk temizleme uygulamasını çalıştırmak için kaldırın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'nun önceki sürümlerini Visual Studio 2017 ile yan yana çalıştırma hakkında sorularınız için [Visual Studio uyumluluk ayrıntılarına](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)bakın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun önceki sürümlerini Visual Studio 2019 ile yan yana çalıştırma hakkında sorularınız için [Visual studio 2019 Platform hedefleme ve uyumluluk](/visualstudio/releases/2019/compatibility/) sayfasına bakın.

::: moniker-end

## <a name="step-2---download-visual-studio"></a>2. adım-Visual Studio 'Yu Indirme

Ardından, Visual Studio önyükleyici dosyasını indirin.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Bunu yapmak için, aşağıdaki düğmeyi seçin, istediğiniz Visual Studio sürümünü seçin, **Kaydet**' i seçin ve sonra **klasörü aç**' ı seçin.

 > [!div class="button"]
 > [Visual Studio’yu indirin](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>3. adım-Visual Studio yükleyicisini yükleme

Visual Studio Yükleyicisi yüklemek için önyükleyici dosyasını çalıştırın. Bu yeni basit yükleyici, Visual Studio 'Yu yüklemek ve özelleştirmek için ihtiyacınız olan her şeyi içerir.

1. **İndirmeler** klasöründen, eşleşen önyükleyiciyi çift tıklayın veya aşağıdaki dosyalardan birine benzer:

   * Visual Studio Community için **vs_community.exe**
   * Visual Studio Professional için **vs_professional.exe**
   * Visual Studio Enterprise için **vs_enterprise.exe**

   Bir kullanıcı hesabı denetimi bildirimi alırsanız **Evet**' i seçin.

2. Microsoft [Lisans koşulları](https://visualstudio.microsoft.com/license-terms/) ' nı ve Microsoft [Gizlilik bildirimi](https://privacy.microsoft.com/privacystatement)' ni kabul etmeniz istenir. **Devam**'ı seçin.

   ![Lisans koşulları ve gizlilik bildirimi](media/privacy-and-license-terms.png "Microsoft lisans koşulları ve gizlilik bildirimi")

## <a name="step-4---choose-workloads"></a>4. adım-iş yüklerini seçin

Yükleyici yüklendikten sonra, istediğiniz özellik kümelerini (veya iş yüklerini) seçerek yüklemenizi özelleştirmek için kullanabilirsiniz. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. **Visual Studio yükleyicisi** istediğiniz iş yükünü bulun.

   ![Visual Studio 2017: iş yükü yüklemesi](../install/media/vs-installer-installing-workloads.png)

     Örneğin, ".NET masaüstü geliştirme" iş yükünü seçin. 20 ' den fazla dil için temel kod düzenleme desteğini içeren, bir proje gerektirmeden herhangi bir klasörden kod açma ve düzenleme özelliği ve Tümleşik kaynak kodu denetimi olan varsayılan çekirdek Düzenleyicisi ile gelir.

1. İstediğiniz iş yüklerini seçtikten sonra, **yükler**' i seçin.

    Ardından, Visual Studio yüklemenizin ilerlemesini gösteren durum ekranları görüntülenir.

 ::: moniker-end

::: moniker range="vs-2019"

1. **Visual Studio yükleyicisi** istediğiniz iş yükünü bulun.

   ![Visual Studio 2019: iş yükü yüklemesi](../install/media/vs-2019/vs-installer-workloads.png)

     Örneğin, "ASP.NET ve Web geliştirme" iş yükünü seçin. 20 ' den fazla dil için temel kod düzenleme desteğini içeren, bir proje gerektirmeden herhangi bir klasörden kod açma ve düzenleme özelliği ve Tümleşik kaynak kodu denetimi olan varsayılan çekirdek Düzenleyicisi ile gelir.

1. İstediğiniz iş yüklerini seçtikten sonra, **yükler**' i seçin.

    Ardından, Visual Studio yüklemenizin ilerlemesini gösteren durum ekranları görüntülenir.

 ::: moniker-end

> [!TIP]
> Yüklemeden sonra dilediğiniz zaman, ilk olarak yüklediğiniz iş yüklerini veya bileşenleri yükleyebilirsiniz. Visual Studio açıksa **Araçlar**' a gidin  >  **Araçlar ve Özellikler al...** Visual Studio yükleyicisi açılır. Ya da, Başlat menüsünden **Visual Studio yükleyicisi** açın. Buradan, yüklemek istediğiniz iş yüklerini veya bileşenleri seçebilirsiniz. Ardından **Değiştir**' i seçin.

## <a name="step-5---choose-individual-components-optional"></a>5. adım-tek tek bileşenleri seçin (Isteğe bağlı)

Visual Studio yüklemenizi özelleştirmek için Iş yükleri özelliğini kullanmak istemiyorsanız veya bir iş yükü yüklemesinden daha fazla bileşen eklemek istiyorsanız **, tek tek bileşenler sekmesinden tek** tek bileşenleri yükleyerek veya ekleyerek yapabilirsiniz. İstediğinizi seçin ve ardından istemleri izleyin.

::: moniker range="vs-2017"

  ![Visual Studio 2017-ayrı bileşenleri yükler](media/vs-installer-installing-components.png "Visual Studio bireysel bileşenlerini yükler")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-ayrı bileşenleri yükler](media/vs-2019/vs-installer-individual-components.png "Visual Studio bireysel bileşenlerini yükler")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>6. adım-dil paketlerini (Isteğe bağlı) yükler

Varsayılan olarak, yükleyici programı ilk kez çalıştırıldığında işletim sisteminin dilini eşleştirmeye çalışır. Visual Studio 'Yu seçtiğiniz bir dilde yüklemek için Visual Studio Yükleyicisi **dil paketleri** sekmesini seçin ve ardından istemleri izleyin.

::: moniker range="vs-2017"

  ![Visual Studio 2017-dil paketlerini yükler](media/vs-installer-installing-language-packs.png "Visual Studio dil paketlerini yükler")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019-dil paketlerini yükler](media/vs-2019/vs-installer-language-packs.png "Visual Studio dil paketlerini yükler")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Yükleyici dilini komut satırından değiştirme

Varsayılan dili değiştirebilmeniz için, yükleyiciyi komut satırından çalıştırmak sizin için başka bir yoldur. Örneğin, aşağıdaki komutu kullanarak yükleyiciyi Ingilizce olarak çalışmaya zorlayabilirsiniz: `vs_installer.exe --locale en-US` . Yükleyici bir sonraki sefer çalıştırıldığında bu ayarı anımsayacaktır. Yükleyici şu dil belirteçlerini destekler: zh-cn, zh-tw, CS-CZ, en-US, es-es, fr-fr, de-de, IT-it, ja-JP

## <a name="step-7---select-the-installation-location-optional"></a>7. adım-yükleme konumunu seçin (Isteğe bağlı)

::: moniker range="vs-2017"

**15,7 ' deki yenilikler**: artık, sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini azaltabilirsiniz. İndirme önbelleğini, paylaşılan bileşenleri, SDK 'Ları ve araçları farklı sürücülere taşımayı ve Visual Studio 'Yu en hızlı şekilde çalıştıran sürücüde tutmayı seçebilirsiniz.

  ![Visual Studio 2017-yükleme konumlarını değiştirme](media/installation-options-by-location.png "Yükleme konumunu değiştirme")

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun yükleme ayak izini sistem sürücünüzde azaltabilirsiniz. İndirme önbelleğini, paylaşılan bileşenleri, SDK 'Ları ve araçları farklı sürücülere taşımayı ve Visual Studio 'Yu en hızlı şekilde çalıştıran sürücüde tutmayı seçebilirsiniz.

  ![Visual Studio 2019-yükleme konumlarını seçme](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin")

::: moniker-end

> [!IMPORTANT]
> Yalnızca Visual Studio 'Yu ilk kez yüklediğinizde, farklı bir sürücü seçebilirsiniz. Zaten yüklediyseniz ve sürücüleri değiştirmek istiyorsanız, Visual Studio 'Yu kaldırmalı ve ardından yeniden yüklemeniz gerekir.

Daha fazla bilgi için bkz. [yükleme konumlarını seçme](change-installation-locations.md) sayfası.

## <a name="step-8---start-developing"></a>8. adım-geliştirmeye başlama

::: moniker range="vs-2017"

1. Visual Studio yüklemesi tamamlandıktan sonra, Visual Studio ile geliştirmeye başlamak için **Başlat** düğmesini seçin.

2. **Dosya**' yı ve ardından **Yeni proje**' yi seçin.

3. Bir proje türü seçin.

   Örneğin, [bir C++ uygulaması oluşturmak](/cpp/get-started/tutorial-console-cpp)Için, **yüklü**' ı seçin, **Visual C++**' ı genişletin ve ardından derlemek istediğiniz C++ proje türünü seçin.

   [C# uygulaması oluşturmak](../get-started/csharp/tutorial-console.md)Için, **yüklü**, **Visual C#**' yi ve ardından derlemek istediğiniz c# proje türünü seçin.

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
* [Mac için Visual Studio’yu yükleyin](/visualstudio/mac/installation)
 