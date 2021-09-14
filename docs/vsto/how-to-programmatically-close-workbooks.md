---
title: 'Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma'
description: Etkin çalışma kitabını kapatmayı öğrenin veya program aracılığıyla kapatacak bir çalışma kitabı belirtebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 21b789a2a722e78d0a89f7db9b1eaeaf28d9db58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633961"
---
# <a name="how-to-programmatically-close-workbooks"></a>Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma
  Etkin çalışma kitabını kapatabilirsiniz veya kapatacak bir çalışma kitabı belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Etkin çalışma kitabını kapatma
 Etkin çalışma kitabını kapatmaya ilişkin iki yordam vardır: biri belge düzeyi özelleştirmeler için, biri de VSTO için.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede etkin çalışma kitabını kapatmak için

1. Özelleştirmeyle <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> ilişkili çalışma kitabını kapatmak için yöntemini çağırma. Aşağıdaki kod örneğini kullanmak için, aşağıdaki kod örneği `Sheet1` için belge düzeyi projesinde sınıf içinde Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Bir çalışma kitabındaki etkin çalışma kitabını VSTO için

1. Etkin çalışma <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> kitabını kapatmak için yöntemini çağırma. Aşağıdaki kod örneğini kullanmak için, bunu bir VSTO `ThisAddIn` add-in projesinde sınıf içinde Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Ad ile belirttiğiniz çalışma kitabını kapatma
 Add-ins ve belge düzeyinde özelleştirmeler için adla VSTO çalışma kitabını kapatmanız aynıdır.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Ad ile belirttiğiniz çalışma kitabını kapatmak için

1. Çalışma kitabı adını koleksiyon için bağımsız değişken olarak <xref:Microsoft.Office.Interop.Excel.Workbooks> belirtin. Aşağıdaki kod örneğinde **NewWorkbook** adlı bir çalışma kitabının Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl musunuz: Program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
