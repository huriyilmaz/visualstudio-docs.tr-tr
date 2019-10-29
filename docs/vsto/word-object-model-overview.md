---
title: Word nesne modeline genel bakış
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e66d6cda802b2b1243911e1927af751e2cdbe9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985385"
---
# <a name="word-object-model-overview"></a>Word nesne modeline genel bakış
  Visual Studio 'da Word çözümleri geliştirirken Word nesne modeliyle etkileşime geçin. Bu nesne modeli, Word için birincil birlikte çalışma derlemesinde sunulan sınıflardan ve arabirimlerden oluşur ve <xref:Microsoft.Office.Interop.Word> ad alanında tanımlanır.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Bu konuda Word nesne modeli hakkında kısa bir genel bakış sunulmaktadır. Tüm Word nesne modeli hakkında daha fazla bilgi sağlayabileceğiniz kaynaklar için, bkz. [Word nesne modeli belgelerini kullanma](#WordOMDocumentation).

 Belirli görevleri gerçekleştirmek için Word nesne modelini kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Belgelerle çalışma](../vsto/working-with-documents.md)

- [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)

- [Tablolarla çalışma](../vsto/working-with-tables.md)

## <a name="understanding"></a>Word nesne modelini anlama
 Word, etkileşime girebilmeniz için yüzlerce nesne sağlar. Bu nesneler, Kullanıcı arabirimini yakından takip eden bir hiyerarşide düzenlenir. Hiyerarşinin üst kısmında <xref:Microsoft.Office.Interop.Word.Application> nesnesidir. Bu nesne, Word 'ün geçerli örneğini temsil eder. <xref:Microsoft.Office.Interop.Word.Application> nesnesi <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>ve <xref:Microsoft.Office.Interop.Word.Range> nesnelerini içerir. Bu nesnelerin her biri, nesne üzerinde işleme ve etkileşimde bulunmak için erişebileceğiniz birçok yöntem ve özelliğe sahiptir.

 Aşağıdaki çizimde, Word nesne modeli hiyerarşisinde bu nesnelerin bir görünümü gösterilmektedir.

 ![Word nesne modeli grafiği](../vsto/media/wrwordobjectmodel.gif "Word nesne modeli grafiği")

 İlk bakışta nesneler çakışacak şekilde görünür. Örneğin, <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Interop.Word.Selection> nesneleri hem <xref:Microsoft.Office.Interop.Word.Application> nesnesinin üyeleridir, ancak <xref:Microsoft.Office.Interop.Word.Document> nesnesi de <xref:Microsoft.Office.Interop.Word.Selection> nesnesinin bir üyesidir. Hem <xref:Microsoft.Office.Interop.Word.Document> hem de <xref:Microsoft.Office.Interop.Word.Selection> nesneler <xref:Microsoft.Office.Interop.Word.Bookmark> ve <xref:Microsoft.Office.Interop.Word.Range> nesnelerini içerir. Aynı nesne türüne erişmek için birden çok yol olduğu için çakışma vardır. Örneğin, bir <xref:Microsoft.Office.Interop.Word.Range> nesnesine biçimlendirme uygularsınız; Ancak, belirli bir paragrafın, bir bölümün veya tüm belgenin bulunduğu aralığa erişmek isteyebilirsiniz.

 Aşağıdaki bölümler en üst düzey nesneleri ve birbirleriyle nasıl etkileşime gireceğini kısaca açıklamaktadır. Bu nesneler aşağıdaki beş içerir:

- Uygulama nesnesi

- Belge nesnesi

- Seçim nesnesi

- Aralık nesnesi

- Bookmark nesnesi

  Word nesne modeline ek olarak, Visual Studio 'daki Office projeleri, Word nesne modelindeki bazı nesneleri genişleten *konak öğeleri* ve *konak denetimleri* sağlar. Konak öğeleri ve konak denetimleri genişledikleri Word nesneleri gibi davranır, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için bkz. Genişletilmiş nesneler ve [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) [kullanarak Word 'ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md) .

### <a name="application-object"></a>Uygulama nesnesi
 <xref:Microsoft.Office.Interop.Word.Application> nesnesi Word uygulamasını temsil eder ve diğer tüm nesnelerin üst öğesidir. Üyeleri genellikle bir bütün olarak Word 'e uygulanır. Word ortamını denetlemek için özelliklerini ve yöntemlerini kullanabilirsiniz.

 VSTO eklenti projelerinde, `ThisAddIn` sınıfının `Application` alanını kullanarak <xref:Microsoft.Office.Interop.Word.Application> nesnesine erişebilirsiniz. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 Belge düzeyi projelerinde, `ThisDocument` sınıfının <xref:Microsoft.Office.Tools.Word.Document.Application%2A> özelliğini kullanarak <xref:Microsoft.Office.Interop.Word.Application> nesnesine erişebilirsiniz.

