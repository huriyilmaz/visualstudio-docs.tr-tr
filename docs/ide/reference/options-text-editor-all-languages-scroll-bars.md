---
title: Seçenekler, metin düzenleyici, tüm diller, kaydırma çubukları
description: Visual Studio içindeki kod düzenleyici kaydırma çubuklarının varsayılan davranışını değiştirmek için tüm diller bölümündeki kaydırma çubukları sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 49202672f46efa9a0102b46563c6a80c9ed475e31aee690be6ab19cfc8748c7c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372380"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Seçenekler, metin düzenleyici, tüm diller, kaydırma çubukları
Bu iletişim kutusu, kod Düzenleyicisi kaydırma çubuğunun varsayılan davranışını değiştirmenize olanak sağlar. Bu seçenekleri göstermek için, **Araçlar** menüsünden **Seçenekler** ' i seçin. **Metin Düzenleyicisi** klasörü Içinde **tüm diller** alt klasörünü genişletin ve ardından **kaydırma çubukları**' nı seçin.

> [!CAUTION]
> Bu sayfa tüm geliştirme dillerinin varsayılan seçeneklerini ayarlar. Bu iletişim kutusundaki bir seçeneğin sıfırlanması, burada seçili olan seçimlerin her birinde kaydırma çubuklarının seçeneklerini sıfırlayacaktır. Yalnızca bir dile ait metin düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

## <a name="show-horizontal-scroll-bar"></a>Yatay kaydırma çubuğunu göster

Seçildiğinde, düzenleyicinin görüntüleme alanının dışında kalan öğeleri görüntülemek için yan yana kaydırma yapmanıza olanak sağlayan bir yatay kaydırma çubuğu görüntüler. Yatay kaydırma çubukları kullanılamıyorsa, kaydırma yapmak için imleç tuşlarını kullanabilirsiniz.

## <a name="show-vertical-scroll-bar"></a>Dikey kaydırma çubuğunu göster

Seçildiğinde, düzenleyicinin görüntüleme alanının dışında kalan öğeleri görüntülemek için yukarı ve aşağı kaydırma yapmanıza olanak sağlayan dikey bir kaydırma çubuğu görüntüler. Dikey kaydırma çubukları yoksa, kaydırmak için sayfa yukarı, sayfa aşağı ve imleç tuşlarını kullanabilirsiniz.

## <a name="display"></a>Göster

### <a name="show-annotations-over-vertical-scroll-bar"></a>Dikey kaydırma çubuğunun üzerinde ek açıklamaları göster

Dikey kaydırma çubuğunun aşağıdaki ek açıklamaları gösterilip gösterilmeyeceğini seçin:

- değişiklikler
- işaretler
- hatalar
- şapka işareti konumu

> [!TIP]
> **Işaretleri göster** seçeneği kesme noktaları ve yer işaretleri içerir.

Büyük bir kod dosyası açarak ve dosyadaki birkaç yerde oluşan bazı metinleri değiştirerek deneyin. Kaydırma çubuğu, değişikliklerinizin etkisini gösterir. bu sayede, sahip olmayan bir şeyi değiştirdiyseniz değişikliklerinizi geri alabilirsiniz.

Kod düzenlenirken çeşitli renklerin ve simgelerin anlamı olan [Gelişmiş kaydırma çubuğu](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) blog gönderisine bakın.

## <a name="behavior"></a>Davranış

Kaydırma çubuğunun iki modu vardır: çubuk modu ve eşleme modu.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için çubuk modunu kullan

*Çubuk modu* , kaydırma çubuğundaki ek açıklama göstergelerini görüntüler. Kaydırma çubuğuna tıkladığınızda sayfa yukarı veya aşağı kaydırılır, ancak dosyadaki bu konuma atlamaz.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için eşleme modunu kullan

*Harita modunda*, kaydırma çubuğundaki bir konuma tıkladığınızda, imleç yalnızca bir sayfada yukarı veya aşağı kaydırmak yerine dosyada bu konuma atlar. Kod satırları, kaydırma çubuğunda küçük olarak gösterilir. Eşleme sütununun ne kadar geniş olduğunu seçerek **kaynak genel bakış**' da bir değer seçebilirsiniz. İşaretçiyi haritada tuttuğunuz zaman kodun daha büyük bir önizlemesini etkinleştirmek için **Önizleme araç Ipucunu göster** seçeneğini belirleyin. Daraltılmış bölgeler farklı şekilde genişleyebilir ve çift tıkladığınızda genişletilir.

> [!TIP]
> **Kaynak genel bakışını** **kapalı** olarak ayarlayarak, eşleme modunda küçük kod görünümünü kapatabilirsiniz. **Önizleme araç Ipucunu göster** seçiliyse, işaretçinizi kaydırma çubuğunun üzerine getirdiğinizde bu konumdaki kodun önizlemesini görmeye devam edersiniz ve imleç, tıkladığınızda dosyada bu konuma atlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: kaydırma çubuğunu özelleştirme](../how-to-track-your-code-by-customizing-the-scrollbar.md)