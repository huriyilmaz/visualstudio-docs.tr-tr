---
title: Excel nesne modeline genel bakış
description: Excel Microsoft Office kullanan çözümler geliştirmek için Excel nesne modeli tarafından sunulan nesnelerle etkileşime girebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 509378b13e48f21a1148d700addd9ac4e78985e9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825699"
---
# <a name="excel-object-model-overview"></a>Excel nesne modeline genel bakış
  Excel Microsoft Office kullanan çözümler geliştirmek için Excel nesne modeli tarafından sunulan nesnelerle etkileşim kurabilirsiniz. Bu konu, en önemli nesneleri tanıtır:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Nesne modeli Kullanıcı arabirimini yakından izler. <xref:Microsoft.Office.Interop.Excel.Application>Nesnesi tüm uygulamayı temsil eder ve her <xref:Microsoft.Office.Interop.Excel.Workbook> nesne bir nesne koleksiyonu içerir `Worksheet` . Buradan, hücreleri temsil eden ana soyutlama <xref:Microsoft.Office.Interop.Excel.Range> nesnesidir ve tek tek hücreler veya hücre gruplarıyla çalışmanıza olanak sağlar.

  Excel nesne modeline ek olarak, Visual Studio 'daki Office projeleri, Excel nesne modelindeki bazı nesneleri genişleten *konak öğeleri* ve *konak denetimleri* sağlar. Konak öğeleri ve konak denetimleri genişledikleri Excel nesneleri gibi davranır, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için bkz. Genişletilmiş nesneler ve [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) [kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md) .

  Bu konuda, Excel nesne modeline kısa bir genel bakış sunulmaktadır. Tüm Excel nesne modeli hakkında daha fazla bilgi edinmek için bkz. [Excel nesne modeli belgelerini kullanma](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Excel projesindeki nesnelere erişme
 Excel için yeni bir VSTO eklentisi projesi oluşturduğunuzda, Visual Studio otomatik olarak bir *ThisAddIn. vb* veya *ThisAddIn. cs* kod dosyası oluşturur. Veya kullanarak uygulama nesnesine erişebilirsiniz `Me.Application` `this.Application` .

 Excel için yeni bir belge düzeyi projesi oluşturduğunuzda, yeni bir Excel çalışma kitabı veya Excel şablonu projesi oluşturma seçeneğiniz vardır. Visual Studio, hem çalışma kitabı hem de şablon projeleri için yeni Excel projenizde aşağıdaki kod dosyalarını otomatik olarak oluşturur.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook. vb|ThisWorkbook. cs|
|Sayfa1. vb|Sayfa1. cs|
|Sheet2. vb|Sheet2. cs|
|Sheet3. vb|Sheet3. cs|

 Projenizdeki sınıfı,,, `Globals` `ThisWorkbook` `Sheet1` `Sheet2` veya `Sheet3` ilgili sınıfın dışından erişmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md). Aşağıdaki örnek, <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> `Sheet1` kodun `Sheet` *n* sınıflarından veya sınıfından birine yerleştirilmiş olmasına bakılmaksızın yöntemini çağırır `ThisWorkbook` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet82":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet82":::

 Excel belgesindeki veriler yüksek oranda yapılandırıldığı için, nesne modeli hiyerarşik ve kolay bir şekilde yapılandırılmıştır. Excel, etkileşim kurmak isteyebileceğiniz yüzlerce nesne sağlar, ancak kullanılabilir nesnelerin küçük bir alt kümesine odaklanarak nesne modelinde iyi bir başlangıç yapabilirsiniz. Bu nesneler aşağıdaki dört içerir:

- Uygulama

- Çalışma Kitabı

- Çalışma Sayfası

- Aralık

  Bu dört nesne ve üyeleri etrafında Excel merkezleriyle yapılan çalışmanın çoğu.

### <a name="application-object"></a>Uygulama nesnesi
 Excel <xref:Microsoft.Office.Interop.Excel.Application> nesnesi, Excel uygulamasının kendisini temsil eder. <xref:Microsoft.Office.Interop.Excel.Application>Nesnesi, çalışan uygulamayla ilgili bilgilerin, bu örneğe uygulanan seçeneklerin ve geçerli kullanıcı nesnelerinin örnek içinde açık olduğu hakkında harika bir bilgi sunar.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> <xref:Microsoft.Office.Interop.Excel.Application> Excel 'deki nesnesinin özelliğini **false** olarak ayarlamanız gerekir. Bu özelliğin false olarak ayarlanması, Excel 'In konak denetimlerinin olayları da dahil olmak üzere tüm olayları oluşturmasını engeller.

