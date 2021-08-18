---
title: Seçenekler, Metin Düzenleyici, Tüm Diller
description: Kod Düzenleyicisi'nin varsayılan davranışını değiştirmek için Tüm Diller bölümündeki Genel sayfasını kullanmayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f581f48efb9fbba97aa65b9826f7114f7377e951
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101004"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Seçenekler iletişim kutusu: Metin Düzenleyici \> Tüm Diller

Bu iletişim kutusu, Kod Düzenleyicisi'nin varsayılan davranışını değiştirmenizi sağlar. Bu ayarlar, HTML Tasarımcısı'nın Kaynak görünümü gibi Kod Düzenleyicisi'ni temel alan diğer düzenleyiciler için de geçerlidir. Bu iletişim kutusunu açmak için Araçlar **menüsünden** **Seçenekler'i** seçin. Metin Düzenleyici **klasöründe** Tüm Diller alt **klasörünü genişletin** ve ardından Genel'i **seçin.**

> [!CAUTION]
> Bu sayfa, tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneğin sıfırlanması, tüm dillerdeki Genel seçeneklerini burada seçili olan seçeneklere sıfırlar. Yalnızca bir dil için Metin Düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörlerini genişletin ve seçenek sayfalarını seçin.

Bazı programlama dilleri için Genel seçenekler sayfalarında bir seçenek seçildiğinde gri bir onay işareti görüntülenir, ancak diğerleri için görüntülenmez.

## <a name="statement-completion"></a>Deyim Tamamlama

**Üyeleri otomatik listele**

Seçildiğinde, düzenleyicide siz yazarak IntelliSense tarafından kullanılabilir üyelerin, özelliklerin, değerlerin veya yöntemlerin açılır listeleri görüntülenir. Öğeyi kodunuza eklemek için açılır listeden herhangi bir öğe seçin. Bu seçeneğin seçerek Gelişmiş **üyeleri gizle seçeneğine olanak** sağlar.

**Gelişmiş üyeleri gizleme**

Seçildiğinde, yalnızca en sık kullanılan öğeleri görüntüleyerek açılır deyim tamamlama listelerini kısaltabilir. Diğer öğeler listeden filtrelenmiş.

**Parametre bilgileri**

Seçildiğinde, geçerli bildirim veya yordamın tam söz dizimi düzenleyicide ekleme noktası altında ve tüm kullanılabilir parametreleriyle birlikte görüntülenir. Ataydığınız sonraki parametre kalın olarak görüntülenir.

## <a name="settings"></a>Ayarlar

**Sanal alanı etkinleştirme**

Bu seçenek seçildiğinde ve **Sözcük kaydırma** temiz olduğunda, Kod Düzenleyicisi'nde bir satırın sonunun ötesinde herhangi bir yere tıklar ve yazabilirsiniz. Bu özellik, açıklamalarınızı kodunuzun yanındaki tutarlı bir noktaya konumlandırmak için kullanılabilir.

**Sözcük kaydırma**

Seçildiğinde, bir satırın görüntülenebilir düzenleyici alanı ötesine yatay olarak genişleten herhangi bir kısmı otomatik olarak bir sonraki satırda görüntülenir. Bu seçeneğin seçerek **sözcük kaydırma için görselleri göster seçeneğine olanak** sağlar.

> [!NOTE]
> Sözcük **Kaydırma** açıkken Sanal **Alan özelliği** kapalıdır.

**Sözcük kaydırma için görsel ifadeleri gösterme**

Seçildiğinde, uzun bir çizginin ikinci satıra kaydırılan bir dönüş oku göstergesi görüntülenir.

![LineBreakSymbol ekran görüntüsü](../../ide/reference/media/linebreak.gif)

Bu göstergeleri görüntülememeyi tercih ediyorsanız bu seçeneğin temizlemesi gerekir.

> [!NOTE]
> Bu anımsatıcı okları kodunuza eklenmez ve yazdırılmaz. Bunlar yalnızca başvuruya göredir.

**Satır numaraları**

Seçildiğinde, her kod satırı yanında bir satır numarası görünür.

> [!NOTE]
> Bu satır numaraları kodunuza eklenmez ve yazdırılmaz. Bunlar yalnızca başvuruya göredir.

**Tek tıklamayla URL gezintisini etkinleştirme**

Seçildiğinde, fare imleci düzenleyicide bir URL'den geçerken işaret eden el olarak değişir. Belirtilen sayfayı web tarayıcınızda görüntülemek için URL'ye tıklayabilirsiniz.

**Gezinti çubuğu**

Seçildiğinde, kod **düzenleyicisinin** üst kısmında Gezinti çubuğunu görüntüler. Açılan Nesneler **ve** **Üyeler** listeleri, kodunuzdaki belirli bir nesneyi seçmenize, üyelerinden birini seçmenize ve Kod Düzenleyicisi'nde seçili üyenin bildirimine gezinmenize olanak sağlar.

**Seçim yoksa Boş satırlara Kesme veya Kopyalama komutları uygulama**

Bu seçenek, ekleme noktasını boş bir satıra yerleştirme, hiçbir şey seçme ve ardından Kopyala veya Kes'i seçerek düzenleyicinin davranışını ayarlar.

- Bu seçenek seçildiğinde boş satır kopyalanır veya kesilir. Yapıştır'ı tamamlarsanız yeni, boş bir satır eklenir.

- Bu seçenek temiz olduğunda, Kes komutu boş satırları kaldırır. Ancak Panodaki veriler korunur. Bu nedenle Yapıştır komutunu kullanırsanız panoya en son kopyalanan içerik yapıştırır. Daha önce hiçbir şey kopyalanmazsa hiçbir şey yapıştırlanmaz.

Bir satır boş değilken bu ayarın Kopyala veya Kes üzerinde hiçbir etkisi yoktur. Hiçbir şey seçilmezse, satırın tamamı kopyalanır veya kesilir. Yapıştırıyorsanız, satırın tamamının ve bitiş çizgisi karakterinin metni yapıştırıldı.

> [!TIP]
> Boşluklar, sekmeler ve satır uçları göstergelerini görüntülemek ve girintili satırları tamamen  boş  satırlardan ayırmak için Düzenle menüsünden Gelişmiş'i seçin ve Boşluğu **Görüntüle'yi seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense'i kullanma](../../ide/using-intellisense.md)