### <a name="document-object"></a>Belge nesnesi
 <xref:Microsoft.Office.Interop.Word.Document> nesnesi Word programlamasında orta. Bir belgeyi ve tüm içeriğini temsil eder. Bir belge açtığınızda veya yeni bir belge oluşturduğunuzda, <xref:Microsoft.Office.Interop.Word.Application> nesnesinin <xref:Microsoft.Office.Interop.Word.Documents> koleksiyonuna eklenen yeni bir <xref:Microsoft.Office.Interop.Word.Document> nesnesi oluşturursunuz. Odağa sahip belgeye etkin belge denir. <xref:Microsoft.Office.Interop.Word.Application> nesnesinin <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> özelliği tarafından temsil edilir.

 Visual Studio 'daki Office geliştirme araçları, <xref:Microsoft.Office.Tools.Word.Document> türünü sağlayarak <xref:Microsoft.Office.Interop.Word.Document> nesnesini genişletir. Bu tür, bir <xref:Microsoft.Office.Interop.Word.Document> nesnesinin tüm özelliklerine erişmenizi sağlayan bir *konak öğesidir* ve ek olaylar ve yönetilen denetimler ekleyebilme özelliği ekler.

 Belge düzeyi projesi oluşturduğunuzda, projenizdeki oluşturulan `ThisDocument` sınıfını kullanarak <xref:Microsoft.Office.Tools.Word.Document> üyelere erişebilirsiniz. <xref:Microsoft.Office.Tools.Word.Document> ana bilgisayar öğesinin üyelerine, `ThisDocument` sınıfındaki **Koddan veya** **Bu** anahtar sözcüğü, `ThisDocument` sınıfının dışındaki koddan `Globals.ThisDocument` kullanarak erişebilirsiniz. Daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md). Örneğin, belgedeki ilk paragrafı seçmek için aşağıdaki kodu kullanın.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 VSTO eklenti projelerinde, çalışma zamanında <xref:Microsoft.Office.Tools.Word.Document> ana bilgisayar öğeleri oluşturabilirsiniz. Oluşturulan konak öğesini, ilişkili belgeye denetim eklemek için kullanabilirsiniz. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Seçim nesnesi
 <xref:Microsoft.Office.Interop.Word.Selection> nesnesi şu anda seçili olan alanı temsil eder. Sözcük Kullanıcı arabiriminde, kalın metin gibi bir işlem gerçekleştirdiğinizde, metni seçer veya vurgulayabilir ve ardından biçimlendirmeyi uygularsınız. <xref:Microsoft.Office.Interop.Word.Selection> nesnesi her zaman bir belgede bulunur. Hiçbir şey seçilmezse, ekleme noktasını temsil eder. Ayrıca, bir seçim bitişik olmayan birden çok metin bloğunu kapsayabilir.

### <a name="range-object"></a>Aralık nesnesi
 <xref:Microsoft.Office.Interop.Word.Range> nesnesi bir belgedeki bitişik bir alanı temsil eder ve bir başlangıç karakteri konumu ve bitiş karakteri konumu tarafından tanımlanır. Tek bir <xref:Microsoft.Office.Interop.Word.Range> nesnesiyle sınırlı değilsiniz. Aynı belgede birden çok <xref:Microsoft.Office.Interop.Word.Range> nesnesi tanımlayabilirsiniz. <xref:Microsoft.Office.Interop.Word.Range> nesne aşağıdaki özelliklere sahiptir:

- Yalnızca ekleme noktası, bir metin aralığı veya tüm belgeyi içerebilir.

- Boşluk, sekme karakteri ve paragraf işaretleri gibi yazdırılamayan karakterler içerir.

- Bu, geçerli seçim tarafından temsil edilen alan olabilir veya geçerli seçimden farklı bir alanı temsil edebilir.

- Her zaman görünür olan bir seçimden farklı olarak, bir belgede görünmez.

- Bir belge ile kaydedilmez ve yalnızca kod çalışırken bulunur.

  Bir aralığın sonuna metin eklediğinizde, sözcük otomatik olarak aralığı eklenecek metni içerecek şekilde genişletir.

