---
title: Seçenekler, Metin Düzenleyici, Tüm Diller
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9815bdec94ce32a3bfcc170dd95d834bc43ea58f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566884"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Seçenekler iletişim kutusu: \> Metin Düzenleyicitüm Diller

Bu iletişim kutusu, Kod Düzenleyicisi'nin varsayılan davranışını değiştirmenize olanak tanır. Bu ayarlar, HTML Tasarımcısı'nın Kaynak görünümü gibi Kod Düzenleyicisi'ni temel alan diğer düzenleyiciler için de geçerlidir. Bu iletişim kutusunu açmak için **Araçlar** menüsünden **Seçenekler'i** seçin. Metin **Düzenleyicisi** klasöründe, **Tüm Diller** alt klasörünü genişletin ve ardından **Genel'i**seçin.

> [!CAUTION]
> Bu sayfa, tüm geliştirme dilleri için varsayılan seçenekleri ayarlar. Bu iletişim kutusundaki bir seçeneği sıfırlamanın, tüm dillerdeki Genel seçenekleri burada seçilecek seçeneklere sıfırlayacak olduğunu unutmayın. Metin Düzenleyicisi seçeneklerini yalnızca bir dil için değiştirmek için, söz sözlere dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

Bazı programlama dilleri için Genel seçenekler sayfalarında bir seçenek seçildiğinde gri leştirilmiş bir onay işareti görüntülenir, ancak diğerleri için gösterilmez.

## <a name="statement-completion"></a>Deyim Tamamlama

**Otomatik liste üyeleri**

Seçildiğinde, editöre yazdığınız gibi kullanılabilir üyelerin, özelliklerin, değerlerin veya yöntemlerin açılır listeleri IntelliSense tarafından görüntülenir. Öğeyi kodunuza eklemek için açılır listeden herhangi bir öğe seçin. Bu seçeneğin seçilmesi **gelişmiş üyeleri gizle** seçeneğini etkinleştiri.

**Gelişmiş üyeleri gizleme**

Seçildiğinde, yalnızca en sık kullanılan öğeleri görüntüleyerek açılır ekstre tamamlama listelerini kısaltır. Diğer öğeler listeden filtrelenir.

**Parametre bilgileri**

Seçildiğinde, geçerli bildirim veya yordamın tam sözdizimi, kullanılabilir parametrelerin tümüyle birlikte düzenleyicideki ekleme noktasının altında görüntülenir. Atayabileceğiniz bir sonraki parametre kalın olarak görüntülenir.

## <a name="settings"></a>Ayarlar

**Sanal alanı etkinleştirme**

Bu seçenek seçildiğinde ve **Word kaydırma** temizlendiğinde, Kod Düzenleyicisi ve türünde bir satırın sonuna kadar herhangi bir yeri tıklatabilirsiniz. Bu özellik, yorumları kodunuzun yanındaki tutarlı bir noktada konumlandırmak için kullanılabilir.

**Sözcük kaydırma**

Seçildiğinde, görüntülenebilir düzenleyici alanının ötesine yatay olarak yayılan bir satırın herhangi bir bölümü otomatik olarak bir sonraki satırda görüntülenir. Bu seçeneğin seçilmesi, sözcük kaydırma seçeneği **için görsel glifleri göster'i** sağlar.

> [!NOTE]
> **Word Wrap** açıkken **Sanal Alan** özelliği kapatılır.

**Sözcük kaydırma için görsel glifleri göster**

Seçildiğinde, uzun bir çizginin ikinci bir satıra kaydırıldığı bir iade ok göstergesi görüntülenir.

![LineBreakSymbol ekran görüntüsü](../../ide/reference/media/linebreak.gif)

Bu göstergeleri görüntülememeyi tercih ediyorsanız bu seçeneği temizleyin.

> [!NOTE]
> Bu anımsatıcı okları kodunuza eklenmez ve yazdırılmaz. Onlar sadece referans içindir.

**Satır numaraları**

Seçildiğinde, her kod satırının yanında bir satır numarası görüntülenir.

> [!NOTE]
> Bu satır numaraları kodunuza eklenmez ve yazdırılmaz. Onlar sadece referans içindir.

**Tek tıklamayla URL gezintisini etkinleştirme**

Seçildiğinde, fare imleci düzenleyicideki bir URL'nin üzerinden geçerken bir işaretleme eline dönüşür. Belirtilen sayfayı web tarayıcınızda görüntülemek için URL'yi tıklatabilirsiniz.

**Navigasyon çubuğu**

Seçildiğinde, kod düzenleyicisinin üst kısmında **Gezinti çubuğu** görüntülenir. Açılan **Nesneler** ve **Üyeler** listeleri, kodunuzda belirli bir nesneyi seçmenize, üyelerinden seçim yapmanızı ve Kod Düzenleyicisi'nde seçili üyenin bildirimine gidin.

**Seçim olmadığında boş satırlara Kesme veya Kopyala komutları uygulama**

Bu seçenek, ekleme noktasını boş bir satıra yerleştirdiğinizde, hiçbir şey seçmediğinizde ve sonra Kopyala veya Kesdiğinizde düzenleyicinin davranışını ayarlar.

- Bu seçenek seçildiğinde, boş satır kopyalanır veya kesilir. Daha sonra Yapıştırırsanız, yeni, boş bir satır eklenir.

- Bu seçenek temizlendiğinde, Kesme komutu boş satırları kaldırır. Ancak, Pano'daki veriler korunur. Bu nedenle, Yapıştır komutunu kullanırsanız, panoya en son kopyalanan içerik yapıştırılır. Daha önce hiçbir şey kopyalanmadıysa, hiçbir şey yapıştırılan.

Bir satır boş olmadığında bu ayarın Kopyala veya Kes üzerinde hiçbir etkisi yoktur. Hiçbir şey seçili değilse, tüm satır kopyalanır veya kesilir. Daha sonra Yapıştırırsanız, tüm satırın metni ve bitiş çizgisi karakteri yapıştırılır.

> [!TIP]
> Boşluklar, sekmeler ve satır uçları için göstergeleri görüntülemek ve böylece girinilmiş satırları tamamen boş satırlardan ayırt etmek **için, Düzenle** menüsünden **Gelişmiş'i** seçin ve **Beyaz Uzayı Görüntüle'yi**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
