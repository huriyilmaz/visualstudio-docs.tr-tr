---
title: Genişletilmiş Excel kullanarak nesneleri otomatikleştirme
description: Excel geliştirme Visual Studio konak öğelerini ve konak denetimlerini çözümleriniz içinde kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635449"
---
# <a name="automate-excel-by-using-extended-objects"></a>Genişletilmiş Excel kullanarak nesneleri otomatikleştirme
  Bir Excel geliştirme Visual Studio, çözümleriniz içinde konak *öğelerini* *ve konak* denetimlerini kullanabilirsiniz. Bunlar, ve nesneleri gibi Excel nesne modelinde yaygın olarak kullanılan bazı nesneleri (örneğin, Excel için birincil birlikte çalışma derlemesi tarafından ortaya çıkaran nesne modeli) genişleten <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> nesnelerdir. Genişletilmiş nesneler, temel Excel nesneleri gibi davranır, ancak nesnelere yeni olaylar ve veri bağlama özellikleri gibi ek özellikler ekler.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Konak öğeleri ve konak denetimleri hem VSTO hem de belge düzeyi özelleştirmelerinde kullanılabilir, ancak bunların kullanılaları bağlam her çözüm türü için farklıdır. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

## <a name="excel-host-items"></a>Excel öğelerini barındırma
 Excel projeleri çeşitli konak öğelerine erişim sağlar:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Bu konak öğesi projenizin çalışma sayfasını içerir ve temsil eder. Ayrıca konak denetimleri ve Windows Forms denetimleri de dahil olmak üzere yönetilen denetimler için kapsayıcı olarak hareket eder ve yüzeyindeki denetimler hakkında bilgi sağlar. Daha fazla bilgi için bkz. [Çalışma sayfası konak öğesi.](../vsto/worksheet-host-item.md)

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Bu konak öğesi, projenizin çalışma kitabını temsil eder ve çalışma kitabındaki tüm çalışma sayfaları tarafından paylaşılan bileşenler için bir kapsayıcı olarak davranır. Daha fazla bilgi için bkz. [Çalışma kitabı konak öğesi.](../vsto/workbook-host-item.md)

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Bu konak öğesi, çalışma Excel içeren ve olayları ortaya çıkaran bir çalışma sayfasıdır.

     Tasarım zamanında, belge düzeyi özelleştirme projenize yeni bir sayfa Microsoft Office Excel grafik sayfası eklerken, Visual Studio otomatik olarak bir konak <xref:Microsoft.Office.Tools.Excel.ChartSheet> öğesi oluşturur.

     Konak <xref:Microsoft.Office.Tools.Excel.ChartSheet> öğesi, çalışma Excel çalışma sayfası olsa da grafik sayfasına herhangi bir denetim ekamazsiniz. Çalışma sayfasında grafik olan başka denetimlere sahip olmak için grafik sayfası kullanmayın. Bunun yerine, konak denetimi kullanarak grafiği çalışma sayfasına katıştırılmış nesne olarak <xref:Microsoft.Office.Tools.Excel.Chart> ekleyebilirsiniz. Daha fazla bilgi için [bkz. Grafik denetimi.](../vsto/chart-control.md)

## <a name="excel-host-controls"></a>Excel konak denetimleri
 Çalışma kitaplarını ve çalışma sayfalarını Excel, düzenlemenize ve otomatikleştirmenize yardımcı olacak çeşitli konak denetimleri vardır. Bu konak denetimleri, yerel nesne modellerinde yer alan ve yerel Excel sahip olmayan olaylar ve veri bağlama özellikleri sağlar.

 Konak projelerinde kullanabileceğiniz konak denetimleri hakkında daha fazla Excel aşağıdaki konulara bakın:

- [Grafik denetimi](../vsto/chart-control.md)

- [ListObject denetimi](../vsto/listobject-control.md)

- [NamedRange denetimi](../vsto/namedrange-control.md)

- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: ListObject denetimlerini verilerle doldurma](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: Çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Nasıl olur: NamedRange denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-namedrange-controls.md)
- [Nasıl olur: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Nasıl kullanılır: ListObject denetimine yeni bir satır eklendiği zaman verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Nasıl kullanılır: ListObject sütunlarını veriyle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
- [Adım adım kılavuz: NamedRange denetimi olaylarına karşı programla](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office için denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
