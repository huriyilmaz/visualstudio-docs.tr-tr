---
title: Erişilebilirlik için temaları, yazı tiplerini, metni ve karşıtlığı değiştirme
description: kullanım kolaylığı ve erişilebilirlik sorunları için Visual Studio renk temalarını, yazı tipi renklerini, metin boyutlarını ve çok karşıtlıklı renkleri değiştirmeyi öğrenin.
ms.date: 12/17/2020
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
ms.openlocfilehash: fc40b2200f360f42e5276f36586714e90aabf87a
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430540"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Nasıl yapılır: Visual Studio yazı tiplerini, renkleri ve temaları değiştirme

Visual Studio yazı tiplerini ve renkleri birçok şekilde değiştirebilirsiniz. Örneğin, varsayılan mavi renk temasını koyu Tema ("koyu mod" olarak da adlandırılır) olarak değiştirebilirsiniz. Gereksinimlerinize en uygun olan bir ek kontrast teması da seçebilirsiniz. Hem IDE hem de kod düzenleyicisinde varsayılan yazı tipini ve metin boyutunu değiştirebilirsiniz.

## <a name="change-the-color-theme"></a>Renk temasını değiştirme

Visual Studio içindeki IDE çerçevesinin ve araç pencerelerinin renk temasını değiştirme.

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam**  >  **genel**' i seçin.

1. **Renk teması** listesinde, varsayılan **mavi** temayı, **ışık** temasını, **koyu** temayı veya **mavi (ekstra Karşıtlık)** temasını seçin.

   ![Renk temasını değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-theme.png "Renk temasını değiştirmek için kullanabileceğiniz seçenekler iletişim kutusunun ekran görüntüsü")

    > [!NOTE]
    > Bir renk temasını değiştirdiğinizde, IDE 'deki metin, bu temanın varsayılan veya daha önce özelleştirilmiş yazı tiplerine ve boyutlarına geri döner.

    :::moniker range="vs-2017"

    > [!TIP]
    > [Visual Studio 2017 için renk teması düzenleyicisini](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)yükleyerek kendi Visual Studio temalarınızı oluşturabilir ve düzenleyebilirsiniz.

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > [Visual Studio Color teması tasarımcısını](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)yükleyerek kendi Visual Studio temalarınızı oluşturabilir ve düzenleyebilirsiniz.

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Yazı tiplerini ve metin boyutunu değiştirme

Tüm IDE çerçevesi ve araç pencereleri için ya da yalnızca belirli pencereler veya metin öğeleri için yazı tipi ve metin boyutunu değiştirebilirsiniz. Ayrıca, düzenleyicideki yazı tipini ve metin boyutunu da değiştirebilirsiniz.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>IDE 'deki yazı tipini ve metin boyutunu değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam**  >  **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde **ortam**' ı seçin.

   ![IDE 'deki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü](media/fonts-colors-environment.png "IDE 'deki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü")

    > [!NOTE]
    > Yalnızca araç pencerelerinin yazı tipini değiştirmek istiyorsanız, **ayarları göster** listesinde, **tüm metin aracı Windows**' ni seçin.

1. **Yazı** tipi ve **Boyut** seçeneklerini değiştirerek IDE için yazı tipini ve metin boyutunu değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Düzenleyicideki yazı tipini ve metin boyutunu değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam**  >  **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin.

   ![Düzenleyicideki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü](media/fonts-colors-text-editor.png "Düzenleyicideki yazı tiplerini ve renkleri değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü")

1. Düzenleyicinin yazı tipini ve metin boyutunu değiştirmek için **yazı tipi** ve **Boyut** seçeneklerini değiştirin.

1. **Görüntüleme öğelerinde** uygun öğeyi seçin ve ardından **öğe ön** planı ve **öğe arka plan** seçeneklerini değiştirin.

Daha fazla bilgi için bkz. [Düzenleyici için yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) sayfası.

## <a name="accessibility-options"></a>Erişilebilirlik seçenekleri

Görme zorluğu yaşıyorsanız, sizin için renk teması seçenekleri vardır. bir bilgisayardaki *tüm* uygulamalar ve kullanıcı arabirimi veya yalnızca Visual Studio için ek karşıtlık seçeneği için yüksek karşıtlıklı bir seçenek kullanabilirsiniz.

### <a name="use-windows-high-contrast"></a>Windows yüksek karşıtlık kullanın

Windows yüksek karşıtlık seçeneğini değiştirmek için aşağıdaki yordamlardan birini kullanın:

- Windows veya herhangi bir Microsoft uygulamasında **sol Alt** + **sol shıft** + **PrtScn** tuşlarına basın.

- Windows ' de,   >    >    >  **yüksek karşıtlık** Ayarlar erişim kolaylığı ' nı seçin.

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
