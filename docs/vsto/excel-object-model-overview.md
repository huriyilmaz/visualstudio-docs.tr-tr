---
title: Excel nesne modeline genel bakış
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
ms.openlocfilehash: cf81dea230c2cfc33eb19ca001d8c9ed06b0489c
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661854"
---
# <a name="excel-object-model-overview"></a>Excel nesne modeline genel bakış
  Excel Microsoft Office kullanan çözümler geliştirmek için Excel nesne modeli tarafından sunulan nesnelerle etkileşim kurabilirsiniz. Bu konu, en önemli nesneleri tanıtır:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Nesne modeli Kullanıcı arabirimini yakından izler. <xref:Microsoft.Office.Interop.Excel.Application> nesnesi tüm uygulamayı temsil eder ve her bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesi `Worksheet` nesnelerinin bir koleksiyonunu içerir. Buradan, hücreleri temsil eden ana soyutlama <xref:Microsoft.Office.Interop.Excel.Range> nesnesidir ve tek tek hücreler veya hücre gruplarıyla çalışmanıza olanak sağlar.

  Excel nesne modeline ek olarak, Visual Studio 'daki Office projeleri, Excel nesne modelindeki bazı nesneleri genişleten *konak öğeleri* ve *konak denetimleri* sağlar. Konak öğeleri ve konak denetimleri genişledikleri Excel nesneleri gibi davranır, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için bkz. Genişletilmiş nesneler ve [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) [kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md) .

  Bu konuda, Excel nesne modeline kısa bir genel bakış sunulmaktadır. Tüm Excel nesne modeli hakkında daha fazla bilgi edinmek için bkz. [Excel nesne modeli belgelerini kullanma](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Excel projesindeki nesnelere erişme
 Excel için yeni bir VSTO eklentisi projesi oluşturduğunuzda, Visual Studio otomatik olarak bir *ThisAddIn. vb* veya *ThisAddIn.cs* kod dosyası oluşturur. `Me.Application` veya `this.Application`kullanarak uygulama nesnesine erişebilirsiniz.

 Excel için yeni bir belge düzeyi projesi oluşturduğunuzda, yeni bir Excel çalışma kitabı veya Excel şablonu projesi oluşturma seçeneğiniz vardır. Visual Studio, hem çalışma kitabı hem de şablon projeleri için yeni Excel projenizde aşağıdaki kod dosyalarını otomatik olarak oluşturur.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook. vb|ThisWorkbook.cs|
|Sayfa1. vb|Sheet1.cs|
|Sheet2. vb|Sheet2.cs|
|Sheet3. vb|Sheet3.cs|

 Projenizdeki `Globals` sınıfını, ilgili sınıfın dışından `ThisWorkbook`, `Sheet1`, `Sheet2`veya `Sheet3` erişmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md). Aşağıdaki örnek, kodun `Sheet`*n* sınıflarından veya `ThisWorkbook` sınıfından birine yerleştirilmiş olup olmamasına bakılmaksızın `Sheet1` <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> yöntemini çağırır.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Excel belgesindeki veriler yüksek oranda yapılandırıldığı için, nesne modeli hiyerarşik ve kolay bir şekilde yapılandırılmıştır. Excel, etkileşim kurmak isteyebileceğiniz yüzlerce nesne sağlar, ancak kullanılabilir nesnelerin küçük bir alt kümesine odaklanarak nesne modelinde iyi bir başlangıç yapabilirsiniz. Bu nesneler aşağıdaki dört içerir:

- Uygulama

- Çalışma Kitabı

- Çalışma Sayfası

- Aralık

  Bu dört nesne ve üyeleri etrafında Excel merkezleriyle yapılan çalışmanın çoğu.

### <a name="application-object"></a>Uygulama nesnesi
 Excel <xref:Microsoft.Office.Interop.Excel.Application> nesnesi, Excel uygulamasının kendisini temsil eder. <xref:Microsoft.Office.Interop.Excel.Application> nesnesi, çalışan uygulama, bu örneğe uygulanan seçenekler ve örnek içinde açık olan geçerli kullanıcı nesneleri hakkında harika bir bilgi sunar.

> [!NOTE]
> Excel 'de <xref:Microsoft.Office.Interop.Excel.Application> nesnesinin <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> özelliğini **false**olarak ayarlamanız gerekir. Bu özelliğin false olarak ayarlanması, Excel 'In konak denetimlerinin olayları da dahil olmak üzere tüm olayları oluşturmasını engeller.

