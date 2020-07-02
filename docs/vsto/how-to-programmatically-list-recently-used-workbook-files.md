---
title: 'Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f4f34a8ed848d548b2e23d3f9a3cf3c603c7cad
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541368"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>Özelliği, son kullanılan dosyalar Microsoft Office Excel listesinde görünen tüm dosyaların adlarını içeren bir koleksiyon döndürür. Listenin uzunluğu, kullanıcının tutulması için seçtiği dosya sayısına bağlı olarak değişir. Sonuçları bir aralıkta görüntüleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Son kullanılan çalışma kitaplarını bir Aralık nesnesinde listelemek için

1. Son kullanılan dosyalar listesinde döngü yapın ve adları bir nesneye göre hücrelerde görüntüleyin <xref:Microsoft.Office.Interop.Excel.Range> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
