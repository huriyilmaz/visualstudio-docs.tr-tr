---
title: 'Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519879"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma
  Microsoft Office bir Excel çalışma sayfasından programlı bir şekilde korumayı kaldırabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek `getPasswordFromUser` , kullanıcıdan alınan bir parolayı içeren değişkenini kullanır.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasının korumasını kaldırma

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>Çalışma sayfasının yöntemini çağırın ve gerekirse parolayı geçirin. Bu örnek, adlı bir çalışma sayfasıyla çalıştığınızı varsayar `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>VSTO eklentideki çalışma sayfasının korumasını kaldırma

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>Etkin çalışma sayfasının yöntemini çağırın ve gerekirse parolayı geçirin.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma](../vsto/how-to-programmatically-protect-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
