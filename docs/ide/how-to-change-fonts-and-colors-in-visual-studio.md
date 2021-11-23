---
title: Erişilebilirlik için temaları, yazı tiplerini, metinleri ve karşıtlığı değiştirme
description: Kullanım kolaylığı ve erişilebilirlik Visual Studio renk temalarını, yazı tipi renklerini, metin boyutlarını ve ek karşıtlık renklerini nasıl değiştiryebilirsiniz?
ms.date: 11/19/2021
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3bba9cf88014935db69a07ec0e16f0b16eea1a62
ms.sourcegitcommit: e0a642bbd0a74c292b3b1d8046733cfdf93af70e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2021
ms.locfileid: "132918918"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Nasıl yapabilirsiniz: Visual Studio'da yazı tiplerini, renkleri ve temaları değiştirme

::: moniker range=">=vs-2022"

Yazı tiplerini ve renkleri farklı Visual Studio değiştirebilirsiniz. Örneğin, varsayılan koyu temayı ("koyu mod" olarak da adlandırılır) açık tema, mavi tema, ek karşıtlık teması veya sistem ayarlarınıza uygun bir tema olarak değiştirebilirsiniz. Ayrıca hem IDE'de hem de kod düzenleyicisinde varsayılan yazı tipi ve metin boyutunu değiştirebilirsiniz.

