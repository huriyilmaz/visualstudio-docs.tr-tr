---
title: Erişilebilirlik için temaları, yazı tiplerini, metni ve karşıtlığı değiştirme
description: kullanım kolaylığı ve erişilebilirlik sorunları için Visual Studio renk temalarını, yazı tipi renklerini, metin boyutlarını ve çok karşıtlıklı renkleri değiştirmeyi öğrenin.
ms.date: 11/24/2021
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
ms.openlocfilehash: cc4aa4384b5be48d6456dccb38a6a92023b6ad04
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108883"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Nasıl yapılır: Visual Studio yazı tiplerini, renkleri ve temaları değiştirme

::: moniker range=">=vs-2022"

Visual Studio yazı tiplerini ve renkleri çeşitli yollarla değiştirebilirsiniz. Örneğin, varsayılan koyu temayı ("koyu mod" olarak da bilinir) bir açık temaya, mavi temaya, çok karşıtlıklı temaya veya sistem ayarlarınızla eşleşen bir temaya değiştirebilirsiniz. Ayrıca, hem IDE hem de kod düzenleyicisinde varsayılan yazı tipini ve metin boyutunu değiştirebilirsiniz.

> [!TIP]
> hafif renk karşıtlığı oranı ayarlamaları hakkında daha fazla bilgi edinmek için [**Visual Studio 2022 blog postasında kullanıcı arabirimini yükselttik**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) ve Visual Studio herkes için daha erişilebilir hale getirmek üzere eklediğimiz yeni bir basamaklı dia kodu yazı tipi hakkında daha fazla bilgi edinmek için bkz..

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio yazı tiplerini ve renkleri birçok şekilde değiştirebilirsiniz. Örneğin, varsayılan mavi renk temasını koyu Tema ("koyu mod" olarak da adlandırılır) olarak değiştirebilirsiniz. Gereksinimlerinize en uygun olan bir ek kontrast teması da seçebilirsiniz. Hem IDE hem de kod düzenleyicisinde varsayılan yazı tipini ve metin boyutunu değiştirebilirsiniz.

::: moniker-end

## <a name="change-the-color-theme"></a>Renk temasını değiştirme

Visual Studio içindeki IDE çerçevesinin ve araç pencerelerinin renk temasını değiştirme.

::: moniker range=">=vs-2022"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **genel**' i seçin.

1. **Renk teması** listesinde, varsayılan **koyu** temayı, **ışık** temasını, **mavi** temayı veya **mavi (ekstra Karşıtlık)** temasını seçin.

   Windows, **sistem ayarını kullan**' ı seçerek, kullandığı temayı kullanmayı da tercih edebilirsiniz.

   :::image type="content" source="media/vs-2022/fonts-colors-theme.png" alt-text="Renk temasını değiştirebileceğiniz Seçenekler iletişim kutusunun ekran görüntüsü.":::

   > [!NOTE]
   > Bir renk temasını değiştirdiğinizde, IDE 'deki metin, bu temanın varsayılan veya daha önce özelleştirilmiş yazı tiplerine ve boyutlarına geri döner.

    > [!TIP]
    > Daha da fazla tema seçeistiyor musunuz? [**Visual Studio market**](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Themes&sortBy=Installs)'teki özel temaların geniş yelpazesini inceleyin. ayrıca, VS Code tabanlı yeni Visual Studio 2022 özel temalarının örneklerini görmek için, [**yeni Visual Studio temalarının bir koleksiyonunu tanıtma**](https://devblogs.microsoft.com/visualstudio/custom-themes/) blog gönderisine göz atın.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **genel**' i seçin.

1. **Renk teması** listesinde, varsayılan **mavi** temayı, **ışık** temasını, **koyu** temayı veya **mavi (ekstra Karşıtlık)** temasını seçin.

   ![Renk temasını değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-theme.png "Renk temasını değiştirmek için kullanabileceğiniz seçenekler iletişim kutusunun ekran görüntüsü.")

   > [!NOTE]
   > Bir renk temasını değiştirdiğinizde, IDE 'deki metin, bu temanın varsayılan veya daha önce özelleştirilmiş yazı tiplerine ve boyutlarına geri döner.

    > [!TIP]
    > bir uzantıyı kullanarak kendi Visual Studio temalarınızı oluşturabilir ve düzenleyebilirsiniz. kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak aşağıdaki iki seçenekten birini seçin:
    > - [Visual Studio 2019 için renk teması tasarımcısı](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).
    > - [Visual Studio 2017 için renk teması düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)

::: moniker-end

