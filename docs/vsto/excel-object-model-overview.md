---
title: Excel Nesne modeline genel bakış
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649421"
---
# <a name="excel-object-model-overview"></a>Excel nesne modeline genel bakış
  Microsoft Office Excel'i kullanan çözümler geliştirmek için Excel nesnesi modeli tarafından sağlanan nesnelerle etkileşim kurabilirsiniz. Bu konu en önemli nesneleri tanır:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Nesne modeli kullanıcı arabirimini yakından izler. Nesne <xref:Microsoft.Office.Interop.Excel.Application> tüm uygulamayı temsil eder <xref:Microsoft.Office.Interop.Excel.Workbook> ve her `Worksheet` nesne bir nesne koleksiyonu içerir. Buradan, hücreleri temsil eden ana soyutlama, tek tek hücreler veya hücre gruplarıyla çalışmanızı sağlayan <xref:Microsoft.Office.Interop.Excel.Range> nesnedir.

  Visual Studio'daki Office projeleri, Excel nesnesi modeline ek olarak, Excel nesnesi modelindeki bazı nesneleri genişleten *ana bilgisayar öğeleri* ve ana bilgisayar *denetimleri* sağlar. Ana bilgisayar öğeleri ve ana bilgisayar denetimleri genişlettikleri Excel nesneleri gibi, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için genişletilmiş nesneler ve Ana Bilgisayar öğeleri ve ana bilgisayar denetimlerine genel bakış [kullanarak Excel'i otomatikleştir'e](../vsto/automating-excel-by-using-extended-objects.md) [bakın.](../vsto/host-items-and-host-controls-overview.md)

  Bu konu, Excel nesne modeline kısa bir genel bakış sağlar. Tüm Excel nesne modeli hakkında daha fazla bilgi edinebileceğiniz kaynaklar [için](#ExcelOMDocumentation)bkz.

## <a name="access-objects-in-an-excel-project"></a>Excel projesindeki nesnelere erişin
 Excel için yeni bir VSTO Eklenti projesi oluşturduğunuzda, Visual Studio otomatik olarak bir *ThisAddIn.vb* veya *ThisAddIn.cs* kod dosyası oluşturur. Uygulama nesnesi'ne `Me.Application` kullanarak `this.Application`veya .

 Excel için yeni bir belge düzeyinde proje oluşturduğunuzda, yeni bir Excel Çalışma Kitabı veya Excel Şablonu projesi oluşturma seçeneğiniz olur. Visual Studio, hem çalışma kitabı hem de şablon projeleri için yeni Excel projenizde otomatik olarak aşağıdaki kod dosyalarını oluşturur.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sayfa1.vb|Sheet1.cs|
|Sayfa2.vb|Sheet2.cs|
|Sayfa 3.vb|Sheet3.cs|

 Projenizdeki `Globals` sınıfı ilgili `ThisWorkbook` `Sheet1` `Sheet2`sınıfın dışından erişmek için `Sheet3` kullanabilirsiniz. Daha fazla bilgi için [Bkz. Office projelerindeki nesnelere Genel erişim.](../vsto/global-access-to-objects-in-office-projects.md) Aşağıdaki örnek, <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> kodun `Sheet1` `Sheet` *n* sınıflarından birine mi yoksa `ThisWorkbook` sınıfa mı yerleştirildiğine bakılmaksızın yöntemini çağırır.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Excel belgesindeki veriler yüksek oranda yapılandırılmış olduğundan, nesne modeli hiyerarşik ve basittir. Excel, etkileşimde bulunabileceğiniz yüzlerce nesne sağlar, ancak kullanılabilir nesnelerin küçük bir alt kümesine odaklanarak nesne modeline iyi bir başlangıç yapabilirsiniz. Bu nesneler aşağıdaki dört içerir:

- Uygulama

- Çalışma Kitabı

- Çalışma Sayfası

- Aralık

  Excel ile yapılan çalışmaların çoğu bu dört nesne ve üyeleri etrafında merkezler.

### <a name="application-object"></a>Uygulama nesnesi
 Excel <xref:Microsoft.Office.Interop.Excel.Application> nesnesi Excel uygulamasının kendisini temsil eder. Nesne, <xref:Microsoft.Office.Interop.Excel.Application> çalışan uygulama, bu örne uygulanan seçenekler ve örnek içinde geçerli kullanıcı nesneleri hakkında çok sayıda bilgi ortaya çıkarır.

> [!NOTE]
> Excel'deki <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> nesnenin özelliğini <xref:Microsoft.Office.Interop.Excel.Application> **false**olarak ayarlamamalısınız. Bu özelliği yanlış olarak ayarlamak, Excel'in ana bilgisayar denetimleri olayları da dahil olmak üzere herhangi bir olayı yükseltmesini engeller.

### <a name="workbook-object"></a>Çalışma kitabı nesnesi
 Nesne, <xref:Microsoft.Office.Interop.Excel.Workbook> Excel uygulaması içinde tek bir çalışma kitabını temsil eder.

 Visual Studio'daki Office geliştirme <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Workbook> araçları, türü sağlayarak nesneyi genişletir. Bu tür, bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesnenin tüm özelliklerine erişmenizi sağlar. Daha fazla bilgi için [Çalışma Kitabı ana bilgisayar öğesine](../vsto/workbook-host-item.md)bakın.

### <a name="worksheet-object"></a>Çalışma sayfası nesnesi
 Nesne <xref:Microsoft.Office.Interop.Excel.Worksheet> koleksiyonun <xref:Microsoft.Office.Interop.Excel.Worksheets> bir üyesidir. Özellikleri, yöntemleri ve olayları <xref:Microsoft.Office.Interop.Excel.Worksheet> çoğu aynı veya üyeleri <xref:Microsoft.Office.Interop.Excel.Application> veya <xref:Microsoft.Office.Interop.Excel.Workbook> nesneleri tarafından sağlanan benzer.

 Excel bir <xref:Microsoft.Office.Interop.Excel.Sheets> <xref:Microsoft.Office.Interop.Excel.Workbook> nesnenin özelliği olarak bir koleksiyon sağlar. Koleksiyonun <xref:Microsoft.Office.Interop.Excel.Sheets> her üyesi bir <xref:Microsoft.Office.Interop.Excel.Worksheet> veya <xref:Microsoft.Office.Interop.Excel.Chart> nesnedir.

 Visual Studio'daki Office geliştirme <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Tools.Excel.Worksheet> araçları, türü sağlayarak nesneyi genişletir. Bu tür, bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnenin tüm özelliklerine ve yönetilen denetimleri barındırma ve yeni olayları işleme olanağı gibi yeni özelliklere erişmenizi sağlar. Daha fazla bilgi için [Çalışma Sayfası ana bilgisayar öğesine](../vsto/worksheet-host-item.md)bakın.

### <a name="range-object"></a>Aralık nesnesi
 Nesne, <xref:Microsoft.Office.Interop.Excel.Range> Excel uygulamalarınızda en çok kullanacağınız nesnedir. Excel'deki herhangi bir bölgeyi işlemeden önce, <xref:Microsoft.Office.Interop.Excel.Range> bunu bir nesne olarak ifade etmeli ve bu aralığın yöntemleri ve özellikleriyle çalışmanız gerekir. Bir <xref:Microsoft.Office.Interop.Excel.Range> nesne bir hücreyi, bir satırı, bir sütunu, bitişik veya bitişik olmayan bir hücre bloğu içeren bir hücre seçimini ve hatta birden çok sayfadaki bir hücre grubunu temsil eder.

 Visual Studio <xref:Microsoft.Office.Interop.Excel.Range> <xref:Microsoft.Office.Tools.Excel.NamedRange> ve <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> türleri sağlayarak nesne genişletir. Bu türler, bir <xref:Microsoft.Office.Interop.Excel.Range> nesneyle aynı özelliklerin çoğunun yanı sıra veri bağlama özelliği ve yeni olaylar gibi yeni özelliklere sahiptir. Daha fazla bilgi için [Bkz. NamedRange denetimi](../vsto/namedrange-control.md) ve [XmlMappedRange denetimi.](../vsto/xmlmappedrange-control.md)

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Excel nesne modeli belgelerini kullanma
 Excel nesne modeli hakkında tam bilgi için Excel birincil interop derleme (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil interop montaj başvurusu
 Excel PIA başvuru belgeleri, Excel için birincil interop derlemesindeki türleri açıklar. Bu dokümantasyon aşağıdaki konumdan edinilebilir: [Excel 2010 birincil interop derleme başvurusu.](office-primary-interop-assemblies.md)

 Pia'daki sınıflar ve arabirimler arasındaki farklar ve PIA'daki olayların nasıl uygulandığı gibi Excel PIA'sının tasarımı hakkında daha fazla bilgi için Bkz. [Office birincil interop derlemelerinde sınıflara ve arabirimlerine genel bakış.](/previous-versions/office/office-12/ms247299(v=office.12))

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Visual Basic for Applications (VBA) koduna maruz kaldığında Excel nesne modelini belgeler. Daha fazla bilgi için [Bkz. Excel 2010 nesne modeli başvurusu.](/office/vba/api/overview/Excel/object-model)

 VBA nesne modeli başvurusundaki tüm nesneler ve üyeler Excel PIA'daki tür ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki Çalışma Sayfası nesnesi Excel PIA'daki <xref:Microsoft.Office.Interop.Excel.Worksheet> nesneye karşılık gelir. VBA nesne modeli başvurusu çoğu özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio kullanarak oluşturduğunuz bir Excel projesinde kullanmak istiyorsanız, bu başvuruda VBA kodunu Visual Basic veya Visual C# adresine çevirmeniz gerekir.

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Excel çözümleri](../vsto/excel-solutions.md)|Microsoft Office Excel için belge düzeyinde özelleştirmeler ve VSTO Eklentileri nasıl oluşturabileceğinizi açıklar.|
|[Aralıklarla çalışın](../vsto/working-with-ranges.md)|Aralıklarla ortak görevlerin nasıl gerçekleştirildiğini gösteren örnekler sağlar.|
|[Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)|Çalışma sayfaları ile ortak görevlerin nasıl gerçekleştirildiğini gösteren örnekler sağlar.|
|[Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)|Çalışma kitaplarıyla ortak görevlerin nasıl gerçekleştirildiğini gösteren örnekler sağlar.|
