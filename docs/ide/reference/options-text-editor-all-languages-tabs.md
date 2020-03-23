---
title: Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc169960cf757e4e334d5f77b06ff70b0d6da7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594753"
---
# <a name="options-text-editor-all-languages-tabs"></a>Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler

Bu iletişim kutusu, Kod Düzenleyicisi'nin varsayılan davranışını değiştirmenize olanak tanır. Bu ayarlar, HTML Tasarımcısı'nın Kaynak görünümü gibi Kod Düzenleyicisi'ni temel alan diğer düzenleyiciler için de geçerlidir. Bu seçenekleri görüntülemek için **Araçlar** menüsünden **Seçenekler'i** seçin. Metin **Düzenleyicisi** klasöründe **Tüm Diller** alt klasörünü genişletin ve ardından **Sekmeleri**seçin.

> [!CAUTION]
> Bu sayfa, tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneği sıfırlamanın, tüm dillerdeki Sekmeseçeneklerini burada seçilecek seçeneklere sıfırlayacak olduğunu unutmayın. Metin Düzenleyicisi seçeneklerini yalnızca bir dil için değiştirmek için, söz sözlere dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

Belirli programlama dilleri için Sekmeler seçenekleri sayfalarında farklı ayarlar seçilirse, farklı **Girinti** seçenekleri için "Tek tek metin biçimlerinin girinti ayarları birbiriyle çakışıyor" iletisi görüntülenir; ve "Tek tek metin biçimlerinin sekme ayarları birbiriyle çakışıyor" iletisi, farklı **Sekme** seçenekleri için görüntülenir. Örneğin, Visual Basic için **Akıllı girinti** seçeneği seçilirse, ancak Visual C++için **Blok girintisi** seçilirse bu anımsatıcı görüntülenir.

## <a name="indenting"></a>Girintileme

None

Seçildiğinde, yeni satırlar girintisi değildir. Ekleme noktası yeni bir satırın ilk sütununa yerleştirilir.

Blok

Seçildiğinde, yeni satırlar otomatik olarak girintilir. Ekleme noktası, önceki satırla aynı başlangıç noktasına yerleştirilir.

Akıllı

Seçildiğinde, geliştirme diliniz için diğer kod biçimlendirme ayarlarına ve IntelliSense kurallarına göre kod bağlamına uyacak şekilde yeni satırlar konumlandırılır. Bu seçenek tüm geliştirme dilleri için kullanılamaz.

Örneğin, bir açılış ayracı ( { ) ve kapanış ayracı ( } ) arasında kaplanmış çizgiler, hizalanmış ayraçların konumundan otomatik olarak eksek durağı olarak girintilenebilir.

## <a name="tabs"></a>Sekmeler

Sekme boyutu

Sekme durakları arasındaki boşluklardaki mesafeyi ayarlar. Varsayılan dört boşluk.

Girintisi boyutu

Boyutu otomatik girintinin boşluklarında ayarlar. Varsayılan dört boşluk. Sekme karakterleri, boşluk karakterleri veya her ikisi belirtilen boyutu doldurmak için eklenir.

Boşluk ekleme

Seçili olduğunda, girintisi işlemleri TAB karakterleri değil, yalnızca boşluk karakterleri ekleyin. **Girinti boyutu** 5 olarak ayarlanmışsa, örneğin, TAB tuşuna veya **Biçimlendirme** araç çubuğundaki **Girinti artır** düğmesine her bastığınızda beş boşluk karakteri eklenir.

Sekmeleri izleyin

Seçildiğinde, girintin işlemleri mümkün olduğunca çok SAYıDA TAB karakteri ekleyin. Her SEKME **karakteri, Sekme boyutunda**belirtilen boşluk sayısını doldurur. **Girintisi boyutu** **Sekme boyutunun**çift katı değilse, boşluğu doldurmak için boşluk karakterleri eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
