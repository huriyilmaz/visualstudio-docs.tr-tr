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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566884"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Seçenekler iletişim kutusu: tüm diller \> metin Düzenleyicisi

Bu iletişim kutusu, kod düzenleyicisinin varsayılan davranışını değiştirmenize izin verir. Bu ayarlar ayrıca, HTML tasarımcısının kaynak görünümü gibi kod düzenleyicisine dayalı diğer düzenleyiciler için de geçerlidir. Bu iletişim kutusunu açmak için, **Araçlar** menüsünden **Seçenekler** ' i seçin. **Metin Düzenleyicisi** klasörü Içinde **tüm diller** alt klasörünü genişletin ve ardından **genel**' i seçin.

> [!CAUTION]
> Bu sayfa tüm geliştirme dillerinin varsayılan seçeneklerini ayarlar. Bu iletişim kutusunda bir seçeneğin sıfırlanması, burada seçili olan seçeneklere ilişkin tüm dillerdeki genel seçenekleri sıfırlayacaktır. Yalnızca bir dile ait metin düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

Bazı programlama dillerinin genel seçenekler sayfalarında bir seçenek seçildiğinde gri onay işareti görüntülenir, ancak diğerleri için değildir.

## <a name="statement-completion"></a>Deyim Tamamlama

**Üyeleri otomatik Listele**

Seçildiğinde, kullanılabilir üyelerin, özelliklerin, değerlerin veya yöntemlerin açılır listeleri, düzenleyicide yazarken IntelliSense tarafından görüntülenir. Öğeyi kodunuza eklemek için açılır listedeki herhangi bir öğeyi seçin. Bu seçeneğin belirlenmesi, **Gelişmiş üyeleri Gizle** seçeneğini sunar.

**Gelişmiş üyeleri gizle**

Seçildiğinde, yalnızca en yaygın olarak kullanılan öğeleri görüntüleyerek açılan deyimin tamamlanma listelerini kısaltır. Diğer öğeler listeden filtrelenir.

**Parametre bilgileri**

Seçildiğinde, geçerli bildirim veya yordamın bütün sözdizimi, tüm kullanılabilir parametreleriyle birlikte düzenleyicide ekleme noktası altında görüntülenir. Atayabilmeniz için bir sonraki parametre kalın yazı tipinde görüntülenir.

## <a name="settings"></a>Ayarlar

**Sanal alanı etkinleştir**

Bu seçenek belirlendiğinde ve **sözcük kaydırmayı** temizlenmemiş olduğunda, kod düzenleyici ve türünde bir satırın sonundaki herhangi bir yere tıklayabilirsiniz. Bu özellik, kodunuzun yanındaki tutarlı bir noktada Yorumları konumlandırmak için kullanılabilir.

**Sözcük kaydır**

Seçildiğinde, bir satırın, görüntülenebilir düzenleyici alanının ötesinde yatay olarak genişleyen herhangi bir kısmı otomatik olarak bir sonraki satırda görüntülenir. Bu seçeneğin belirlenmesi, **sözcük kaydırması için görsel glifleri göster** seçeneğinin kullanılmasına izin vermez.

> [!NOTE]
> **Sözcük kaydırması** açık durumdayken **sanal alan** özelliği kapalıdır.

**Sözcük kaydırması için görsel glifleri göster**

Seçildiğinde, uzun bir çizginin ikinci bir satıra sarmaladığı bir dönüş oku göstergesi görüntülenir.

![LineBreakSymbol ekran görüntüsü](../../ide/reference/media/linebreak.gif)

Bu göstergeleri görüntülememayı tercih ediyorsanız bu seçeneği temizleyin.

> [!NOTE]
> Bu anımsatıcı okları kodunuza eklenmez ve yazdırılmıyor. Bunlar yalnızca başvuru amaçlıdır.

**Satır numaraları**

Seçildiğinde, her kod satırının yanında bir satır numarası görünür.

> [!NOTE]
> Bu satır numaraları kodunuza eklenmez ve yazdırılmıyor. Bunlar yalnızca başvuru amaçlıdır.

**Tek tıklama URL gezintisini etkinleştir**

Seçildiğinde fare imleci, düzenleyicide bir URL üzerinden geçen bir işaret halinde değişir. Web tarayıcınızda belirtilen sayfayı göstermek için URL 'ye tıklayabilirsiniz.

**Gezinti çubuğu**

Seçildiğinde, kod düzenleyicisinin en üstündeki **Gezinti çubuğunu** görüntüler. Açılan **nesneler** ve **Üyeler** listeleri, kodunuzda belirli bir nesneyi seçmenizi, üyelerinden seçim yapmanıza ve kod düzenleyicisinde seçili üyenin bildirimine götürür.

**Seçim olmadığında boş satırlara Kes veya Kopyala komutlarını Uygula**

Bu seçenek, ekleme noktasını boş bir satıra yerleştirdiğinizde düzenleyicinin davranışını ayarlar, hiçbir şey seçin ve sonra Kopyala veya kes.

- Bu seçenek belirlendiğinde boş satır kopyalanır veya kesilir. Daha sonra yapıştırırsanız, yeni, boş bir satır eklenir.

- Bu seçenek temizlenmiş olduğunda kes komutu boş satırları kaldırır. Ancak, Panodaki veriler korunur. Bu nedenle, Yapıştır komutunu kullanırsanız, pano 'Ya en son kopyaladığınız içerik yapıştırılır. Daha önce hiçbir şey kopyalanmadığı takdirde hiçbir şey yapıştırılmaz.

Bu ayarın, bir satır boş olmadığında kopyalama veya kesme üzerinde hiçbir etkisi yoktur. Hiçbir şey seçilmezse, tüm satır kopyalanır veya kesilir. Daha sonra yapıştırırsanız, tüm satırın metni ve onun EndLine karakteri yapıştırılır.

> [!TIP]
> Boşluk, sekme ve satır uçları göstergelerini görüntülemek ve bu nedenle girintili çizgileri tamamen boş olan satırlardan ayırt etmek için, **Düzenle** menüsünden **Gelişmiş** ' i seçin ve **boşluğu görüntüle**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
