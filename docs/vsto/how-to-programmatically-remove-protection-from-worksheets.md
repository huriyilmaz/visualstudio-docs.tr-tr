---
title: 'Nasıl yapılanlar: Çalışma sayfalarından program aracılığıyla korumayı kaldırma'
description: Çalışma sayfasındaki korumayı program Visual Studio kaldırmak için Microsoft Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: af5fb0cab5501b6a5bbe19025be6f963728ee477
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092182"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Nasıl yapılanlar: Çalışma sayfalarından program aracılığıyla korumayı kaldırma
  Program aracılığıyla bir çalışma sayfasından korumayı Microsoft Office Excel kaldırabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek, kullanıcıdan `getPasswordFromUser` alınan bir parolayı içeren değişkenlerini kullanır.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede çalışma sayfasının korumasını kaldırma

1. Gerekirse <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> çalışma sayfasının yöntemini çağırarak parolayı girin. Bu örnekte adlı bir çalışma sayfasıyla çalıştığı `Sheet1` varsayıyorum.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Çalışma sayfasındaki çalışma sayfasının korumasını VSTO için

1. Etkin <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> çalışma sayfasının yöntemini çağırarak gerekirse parolayı girin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-workbooks.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
