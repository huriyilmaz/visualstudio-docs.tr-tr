---
title: Word nesne modeline genel bakış
description: Word nesne modeli, Word için birincil birlikte çalışma derlemesinde sağlanan ve Word ad alanında tanımlanan sınıflardan ve arabirimlerden oluşur.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 919253f271da3c8f7d486ea9bfd8706c2bd66c71
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068471"
---
# <a name="word-object-model-overview"></a>Word nesne modeline genel bakış
  Visual Studio'da Word çözümleri Visual Studio Word nesne modeliyle etkileşime geçmeniz gerekir. Bu nesne modeli, Word için birincil birlikte çalışma derlemesinde sağlanan ve ad alanında tanımlanan sınıflardan ve arabirimlerden <xref:Microsoft.Office.Interop.Word> oluşur.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Bu konu, Word nesne modeline kısa bir genel bakış sağlar. Tüm Word nesne modeli hakkında daha fazla bilgi edinebilirsiniz kaynakları için [Bkz. Word nesne modeli belgelerini kullanma.](#WordOMDocumentation)

 Belirli görevleri gerçekleştirmek için Word nesne modelini kullanma hakkında bilgi için aşağıdaki konulara bakın:

- [Belgelerle çalışma](../vsto/working-with-documents.md)

- [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)

- [Tablolarla çalışma](../vsto/working-with-tables.md)

## <a name="understand-the-word-object-model"></a><a name="understanding"></a> Word nesne modelini anlama
 Word, etkileşim kurabilirsiniz yüzlerce nesne sağlar. Bu nesneler, kullanıcı arabirimini yakından izleyen bir hiyerarşide düzenlenir. Hiyerarşinin en üstünde nesnesi <xref:Microsoft.Office.Interop.Word.Application> yer alır. Bu nesne geçerli Word örneğini temsil eder. nesnesi <xref:Microsoft.Office.Interop.Word.Application> , <xref:Microsoft.Office.Interop.Word.Document> , ve <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Bookmark> nesnelerini <xref:Microsoft.Office.Interop.Word.Range> içerir. Bu nesnelerin her biri, nesneyi işlemek ve nesneyle etkileşim kurmak için erişebilirsiniz birçok yöntem ve özele sahiptir.

 Aşağıdaki çizimde, Word nesne modelinin hiyerarşisinde bu nesnelerin bir görünümü gösterilmiştir.

 ![Word Nesne Modeli grafiği](../vsto/media/wrwordobjectmodel.gif "Word nesne modeli grafiği")

 İlk bakışta nesneler çakışıyor gibi görünür. Örneğin, <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Interop.Word.Selection> nesneleri hem nesnenin üyesi hem de <xref:Microsoft.Office.Interop.Word.Application> nesnesi aynı zamanda nesnenin bir <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> üyesidir. Hem hem <xref:Microsoft.Office.Interop.Word.Document> de <xref:Microsoft.Office.Interop.Word.Selection> nesneleri ve <xref:Microsoft.Office.Interop.Word.Bookmark> nesnelerini <xref:Microsoft.Office.Interop.Word.Range> içerir. Aynı nesne türüne erişmenin birden çok yolu olduğundan çakışma vardır. Örneğin, bir nesneye biçimlendirme uygulayabilirsiniz; ancak geçerli seçim aralığına, belirli bir paragrafa, bir bölüme veya belgenin tamamına <xref:Microsoft.Office.Interop.Word.Range> erişmek istiyor olabilir.

 Aşağıdaki bölümlerde üst düzey nesneler ve birbirleriyle nasıl etkileşime geçmeleri açıklanmaktadır. Bu nesneler şunlardır:

- Uygulama nesnesi

- Belge nesnesi

- Seçim nesnesi

- Aralık nesnesi

