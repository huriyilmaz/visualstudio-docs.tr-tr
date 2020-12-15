---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma'
description: Visual Studio 'Yu kullanarak bir Microsoft Excel çalışma kitabını programlı bir şekilde açabilir veya var olan bir çalışma kitabıyla nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f7de4072df177bd9a7c6ae23bf59e44e50d56e32
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523890"
---
# <a name="how-to-programmatically-open-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Microsoft Office Excel 'deki koleksiyon, tüm açık çalışma kitapları ile çalışmayı ve çalışma kitaplarını açmayı olanaklı kılar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Mevcut bir çalışma kitabını açmak için

1. <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> <xref:Microsoft.Office.Interop.Excel.Workbooks> Çalışma kitabının yolunu geçirerek koleksiyonun yöntemini kullanın.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- Adlı bir çalışma kitabı `YourWorkbook.xls` , C sürücüsünde adlı bir dizinde bulunmalıdır `Test` .

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
