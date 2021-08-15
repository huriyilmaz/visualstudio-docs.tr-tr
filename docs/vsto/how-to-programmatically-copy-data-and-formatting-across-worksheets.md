---
title: Verileri ve biçimlendirmeyi program aracılığıyla çalışma sayfaları arasında kopyalama
description: FillAcrossSheets yöntemini kullanarak bir sayfada yer alan bir aralıktan çalışma kitabındaki diğer tüm sayfalara veri kopyalamayı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fb87be6aefda46033c13911be0d1781ceaa8999bf26d7111204cb4a9dd7fa0d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268098"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Nasıl kullanılır: Çalışma sayfaları arasında program aracılığıyla veri kopyalama ve biçimlendirme
  yöntemini kullanarak bir sayfada yer alan bir aralıktan çalışma kitabındaki diğer tüm sayfalara veri <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> kopyaabilirsiniz. Bir aralık belirtin ve verileri, biçimlendirmeyi veya her ikisini birden kopyalamak isteyip istemeyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, çalışma sayfasında adlı `rangeData` bir aralık gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarını program aracılığıyla yeni çalışma sayfalarına ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl kullanılır: Seçilen hücreleri içeren çalışma sayfası satırlarında biçimlendirmeyi program aracılığıyla değiştirme](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
