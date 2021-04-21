---
title: 'Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma'
description: Visual Studio kullanarak programlı bir şekilde yeni bir Microsoft Excel çalışma kitabı oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a0a6e0b7b81c472ce03b1255c2c6899df0389da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825985"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma
  Program aracılığıyla bir çalışma kitabı oluşturduğunuzda, <xref:Microsoft.Office.Interop.Excel.Workbook> konak öğesi değil, yerel bir nesnedir <xref:Microsoft.Office.Tools.Excel.Workbook> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 <xref:Microsoft.Office.Tools.Excel.Workbook>VSTO eklenti projesindeki bir nesne için bir konak öğesi oluşturabilirsiniz <xref:Microsoft.Office.Interop.Excel.Workbook> . Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Yeni bir çalışma kitabı oluşturmak için

1. <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>Koleksiyonun yöntemini kullanın <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet1":::

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
