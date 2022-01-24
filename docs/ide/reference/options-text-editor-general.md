---
title: Seçenekler, Metin Düzenleyici, Genel
description: Kod ve metin düzenleyicisi için genel ayarları değiştirmek üzere Genel Visual Studio kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/15/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
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
ms.openlocfilehash: 32d55c85524fc895e8d6768597287730f61695f4
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650381"
---
# <a name="options-dialog-box-text-editor--general"></a>Seçenekler iletişim kutusu: Metin Düzenleyici \> Genel

Bu iletişim kutusu, uygulama kodunun ve metin düzenleyicisinin Visual Studio ayarlarını değiştirmenizi sağlar. Bu iletişim kutusunu görüntülemek için Araçlar **menüsünde Seçenekler'i** seçin, Metin Düzenleyici **klasörünü** genişletin ve ardından Genel'i **seçin.** 

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/tools-options-text-editor-general.png" alt-text="Seçenekler iletişim kutusundaki metin düzenleyicisinin genel ayarlarının ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/vs-2019/tools-options-text-editor-general.png" alt-text="Seçenekler iletişim kutusundaki metin düzenleyicisinin genel ayarlarının ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/tools-options-text-editor-general.png" alt-text="Seçenekler iletişim kutusundaki metin düzenleyicisinin genel ayarlarının ekran görüntüsü.":::

::: moniker-end

## <a name="settings"></a>Ayarlar

Araçlar Ayarlar Düzenleyicisi   >  **Genel'in**  >  **Aşağıdaki Seçenekler**  >  **bölümünde** aşağıdaki seçenekler yer almaktadır.

### <a name="drag-and-drop-text-editing"></a>Metin düzenlemeyi sürükleyip bırakma

Bu ayar seçildiğinde, metni seçerek ve fareyle geçerli belge içindeki başka bir konuma veya başka bir açık belgeye sürükleyerek taşımayı sağlar.

::: moniker range="vs-2022"

### <a name="select-subword-on-double-click"></a>Çift tıklamada alt sözcük seçme

Bu ayarı değiştirerek çift tıklarsanız, tam sözcük yerine yalnızca bir alt sözcük seçer. (Örnek olarak medial büyük harflerini kullanırken bu yararlı olabilir.)

::: moniker-end

### <a name="automatic-delimiter-highlighting"></a>Otomatik sınırlayıcı vurgulama

Seçildiğinde, parametreleri veya öğe-değer çiftlerini ve eşleşen ayraçları ayıran sınırlayıcı karakterler vurgulanır.

### <a name="track-changes"></a>Değişiklikleri izleme

Kod düzenleyicisi seçildiğinde, dosya en son kaydedildikten sonra değiştirilen kodu işaretlemek için seçim kenar boşluğunda dikey sarı bir çizgi görünür. Değişiklikleri kaydeden dikey çizgiler yeşil olur.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>İmza olmadan UTF-8 kodlamasını otomatik algılama

Düzenleyici varsayılan olarak, bayt sırası işaretlerini veya karakter kümesi etiketlerini arayarak kodlamayı algılar. Geçerli belgede hiçbiri bulunamasa, kod düzenleyicisi byte dizilerini taraarak UTF-8 kodlamasını otomatik olarak algılamaya çalışır. Kodlamanın otomatik algılamasını devre dışı bırakmak için bu seçeneğin temizlerini kullanın.

### <a name="follow-project-coding-conventions"></a>Proje kodlama kurallarına uyma

Bu seçildiğinde, projenin belirtilen kodlama kuralları, kişisel projeleriniz üzerinde kullanabileceğiniz kodlama kurallarına geçersiz kılar.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Tanıma Git gerçekleştirmek için fare tıklamayı etkinleştirme

Seçildiğinde, Ctrl tuşuna **basarak** fareye tıklarken bir öğenin üzerine gelin. Bunu yapmak sizi seçili öğenin tanımına alır. Değiştirici tuş kullan açılan **menüsünden Alt** veya **Ctrl**  +  **Alt** **tuşlarını da** seçebilirsiniz.

#### <a name="open-definition-in-peek-view"></a>Tanıma göz atma görünümünde açma

Öğenin tanımını kod düzenleyicisinde geçerli konumunuzdan uzak kalmadan bir pencerede görüntülemek için bu onay kutusunu seçin. Daha fazla bilgi için, [bkz. How to: View and edit code by using Peek Definition](../how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="display"></a>Göster

Araçlar **Seçeneği'nin Metin**  >  > **Genel'in**  >  **Görüntüleme bölümünde** aşağıdaki seçenekler yer almaktadır.

::: moniker range=">=vs-2019"

### <a name="view-whitespace"></a>Boşluğu görüntüleme

Seçildiğinde, boşlukları ve sekmeleri görselleştirebilirsiniz.

::: moniker-end

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

Seçildiğinde düzenleyicide, tek tek kod bloklarını kolayca tanımlamanıza olanak sağlayan yapılandırılmış kod blokları ile birlikte dikey çizgiler görünür.

::: moniker range=">=vs-2019"

### <a name="show-error-squiggles"></a>Hata geçişlerini göster

Seçildiğinde, dalgalı çizgiler olarak bilinen farklı renkli dalgalı alt çizgiler kodunda görünür. (Kırmızı geçişler söz dizimi hatalarını, mavi derleyici hatalarını, yeşil uyarıları ve mor da diğer hata türlerini gösterir.)

### <a name="show-file-health-indicator"></a>Dosya durumu göstergesini göster

Seçildiğinde, düzenleyicinin sol alt köşesinde kod temizleme seçeneklerine sahip bir dosya durumu gösterge durumu (hatalar, uyarılar) çubuğu görüntülenir.

### <a name="line-spacing"></a>Satır aralığı

1,0 olan varsayılan satır aralığını istediğiniz artışla değiştirmek için bu denetimi kullanarak 1,15, 1,5, 2,0, 2,5 ve 3,0 değerini dahil edin.

### <a name="show-editing-context-in-the-editor"></a>Düzenleme bağlamını düzenleyicide gösterme

Bağlam ayarlarını düzenlemeyi tamamen değiştirmek veya aşağıdaki ayarlardan birini seçerek tercihinizi kişiselleştirmek için bu denetimi kullanın:

- Çizgi/Sütun
- Seçim
- Ekle/Üzerine Yaz
- Sekme/Boşluk
- Satır bitişleri

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../../ide/reference/options-text-editor-all-languages.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Seçenekler, Metin Düzenleyici, Dosya Uzantısı](../../ide/reference/options-text-editor-file-extension.md)
- [Klavye Kısayollarını Tanımlama ve Özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Düzenleyiciyi Özelleştirme](../how-to-change-text-case-in-the-editor.md)
- [IntelliSense'i kullanma](../../ide/using-intellisense.md)
