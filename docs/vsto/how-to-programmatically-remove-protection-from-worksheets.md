---
title: 'Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma'
description: Visual Studio 'Yu kullanarak Microsoft Excel çalışma sayfasından korumayı programlı bir şekilde nasıl kaldırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c392ee3434edf9211a4a3061e7a83a8621960430
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824165"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma
  Microsoft Office bir Excel çalışma sayfasından programlı bir şekilde korumayı kaldırabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek `getPasswordFromUser` , kullanıcıdan alınan bir parolayı içeren değişkenini kullanır.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasının korumasını kaldırma

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>Çalışma sayfasının yöntemini çağırın ve gerekirse parolayı geçirin. Bu örnek, adlı bir çalışma sayfasıyla çalıştığınızı varsayar `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>VSTO eklentideki çalışma sayfasının korumasını kaldırma

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>Etkin çalışma sayfasının yöntemini çağırın ve gerekirse parolayı geçirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma](../vsto/how-to-programmatically-protect-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
