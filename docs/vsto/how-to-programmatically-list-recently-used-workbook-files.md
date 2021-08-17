---
title: 'Nasıl kullanılır: Son kullanılan çalışma kitabı dosyalarını program aracılığıyla listele'
description: Çalışma kitabı dosyalarını kullanarak son kullanılanları program aracılığıyla Microsoft Excel nasıl listeleyebilirsiniz Visual Studio.
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
ms.openlocfilehash: 738340efbdc7f266ae8da5ed10363858df970f7175507ddf73e4c5ec5097a4ec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351843"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Nasıl kullanılır: Son kullanılan çalışma kitabı dosyalarını program aracılığıyla listele
  özelliği, <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> son kullanılan dosyalar listesinde görünen tüm dosyaların adlarını Microsoft Office Excel bir koleksiyon döndürür. Listenin uzunluğu, kullanıcının korumayı seçmiş olduğu dosya sayısına bağlı olarak değişir. Sonuçları bir aralıkta görüntüleniyor.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Bir aralık nesnesinde son kullanılan çalışma kitaplarını listele

1. Son dosyalar listesinde döngüye geçerek adları bir nesneye göre hücrelerde <xref:Microsoft.Office.Interop.Excel.Range> görüntüler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
