---
title: Office Projelerindeki Nesnelere Genel erişim
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f76a2e74315980764a2cdffe67af4403552de7fe
ms.sourcegitcommit: d293c0e3e9cc71bd4117b6dfd22990d52964addc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/10/2020
ms.locfileid: "88041057"
---
# <a name="global-access-to-objects-in-office-projects"></a>Office Projelerindeki Nesnelere Genel erişim
  Bir Office projesi oluşturduğunuzda, Visual Studio otomatik olarak projede adlı bir sınıf oluşturur `Globals` . `Globals`Çalışma zamanında, projedeki herhangi bir koddan farklı proje öğelerine erişmek için sınıfını kullanabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Globals sınıfını kullanma
 `Globals`, projenizdeki belirli öğelere başvuruları tutan statik bir sınıftır. `Globals`Sınıfını kullanarak, çalışma zamanında projedeki herhangi bir koddan aşağıdaki öğelere erişebilirsiniz:

- `ThisWorkbook` `Sheet` Excel çalışma kitabı veya şablon projesindeki ve *n* sınıfları. `Globals.ThisWorkbook`Ve `Sheet` *n* özelliklerini kullanarak bu nesnelere erişebilirsiniz.

- `ThisDocument`Word belgesi veya şablon projesindeki sınıf. Özelliğini kullanarak bu nesneye erişebilirsiniz `Globals.ThisDocument` .

- `ThisAddIn`VSTO eklenti projesindeki sınıfı. Özelliğini kullanarak bu nesneye erişebilirsiniz `Globals.ThisAddIn` .

- Projenizdeki şerit tasarımcısını kullanarak özelleştirdiğiniz tüm şeritler. Özelliğini kullanarak Şeritlere erişebilirsiniz `Globals.Ribbons` . Daha fazla bilgi için bkz. [çalışma zamanında Şerit 'e erişme](../vsto/accessing-the-ribbon-at-run-time.md).

- Outlook VSTO eklenti projesindeki tüm Outlook form bölgeleri. Özelliğini kullanarak form bölgelerine erişebilirsiniz `Globals.FormRegions` . Daha fazla bilgi için bkz. [çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md).

- Şerit denetimleri oluşturmanızı ve veya öğesini hedefleyen projelerde çalışma zamanında öğeleri barındırmanızı sağlayan bir fabrika nesnesi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Özelliğini kullanarak bu nesneye erişebilirsiniz `Globals.Factory` . Bu nesne, aşağıdaki arayüzleri uygulayan bir sınıfın örneğidir:

  - [Microsoft. Office. Tools. Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft. Office. Tools. Excel. Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft. Office. Tools. Outlook. Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft. Office. Tools. Word. Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Örneğin, `Globals.Sheet1` <xref:Microsoft.Office.Tools.Excel.NamedRange> `Sheet1` bir Kullanıcı, Excel için belge düzeyindeki bir projede eylemler bölmesindeki bir düğmeye tıkladığında bir denetime metin eklemek için özelliğini kullanabilirsiniz.

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

 `Globals`Belge veya VSTO eklentisi başlatılmadan önce sınıfı kullanmayı deneyen kod, çalışma zamanı özel durumu oluşturabilir. Örneğin, sınıf `Globals` düzeyinde bir değişken bildirirken kullanılması başarısız olabilir çünkü `Globals` sınıf, bildirilmeyen nesne örneklendirmeden önce tüm konak öğelerinin başvuruları ile başlatılmamış olabilir.

> [!NOTE]
> `Globals`Sınıf tasarım zamanında hiçbir zaman başlatılmaz, ancak denetim örnekleri tasarımcı tarafından oluşturulur. Yani, bir kullanıcı denetimi sınıfının içinden sınıfının bir özelliğini kullanan bir kullanıcı denetimi oluşturursanız `Globals` , döndürülen nesneyi kullanmayı denemeden önce özelliğin **null** döndürüp döndürmediğini denetlemeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
