---
title: 'Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme'
titleSuffix: ''
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
ms.openlocfilehash: 5e3d6b57251bb19cfb02849defb157c949f4ce35
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585164"
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
