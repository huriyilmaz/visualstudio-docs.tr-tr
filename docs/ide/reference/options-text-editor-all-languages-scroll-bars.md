---
title: Seçenekler, Metin Düzenleyicisi, Tüm Diller, Kaydırma Çubukları
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54ce07537adc436f719de8596657d1367afcb87d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588804"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Seçenekler, Metin Düzenleyicisi, Tüm Diller, Kaydırma Çubukları
Bu iletişim kutusu, kod düzenleyicisi kaydırma çubuğunun varsayılan davranışını değiştirmenizi sağlar. Bu seçenekleri görüntülemek için **Araçlar** menüsünden **Seçenekler'i** seçin. Metin **Düzenleyicisi** klasöründe, **Tüm Diller** alt klasörünü genişletin ve ardından **Çubuklar Kaydırma'yı**seçin.

> [!CAUTION]
> Bu sayfa, tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneği sıfırlamak, tüm dillerdeki Kaydırma Çubukları seçeneklerini burada seçilecek seçeneklere sıfırlar. Metin Düzenleyicisi seçeneklerini yalnızca bir dil için değiştirmek için, söz sözlere dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

## <a name="show-horizontal-scroll-bar"></a>Yatay kaydırma çubuğugöster

Seçildiğinde, Düzenleyici'nin görüntüleme alanının dışına düşen öğeleri görüntülemek için yan yana kaydırma yapmanızı sağlayan yatay bir kaydırma çubuğu görüntüler. Yatay kaydırma çubukları kullanılamıyorsa, kaydırma yapmak için imleç tuşlarını kullanabilirsiniz.

## <a name="show-vertical-scroll-bar"></a>Dikey kaydırma çubuğugöster

Seçildiğinde, Düzenleyici'nin görüntüleme alanının dışına düşen öğeleri görüntülemek için yukarı ve aşağı kaydırmanızı sağlayan dikey bir kaydırma çubuğu görüntüler. Dikey kaydırma çubukları yoksa, kaydırmak için Sayfa Yukarı, Sayfa Aşağı ve imleç tuşlarını kullanabilirsiniz.

## <a name="display"></a>Ekran

### <a name="show-annotations-over-vertical-scroll-bar"></a>Dikey kaydırma çubuğuüzerinde ek açıklamaları göster

Dikey kaydırma çubuğunun aşağıdaki ek açıklamaları gösterip göstermeyeceğini seçin:

- değişiklikler
- işaretler
- hatalar
- caret pozisyonu

> [!TIP]
> **İşaretleri Göster** seçeneği kesme noktalarını ve yer imlerini içerir.

Büyük bir kod dosyasını açarak ve dosyanın çeşitli yerlerinde oluşan bazı metinleri değiştirerek deneyin. Kaydırma çubuğu değiştirmelerin etkisini gösterir, böylece değiştirmemeniz gereken bir şeyi değiştirirseniz değişikliklerinizi geri çekebilirsiniz.

Kodu düzenlerken çeşitli renk ve sembollerin ne anlama geldiğini niçin [yaptığıgelişmiş kaydırma çubuğu](https://blogs.msdn.microsoft.com/cdnstudents/2014/01/21/visual-studio-tips-and-tricks-enhanced-scroll-bar/) blog gönderisini görün.

## <a name="behavior"></a>Davranış

Kaydırma çubuğunun iki modu vardır: çubuk modu ve harita modu.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için çubuk modunu kullanma

*Çubuk modu* kaydırma çubuğunda ek açıklama göstergelerini görüntüler. Kaydırma çubuğuna tıkladığınızda sayfa yukarı veya aşağı kaydırılır, ancak dosyadaki o konuma atlamaz.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için harita modunu kullanma

*Harita modunda,* kaydırma çubuğundaki bir konumu tıklattığınızda, imleç bir sayfayı yukarı veya aşağı kaydırmak yerine dosyadaki o konuma atlar. Kod satırları, kaydırma çubuğunda minyatür olarak gösterilir. **Kaynak'a genel bakış'ta**bir değer seçerek harita sütununne ne kadar geniş olduğunu seçebilirsiniz. İşaretçiyi haritada dinlendirdiğinizde kodun daha büyük bir önizlemesini etkinleştirmek için **Önizleme Araç İpucu** seçeneğini belirleyin. Daraltılmış bölgeler farklı şekilde gölgelenir ve çift tıklattığınızda genişletilir.

> [!TIP]
> **Kaynak genel görünümünü** **Kapalı**olarak ayarlayarak harita modunda minyatür kod görünümünü kapatabilirsiniz. **Önizleme Araç İpucunu Göster** seçilirse, işaretçinizin kaydırma çubuğunda gezinmesini yaptığınızda o konumda kodun önizlemesini görmeye devam edeyim ve bunu tıklattığınızda imleç yine de dosyadaki o konuma atlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılsın: Kaydırma çubuğunu özelleştirin](../how-to-track-your-code-by-customizing-the-scrollbar.md)
