---
title: Seçenekler, metin düzenleyici, genel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662257"
---
# <a name="options-text-editor-general"></a>Seçenekler, Metin Düzenleyici, Genel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kod ve metin Düzenleyicisi için genel ayarları değiştirmenize olanak sağlar. Bu iletişim kutusunu göstermek için, **Araçlar** menüsünde **Seçenekler** ' e tıklayın, **metin düzenleyici** klasörünü genişletin ve ardından **genel**' e tıklayın.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Ayarlar
 Seçili olduğunda sürükle ve bırak metin düzenlemesi, metni seçerek ve fareyle geçerli belge veya başka bir açık belge içindeki başka bir konuma sürükleyerek metin taşımanızı sağlar.

 Seçili olduğunda otomatik sınırlayıcı vurgulama, parametreleri veya öğe-değer çiftlerini ve eşleşen küme ayraçlarını ayıran sınırlayıcı karakterler vurgulanır.

 Değişiklikleri izle kod Düzenleyicisi seçildiğinde, dosyanın en son kaydedduğundan bu yana değiştirilen kodu işaretlemek için seçim kenar boşluğunda dikey sarı bir çizgi görünür. Değişiklikleri kaydettiğinizde dikey satırlar yeşil olur.

 Varsayılan olarak imza olmadan UTF-8 kodlamasını otomatik algıla, düzenleyici, bayt sırası işaretlerini veya karakter kümesi etiketlerini arayarak kodlamayı algılar. Geçerli belgede hiçbiri bulunmazsa, kod Düzenleyicisi bayt dizilerini tarayarak UTF-8 kodlamasını otomatik algılamayı dener. Kodlamanın otomatik algılanmasını devre dışı bırakmak için bu seçeneği temizleyin.

## <a name="display"></a>Göster
 Seçim kenar boşluğu seçildiğinde, düzenleyicinin metin alanının sol kenarı üzerinde dikey bir kenar boşluğu görüntüler. Metnin tamamını seçmek için bu kenar boşluğuna tıklayabilir veya ardışık metin satırları seçmek için tıklayıp sürükleyebilirsiniz.

|Seçim kenar boşluğu|Seçim kenar boşluğu kapalı|
|-------------------------|--------------------------|
|![HTMLpageSelectionMarginOn ekran görüntüsü](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff ekran görüntüsü](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

 Gösterge kenar boşluğu seçildiğinde, düzenleyicinin metin alanının sol kenarının dışında dikey bir kenar boşluğu görüntüler. Bu kenar boşluğuna tıkladığınızda metinle ilgili bir simge ve araç Ipucu görünür. Örneğin, kesme noktası veya görev listesi kısayolları gösterge kenar boşluğunda görüntülenir. Gösterge kenar boşluğu bilgileri yazdırılmaz.

 Dikey kaydırma çubuğu seçildiğinde, düzenleyicinin görüntüleme alanının dışında kalan öğeleri görüntülemek için yukarı ve aşağı kaydırma yapmanıza olanak sağlayan dikey bir kaydırma çubuğu görüntülenir. Dikey kaydırma çubukları yoksa, kaydırmak için sayfa yukarı, sayfa aşağı ve imleç tuşlarını kullanabilirsiniz.

 Yatay kaydırma çubuğu seçildiğinde, düzenleyicinin görüntüleme alanının dışında kalan öğeleri görüntülemek için yan yana kaydırma yapmanıza olanak sağlayan bir yatay kaydırma çubuğu görüntüler. Yatay kaydırma çubukları kullanılamıyorsa, kaydırma yapmak için imleç tuşlarını kullanabilirsiniz.

 Geçerli satırı Vurgula seçildiğinde, imlecin bulunduğu kod satırının etrafında gri bir kutu görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.
 [Seçenekler, metin düzenleyici, tüm diller](../../ide/reference/options-text-editor-all-languages.md) [Seçenekler, metin düzenleyici, tüm diller, sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md) [Seçenekler, metin düzenleyici, dosya uzantısı](../../ide/reference/options-text-editor-file-extension.md) [klavye kısayollarını tanımlama ve özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) , [IntelliSense kullanarak](../../ide/using-intellisense.md) [düzenleyiciyi özelleştirme](../../ide/customizing-the-editor.md)
