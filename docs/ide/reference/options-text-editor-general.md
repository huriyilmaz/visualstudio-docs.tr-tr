---
title: Seçenekler, Metin Düzenleyici, Genel
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebe526bbac859777edb4c2c78c65a1cdbd27fc85
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568418"
---
# <a name="options-dialog-box-text-editor--general"></a>Seçenekler iletişim kutusu: metin Düzenleyicisi \> genel

Bu iletişim kutusu, Visual Studio kodu ve metin Düzenleyicisi için genel ayarları değiştirmenize olanak sağlar. Bu iletişim kutusunu göstermek için, **Araçlar** menüsünde **Seçenekler** ' i seçin, **metin düzenleyici** klasörünü genişletin ve ardından **genel**' i seçin.

## <a name="settings"></a>Ayarlar

### <a name="drag-and-drop-text-editing"></a>Sürükle ve bırak metin düzenlemesi

Seçildiğinde, metni seçip fareyle geçerli belge veya başka bir açık belge içindeki başka bir konuma sürükleyerek metni taşımanızı sağlar.

### <a name="automatic-delimiter-highlighting"></a>Otomatik sınırlayıcı vurgulama

Seçildiğinde, parametreleri veya öğe-değer çiftlerini ve eşleşen küme ayraçlarını ayıran sınırlayıcı karakterler vurgulanır.

### <a name="track-changes"></a>Değişiklikleri izleme

Kod Düzenleyicisi seçildiğinde, dosyanın en son kaydedduğundan bu yana değiştirilen kodu işaretlemek için seçim kenar boşluğunda dikey sarı bir çizgi görünür. Değişiklikleri kaydettiğinizde dikey satırlar yeşil olur.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>İmza olmadan UTF-8 kodlamasını otomatik algıla

Varsayılan olarak düzenleyici, bayt sırası işaretlerini veya karakter kümesi etiketlerini arayarak kodlamayı algılar. Geçerli belgede hiçbiri bulunmazsa, kod Düzenleyicisi, bayt dizilerini tarayarak UTF-8 kodlamasını otomatik algıla girişiminde bulunur. Kodlamanın tekrar algılanmasını devre dışı bırakmak için bu seçeneği temizleyin.

### <a name="follow-project-coding-conventions"></a>Proje kodlama kurallarını izleyin

Seçildiğinde, projenin belirtilen kodlama kuralları kişisel projelerinizde kullandığınız tüm kodlama kurallarını geçersiz kılar.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Tanıma Git işlemini gerçekleştirmek için fare tıklamasını etkinleştir

Seçildiğinde, **CTRL** tuşuna basabilir ve fareyle tıklarken bir öğenin üzerine geldiğinizde üzerine gelebilmeniz gerekir. Bunun yapılması sizi seçili öğenin tanımına götürür. **Değiştirici tuşu kullan** açılır listesinden alt veya **CTRL** + **alt** **tuşlarını da seçebilirsiniz** .

Öğenin tanımını, kod düzenleyicisinde geçerli konumunuzla uzaklaşmadan bir pencerede görüntülemek için, **görünümü göz atma ' da aç** onay kutusunu seçin.

## <a name="display"></a>Ekran

### <a name="selection-margin"></a>Seçim kenar boşluğu

Seçildiğinde, düzenleyicinin metin alanının sol kenarı üzerinde dikey bir kenar boşluğu görüntüler. Metnin tamamını seçmek için bu kenar boşluğuna tıklayabilir veya ardışık metin satırları seçmek için tıklayıp sürükleyebilirsiniz.

|Seçim kenar boşluğu|Seçim kenar boşluğu kapalı|
| - | - |
|![HTMLpageSelectionMarginOn ekran görüntüsü](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff ekran görüntüsü](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Gösterge kenar boşluğu

Seçildiğinde, düzenleyicinin metin alanının sol kenarının dışında dikey bir kenar boşluğu görüntüler. Bu kenar boşluğuna tıkladığınızda metinle ilgili bir simge ve araç Ipucu görünür. Örneğin, kesme noktası veya görev listesi kısayolları gösterge kenar boşluğunda görüntülenir. Gösterge kenar boşluğu bilgileri yazdırılmaz.

### <a name="highlight-current-line"></a>Geçerli satırı Vurgula

Seçildiğinde, imlecin bulunduğu kod satırının etrafında gri bir kutu görüntüler.

### <a name="show-structure-guide-lines"></a>Yapı Kılavuzu çizgilerini göster

Seçildiğinde, düzenleyicide tek tek kod bloklarını kolayca tanımlamanızı sağlayan, yapılandırılmış kod bloklarıyla bir dikey çizgi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Seçenekler, Metin Düzenleyici, Dosya Uzantısı](../../ide/reference/options-text-editor-file-extension.md)
- [Klavye Kısayollarını Tanımlama ve Özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
