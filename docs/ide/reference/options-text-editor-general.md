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
ms.openlocfilehash: ed55d65555425b04749696b5510cfe799d2a1194
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472825"
---
# <a name="options-dialog-box-text-editor--general"></a>Seçenekler iletişim kutusu: \> Metin Düzenleyici Genel

Bu iletişim kutusu, Visual Studio kodu ve metin düzenleyicisi için genel ayarları değiştirmenizi sağlar. Bu iletişim kutusunu görüntülemek için **Araçlar** menüsünde **Seçenekler'i** seçin, **Metin Düzenleyicisi** klasörünü genişletin ve ardından **Genel'i**seçin.

## <a name="settings"></a>Ayarlar

### <a name="drag-and-drop-text-editing"></a>Metin düzenlemeyi sürükleyip bırak

Seçildiğinde, metni seçerek ve fareyle birlikte geçerli belge veya başka bir açık belge içinde başka bir konuma sürükleyerek metni taşımanızı sağlar.

### <a name="automatic-delimiter-highlighting"></a>Otomatik delimiter vurgulama

Seçildiğinde, parametreleri veya madde değeri çiftlerini ayıran ve eşleşen ayraçları ayıran sınır dışı layıcı karakterler vurgulanır.

### <a name="track-changes"></a>Değişiklikleri izleme

Kod düzenleyicisi seçildiğinde, dosya en son kaydedildikten sonra değiştirilen kodu işaretlemek için seçim kenar boşluğunda dikey sarı bir çizgi görüntülenir. Değişiklikleri kaydettiğinizde, dikey çizgiler yeşil olur.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>UtF-8 kodlamayı imza olmadan otomatik olarak algıla

Varsayılan olarak, düzenleyici bayt sipariş işaretleri veya charset etiketleri arayarak kodlama algılar. Geçerli belgede ikisi de bulunmazsa, kod düzenleyicisi bayt dizilerini tarayarak UTF-8 kodlamasını otomatik algılamaya çalışır. Kodlamanın otomatik algılamasını devre dışı kaltın için bu seçeneği temizleyin.

### <a name="follow-project-coding-conventions"></a>Proje kodlama kurallarını izleyin

Seçildiğinde, projenin belirtilen kodlama kuralları kişisel projelerinizde kullandığınız kodlama kurallarını geçersiz kılar.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Tanıma Git'i gerçekleştirmek için fare tıklatmasını etkinleştirme

Seçildiğinde **Ctrl** tuşuna basabilir ve fareyi tıklatırken bir öğenin üzerine gezinebilirsiniz. Bunu yapmak sizi seçili öğenin tanımına götürür. Ayrıca, Alt **veya** **Ctrl** + **Alt'ı** **Kullan değiştirici anahtarı** açılır bırak'ından da seçebilirsiniz.

Kodun düzenleyicisinde geçerli konumunuzdan uzaklaşmadan öğenin tanımını bir pencerede görüntülemek için peek görünüm onay kutusunda **Açık tanımını** seçin.

## <a name="display"></a>Ekran

### <a name="selection-margin"></a>Seçim kenar boşluğu

Seçildiğinde, düzenleyicinin metin alanının sol kenarı boyunca dikey bir kenar boşluğu görüntüler. Bir metin satırının tamamını seçmek için bu kenar boşluğu tıklatabilir veya ardışık metin satırlarını seçmek için tıklatıp sürükleyebilirsiniz.

|Seçim Kenar Boşluğu üzerinde|Seçim Kenar Boşluğu kapalı|
| - | - |
|![HTMLpageSelectionMarginOn ekran görüntüsü](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff ekran görüntüsü](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Gösterge marjı

Seçildiğinde, düzenleyicinin metin alanının sol kenarının dışında dikey bir kenar boşluğu görüntüler. Bu kenar boşluğu tıklattığınızda, metinle ilgili bir simge ve Araç İpucu görüntülenir. Örneğin, kesme noktası veya görev listesi kısayolları gösterge kenar boşluğunda görünür. Gösterge Marjı bilgileri yazdırılmaz.

### <a name="highlight-current-line"></a>Geçerli satırı vurgulama

Seçildiğinde, imlecin bulunduğu kod satırının etrafında gri bir kutu görüntüler.

### <a name="show-structure-guide-lines"></a>Yapı kılavuz çizgilerini göster

Seçildiğinde, yapılandırılmış kod bloklarıyla hizalanan düzenleyicide dikey çizgiler görünür ve bu da kod bloklarını tek tek belirlemenize olanak tanır.

### <a name="show-file-health-indicator"></a>Dosya sistem durumu göstergesini göster

Seçildiğinde, kod temizleme seçenekleri içeren bir dosya durumu göstergesi durumu (hatalar, uyarılar) çubuğu düzenleyicinin sol alt köşesinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Seçenekler, Metin Düzenleyici, Dosya Uzantısı](../../ide/reference/options-text-editor-file-extension.md)
- [Klavye Kısayollarını Tanımlama ve Özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
