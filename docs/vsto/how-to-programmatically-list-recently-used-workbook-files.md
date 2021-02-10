---
title: 'Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme'
description: Visual Studio kullanarak, son kullanılan Microsoft Excel çalışma kitabı dosyalarını program aracılığıyla nasıl listeleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75405c7a2e02189e205edf6615c5d95a8f1d023c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963152"
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
