---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee7444c63c2d774e9b22ea612049f09429729c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537637"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma
  Microsoft Office bir Excel çalışma kitabını, kullanıcıların çalışma sayfaları ekleyememesi veya silememeleri ve ayrıca çalışma kitabının korumasını kaldırmak için koruyabilirsiniz. İsteğe bağlı olarak bir parola belirtebilir, yapının korunmasını isteyip istemediğinizi belirtebilir (böylece kullanıcılar, sayfaları taşıyabilir) ve çalışma kitabının pencerelerinin korunmasını isteyip istemediğinizi belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Çalışma kitabının korunması, kullanıcıların hücreleri düzenlemesini durdurmaz. Verileri korumak için çalışma sayfalarını korumanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md).

 Aşağıdaki kod örnekleri, kullanıcıdan alınan bir parolayı içeren bir değişken kullanır.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir çalışma kitabını koruma

### <a name="to-protect-a-workbook"></a>Çalışma kitabını korumak için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>Çalışma kitabının yöntemini çağırın ve bir parola ekleyin. Aşağıdaki kod örneğini kullanmak için, `ThisWorkbook` bir sayfa sınıfında değil sınıfında çalıştırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Çalışma kitabının korumasını kaldırma

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>Gerekirse bir parola geçirerek yöntemi çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisWorkbook` bir sayfa sınıfında değil sınıfında çalıştırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Uygulama düzeyi eklentisi kullanarak çalışma kitabını koruma

### <a name="to-protect-a-workbook"></a>Çalışma kitabını korumak için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>Çalışma kitabının yöntemini çağırın ve bir parola ekleyin. Bu kod örneği, etkin çalışma kitabını kullanır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Çalışma kitabının korumasını kaldırma

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>Etkin çalışma kitabının yöntemini çağırın, gerekirse parolayı geçirerek. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
