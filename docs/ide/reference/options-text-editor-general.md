---
title: Seçenekler, Metin Düzenleyici, Genel
description: Genel sayfasını kullanarak kod ve metin düzenleyicinin genel ayarlarını Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.Advanced
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7cfd0ef18f85511d23825468f1b208c34bc7e209
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151242"
---
# <a name="options-dialog-box-text-editor--general"></a>Seçenekler iletişim kutusu: Metin Düzenleyici \> Genel

Bu iletişim kutusu, uygulama kodunun ve metin düzenleyicisinin Visual Studio ayarlarını değiştirmenizi sağlar. Bu iletişim kutusunu görüntülemek için Araçlar **menüsünde Seçenekler'i** seçin, Metin Düzenleyici **klasörünü** genişletin ve ardından Genel'i **seçin.** 

## <a name="settings"></a>Ayarlar

### <a name="drag-and-drop-text-editing"></a>Metin düzenlemeyi sürükleyip bırakma

Seçildiğinde, metni seçerek ve fareyle geçerli belge içinde başka bir konuma veya başka bir açık belgeye sürükleyerek taşımayı sağlar.

### <a name="automatic-delimiter-highlighting"></a>Otomatik sınırlayıcı vurgulama

Seçildiğinde, parametreleri veya öğe-değer çiftlerini ve eşleşen ayraçları ayıran sınırlayıcı karakterler vurgulanır.

### <a name="track-changes"></a>Değişiklikleri izleme

Kod düzenleyicisi seçildiğinde, dosya en son kaydedildikten sonra değiştirilen kodu işaretlemek için seçim kenar boşluğunda dikey sarı bir çizgi görünür. Değişiklikleri kaydeden dikey çizgiler yeşil olur.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>İmza olmadan UTF-8 kodlamasını otomatik algılama

Düzenleyici varsayılan olarak, bayt sırası işaretlerini veya karakter kümesi etiketlerini arayarak kodlamayı algılar. Geçerli belgede hiçbiri bulunamasa, kod düzenleyicisi byte dizilerini taraarak UTF-8 kodlamasını otomatik olarak algılamaya çalışır. Kodlamanın otomatik algılamasını devre dışı bırakmak için bu seçeneğin temizlemesini seçin.

### <a name="follow-project-coding-conventions"></a>Proje kodlama kurallarına uyma

Bu seçildiğinde, projenin belirtilen kodlama kuralları, kişisel projeleriniz üzerinde kullanmakta olduğunu tüm kodlama kuralları geçersiz kılar.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Tanıma Git gerçekleştirmek için fare tıklamayı etkinleştirme

Seçildiğinde, Ctrl tuşuna **basarak** fareye tıklarken bir öğenin üzerine gelin. Bunu yapmak sizi seçili öğenin tanımına alır. Değiştirici tuş kullan açılan **menüsünden Alt** veya **Ctrl**  +  **Alt** **tuşlarını da** seçebilirsiniz.

Öğenin **tanımını kod düzenleyicisinde** geçerli konumunuzdan uzak kalmadan bir pencerede görüntülemek için Tanımı göz atma görünümünde aç onay kutusunu seçin.

## <a name="display"></a>Göster

### <a name="selection-margin"></a>Seçim kenar boşluğu

Seçildiğinde, düzenleyicinin metin alanı sol kenarı boyunca dikey bir kenar boşluğu görüntüler. Bir metin satırın tamamını seçmek için bu kenar boşluğuna tıklar veya tıklar ve sürükleyerek ardışık metin satırları seçersiniz.

|Seçim Kenar Boşluğu açık|Seçim Kenar Boşluğu kapalı|
| - | - |
|![HTMLpageSelectionMarginOn ekran görüntüsü](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff ekran görüntüsü](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Gösterge kenar boşluğu

Seçildiğinde, düzenleyicinin metin alanı sol kenarının dışında dikey bir kenar boşluğu görüntüler. Bu kenar boşluğuna tıklarsanız, metinle ilgili bir simge ve ToolTip görüntülenir. Örneğin, kesme noktası veya görev listesi kısayolları gösterge kenar boşluğunda görünür. Gösterge Kenar Boşluğu bilgileri yazdırılmaz.

### <a name="highlight-current-line"></a>Geçerli satırı vurgulama

Seçildiğinde, imlecin bulunduğu kod çizgisinin etrafında gri bir kutu görüntüler.

### <a name="show-structure-guide-lines"></a>Yapı kılavuz çizgilerini göster

Seçildiğinde düzenleyicide dikey çizgiler, tek tek kod bloklarını kolayca tanımlamanıza olanak sağlayan yapılandırılmış kod blokları ile birlikte görünür.

### <a name="show-file-health-indicator"></a>Dosya durumu göstergesini göster

Seçildiğinde, düzenleyicinin sol alt köşesinde kod temizleme seçenekleriyle birlikte bir dosya durumu gösterge durumu (hatalar, uyarılar) çubuğu görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Seçenekler, Metin Düzenleyici, Dosya Uzantısı](../../ide/reference/options-text-editor-file-extension.md)
- [Klavye Kısayollarını Tanımlama ve Özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
- [IntelliSense'i kullanma](../../ide/using-intellisense.md)
