---
title: 'Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme'
description: Visual Studio kullanarak son kullanılan Microsoft Excel çalışma kitabı dosyalarını program aracılığıyla nasıl listeleyeceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e9652a60149a068643a4a8d0b06728534a4ac521
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725569"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Nasıl yapılır: son kullanılan çalışma kitabı dosyalarını program aracılığıyla listeleme
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>özelliği, son kullanılan dosyaların Microsoft Office Excel listesinde görünen tüm dosyaların adlarını içeren bir koleksiyon döndürür. Listenin uzunluğu, kullanıcının tutulması için seçtiği dosya sayısına bağlı olarak değişir. Sonuçları bir aralıkta görüntüleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Son kullanılan çalışma kitaplarını bir Aralık nesnesinde listelemek için

1. Son kullanılan dosyalar listesinde döngü yapın ve adları bir nesneye göre hücrelerde görüntüleyin <xref:Microsoft.Office.Interop.Excel.Range> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
