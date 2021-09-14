---
title: Seçenekler, Metin Düzenleyici, Tüm Diller, Kaydırma Çubukları
description: Kod düzenleyicisi kaydırma çubuklarının varsayılan davranışını değiştirmek için Tüm Diller bölümündeki Kaydırma Çubukları sayfasını kullanmayı Visual Studio.
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
ms.openlocfilehash: 111fd2231d775b4c69c7510568c8a9aea5e97188
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627201"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Seçenekler, Metin Düzenleyici, Tüm Diller, Kaydırma Çubukları
Bu iletişim kutusu, kod düzenleyicisi kaydırma çubuğunun varsayılan davranışını değiştirmenizi sağlar. Bu seçenekleri görüntülemek için Araçlar **menüsünden** **Seçenekler'i** seçin. Metin Düzenleyici **klasöründe** Tüm Diller alt **klasörünü genişletin** ve Ardından Kaydırma Çubukları'ı **seçin.**

> [!CAUTION]
> Bu sayfa tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneğin sıfırlanması, tüm dillerdeki Kaydırma Çubukları seçeneklerini burada seçilen seçeneklere sıfırlar. Yalnızca bir dil için Metin Düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörlerini genişletin ve seçenek sayfalarını seçin.

## <a name="show-horizontal-scroll-bar"></a>Yatay kaydırma çubuğunu göster

Seçildiğinde, Düzenleyici'nin görüntüleme alanı dışına düşen öğeleri görüntülemek için yan yana kaydırma sağlayan bir yatay kaydırma çubuğu görüntüler. Yatay kaydırma çubuğu kullanılamıyorsa, kaydırmak için imleç tuşlarını kullanabilirsiniz.

## <a name="show-vertical-scroll-bar"></a>Dikey kaydırma çubuğunu göster

Seçildiğinde, Düzenleyici'nin görüntüleme alanı dışına düşen öğeleri görüntülemek için yukarı ve aşağı kaydırma sağlayan bir dikey kaydırma çubuğu görüntüler. Dikey kaydırma çubuğu kullanılamıyorsa sayfa yukarı, Sayfa Aşağı ve imleç tuşlarını kullanarak kaydırabilirsiniz.

## <a name="display"></a>Göster

### <a name="show-annotations-over-vertical-scroll-bar"></a>Ek açıklamaları dikey kaydırma çubuğu üzerinde gösterme

Dikey kaydırma çubuğunun aşağıdaki ek açıklamaları gösterip gösterir olmadığını seçin:

- değişiklikler
- işaretler
- hatalar
- caret konumu

> [!TIP]
> İşaretleri **göster** seçeneği kesme noktaları ve yer işaretleri içerir.

Büyük bir kod dosyası açarak ve dosyanın çeşitli yerlerinde oluşan bazı metinleri değiştirerek bunu deneyin. Kaydırma çubuğu, değiştirmelerin etkisini gösterir. Bu nedenle, değiştirme yapmamanız gereken bir şeyi değiştirmeniz gerekirse değişikliklerinizi geri çıkarabilirsiniz.

Kodu [düzenlerken çeşitli renklerin ve](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) simgelerin ne anlama geldiğinden ilgili Gelişmiş kaydırma çubuğu blog gönderisi'ne bakın.

## <a name="behavior"></a>Davranış

Kaydırma çubuğunun iki modu vardır: çubuk modu ve harita modu.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için çubuk modunu kullanma

*Çubuk modu,* kaydırma çubuğunda ek açıklama göstergeleri görüntüler. Kaydırma çubuğuna tıklarsanız sayfa yukarı veya aşağı kaydırılabilir ancak dosyada bu konuma atlanmaz.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için harita modunu kullanma

Harita *modunda,* kaydırma çubuğundaki bir konuma tıklarsanız, imleç bir sayfayı yukarı veya aşağı kaydırmak yerine dosyada o konuma atlar. Kayan çubukta kod satırları gösterilir. Kaynak genel bakış'ta bir değer seçerek eşleme sütununu ne kadar geniş **olduğunu seçebilirsiniz.** İşaretçiyi haritada dinleniyorken kodun daha büyük bir önizlemesini etkinleştirmek için Önizleme Araç **İpucu'nı Göster seçeneğini** belirleyin. Daraltılmış bölgeler farklı şekilde gölgelidir ve çift tıklarken genişler.

> [!TIP]
> Kaynak genel bakış ayarını Kapalı olarak ayarerek harita modunda kod görünümünü **kapatabilirsiniz.**  Önizleme **Araç** İpucu göster seçeneği seçiliyse, işaretçinizi kaydırma çubuğunun üzerine yerleştirerek ilgili konumda kodun önizlemesini görmeye devam edersiniz ve imleç, tıklarsanız dosyada o konuma atlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: Kaydırma çubuğunu özelleştirme](../how-to-track-your-code-by-customizing-the-scrollbar.md)