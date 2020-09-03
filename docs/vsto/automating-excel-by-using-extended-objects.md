---
title: Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65734f5397bae8c35fb8e312041d0600b8fa84e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254340"
---
# <a name="automate-excel-by-using-extended-objects"></a>Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme
  Visual Studio 'da Excel çözümleri geliştirirken, çözümlerinizde *konak öğelerini* ve *konak denetimini*kullanabilirsiniz. Bunlar, ve nesneleri gibi, Excel nesne modelinde (yani, Excel için birincil birlikte çalışma derlemesi tarafından sunulan nesne modelinde) belirli yaygın kullanılan nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> . Genişletilmiş nesneler, temel aldığı Excel nesneleri gibi davranır, ancak nesnelere yeni olaylar ve veri bağlama özellikleri gibi ek özellikler ekler.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Konak öğeleri ve konak denetimleri, hem VSTO eklenti hem de belge düzeyi özelleştirmelerinde kullanılabilir, ancak bunların kullanılabileceği bağlam her bir çözüm türü için farklı olabilir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Excel konak öğeleri
 Excel projeleri, birkaç konak öğesine erişmenizi sağlar:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Bu konak öğesi projenizdeki bir çalışma sayfasını içerir ve temsil eder. Ayrıca, konak denetimleri ve Windows Forms denetimleri de dahil olmak üzere, yönetilen denetimler için bir kapsayıcı görevi görür ve yüzeyinde denetimlerle ilgili bilgileri saklar. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Bu konak öğesi projenizdeki çalışma kitabını temsil eder ve çalışma kitabındaki tüm çalışma sayfaları tarafından paylaşılan bileşenler için bir kapsayıcı görevi görür. Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Bu konak öğesi Excel 'de yalnızca bir grafik içeren ve olayları açığa çıkaran bir çalışma sayfası.

     Tasarım zamanında, Microsoft Office Excel belge düzeyi özelleştirme projenizde yeni bir sayfa olarak bir grafik sayfası eklediğinizde, Visual Studio otomatik olarak bir <xref:Microsoft.Office.Tools.Excel.ChartSheet> konak öğesi oluşturur.

     Bir <xref:Microsoft.Office.Tools.Excel.ChartSheet> konak öğesi Excel 'deki bir çalışma sayfası olsa da, grafik sayfasına herhangi bir denetim ekleyemezsiniz. Grafik içeren bir çalışma sayfasında diğer denetimlere sahip olmak istiyorsanız, bir grafik sayfası kullanmayın. Bunun yerine, konak denetimini kullanarak bir grafiği çalışma sayfasına katıştırılmış nesne olarak yerleştirebilirsiniz <xref:Microsoft.Office.Tools.Excel.Chart> . Daha fazla bilgi için bkz. [Chart Control](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>Excel konak denetimleri
 Excel için, çalışma kitaplarını ve çalışma sayfalarını oluşturmanıza, düzenlemenize ve otomatikleştirmenize yardımcı olan birkaç konak denetimi vardır. Bu konak denetimleri, yerel Excel nesne modelindeki karşılıkları olmayan olaylar ve veri bağlama özellikleri sağlar.

 Excel projelerinde kullanabileceğiniz konak denetimleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Grafik denetimi](../vsto/chart-control.md)

- [ListObject denetimi](../vsto/listobject-control.md)

- [NamedRange denetimi](../vsto/namedrange-control.md)

- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Nasıl yapılır: ListObject sütunlarını verilerle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
- [İzlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
