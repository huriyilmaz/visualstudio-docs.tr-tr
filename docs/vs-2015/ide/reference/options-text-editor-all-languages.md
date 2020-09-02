---
title: Seçenekler, metin düzenleyici, tüm diller | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662398"
---
# <a name="options-text-editor-all-languages"></a>Seçenekler, Metin Düzenleyici, Tüm Diller
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, kod düzenleyicisinin varsayılan davranışını değiştirmenize izin verir. Bu ayarlar ayrıca, HTML tasarımcısının kaynak görünümü gibi kod düzenleyicisine dayalı diğer düzenleyiciler için de geçerlidir. Bu iletişim kutusunu açmak için, **Araçlar** menüsünden **Seçenekler** ' i seçin. **Metin Düzenleyicisi** klasörü Içinde **tüm diller** alt klasörünü genişletin ve ardından **genel**' i seçin.

> [!CAUTION]
> Bu sayfa tüm geliştirme dillerinin varsayılan seçeneklerini ayarlar. Bu iletişim kutusunda bir seçeneğin sıfırlanması, burada seçili olan seçeneklere ilişkin tüm dillerdeki genel seçenekleri sıfırlayacaktır. Yalnızca bir dile ait metin düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

 Bazı programlama dillerinin genel seçenekler sayfalarında bir seçenek seçildiğinde gri onay işareti görüntülenir, ancak diğerleri için değildir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Deyim Tamamlama
 Seçili olduğunda üyeleri otomatik Listele, kullanılabilir üyelerin, özelliklerin, değerlerin veya yöntemlerin açılır listeleri, düzenleyicide yazarken IntelliSense tarafından görüntülenir. Öğeyi kodunuza eklemek için açılır listedeki herhangi bir öğeyi seçin. Bu seçeneğin belirlenmesi, **Gelişmiş üyeleri Gizle** seçeneğini sunar.

 Seçili olduğunda Gelişmiş üyeleri gizleyin, yalnızca en sık kullanılan öğeleri görüntüleyerek açılan deyimin tamamlanma listelerini kısaltır. Diğer öğeler listeden filtrelenir.

 Parametre bilgisi seçildiğinde, geçerli bildirim veya yordamın tüm sözdizimi, tüm kullanılabilir parametreleriyle birlikte düzenleyicideki ekleme noktası altında görüntülenir. Atayabilmeniz için bir sonraki parametre kalın yazı tipinde görüntülenir.

## <a name="settings"></a>Ayarlar
 Sanal alanı etkinleştir Bu seçenek belirlendiğinde ve **sözcük kaydırması** silinirse, kod düzenleyici ve türündeki bir satırın sonundaki herhangi bir yere tıklayabilirsiniz. Bu özellik, kodunuzun yanındaki tutarlı bir noktada Yorumları konumlandırmak için kullanılabilir.

 Sözcük kaydırmayı seçtiğinizde, bir satırın, görüntülenebilir düzenleyici alanının ötesinde yatay olarak genişleyen bir kısmı otomatik olarak bir sonraki satırda görüntülenir. Bu seçeneğin belirlenmesi, **sözcük kaydırması için görsel glifleri göster** seçeneğinin kullanılmasına izin vermez.

> [!NOTE]
> **Sözcük kaydırması** açık durumdayken **sanal alan** özelliği kapalıdır.

 Sözcük kaydırma için görsel glifleri göster seçildiğinde, uzun bir çizginin ikinci bir satıra sarmaladığı bir dönüş oku göstergesi görüntülenir.

 ![LineBreakSymbol ekran görüntüsü](../../ide/reference/media/linebreak.gif "LineBreak")

 Bu göstergeleri görüntülememayı tercih ediyorsanız bu seçeneği temizleyin.

> [!NOTE]
> Bu anımsatıcı okları kodunuza eklenmez ve yazdırılmıyor. Bunlar yalnızca başvuru amaçlıdır.

 Seçim olmadığında boş satırlara Kes veya Kopyala komutlarını Uygula Bu seçenek, ekleme noktasını boş bir satıra yerleştirdiğinizde düzenleyicinin davranışını ayarlar, hiçbir şey seçin ve ardından Kopyala veya kes.

- Bu seçenek belirlendiğinde boş satır kopyalanır veya kesilir. Daha sonra yapıştırırsanız, yeni, boş bir satır eklenir.

- Bu seçenek temizlenmiş olduğunda kes komutu boş satırları kaldırır. Ancak, Panodaki veriler korunur. Bu nedenle, Yapıştır komutunu kullanırsanız, pano 'Ya en son kopyaladığınız içerik yapıştırılır. Daha önce hiçbir şey kopyalanmadığı takdirde hiçbir şey yapıştırılmaz.

  Bu ayarın, bir satır boş olmadığında kopyalama veya kesme üzerinde hiçbir etkisi yoktur. Hiçbir şey seçilmezse, tüm satır kopyalanır veya kesilir. Daha sonra yapıştırırsanız, tüm satırın metni ve onun EndLine karakteri yapıştırılır.

> [!TIP]
> Boşluk, sekme ve satır uçları göstergelerini görüntülemek ve bu nedenle girintili çizgileri tamamen boş olan satırlardan ayırt etmek için, **Düzenle** menüsünden **Gelişmiş** ' i seçin ve **boşluğu görüntüle**' yi seçin.

## <a name="display"></a>Göster
 Satır numaraları seçildiğinde, her kod satırının yanında bir satır numarası görünür.

> [!NOTE]
> Bu satır numaraları kodunuza eklenmez ve yazdırılmıyor. Bunlar yalnızca başvuru amaçlıdır.

 Tek tıklamayla URL gezintisini etkinleştir seçili olduğunda fare imleci, düzenleyicide bir URL üzerinden geçerken bir işaret halinde değişir. Web tarayıcınızda belirtilen sayfayı göstermek için URL 'ye tıklayabilirsiniz.

 Gezinti çubuğu seçildiğinde, kod düzenleyicisinin en üstündeki **Gezinti çubuğunu** görüntüler. Açılan **nesneler** ve **Üyeler** listeleri, kodunuzda belirli bir nesneyi seçmenizi, üyelerinden seçim yapmanıza ve kod düzenleyicisinde seçili üyenin bildirimine götürür.

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense kullanarak](../../ide/using-intellisense.md) [Seçenekler, metin düzenleyici, tüm diller, sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md) [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
