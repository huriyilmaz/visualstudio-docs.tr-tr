---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme'
description: Yol değiştirmeden Microsoft Excel çalışma kitaplarını program aracılığıyla kaydedin ve çalışma kitabının bir kopyasını bellekte değişiklik yapmadan kaydedin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828988"
---
# <a name="how-to-programmatically-save-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme
  Çalışma kitabını kaydetmek için birkaç yol vardır. Yolu değiştirmeden bir çalışma kitabını kaydedebilirsiniz. Çalışma kitabı daha önce kaydedilmemişken, bir yol belirterek çalışma kitabını kaydetmeniz gerekir. Açık bir yol olmadan, Microsoft Office Excel dosyayı oluşturulduğu sırada verilen adla geçerli klasöre kaydeder. Çalışma kitabının bir kopyasını bellekte bulunan açık çalışma kitabında değişiklik yapmadan da kaydedebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Yolu değiştirmeden çalışma kitabını kaydetme

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyi özelleştirmesiyle ilişkili bir çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A>Sınıfının yöntemini çağırın `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin etkin çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>Etkin çalışma kitabını kaydetmek için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Excel IÇIN VSTO eklenti projesindeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Yeni bir yola sahip bir çalışma kitabını kaydetme
 Belirtilen çalışma kitabını yeni bir konuma veya yeni bir adla kaydedebilirsiniz, isteğe bağlı olarak bir dosya biçimi, parola, erişim modu ve daha fazlasını belirtebilirsiniz.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A>Bazı biçimlerde kaydetme etkileşimi gerektirdiğinden çalışma kitabını yeni bir yola kaydetmeden önce özelliğini **false** olarak ayarlamak isteyebilirsiniz. Bu özelliğin **false** olarak ayarlanması, Excel 'in tüm varsayılanları kullanmasına neden olur.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyi özelleştirmesiyle ilişkili bir çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>Sınıfının yöntemini çağırın `ThisWorkbook` . Aşağıdaki kod örneğini kullanmak için `ThisWorkbook` sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin etkin çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>Etkin çalışma kitabını yeni bir yola kaydetmek için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Excel IÇIN VSTO eklenti projesindeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Çalışma kitabının bir kopyasını kaydet
 Çalışma kitabının bir kopyasını bellekteki açık çalışma kitabını değiştirmeden bir dosyaya kaydedebilirsiniz. Bu, çalışma kitabının konumunu değiştirmeden bir yedek kopya oluşturmak istediğinizde yararlıdır.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyi özelleştirmesiyle ilişkili bir çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A>Sınıfının yöntemini çağırın `ThisWorkbook` . Aşağıdaki kod örneğini kullanmak için `ThisWorkbook` sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin etkin çalışma kitabını kaydetmek için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>Etkin çalışma kitabının bir kopyasını kaydetmek için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Excel IÇIN VSTO eklenti projesindeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Güçlü programlama
 Çalışma kitabını kaydetme veya kopyalama yöntemini etkileşimli olarak iptal etmek kodunuzda bir çalışma zamanı hatası oluşturur. Örneğin, yordamınız yöntemi çağırırsa, <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> ancak Excel 'den istemleri devre dışı bırakmazsa ve istendiğinde, Excel bir çalışma  zamanı hatası oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
