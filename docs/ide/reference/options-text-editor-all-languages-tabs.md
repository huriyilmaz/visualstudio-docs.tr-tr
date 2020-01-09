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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594753"
---
# <a name="options-text-editor-all-languages-tabs"></a>Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler

Bu iletişim kutusu, kod düzenleyicisinin varsayılan davranışını değiştirmenize izin verir. Bu ayarlar ayrıca, HTML tasarımcısının kaynak görünümü gibi kod düzenleyicisine dayalı diğer düzenleyiciler için de geçerlidir. Bu seçenekleri göstermek için, **Araçlar** menüsünden **Seçenekler** ' i seçin. **Metin Düzenleyicisi** klasörü Içinde **tüm diller** alt klasörünü genişletin ve ardından **Sekmeler**' i seçin.

> [!CAUTION]
> Bu sayfa tüm geliştirme dillerinin varsayılan seçeneklerini ayarlar. Bu iletişim kutusunda bir seçeneğin sıfırlanması, burada seçili olan seçimler için tüm dillerdeki sekmeler seçeneklerini sıfırlayacaktır. Yalnızca bir dile ait metin düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

Belirli programlama dilleri için sekmeler seçenekler sayfalarında farklı ayarlar seçilirse, "tekil metin biçimleri için girinti ayarları birbirleriyle çakışıyor" iletisi, farklı **girintileme** seçenekleri için görüntülenir; ve "tekil metin biçimleri için sekme ayarları birbirleriyle çakışıyor" iletisi, farklı **sekme** seçenekleri için görüntülenir. Örneğin, **akıllı girintileme** seçeneği Visual Basic için seçilmişse bu anımsatıcı görüntülenir, ancak görsel C++için **blok girintileme** seçilidir.

## <a name="indenting"></a>Girintileme

Yok.

Seçildiğinde, yeni satırlar girintili değildir. Ekleme noktası yeni bir satırın ilk sütununa yerleştirilir.

Blok

Seçildiğinde, yeni satırlar otomatik olarak girintilenir. Ekleme noktası, önceki satır ile aynı başlangıç noktasına yerleştirilir.

Akıllı

Seçildiğinde, yeni satırlar kod bağlamına sığacak şekilde konumlandırılır, diğer kod biçimlendirme ayarları ve geliştirme diliniz için IntelliSense kuralları kullanılır. Bu seçenek tüm geliştirme dilleri için kullanılamaz.

Örneğin, bir açma küme ayracı ({) ve bir kapanış ayracı (}) arasına alınmış satırlar otomatik olarak hizalı küme ayraçlarının konumundan fazladan bir sekme durağı girintili olabilir.

## <a name="tabs"></a>Sekmeler

Sekme boyutu

Sekme duraklarının boşluk cinsinden uzaklığını ayarlar. Varsayılan değer dört boşluklardan oluşamaz.

Boyut Girintile

Boyutu otomatik girintide boşluk olarak ayarlar. Varsayılan değer dört boşluklardan oluşamaz. Belirtilen boyutu dolduracak şekilde sekme karakterleri, boşluk karakterleri veya her ikisi de eklenir.

Boşluk Ekle

Seçildiğinde, girinti işlemleri sekme karakterleri değil yalnızca boşluk karakterleri ekler. Örneğin, **girinti boyutu** 5 olarak AYARLANDıYSA, sekme tuşuna veya **biçimlendirme** araç çubuğundaki **Girintiyi Artır** düğmesine her bastığınızda beş boşluk karakteri eklenir.

Sekmeleri izleyin

Seçildiğinde, Girintile işlemleri mümkün olduğunca çok sekme karakteri ekler. Her sekme karakteri, **sekme boyutunda**belirtilen boşluk sayısını doldurur. **Girinti boyutu** **sekme boyutunun**Çift katı değilse, farkı dolduracak şekilde boşluk karakterleri eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
