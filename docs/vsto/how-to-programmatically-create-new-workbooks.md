---
title: 'Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a23f4b089d580d482193d278f22e4990d343097
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545983"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma
  Program aracılığıyla bir çalışma kitabı oluşturduğunuzda, <xref:Microsoft.Office.Interop.Excel.Workbook> konak öğesi değil, yerel bir nesnedir <xref:Microsoft.Office.Tools.Excel.Workbook> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 <xref:Microsoft.Office.Tools.Excel.Workbook>VSTO eklenti projesindeki bir nesne için bir konak öğesi oluşturabilirsiniz <xref:Microsoft.Office.Interop.Excel.Workbook> . Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Yeni bir çalışma kitabı oluşturmak için

1. <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>Koleksiyonun yöntemini kullanın <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Varsayılan şablondan başka bir şablonu temel alan bir çalışma kitabı oluşturabilirsiniz: yönteme parametre olarak kullanmak istediğiniz şablonu geçirin <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
