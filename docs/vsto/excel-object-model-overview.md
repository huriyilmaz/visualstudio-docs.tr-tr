---
title: Excel Nesne modeline genel bakış
description: Excel nesne modeli tarafından sağlanan nesnelerle etkileşim kurarak Microsoft Office Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5c37a0251d9414871e568275bdb0b94bb55e5c401487e843186186105175d82e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352116"
---
# <a name="excel-object-model-overview"></a>Excel modeline genel bakış
  Microsoft Office Excel kullanan çözümler geliştirmek için, Excel nesne modeli tarafından sağlanan nesnelerle etkileşim kurabilirsiniz. Bu konu başlığında en önemli nesneler tanıtlanmıştır:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Nesne modeli kullanıcı arabirimini yakından izler. nesnesi <xref:Microsoft.Office.Interop.Excel.Application> uygulamanın tamamını temsil eder ve <xref:Microsoft.Office.Interop.Excel.Workbook> her nesne bir nesne koleksiyonu `Worksheet` içerir. Buradan, hücreleri temsil eden temel soyutlama, tek tek hücrelerle veya hücre <xref:Microsoft.Office.Interop.Excel.Range> gruplarıyla çalışmana olanak sağlayan nesnesidir.

  Excel nesne modeline ek olarak, Office projelerinde Visual Studio nesne modelinde  bazı  nesneleri genişleten konak öğeleri ve konak denetimleri Excel sağlar. Konak öğeleri ve konak denetimleri, Excel nesneleri gibi davranır, ancak veri bağlama özellikleri ve ek olaylar gibi ek işlevlere de sahiptir. Daha fazla bilgi için [bkz. Genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md) otomatikleştirme ve Konak öğeleri ve konak [denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

  Bu konu, nesne modeline kısa bir Excel genel bakış sağlar. Nesne modelinin tamamı hakkında daha fazla bilgi Excel kaynaklar için [bkz. Excel nesne modeli belgelerini kullanma.](#ExcelOMDocumentation)

## <a name="access-objects-in-an-excel-project"></a>Bir projedeki nesnelere Excel erişme
 Excel için yeni VSTO Eklenti projesi oluşturursanız, Visual Studio bir *ThisAddIn.vb* veya *ThisAddIn.cs kod* dosyası oluşturur. Application nesnesine veya kullanarak `Me.Application` `this.Application` erişebilirsiniz.

 Excel için yeni bir belge düzeyi proje ekleyebilirsiniz. Excel Çalışma Kitabı veya Excel Şablon projesi oluşturma seçeneğiniz vardır. Visual Studio çalışma kitabı ve şablon projeleri için yeni Excel projesinde aşağıdaki kod dosyalarını otomatik olarak oluşturur.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sayfa1.vb|Sheet1.cs|
|Sayfa2.vb|Sheet2.cs|
|Sayfa3.vb|Sheet3.cs|

 İlgili sınıfın `Globals` dışından , , veya 'a `ThisWorkbook` erişmek `Sheet1` için `Sheet2` `Sheet3` projenizin sınıfını kullanabilirsiniz. Daha fazla bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md) Aşağıdaki örnek, kodun n sınıflardan biri veya sınıfına yerleştirilip <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> `Sheet1` yerleştirilmilip `Sheet`  yerleştirilmse bile yöntemini `ThisWorkbook` çağırabilir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet82":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet82":::

 Bir belgede yer alan Excel yüksek oranda yapılandırılmış olduğundan nesne modeli hiyerarşik ve basittir. Excel etkileşim kurmak istediğiniz yüzlerce nesne sağlar, ancak kullanılabilir nesnelerin küçük bir alt kümesine odaklanarak nesne modeline iyi bir başlangıç elde edersiniz. Bu nesneler şunlardır:

- Uygulama

- Çalışma Kitabı

- Çalışma Sayfası

- Aralık

  Yapılan çalışmaların büyük bir Excel bu dört nesne ve üyeleri çevresinde merkezleri vardır.

### <a name="application-object"></a>Uygulama nesnesi
 Excel <xref:Microsoft.Office.Interop.Excel.Application> nesnesi, uygulamanın Excel temsil eder. nesnesi çalışan uygulama, bu örnek için uygulanan seçenekler ve örnek içinde açık olan geçerli kullanıcı nesneleri hakkında <xref:Microsoft.Office.Interop.Excel.Application> çok fazla bilgi sunar.

> [!NOTE]
> içinde nesnesinin <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> özelliğini false <xref:Microsoft.Office.Interop.Excel.Application> olarak Excel **değil.** Bu özelliğin false olarak Excel, konak denetimlerinin olayları da dahil olmak üzere herhangi bir olay ortaya çıktısını önler.

### <a name="workbook-object"></a>Çalışma kitabı nesnesi
 nesnesi, <xref:Microsoft.Office.Interop.Excel.Workbook> uygulamanın içindeki tek bir çalışma kitabını Excel temsil eder.

 Office geliştirme araçları Visual Studio <xref:Microsoft.Office.Interop.Excel.Workbook> sağlayarak nesneyi <xref:Microsoft.Office.Tools.Excel.Workbook> genişletmektedir. Bu tür, bir nesnenin tüm özelliklerine erişmeni <xref:Microsoft.Office.Interop.Excel.Workbook> sağlar. Daha fazla bilgi için bkz. [Çalışma kitabı konak öğesi.](../vsto/workbook-host-item.md)

### <a name="worksheet-object"></a>Çalışma sayfası nesnesi
 <xref:Microsoft.Office.Interop.Excel.Worksheet>nesnesi koleksiyonun bir <xref:Microsoft.Office.Interop.Excel.Worksheets> üyesidir. özelliklerinin, yöntemlerinin ve olaylarının <xref:Microsoft.Office.Interop.Excel.Worksheet> çoğu, veya nesneleri tarafından sağlanan üyelerle aynıdır veya <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> benzerdir.

 Excel, <xref:Microsoft.Office.Interop.Excel.Sheets> bir nesnenin özelliği olarak bir koleksiyon <xref:Microsoft.Office.Interop.Excel.Workbook> sağlar. Koleksiyonun her <xref:Microsoft.Office.Interop.Excel.Sheets> üyesi bir veya <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> nesnesidir.

 Office geliştirme araçları Visual Studio <xref:Microsoft.Office.Interop.Excel.Worksheet> sağlayarak nesneyi <xref:Microsoft.Office.Tools.Excel.Worksheet> genişletmektedir. Bu tür, bir nesnenin tüm özelliklerine ve yönetilen denetimleri barındırma ve yeni olayları işleme <xref:Microsoft.Office.Interop.Excel.Worksheet> gibi yeni özelliklere erişmenizi sağlar. Daha fazla bilgi için bkz. [Çalışma sayfası konak öğesi.](../vsto/worksheet-host-item.md)

### <a name="range-object"></a>Aralık nesnesi
 nesnesi, <xref:Microsoft.Office.Interop.Excel.Range> uygulama uygulamalarınızı en çok Excel nesnesidir. Uygulama içinde herhangi bir bölgeyi Excel önce bunu bir nesne olarak ifade etmeli ve bu aralığın <xref:Microsoft.Office.Interop.Excel.Range> yöntemleri ve özellikleriyle çalışmanız gerekir. Nesne <xref:Microsoft.Office.Interop.Excel.Range> bir hücreyi, satırı, sütunu, bir veya daha fazla hücre bloğu içeren hücre seçimini temsil eder. Bu hücre bitişik olabilir veya olmayacaktır, hatta birden çok sayfada bir hücre grubu içerir.

 Visual Studio ve <xref:Microsoft.Office.Interop.Excel.Range> türlerini sağlayarak nesnesini <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> genişleter. Bu türler, bir nesneyle aynı özelliklerin yanı sıra veri bağlama özelliği ve yeni olaylar <xref:Microsoft.Office.Interop.Excel.Range> gibi yeni özelliklere sahiptir. Daha fazla bilgi için bkz. [NamedRange denetimi ve](../vsto/namedrange-control.md) [XmlMappedRange denetimi.](../vsto/xmlmappedrange-control.md)

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Excel nesne modeli belgelerini kullanma
 Excel nesne modeli hakkında tam bilgi için, Excel birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 PiA Excel belgelerinde, veri türleri için birincil birlikte çalışma derlemesinde Excel. Bu belgeler şu konumdan kullanılabilir: [Excel 2010 birincil birlikte çalışma derleme başvurusu.](office-primary-interop-assemblies.md)

 PIA'daki sınıflar ve arabirimler arasındaki farklar ve PIA'daki olayların nasıl uygulanıyor olduğu gibi, Excel PIA'nın tasarımı hakkında daha fazla bilgi için bkz. Office birincil birlikte çalışma [derlemelerinde sınıflara](/previous-versions/office/office-12/ms247299(v=office.12))ve arabirimlere genel bakış.

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Excel (VBA) koduna açık olduğu için Visual Basic for Applications modelini belgeler. Daha fazla bilgi için [bkz. Excel 2010 nesne modeli başvurusu.](/office/vba/api/overview/Excel/object-model)

 VBA nesne modeli başvurusunda yer alan tüm nesneler ve üyeler, PIA'daki türlere ve Excel karşılık gelen. Örneğin, VBA nesne modeli başvurusunda Çalışma Sayfası nesnesi, <xref:Microsoft.Office.Interop.Excel.Worksheet> PIA'nın çalışma Excel karşılık verir. VBA nesne modeli başvurusu çoğu özellik, yöntem ve olay için kod örnekleri sağlar ancak bu başvuruda VBA kodunu Visual Basic veya Visual C# diliyle oluşturmak istediğiniz bir Excel projesinde kullanmak için Visual Studio.

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Excel çözümleri](../vsto/excel-solutions.md)|Belge düzeyinde özelleştirmeler oluşturma ve VSTO için eklenti oluşturma Microsoft Office Excel.|
|[Aralıklarla çalışma](../vsto/working-with-ranges.md)|Aralıklarla ortak görevlerin nasıl gerçekleştireceklerini göstermek için örnekler sağlar.|
|[Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)|Çalışma sayfalarıyla ortak görevlerin nasıl gerçekleştireceklerini göstermek için örnekler sağlar.|
|[Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)|Çalışma kitaplarıyla ortak görevlerin nasıl gerçekleştireceklerini göstermek için örnekler sağlar.|