### <a name="workbook-object"></a>Çalışma kitabı nesnesi
 <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesi Excel uygulaması içindeki tek bir çalışma kitabını temsil eder.

 Visual Studio 'daki Office geliştirme araçları, <xref:Microsoft.Office.Tools.Excel.Workbook> türünü sağlayarak <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesini genişletir. Bu tür, bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesinin tüm özelliklerine erişmenizi sağlar. Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Çalışma sayfası nesnesi
 <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesi <xref:Microsoft.Office.Interop.Excel.Worksheets> koleksiyonunun bir üyesidir. <xref:Microsoft.Office.Interop.Excel.Worksheet> özellikler, Yöntemler ve olayların birçoğu, <xref:Microsoft.Office.Interop.Excel.Application> veya <xref:Microsoft.Office.Interop.Excel.Workbook> nesneleri tarafından belirtilen üyelere benzerdir.

 Excel, bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesinin özelliği olarak bir <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyonu sağlar. <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyonun her bir üyesi bir <xref:Microsoft.Office.Interop.Excel.Worksheet> ya da <xref:Microsoft.Office.Interop.Excel.Chart> nesnesidir.

 Visual Studio 'daki Office geliştirme araçları, <xref:Microsoft.Office.Tools.Excel.Worksheet> türünü sağlayarak <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesini genişletir. Bu tür, bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesinin tüm özelliklerine erişmenizi sağlar ve yönetilen denetimleri barındırabilme ve yeni olayları işleyebilme gibi yeni özellikler sunar. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Aralık nesnesi
 <xref:Microsoft.Office.Interop.Excel.Range> nesnesi, Excel uygulamalarınızda en çok kullanacağınız nesnedir. Excel içindeki herhangi bir bölgeyi işleyebilmeniz için önce onu <xref:Microsoft.Office.Interop.Excel.Range> nesne olarak ifade etmeniz ve bu aralığın yöntemleri ve özellikleriyle çalışmanız gerekir. <xref:Microsoft.Office.Interop.Excel.Range> nesnesi, bir hücreyi, bir satırı, sütunu, bir veya birden çok hücre bloğunu içeren bir hücre seçimini, hatta bir veya birden çok sayfada bir hücre grubunu temsil eder.

 Visual Studio, <xref:Microsoft.Office.Tools.Excel.NamedRange> ve <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> türlerini sağlayarak <xref:Microsoft.Office.Interop.Excel.Range> nesnesini genişletir. Bu türler <xref:Microsoft.Office.Interop.Excel.Range> nesne ile aynı özelliklerin çoğuna ve veri bağlama özelliği ve yeni olaylar gibi yeni özelliklerden oluşur. Daha fazla bilgi için bkz. [NamedRange Control](../vsto/namedrange-control.md) ve [XmlMappedRange Control](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a>Excel nesne modeli belgelerini kullanma
 Excel nesne modeli hakkında tüm bilgiler için Excel birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 Excel PIA başvuru belgeleri, Excel için birincil birlikte çalışma derlemesindeki türleri açıklar. Bu belge şu konumdan edinilebilir: [Excel 2010 birincil birlikte çalışma derleme başvurusu](/visualstudio/vsto/office-primary-interop-assemblies).

 PIA içindeki sınıflar ve arabirimler arasındaki farklar ve PIA 'teki olayların nasıl uygulandığı gibi, Excel PIA 'in tasarımı hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Excel nesne modelini Visual Basic for Applications (VBA) koduna açık olarak belgeler. Daha fazla bilgi için bkz. [Excel 2010 nesne modeli başvurusu](/office/vba/api/overview/Excel/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, Excel PIA içindeki türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki çalışma sayfası nesnesi Excel PIA 'teki <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesine karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, bunları görsel kullanarak oluşturduğunuz bir Excel projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya C# görsele çevirmeniz gerekir Stu.

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Excel çözümleri](../vsto/excel-solutions.md)|Excel Microsoft Office için belge düzeyinde özelleştirmeler ve VSTO eklentileri oluşturmayı açıklar.|
|[Aralıklar ile çalışma](../vsto/working-with-ranges.md)|Aralıklardan ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
|[Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)|Çalışma sayfalarıyla ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
|[Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)|Çalışma kitaplarıyla ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
