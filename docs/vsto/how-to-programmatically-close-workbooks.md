---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma'
description: Etkin çalışma kitabını nasıl kapatabileceğinizi veya program aracılığıyla kapatılacak bir çalışma kitabı belirtebilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099899"
---
# <a name="how-to-programmatically-close-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma
  Etkin çalışma kitabını kapatabilir veya kapatılacak bir çalışma kitabı belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Etkin çalışma kitabını kapatma
 etkin çalışma kitabını kapatmak için iki yordam vardır: biri belge düzeyi özelleştirmeler ve biri VSTO eklentiler için.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki etkin çalışma kitabını kapatmak için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A>Özelleştirme ile ilişkili çalışma kitabını kapatmak için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `Sheet1` Excel bir belge düzeyi projedeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>VSTO eklentideki etkin çalışma kitabını kapatmak için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A>Etkin çalışma kitabını kapatmak için yöntemini çağırın. aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Excel için VSTO eklenti projesindeki sınıfında çalıştırın.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Ada göre belirttiğiniz bir çalışma kitabını kapatma
 ada göre belirttiğiniz bir çalışma kitabını kapatmanız yöntemi, VSTO eklentileri ve belge düzeyi özelleştirmeleri için aynıdır.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Adına göre belirttiğiniz çalışma kitabını kapatmak için

1. Çalışma kitabı adını koleksiyona bir bağımsız değişken olarak belirtin <xref:Microsoft.Office.Interop.Excel.Workbooks> . Aşağıdaki kod örneği, **NewWorkbook** adlı bir çalışma kitabının Excel açık olduğunu varsayar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