## <a name="change-fonts-and-text-size"></a>Yazı tiplerini ve metin boyutunu değiştirme

Tüm IDE çerçevesi ve araç pencereleri için ya da yalnızca belirli pencereler veya metin öğeleri için yazı tipi ve metin boyutunu değiştirebilirsiniz. Ayrıca, düzenleyicideki yazı tipini ve metin boyutunu da değiştirebilirsiniz.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>IDE 'deki yazı tipini ve metin boyutunu değiştirmek için

::: moniker range=">=vs-2022"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde **ortam**' ı seçin.

   ![IDE 'de yazı tipini ve metin boyutunu değiştirdiğiniz Seçenekler iletişim kutusunun ekran görüntüsü](media/vs-2022/fonts-colors-text-environment.png "IDE 'deki yazı tipini ve metin boyutunu değiştirdiğiniz Seçenekler iletişim kutusunun ekran görüntüsü.")

    > [!NOTE]
    > Yalnızca araç pencerelerinin yazı tipini değiştirmek istiyorsanız, **ayarları göster** listesinde, **tüm metin aracı Windows**' ni seçin.

1. **Yazı** tipi ve **Boyut** seçeneklerini değiştirerek IDE için yazı tipini ve metin boyutunu değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde **ortam**' ı seçin.

   ![IDE 'deki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü](media/fonts-colors-environment.png "IDE 'deki yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü.")

    > [!NOTE]
    > Yalnızca araç pencerelerinin yazı tipini değiştirmek istiyorsanız, **ayarları göster** listesinde, **tüm metin aracı Windows**' ni seçin.

1. **Yazı** tipi ve **Boyut** seçeneklerini değiştirerek IDE için yazı tipini ve metin boyutunu değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

::: moniker-end

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Düzenleyicideki yazı tipini ve metin boyutunu değiştirmek için

::: moniker range=">=vs-2022"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin.

   ![Düzenleyicide yazı tipini ve metin boyutunu değiştirdiğiniz Seçenekler iletişim kutusunun ekran görüntüsü](media/vs-2022/fonts-colors-text-editor.png "Düzenleyicide yazı tipini ve metin boyutunu değiştirdiğiniz Seçenekler iletişim kutusunun ekran görüntüsü.")

1. Düzenleyicinin yazı tipini ve metin boyutunu değiştirmek için **yazı tipi** ve **Boyut** seçeneklerini değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

::: moniker-end

::: moniker range="<=vs-2019"

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam** > **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin.

   ![Düzenleyicideki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü](media/fonts-colors-text-editor.png "Düzenleyicideki yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü.")

1. Düzenleyicinin yazı tipini ve metin boyutunu değiştirmek için **yazı tipi** ve **Boyut** seçeneklerini değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

::: moniker-end

Daha fazla bilgi için bkz. [Düzenleyici için yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) sayfası.

## <a name="accessibility-options"></a>Erişilebilirlik seçenekleri

::: moniker range="vs-2022"

Bir neurodiverse dünyasında, aşağıdaki yazı tipi seçeneklerini ve renk temalarını sunarak farklı öğrenimlerimizi ve düşük Vision kullanıcılarınızı desteklemek istiyoruz:

- Basamakların belirsizliğini sağlamaya yardımcı olmak için harflerin, rakamların ve karakterlerin oranlarına daha fazla ağırlık ekleyen [basamaklı Dia kod](#use-the-cascadia-code-font) yazı tipini kullanabilirsiniz. Basamaklı Dia kodu, kodlarda harflerin de içerir.
- bir bilgisayardaki *tüm* uygulamalar ve kullanıcı arabirimi ya da yalnızca Visual Studio için [çok karşıtlıklı](#use-visual-studio-extra-contrast) bir renk teması için [yüksek karşıtlıklı](#use-windows-high-contrast) bir renk teması kullanmayı tercih edebilirsiniz.

### <a name="use-the-cascadia-code-font"></a>Basamaklı Dia kod yazı tipini kullanın

yeni [**basamaklı dia kodu**](https://github.com/microsoft/cascadia-code#welcome) yazı tipi, Visual Studio 2022 ' de varsayılan yazı tipi olan **Cascade Mono** içerir. Bu fontların her ikisi de daha kolay okunmamalıdır, ancak basamaklı Dia Code yazı tipi bir karakter dizisini bir glife dönüştürmek için kodharfler içerir. Büyük harfleri veya glifleri kodlayarak kişilerin bunların arkasındaki anlamı daha canlı bir şekilde ilişkilendirebilmesini kolaylaştırır.

Aşağıdaki ekran görüntüsünde, varsayılan basamaklı bir mono yazı tipinin örneği gösterilmektedir ve siz kodlarken kullanarak kendiniz bulabileceğiniz matematik sembolleri dahil etmek için bir dizi karakter listelenir.

:::image type="content" source="media/vs-2022/cascadia-mono-font.png" alt-text="Düzenleyicide basamaklı Dia mono yazı tipine bir örnek ekran görüntüsü.":::

Aşağıdaki ekran görüntüsünde, daha önce gösterilen aynı karakter dizisinin, şimdi kodlama veya Glifler olarak dönüştürülebildiği basamaklı Dia kod yazı tipinin bir örneği gösterilmektedir.

:::image type="content" source="media/vs-2022/cascadia-code-font.png" alt-text="Düzenleyicideki basamaklı Dia kod yazı tipine örnek ekran görüntüsü.":::

Basamaklı Dia kodu ekran görüntüsündeki metnin son satırının, yinelenen karakterler arasındaki alanın nasıl azaldığına ve ayrıca daha kolay okunmasını sağlar.

Basamaklı Dia yazı tipleri arasında nasıl geçiş yapılacağı aşağıda verilmiştir:

1. **Araçlar** > **Seçenekler** > **ortam** > **yazı tipleri ve renkler** bölümüne gidin.

1. **Yazı tipi** açılan listesinden, Istediğiniz **basamaklı Dia kodu** yazı tipini veya **basamaklı Dia mono** yazı tipini seçin ve **Tamam**' ı seçin.

    :::image type="content" source="media/vs-2022/cascadia-font-options.png" alt-text="Seçenekler iletişim kutusunda kullanılabilen basamaklı Dia yazı tiplerinin ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

Görme zorluğu yaşıyorsanız, sizin için renk teması seçenekleri vardır. bir bilgisayardaki *tüm* uygulamalar ve kullanıcı arabirimi veya yalnızca Visual Studio için ek karşıtlık seçeneği için yüksek karşıtlıklı bir seçenek kullanabilirsiniz.

::: moniker-end

### <a name="use-windows-high-contrast"></a>Windows yüksek karşıtlık kullanın

Windows yüksek karşıtlık seçeneğini değiştirmek için aşağıdaki yordamlardan birini kullanın:

- Windows veya herhangi bir Microsoft uygulamasında **sol Alt** + **sol shıft** + **PrtScn** tuşlarına basın.

- Windows ' de, **başlat**  >  **Ayarlar**  >  **erişim kolaylığı**' nı seçin. ardından, Windows 10 ve sonraki bölümlerinde bulunan **vizyon** bölümünde **yüksek karşıtlık**' ı seçin.

    > [!WARNING]
    > Windows yüksek karşıtlık ayarı, bilgisayardaki tüm uygulamaları ve kullanıcı arabirimini etkiler.

### <a name="use-visual-studio-extra-contrast"></a>Visual Studio daha fazla karşıtlık kullanın

Visual Studio ekstra karşıtlık seçeneğini değiştirmek için aşağıdaki yordamları kullanın:

1. Visual Studio menü çubuğunda **araçlar**  >  **seçenekler**' i seçin ve ardından seçenekler listesinde **ortam**  >  **genel**' i seçin.

1. **Renk teması** açılan listesinde **mavi (ekstra kontrast)** temasını seçin ve ardından **Tamam**' ı seçin.

kullanabileceğiniz diğer Visual Studio erişilebilirlik seçenekleri hakkında daha fazla bilgi edinmek için [Visual Studio sayfasının erişilebilirlik özelliklerine](../ide/reference/accessibility-features-of-visual-studio.md) bakın.

> [!TIP]
> istediğiniz renk veya yazı tipi için erişilebilirlik seçeneği varsa, ancak şu anda Visual Studio kullanılabilir değil, lütfen [Visual Studio geliştirici Community](https://aka.ms/feedback/suggest?space=8) **bir özellik öner** ' i seçerek bize bildirin. Bu forum ve nasıl çalıştığı hakkında daha fazla bilgi için, [özellik önerme](../ide/suggest-a-feature.md) sayfasına bakın.

## <a name="next-steps"></a>Sonraki adımlar

Yazı tipi ve renk düzenlerini değiştirebileceğiniz tüm Kullanıcı arabirimi (UI) öğeleri hakkında daha fazla bilgi edinmek için, bkz. [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Studio düzenleyicide düzenleyici için yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Visual Studio kodu düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Visual Studio ıde ve düzenleyiciyi kişiselleştirin](../ide/quickstart-personalize-the-ide.md)
