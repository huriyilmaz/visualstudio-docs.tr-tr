---
title: Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler
description: Tüm Diller bölümündeki Sekmeler sayfasını kullanarak kod düzenleyicisi sekmelerinin varsayılan davranışını değiştirme hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e3d984fe1c20ae5eb036a60e6e2b2e6db23890a72a633d33946463f0bcd61034
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372341"
---
# <a name="options-text-editor-all-languages-tabs"></a>Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler

Bu iletişim kutusu, Kod Düzenleyicisi'nin varsayılan davranışını değiştirmenizi sağlar. Bu ayarlar, HTML Tasarımcısı'nın Kaynak görünümü gibi Kod Düzenleyicisi'ni temel alan diğer düzenleyiciler için de geçerlidir. Bu seçenekleri görüntülemek için Araçlar **menüsünden** **Seçenekler'i** seçin. Metin Düzenleyici **klasöründe Tüm** Diller alt **klasörünü genişletin** ve sekmeler'i **seçin.**

> [!CAUTION]
> Bu sayfa, tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneğin sıfırlanması, tüm dillerdeki Sekme seçeneklerini burada seçilen seçeneklere sıfırlar. Yalnızca bir dil için Metin Düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörlerini genişletin ve seçenek sayfalarını seçin.

Belirli programlama dillerinin Sekme seçenekleri sayfalarında farklı ayarlar seçilirse, farklı Girintileme seçenekleri için "Tek tek metin biçimleri için girintileme ayarları çakışıyor" iletisi **görüntülenir.** ve "Tek tek metin biçimleri için sekme ayarları çakışıyor" iletisi, farklı Sekme seçenekleri **için** görüntülenir. Örneğin, bu anımsatıcı,  Visual Basic için Akıllı girintileme seçeneği Visual C++. 

## <a name="indenting"></a>Girintileme

Hiçbiri

Seçildiğinde, yeni satırlar girintilemez. Ekleme noktası yeni bir satırın ilk sütununa yerleştirilir.

Blok

Seçildiğinde, yeni satırlar otomatik olarak girintilenir. Ekleme noktası, önceki satırla aynı başlangıç noktasına yerleştirilir.

Akıllı

Seçildiğinde, yeni satırlar kod bağlamına uyacak şekilde, diğer kod biçimlendirme ayarlarına ve geliştirme diliniz için IntelliSense kurallarına göre konumlandırıldı. Bu seçenek tüm geliştirme dillerinde kullanılamaz.

Örneğin, bir açma ayracı ( { ) ve kapanış ayracı ( } ) arasına alınmış satırlar, hizalanmış ayraçların konumundan ek bir sekme durdurması otomatik olarak girintilenir.

## <a name="tabs"></a>Sekmeler

Sekme boyutu

Sekme durakları arasındaki mesafeyi boşluk olarak ayarlar. Varsayılan değer dört alandır.

Girinti boyutu

Boyutu otomatik girinti boşluklarında ayarlar. Varsayılan değer dört alandır. Belirtilen boyutu doldurmak için sekme karakterleri, boşluk karakterleri veya her ikisi de eklenir.

Boşluk ekleme

Seçildiğinde, girintileme işlemleri SEKME karakterleri değil yalnızca boşluk karakterleri ekler. Girinti **boyutu örneğin** 5 olarak ayarlanırsa, SEKME tuşuna veya Biçimlendirme araç çubuğundaki Girintiyi Artır düğmesine her bastığınızda beş boşluk **karakteri** eklenir. 

Sekmeleri izleyin

Seçildiğinde, girintileme işlemleri mümkün olduğunca çok SEKME karakteri ekler. Her SEKME karakteri, Sekme boyutu'da belirtilen boşluk **sayısını doldurur.** Girinti **boyutu Sekme** boyutunun katları arasında **yer alamasa,** aradaki farkı doldurmak için boşluk karakterleri eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