- Yer işareti nesnesi

  Word nesne modeline ek olarak, Office projelerini Visual Studio  word  nesne modelinde bazı nesneleri genişleten konak öğeleri ve konak denetimleri sağlar. Konak öğeleri ve konak denetimleri genişletildikleri Word nesneleri gibi davranır, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için [bkz. Genişletilmiş nesneleri kullanarak Word'u otomatikleştirme ve](../vsto/automating-word-by-using-extended-objects.md) Konak öğeleri [ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

### <a name="application-object"></a>Uygulama nesnesi
 nesnesi <xref:Microsoft.Office.Interop.Word.Application> Word uygulamasını temsil eder ve diğer tüm nesnelerin üst öğesidir. Üyeleri genellikle Word'e bir bütün olarak uygulanır. Word ortamını kontrol etmek için özelliklerini ve yöntemlerini kullanabilirsiniz.

 Eklenti VSTO sınıfını kullanarak <xref:Microsoft.Office.Interop.Word.Application> nesnesine `Application` `ThisAddIn` erişebilirsiniz. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Belge düzeyi projelerde, sınıfının <xref:Microsoft.Office.Interop.Word.Application> özelliğini kullanarak <xref:Microsoft.Office.Tools.Word.Document.Application%2A> nesnesine `ThisDocument` erişebilirsiniz.

### <a name="document-object"></a>Belge nesnesi
 nesnesi, <xref:Microsoft.Office.Interop.Word.Document> Word programlamanın merkezindedir. Bir belgeyi ve tüm içeriğini temsil eder. Bir belgeyi açıp yeni bir belge ekleyebilirsiniz. Bu, nesnenin <xref:Microsoft.Office.Interop.Word.Document> koleksiyonuna eklenen yeni <xref:Microsoft.Office.Interop.Word.Documents> bir nesne <xref:Microsoft.Office.Interop.Word.Application> oluşturur. Odak noktası olan belgeye etkin belge denir. Nesnenin <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> özelliğiyle temsil <xref:Microsoft.Office.Interop.Word.Application> eder.

 Office geliştirme araçları Visual Studio <xref:Microsoft.Office.Interop.Word.Document> sağlayarak nesneyi <xref:Microsoft.Office.Tools.Word.Document> genişletmektedir. Bu tür, *bir nesnenin tüm* özelliklerine erişmenizi ve ek olaylar ve yönetilen denetimler ekleme olanağı <xref:Microsoft.Office.Interop.Word.Document> ekleyen bir konak öğesidir.

 Belge düzeyi bir proje ekleyebilirsiniz, projenizin <xref:Microsoft.Office.Tools.Word.Document> oluşturulan sınıfını kullanarak `ThisDocument` üyelere erişebilirsiniz. Ana bilgisayar öğesinin üyelerine, sınıftaki koddan Me veya bu anahtar sözcükleri kullanarak veya sınıfın dışındaki <xref:Microsoft.Office.Tools.Word.Document>  bir  `ThisDocument` `Globals.ThisDocument` koddan `ThisDocument` erişebilirsiniz. Daha fazla bilgi için [bkz. Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md) Örneğin, belgede ilk paragrafı seçmek için aşağıdaki kodu kullanın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet120":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet120":::

 Eklenti VSTO içinde, çalışma zamanında <xref:Microsoft.Office.Tools.Word.Document> konak öğeleri oluşturabilirsiniz. Oluşturulan konak öğesini ilişkili belgeye denetim eklemek için kullanabilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="selection-object"></a>Seçim nesnesi
 nesnesi <xref:Microsoft.Office.Interop.Word.Selection> şu anda seçili olan alanı temsil eder. Word kullanıcı arabiriminde kalın metin gibi bir işlem gerçekleştirerek metni seçer veya vurgular ve ardından biçimlendirmeyi uygulayabilirsiniz. Nesnesi <xref:Microsoft.Office.Interop.Word.Selection> her zaman bir belgede yer alan bir nesnedir. Hiçbir şey seçilmezse, ekleme noktasını temsil eder. Ayrıca, bir seçim bitişik olmayan birden çok metin bloğu kapsayıyor olabilir.

### <a name="range-object"></a>Aralık nesnesi
 nesnesi belgedeki bitişik bir alanı temsil eder ve başlangıç karakteri konumu ve bitiş karakteri <xref:Microsoft.Office.Interop.Word.Range> konumu ile tanımlanır. Tek bir nesneyle sınırlı <xref:Microsoft.Office.Interop.Word.Range> olmaz. Aynı belgede birden <xref:Microsoft.Office.Interop.Word.Range> çok nesne tanımlayabilirsiniz. Bir <xref:Microsoft.Office.Interop.Word.Range> nesne aşağıdaki özelliklere sahiptir:

- Yalnızca ekleme noktasını, bir metin aralığını veya belgenin tamamını kapsayabilirsiniz.

- Boşluklar, sekme karakterleri ve paragraf işaretleri gibi yazdırilmeyen karakterleri içerir.

- Geçerli seçimle temsil edilen alan veya geçerli seçimden farklı bir alanı temsil ediyor olabilir.

- Belge, her zaman görünür olan bir seçimden farklı olarak görünür değildir.

- Bir belgeyle birlikte kayıtlı değildir ve yalnızca kod çalışırken mevcuttur.

  Bir aralığın sonuna metin eklerken Word, eklenen metni içerecek şekilde aralığı otomatik olarak genişleter.

### <a name="content-control-objects"></a>İçerik denetimi nesneleri
 , <xref:Microsoft.Office.Interop.Word.ContentControl> Word belgelerinde metin girişini ve sunumunu ve diğer içerik türlerini denetlemeniz için bir yol sağlar. , Zengin metin denetimi, tarih seçici veya birleşik giriş kutusu gibi Word belgelerinde kullanım için iyileştirilmiş birkaç farklı kullanıcı arabirimi <xref:Microsoft.Office.Interop.Word.ContentControl> türü display olabilir. Kullanıcıların belge veya <xref:Microsoft.Office.Interop.Word.ContentControl> şablonun bölümlerini düzenlemesini önlemek için de kullanabilirsiniz.

 Visual Studio, nesneyi birkaç <xref:Microsoft.Office.Interop.Word.ContentControl> farklı konak denetimine genişleter. Nesne, içerik denetimleri için kullanılabilen farklı kullanıcı arabirimi türlerinden herhangi birini görüntüleyene Visual Studio her içerik denetimi için <xref:Microsoft.Office.Interop.Word.ContentControl> farklı bir tür sağlar. Örneğin, zengin metin denetimi oluşturmak için veya tarih seçici oluşturmak için <xref:Microsoft.Office.Tools.Word.RichTextContentControl> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> kullanabilirsiniz. Bu konak denetimleri yerel gibi <xref:Microsoft.Office.Interop.Word.ContentControl> davranır, ancak ek olaylar ve veri bağlama özelliklerine sahiptir. Daha fazla bilgi için bkz. [İçerik denetimleri.](../vsto/content-controls.md)

### <a name="bookmark-object"></a>Yer işareti nesnesi
 nesnesi, hem başlangıç konumu hem de bitiş konumu olan bir <xref:Microsoft.Office.Interop.Word.Bookmark> belge içinde bitişik bir alanı temsil eder. Yer işaretlerini kullanarak bir belgede bir konumu veya belge içinde metin için kapsayıcı olarak işaret atabilirsiniz. Nesne <xref:Microsoft.Office.Interop.Word.Bookmark> ekleme noktasından veya belgenin tamamı kadar büyük olabilir. , <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesini nesnesinden ayrı olarak ayar eden aşağıdaki özelliklere <xref:Microsoft.Office.Interop.Word.Range> sahiptir:

- Yer işaretini tasarım zamanında ad veabilirsiniz.

- <xref:Microsoft.Office.Interop.Word.Bookmark> nesneleri belgeyle birlikte kaydedilir ve bu nedenle kod çalışmadan veya belgeniz kapatılana kadar silinmez.

- Yer işaretleri nesnenin özelliği false veya true olarak ayarlarak <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> <xref:Microsoft.Office.Interop.Word.View> gizlenerek veya **görünür** hale **olabilir.**

  Visual Studio, konak denetimi <xref:Microsoft.Office.Interop.Word.Bookmark> sağlayarak nesneyi <xref:Microsoft.Office.Tools.Word.Bookmark> genişleter. Konak <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi yerel bir gibi <xref:Microsoft.Office.Interop.Word.Bookmark> davranır, ancak ek olaylar ve veri bağlama özelliklerine sahip olur. Verileri bir belge üzerinde yer işareti denetimine bağlamak için, verileri bir Form'daki bir metin kutusu denetimine bağlamayla Windows sekleyebilirsiniz. Daha fazla bilgi için bkz. [Yer işareti denetimi.](../vsto/bookmark-control.md)

## <a name="use-the-word-object-model-documentation"></a><a name="WordOMDocumentation"></a> Word nesne modeli belgelerini kullanma
 Word nesne modeli hakkında tam bilgi için Word birincil birlikte çalışma derlemesi (PIA) başvurusuna ve Visual Basic for Applications (VBA) nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 Word PIA başvuru belgeleri, Word için birincil birlikte çalışma derlemesinde türleri açıklar. Bu belgeler şu konumdan kullanılabilir: [Word 2010 birincil birlikte çalışma derleme başvurusu.](../vsto/office-primary-interop-assemblies.md)

 pıa içindeki sınıflar ve arabirimler arasındaki farklar ve pıa içindeki olayların nasıl uygulandığı gibi, pıa 'ın tasarımı hakkında daha fazla bilgi için, bkz. [Office primary ınterop derlemelerindeki sınıflara ve arayüzlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, VBA kodunda gösterilen Word nesne modelini belgeler. Daha fazla bilgi için bkz. [Word 2010 nesne modeli başvurusu](/office/vba/api/overview/Word/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, PIA sözcükteki türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki belge nesnesi, <xref:Microsoft.Office.Interop.Word.Document> PIA kelimesinin nesnesine karşılık gelir. vba nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, bunları Visual Studio kullanarak oluşturduğunuz bir Word projesinde kullanmak istiyorsanız, bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [birincil birlikte çalışma derlemelerini Office](../vsto/office-primary-interop-assemblies.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Belgelerle çalışma](../vsto/working-with-documents.md)
- [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)
- [Tablolarla çalışma](../vsto/working-with-tables.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
