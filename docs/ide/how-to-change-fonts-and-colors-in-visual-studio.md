---
title: Erişilebilirlik için temaları, yazı tiplerini, metni ve karşıtlığı değiştirme
description: Visual Studio renk temalarını, yazı tipi renklerini, metin boyutlarını ve çok karşıtlıklı renkleri kullanarak kullanım kolaylığı ve erişilebilirlik sorunları için nasıl değiştirileceğini öğrenin.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c52be25c007a16d7e6221663c434767c02d8d50
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683904"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da yazı tiplerini, renkleri ve temaları değiştirme

Visual Studio 'daki yazı tiplerini ve renkleri birçok şekilde değiştirebilirsiniz. Örneğin, varsayılan mavi renk temasını koyu Tema ("koyu mod" olarak da adlandırılır) olarak değiştirebilirsiniz. Gereksinimlerinize en uygun olan bir ek kontrast teması da seçebilirsiniz. Hem IDE hem de kod düzenleyicisinde varsayılan yazı tipini ve metin boyutunu değiştirebilirsiniz.

## <a name="change-the-color-theme"></a>Renk temasını değiştirme

Visual Studio 'daki IDE çerçevesinin ve araç pencerelerinin renk temasını değiştirme.

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam**  >  **genel**' i seçin.

1. **Renk teması** listesinde, varsayılan **mavi** temayı, **ışık** temasını, **koyu** temayı veya **mavi (ekstra Karşıtlık)** temasını seçin.

   ![Renk temasını değiştirmek için Seçenekler iletişim kutusunun ekran görüntüsü](media/fonts-colors-theme.png "Renk temasını değiştirmek için kullanabileceğiniz seçenekler iletişim kutusunun ekran görüntüsü")

    > [!NOTE]
    > Bir renk temasını değiştirdiğinizde, IDE 'deki metin, bu temanın varsayılan veya daha önce özelleştirilmiş yazı tiplerine ve boyutlarına geri döner.

    :::moniker range="vs-2017"

    > [!TIP]
    > [Visual studio 2017 Için renk teması düzenleyicisini](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)yükleyerek kendi Visual Studio temalarınızı oluşturabilir ve düzenleyebilirsiniz.

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > [Visual Studio Color teması tasarımcısını](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)yükleyerek kendi Visual Studio temaları oluşturabilir ve düzenleyebilirsiniz.

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Yazı tiplerini ve metin boyutunu değiştirme

Tüm IDE çerçevesi ve araç pencereleri için ya da yalnızca belirli pencereler veya metin öğeleri için yazı tipi ve metin boyutunu değiştirebilirsiniz. Ayrıca, düzenleyicideki yazı tipini ve metin boyutunu da değiştirebilirsiniz.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>IDE 'deki yazı tipini ve metin boyutunu değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. Seçenekler listesinde **ortam**  >  **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster** listesinde **ortam**' ı seçin.

   ![IDE 'deki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü](media/fonts-colors-environment.png "IDE 'deki yazı tiplerini ve renkleri değiştirme seçenekleri iletişim kutusunun ekran görüntüsü")

    > [!NOTE]
    > Yalnızca araç pencerelerinin yazı tipini değiştirmek istiyorsanız, **ayarları göster** listesinde, **tüm metin araç pencereleri**' ni seçin.

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

Görme zorluğu yaşıyorsanız, sizin için renk teması seçenekleri vardır. Bir bilgisayardaki *Tüm* uygulamalar ve Kullanıcı arabirimi ya da yalnızca Visual Studio için daha fazla karşıtlık seçeneği için yüksek karşıtlıklı bir seçenek kullanabilirsiniz.

### <a name="use-windows-high-contrast"></a>Windows yüksek karşıtlığı kullan

Windows yüksek karşıtlık seçeneğini değiştirmek için aşağıdaki yordamlardan birini kullanın:

- Windows veya herhangi bir Microsoft uygulamasında **sol alt** + **Sol SHIFT** + **PrtScn** tuşlarına basın.

- Windows 'ta, **Başlangıç**  >  **ayarları**  >  **kolay erişim kolaylığı**  >  **yüksek karşıtlık**' ı seçin.

    > [!WARNING]
    > Windows yüksek karşıtlık ayarı bilgisayardaki tüm uygulamaları ve Kullanıcı arabirimini etkiler.

### <a name="use-visual-studio-extra-contrast"></a>Visual Studio ekstra kontrastını kullanın

Visual Studio fazladan karşıtlık seçeneğini değiştirmek için aşağıdaki yordamları kullanın:

1. Visual Studio 'daki menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin ve ardından Seçenekler listesinde **ortam**  >  **genel**' i seçin.

1. **Renk teması** açılan listesinde **mavi (ekstra kontrast)** temasını seçin ve ardından **Tamam**' ı seçin.

Kullanabileceğiniz diğer Visual Studio erişilebilirlik seçenekleri hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md) sayfası.

> [!TIP]
> Yararlı olabilecek ancak Visual Studio 'da Şu anda kullanılamayan renkler veya yazı tiplerinde erişilebilirlik seçeneği varsa lütfen [Visual Studio Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)'nda **bir özellik öner** ' i seçerek bize bildirin. Bu forum ve nasıl çalıştığı hakkında daha fazla bilgi için, [özellik önerme](../ide/suggest-a-feature.md) sayfasına bakın.

## <a name="next-steps"></a>Sonraki adımlar

Yazı tipi ve renk düzenlerini değiştirebileceğiniz tüm Kullanıcı arabirimi (UI) öğeleri hakkında daha fazla bilgi edinmek için, bkz. [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Studio 'da düzenleyici için yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Visual Studio kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Visual Studio IDE ve düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md)
