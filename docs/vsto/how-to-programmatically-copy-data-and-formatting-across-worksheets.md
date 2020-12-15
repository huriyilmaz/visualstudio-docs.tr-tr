---
title: Çalışma sayfalarında verileri ve biçimlendirmeyi program aracılığıyla kopyalama
description: Bir sayfadaki aralıktan verileri bir çalışma kitabındaki diğer tüm sayfalara Fillacrosssheet yöntemini kullanarak nasıl kopyalayabileceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdcae80148e54f2e1adb09d4c69b2dc3268b7428
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523187"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Nasıl yapılır: çalışma sayfaları arasında program aracılığıyla veri kopyalama ve biçimlendirme
  Yöntemini kullanarak bir sayfadaki bir aralıktaki verileri bir çalışma kitabındaki diğer tüm sayfalara kopyalayabilirsiniz <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> . Bir Aralık ve verileri, biçimlendirmeyi veya her ikisini de kopyalamak isteyip istemediğinizi belirtin.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, çalışma sayfasında adlı bir Aralık gerektirir `rangeData` .

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılır: seçili hücreleri içeren çalışma sayfası satırlarında program aracılığıyla biçimlendirmeyi değiştirme](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
