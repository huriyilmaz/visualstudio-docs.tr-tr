---
title: genişletilmiş nesneleri kullanarak Excel otomatikleştirin
description: Visual Studio Excel çözümleri geliştirirken, çözümlerinizde konak öğelerini ve konak denetimlerini kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b2e77cc663a20ff914a3f2bf52ea8c25b7e150a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038196"
---
# <a name="automate-excel-by-using-extended-objects"></a>genişletilmiş nesneleri kullanarak Excel otomatikleştirin
  Visual Studio Excel çözümleri geliştirirken, çözümlerinizde *konak öğelerini* ve *konak denetimini* kullanabilirsiniz. bunlar, ve nesneleri gibi Excel nesne modelinde (yani, birincil birlikte çalışma Excel derlemesi tarafından kullanıma sunulan nesne modeli), yaygın olarak kullanılan nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> . genişletilmiş nesneler, temel aldığı Excel nesneler gibi davranır, ancak nesnelere yeni olaylar ve veri bağlama özellikleri gibi ek özellikler ekler.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ana bilgisayar öğeleri ve konak denetimleri VSTO eklenti ve belge düzeyi özelleştirmelerinde kullanılabilir, ancak bunların kullanılabileceği bağlam her bir çözüm türü için farklı olabilir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Excel konak öğeleri
 Excel projeler, birkaç konak öğesine erişim sağlar:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Bu konak öğesi projenizdeki bir çalışma sayfasını içerir ve temsil eder. ayrıca, konak denetimleri ve Windows Forms denetimleri de dahil olmak üzere, yönetilen denetimler için bir kapsayıcı görevi görür ve yüzeyinde denetimlerle ilgili bilgileri saklar. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Bu konak öğesi projenizdeki çalışma kitabını temsil eder ve çalışma kitabındaki tüm çalışma sayfaları tarafından paylaşılan bileşenler için bir kapsayıcı görevi görür. Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. bu konak öğesi Excel içinde yalnızca bir grafik içeren ve olayları açığa çıkaran bir çalışma sayfası.

     tasarım zamanında bir grafik sayfasını Microsoft Office Excel belge düzeyi özelleştirme projenize yeni bir sayfa olarak eklediğinizde, Visual Studio otomatik olarak bir <xref:Microsoft.Office.Tools.Excel.ChartSheet> konak öğesi oluşturur.

     bir <xref:Microsoft.Office.Tools.Excel.ChartSheet> konak öğesi Excel bir çalışma sayfası olsa da, grafik sayfasına herhangi bir denetim ekleyemezsiniz. Grafik içeren bir çalışma sayfasında diğer denetimlere sahip olmak istiyorsanız, bir grafik sayfası kullanmayın. Bunun yerine, konak denetimini kullanarak bir grafiği çalışma sayfasına katıştırılmış nesne olarak yerleştirebilirsiniz <xref:Microsoft.Office.Tools.Excel.Chart> . Daha fazla bilgi için bkz. [Chart Control](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>Excel konak denetimleri
 çalışma kitaplarını ve çalışma sayfalarını oluşturmanıza, düzenlemenize ve otomatikleştirmenize yardımcı olan Excel için çeşitli konak denetimleri vardır. bu konak denetimleri, yerel Excel nesne modelindeki karşılıkları olmayan olaylar ve veri bağlama özellikleri sağlar.

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
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