### <a name="content-control-objects"></a>İçerik denetim nesneleri
 <xref:Microsoft.Office.Interop.Word.ContentControl>, Word belgelerindeki metin ve diğer içerik türlerinin giriş ve sunumunu denetlemenizi sağlayan bir yol sağlar. Bir <xref:Microsoft.Office.Interop.Word.ContentControl> zengin metin denetimi, tarih seçici veya Birleşik giriş kutusu gibi Word belgelerinde kullanılmak üzere en iyi duruma getirilmiş birçok farklı kullanıcı arabirimi türünü görüntüleyebilir. Ayrıca, kullanıcıların belge veya şablon bölümlerini düzenlemesini engellemek için de bir <xref:Microsoft.Office.Interop.Word.ContentControl> kullanabilirsiniz.

 Visual Studio <xref:Microsoft.Office.Interop.Word.ContentControl> nesnesini birkaç farklı konak denetimine genişletir. <xref:Microsoft.Office.Interop.Word.ContentControl> nesnesi içerik denetimleri için kullanılabilen farklı kullanıcı arabirimi türlerinden birini görüntüleyebilir, Visual Studio her içerik denetimi için farklı bir tür sağlar. Örneğin, bir zengin metin denetimi oluşturmak için bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kullanabilir veya bir tarih seçici oluşturmak için <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> kullanabilirsiniz. Bu konak denetimleri yerel <xref:Microsoft.Office.Interop.Word.ContentControl>gibi davranır, ancak ek olaylara ve veri bağlama yeteneklerine sahiptir. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Bookmark nesnesi
 <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesi, hem başlangıç konumu hem de bitiş konumu ile bir belgedeki bitişik bir alanı temsil eder. Bir belgedeki konumu işaretlemek veya bir belgedeki metin için kapsayıcı olarak yer işaretlerini kullanabilirsiniz. Bir <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesi, ekleme noktasını içerebilir veya belgenin tamamı kadar büyük olabilir. <xref:Microsoft.Office.Interop.Word.Bookmark>, <xref:Microsoft.Office.Interop.Word.Range> nesnesinden ayrı olarak ayarlanan aşağıdaki özelliklere sahiptir:

- Yer işaretini tasarım zamanında adı verebilirsiniz.

- <xref:Microsoft.Office.Interop.Word.Bookmark> nesneler belgeyle birlikte kaydedilir ve bu nedenle kod çalışmayı durdurduğu veya belgeniz kapalıyken silinmez.

- <xref:Microsoft.Office.Interop.Word.View> nesnesinin <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> özelliği **false** veya **true**olarak ayarlanarak, yer işaretleri gizlenebilir veya görünür hale getirilebilir.

  Visual Studio, <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimini sağlayarak <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesini genişletir. <xref:Microsoft.Office.Tools.Word.Bookmark> ana bilgisayar denetimi yerel bir <xref:Microsoft.Office.Interop.Word.Bookmark>gibi davranır, ancak ek olaylara ve veri bağlama yeteneklerine sahiptir. Verileri bir belge üzerinde bir yer işareti denetimine, verileri bir Windows formunda metin kutusu denetimine bağladığınızda aynı şekilde bağlayabilirsiniz. Daha fazla bilgi için bkz. [Bookmark Control](../vsto/bookmark-control.md).

## <a name="WordOMDocumentation"></a>Word nesne modeli belgelerini kullanın
 Word nesne modeli hakkında tüm bilgiler için, Word birincil birlikte çalışma derlemesi (PIA) başvurusuna ve Visual Basic for Applications (VBA) nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 PIA başvuru belgeleri Word için birincil birlikte çalışma derlemesindeki türleri açıklar. Bu belge şu konumdan edinilebilir: [Word 2010 birincil birlikte çalışma derleme başvurusu](../vsto/office-primary-interop-assemblies.md).

 PIA içindeki sınıflar ve arabirimler arasındaki farklar ve PIA içindeki olayların nasıl uygulandığı gibi, PIA 'ın tasarımı hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, VBA kodunda gösterilen Word nesne modelini belgeler. Daha fazla bilgi için bkz. [Word 2010 nesne modeli başvurusu](/office/vba/api/overview/Word/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, PIA sözcükteki türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki belge nesnesi, PIA kelimesinin <xref:Microsoft.Office.Interop.Word.Document> nesnesine karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio 'Yu kullanarak oluşturduğunuz bir Word projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic C# veya görsele çevirmeniz gerekir .

## <a name="see-also"></a>Ayrıca bkz.
- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Belgelerle çalışma](../vsto/working-with-documents.md)
- [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)
- [Tablolarla çalışma](../vsto/working-with-tables.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