> [!TIP]
> Renk karşıtlığı oranı ayarlamaları ve yeni Cascadia Code yazı tipi hakkında daha fazla bilgi edinmek için kullanıcı arabirimini [**Visual Studio 2022'de**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) yükselttik blog gönderisi ve daha kolay erişilebilir hale Visual Studio cascadia Code yazı tipine bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Yazı tiplerini ve renkleri birçok Visual Studio değiştirebilirsiniz. Örneğin, varsayılan mavi renk temasını koyu temayla ("koyu mod" olarak da adlandırılır) değiştirebilirsiniz. İhtiyaçlarınızı en iyi şekilde karşılamak için ek karşıtlıklı bir tema da seçebilirsiniz. Ayrıca hem IDE hem de kod düzenleyicisinde varsayılan yazı tipi ve metin boyutunu değiştirebilirsiniz.

::: moniker-end

## <a name="change-the-color-theme"></a>Renk temasını değiştirme

IDE çerçevesinin renk temasını ve araç pencerelerini aşağıdaki gibi Visual Studio.

::: moniker range=">=vs-2022"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam **Genel'i** > **seçin.**

1. Renk **teması listesinde** varsayılan Koyu temayı,  Açık **temayı,** Mavi temayı veya Mavi (Ek Karşıtlık) **temasını** seçin. 

   Ayrıca Sistem ayarını kullan'ı seçerek Windows **temayı kullanmayı da seçebilirsiniz.**

   :::image type="content" source="media/vs-2022/fonts-colors-theme.png" alt-text="Renk temasını değiştirebilirsiniz Seçenekler iletişim kutusunun ekran görüntüsü.":::

   > [!NOTE]
   > Bir renk temasını değiştirseniz, IDE'de metin bu tema için varsayılan veya daha önce özelleştirilmiş yazı tiplerini ve boyutlarını geri döner.

    > [!TIP]
    > Daha fazla tema seçmek ister misiniz? Visual Studio Market'te çok çeşitli [**özel temalara göz atabilirsiniz.**](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Themes&sortBy=Installs) VS Code tabanlı yeni Visual Studio 2022 özel temalarının örneklerini görmek için Yeni Visual Studio temaları koleksiyonuna tanıtma blog [**gönderisi'ne**](https://devblogs.microsoft.com/visualstudio/custom-themes/) göz atabilirsiniz.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam **Genel'i** > **seçin.**

1. Renk **teması listesinde** varsayılan Mavi  temayı,  Açık temayı, Koyu temayı veya Mavi (Ek Karşıtlık) **temasını** seçin. 

   ![Renk temasını değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-theme.png "Renk temasını değiştirmek için kullanabileceğiniz Seçenekler iletişim kutusunun ekran görüntüsü.")

   > [!NOTE]
   > Bir renk temasını değiştirseniz, IDE'de metin bu tema için varsayılan veya daha önce özelleştirilmiş yazı tiplerini ve boyutlarını geri döner.

    > [!TIP]
    > Bir uzantı kullanarak kendi temalarınızı Visual Studio temalarınızı oluşturabilir ve düzenleyebilirsiniz. Kullandığınız uygulamanın sürümüne bağlı olarak aşağıdaki iki seçenekten birini Visual Studio birini seçin:
    > - [Visual Studio 2019 için Renk Teması Tasarımcısı.](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)
    > - [Visual Studio 2017 için Renk Teması Düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)

::: moniker-end

## <a name="change-fonts-and-text-size"></a>Yazı tiplerini ve metin boyutunu değiştirme

Tüm IDE çerçeve ve araç pencerelerinde veya yalnızca belirli pencereler veya metin öğeleri için yazı tipi ve metin boyutunu değiştirebilirsiniz. Ayrıca düzenleyicide yazı tipini ve metin boyutunu da değiştirebilirsiniz.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>IDE'de yazı tipini ve metin boyutunu değiştirmek için

::: moniker range=">=vs-2022"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam  Yazı Tipleri ve > **Renkler'i seçin.**

1. Ayarları **göster listesinde Ortam'ı** **seçin.**

   ![IDE'de yazı tipi ve metin boyutunu değiştirerek Seçenekler iletişim kutusunun ekran görüntüsü](media/vs-2022/fonts-colors-text-environment.png "IDE'de yazı tipi ve metin boyutunu değiştirerek Seçenekler iletişim kutusunun ekran görüntüsü.")

    > [!NOTE]
    > Yalnızca araç pencereleri için yazı tipini değiştirmek için, Show **settings for list** (Ayarları göster) listesinde Tüm Metin Aracı'nı **Windows.**

1. **IDE'nin** **yazı tipini** ve metin boyutunu değiştirmek için Yazı Tipi ve Boyut seçeneklerini değiştirme.

1. Öğeleri görüntüle'de **uygun öğeyi seçin** ve ardından Öğe ön plan ve Öğe arka **plan** **seçeneklerini** değiştirebilirsiniz.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam  Yazı Tipleri ve > **Renkler'i seçin.**

1. Ayarları **göster listesinde Ortam'ı** **seçin.**

   ![IDE'de yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-environment.png "IDE'de yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü.")

    > [!NOTE]
    > Yalnızca araç pencereleri için yazı tipini değiştirmek için, Show **settings for list** (Ayarları göster) listesinde Tüm Metin Aracı'nı **Windows.**

1. **IDE'nin** **yazı tipini** ve metin boyutunu değiştirmek için Yazı Tipi ve Boyut seçeneklerini değiştirme.

1. Öğeleri görüntüle'de **uygun öğeyi seçin** ve ardından Öğe ön plan ve Öğe arka **plan** **seçeneklerini** değiştirebilirsiniz.

::: moniker-end

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Düzenleyicide yazı tipini ve metin boyutunu değiştirmek için

::: moniker range=">=vs-2022"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam  Yazı Tipleri ve > **Renkler'i seçin.**

1. Liste **ayarlarını göster'de** Metin Düzenleyici'yi **seçin.**

   ![Düzenleyicide yazı tipini ve metin boyutunu değiştirerek Seçenekler iletişim kutusunun ekran görüntüsü](media/vs-2022/fonts-colors-text-editor.png "Düzenleyicide yazı tipini ve metin boyutunu değiştirerek Seçenekler iletişim kutusunun ekran görüntüsü.")

1. Yazı tipi **ve** **Boyut seçeneklerini** değiştirerek düzenleyicinin yazı tipini ve metin boyutunu değiştirebilirsiniz.

1. Öğeleri görüntüle'de **uygun öğeyi seçin** ve ardından Öğe ön plan ve Öğe arka **plan** **seçeneklerini** değiştirebilirsiniz.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. Seçenekler listesinde Ortam  Yazı Tipleri ve > **Renkler'i seçin.**

1. Liste **ayarlarını göster'de** Metin Düzenleyici'yi **seçin.**

   ![Düzenleyicide yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-text-editor.png "Düzenleyicide yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü.")

1. Yazı tipi **ve** **Boyut seçeneklerini** değiştirerek düzenleyicinin yazı tipini ve metin boyutunu değiştirebilirsiniz.

1. Öğeleri görüntüle'de **uygun öğeyi seçin** ve ardından Öğe ön plan ve Öğe arka **plan** **seçeneklerini** değiştirebilirsiniz.

::: moniker-end

Daha fazla bilgi için düzenleyicinin [yazı tiplerini ve renklerini değiştirme sayfasına](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) bakın.

## <a name="accessibility-options"></a>Erişilebilirlik seçenekleri

::: moniker range="vs-2022"

Görme azı ile karşılanıyorsanız yazı tipi seçenekleri ve renk temaları şunlardır:

- Harflerin, rakamların ve karakterlerin oranına daha fazla ağırlık ekleyen [Cascadia Code](#use-the-cascadia-code-font) yazı tipini kullanarak bu yazı tipini kullanabilirsiniz.
- Ayrıca, bir bilgisayarda tüm uygulamalar [ve](#use-windows-high-contrast)  kullanıcı arabirimi için yüksek karşıtlıklı bir renk teması veya yalnızca uygulamalar için fazladan karşıtlıklı bir Visual Studio seçebilirsiniz. [](#use-visual-studio-extra-contrast)

### <a name="use-the-cascadia-code-font"></a>Cascadia Code yazı tipini kullanma

Yeni [**Cascadia Code yazı**](https://github.com/microsoft/cascadia-code#welcome) tipi, 2022 yılındaki varsayılan yazı tipi olan **Cascade Mono'Visual Studio** içerir. Bu yazı tiplerinin her ikisinin de okunma kolay olduğu gibi Cascadia Code yazı tipi de bir karakter dizisini karakter karakterine dönüştüren kodlama özelikleri içerir. Kodlama ve glyph'ler, insanların arkalarında yer alan anlamı bilişsel olarak ilişkilendirmesini kolaylaştırır.

Aşağıdaki ekran görüntüsünde varsayılan Cascadia Mono yazı tipi örneği ve siz kod kullanırken kullanarak bul olabileceğiniz matematiksel sembolleri içeren bir karakter dizisi yer almaktadır.

:::image type="content" source="media/vs-2022/cascadia-mono-font.png" alt-text="Düzenleyicide Cascadia Mono yazı tipi örneği ekran görüntüsü.":::

Aşağıdaki ekran görüntüsünde, daha önce gösterilen aynı karakter serisinin artık kod yazma özelikleri veya karakter karakterlerine dönüştürülmesiyle ilgili bir Cascadia Code yazı tipi örneği gösterilmektedir.

:::image type="content" source="media/vs-2022/cascadia-code-font.png" alt-text="Düzenleyicide Cascadia Code yazı tipi örneği ekran görüntüsü.":::

Cascadia Code ekran görüntüsünde yer alan son metin satırı, yinelenen karakterler arasındaki boşluğun nasıl azaltılmış olduğunu gösterir ve bu da okunmalarını kolaylaştırır.

Cascadia yazı tipleri arasında geçiş yapmak için aşağıdakiler kullanılabilir:

1. Araçlar Seçenekler **Ortam** > **Yazı Tipleri** > **ve** > **renkleri'ne gidin.**

1. Yazı tipi **açılan** listesinden **Cascadia Code** yazı tipini veya istediğiniz **Cascadia Mono** yazı tipini ve ardından Tamam'ı **seçin.**

    :::image type="content" source="media/vs-2022/cascadia-font-options.png" alt-text="Seçenekler iletişim kutusunda bulunan Cascadia yazı tiplerinin ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

Görme güç bir deneyim yaşamanın renk teması seçenekleri vardır. Bir bilgisayarda tüm uygulamalar ve kullanıcı arabirimi için *yüksek* karşıtlıklı bir seçenek veya yalnızca diğer uygulamalar için ek bir karşıtlık Visual Studio kullanabilirsiniz.

::: moniker-end

### <a name="use-windows-high-contrast"></a>Yüksek karşıtlık Windows kullanın

Yüksek karşıtlıklı seçeneğin iki durumlu seçeneğini Windows yordamlardan birini kullanın:

- Bu Windows veya herhangi bir Microsoft uygulamasında, Sol **Alt Sol** + **Shift** + **PrtScn tuşlarına** basın.

- Bu Windows **Başlat'ı Ayarlar**  >    >  **Erişim Kolaylığı.** Daha sonra, görüntü **ve** sonraki Windows 10 Bölümünde Yüksek karşıtlık'ı **seçin.**

    > [!WARNING]
    > Yüksek Windows ayarı, bilgisayarda tüm uygulamaları ve kullanıcı arabirimini etkiler.

### <a name="use-visual-studio-extra-contrast"></a>Daha Visual Studio karşıtlığı kullanma

Ek karşıtlık seçeneğinin iki durumlu Visual Studio yordamları kullanın:

1. Araç çubuğundaki menü Visual Studio Araçlar Seçenekleri'ne tıklayın  >  ve ardından, seçenekler listesinde Ortam **Genel'i**  >  **seçin.**

1. Renk **teması açılan** listesinde Mavi (Ek Karşıtlık) **temasını** ve ardından Tamam'ı **seçin.**

Diğer erişilebilirlik seçenekleri hakkında Visual Studio fazla bilgi edinmek için Visual Studio sayfasındaki Erişilebilirlik [özelliklerine](../ide/reference/accessibility-features-of-visual-studio.md) bakın.

> [!TIP]
> Yararlı olabileceğini düşünebilirsiniz ancak şu anda Visual Studio'da mevcut olmayan renkler veya yazı tipleri için erişilebilirlik seçeneği  varsa lütfen [Visual Studio Developer](https://aka.ms/feedback/suggest?space=8)Community . Bu forum ve nasıl çalıştığını görmek için Özellik [önerin sayfasına](../ide/suggest-a-feature.md) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Yazı tipi ve renk düzenlerini değiştirebilirsiniz tüm kullanıcı arabirimi (UI) öğeleri hakkında daha fazla bilgi edinmek için Yazı Tipleri ve [Renkler, Ortam,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) Seçenekler İletişim Kutusu sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapabilirsiniz: Düzenleyicinin yazı tiplerini ve renklerini Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Visual Studio düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IDE'Visual Studio düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md)