### <a name="workbook-object"></a>Çalışma kitabı nesnesi
 <xref:Microsoft.Office.Interop.Excel.Workbook>Nesnesi Excel uygulaması içindeki tek bir çalışma kitabını temsil eder.

 Visual Studio 'da Office geliştirme araçları, <xref:Microsoft.Office.Interop.Excel.Workbook> türü sağlayarak nesneyi genişletir <xref:Microsoft.Office.Tools.Excel.Workbook> . Bu tür, bir nesnenin tüm özelliklerine erişmenizi sağlar <xref:Microsoft.Office.Interop.Excel.Workbook> . Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Çalışma sayfası nesnesi
 <xref:Microsoft.Office.Interop.Excel.Worksheet>Nesne, koleksiyonun bir üyesidir <xref:Microsoft.Office.Interop.Excel.Worksheets> . Özelliklerinin, yöntemlerinin ve olaylarının birçoğu <xref:Microsoft.Office.Interop.Excel.Worksheet> veya nesneleri tarafından belirtilen üyelere benzerdir <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> .

 Excel bir <xref:Microsoft.Office.Interop.Excel.Sheets> nesnenin özelliği olarak bir koleksiyon sağlar <xref:Microsoft.Office.Interop.Excel.Workbook> . Koleksiyonun her üyesi <xref:Microsoft.Office.Interop.Excel.Sheets> bir <xref:Microsoft.Office.Interop.Excel.Worksheet> ya da bir <xref:Microsoft.Office.Interop.Excel.Chart> nesnedir.

 Visual Studio 'da Office geliştirme araçları, <xref:Microsoft.Office.Interop.Excel.Worksheet> türü sağlayarak nesneyi genişletir <xref:Microsoft.Office.Tools.Excel.Worksheet> . Bu tür, bir nesnenin tüm özelliklerine erişmenizi sağlar <xref:Microsoft.Office.Interop.Excel.Worksheet> ve yönetilen denetimleri barındırmak ve yeni olayları işlemek gibi yeni özelliklere de sahiptir. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Aralık nesnesi
 <xref:Microsoft.Office.Interop.Excel.Range>Nesnesi, Excel uygulamalarınızda en çok kullanacağınız nesnedir. Excel içindeki herhangi bir bölgeyi işleyebilmeniz için önce onu bir nesne olarak ifade etmeniz <xref:Microsoft.Office.Interop.Excel.Range> ve söz konusu aralığın yöntemleriyle ve özellikleriyle çalışmanız gerekir. Bir <xref:Microsoft.Office.Interop.Excel.Range> nesne, bir hücreyi, bir satırı, sütunu, bir veya daha fazla hücre bloğunu içeren bir hücre seçimini, hatta bir veya birden çok sayfada bir hücre grubunu temsil eder.

 Visual Studio <xref:Microsoft.Office.Interop.Excel.Range> , ve türlerini sağlayarak nesneyi genişletir <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> . Bu türler, bir nesneyle aynı özelliklerin çoğuna <xref:Microsoft.Office.Interop.Excel.Range> ve veri bağlama özelliği ve yeni olaylar gibi yeni özelliklere sahiptir. Daha fazla bilgi için bkz. [NamedRange Control](../vsto/namedrange-control.md) ve [XmlMappedRange Control](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a> Excel nesne modeli belgelerini kullanma
 Excel nesne modeli hakkında tüm bilgiler için Excel birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 Excel PIA başvuru belgeleri, Excel için birincil birlikte çalışma derlemesindeki türleri açıklar. Bu belge şu konumdan edinilebilir: [Excel 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md).

 PIA içindeki sınıflar ve arabirimler arasındaki farklar ve PIA 'teki olayların nasıl uygulandığı gibi, Excel PIA 'in tasarımı hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Excel nesne modelini Visual Basic for Applications (VBA) koduna açık olarak belgeler. Daha fazla bilgi için bkz. [Excel 2010 nesne modeli başvurusu](/office/vba/api/overview/Excel/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, Excel PIA içindeki türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki çalışma sayfası nesnesi <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel PIA içindeki nesneye karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio 'Yu kullanarak oluşturduğunuz bir Excel projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Excel çözümleri](../vsto/excel-solutions.md)|Excel Microsoft Office için belge düzeyinde özelleştirmeler ve VSTO eklentileri oluşturmayı açıklar.|
|[Aralıklar ile çalışma](../vsto/working-with-ranges.md)|Aralıklardan ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
|[Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)|Çalışma sayfalarıyla ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
|[Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)|Çalışma kitaplarıyla ortak görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|
