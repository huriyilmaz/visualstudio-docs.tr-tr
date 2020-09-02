---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma'
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
ms.openlocfilehash: 10a849d8545565e450cd099b32a9e3e8f7f11b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537910"
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
