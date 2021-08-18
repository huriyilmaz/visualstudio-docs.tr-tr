---
title: 'Nasıl musunuz: Program aracılığıyla yeni çalışma kitapları oluşturma'
description: Visual Studio kullanarak program aracılığıyla yeni bir Microsoft Excel çalışma kitabı oluşturma hakkında Visual Studio.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dded73f4af9221b096adc7c0cfda8c70fb91a348
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046600"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Nasıl musunuz: Program aracılığıyla yeni çalışma kitapları oluşturma
  Program aracılığıyla bir çalışma kitabı oluşturursanız, bu bir konak <xref:Microsoft.Office.Interop.Excel.Workbook> öğesi değil, yerel <xref:Microsoft.Office.Tools.Excel.Workbook> bir nesnedir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Eklenti <xref:Microsoft.Office.Tools.Excel.Workbook> projesinde bir nesne için <xref:Microsoft.Office.Interop.Excel.Workbook> bir konak VSTO öğesi oluşturabilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-workbook"></a>Yeni çalışma kitabı oluşturmak için

1. Koleksiyonun <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> yöntemini <xref:Microsoft.Office.Interop.Excel.Workbooks> kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet1":::

    > [!NOTE]
    > Varsayılan şablon dışında bir şablonu temel alan bir çalışma kitabı oluşturabilirsiniz: kullanmak istediğiniz şablonu yöntemine parametre olarak <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> iletir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
