---
title: 'Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme'
description: Yolu değiştirmeden Microsoft Excel çalışma kitaplarını program aracılığıyla kaydedin ve açık çalışma kitabını bellekte değiştirmeden çalışma kitabının bir kopyasını kaydedin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fdfcd38aa89d292998f1f1b7997f449b657fb6f4a89efa38c2bcae68516cd8ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267929"
---
# <a name="how-to-programmatically-save-workbooks"></a>Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme
  Bir çalışma kitabını kaydetmenin birkaç yolu vardır. Yolu değiştirmeden çalışma kitabını kaydedebilirsiniz. Çalışma kitabı daha önce kaydedilmişse, bir yol belirterek çalışma kitabını kaydetmelisiniz. Açık bir yol Microsoft Office Excel, dosyayı oluşturulurken verilen adla geçerli klasöre kaydeder. Ayrıca, açık çalışma kitabını bellekte değiştirmeden çalışma kitabının bir kopyasını kaydedebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Yolu değiştirmeden çalışma kitabını kaydetme

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyinde özelleştirmeyle ilişkili bir çalışma kitabını kaydetmek için

1. sınıfının <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> yöntemini `ThisWorkbook` çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Etkin çalışma kitabını bir çalışma VSTO kaydetmek için

1. Etkin çalışma <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> kitabını kaydetmek için yöntemini çağırma. Aşağıdaki kod örneğini kullanmak için, bunu bir VSTO `ThisAddIn` add-in projesinde sınıf içinde Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Çalışma kitabını yeni bir yol ile kaydetme
 İsteğe bağlı olarak bir dosya biçimi, parola, erişim modu ve daha fazlasını belirterek, belirtilen çalışma kitabını yeni bir konuma veya yeni bir adla kaydedebilirsiniz.

> [!NOTE]
> Bazı biçimlerde kaydetme etkileşim gerektirdiği için, çalışma kitabını yeni bir yol ile kaydetmeden önce özelliğini <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> **False** olarak ayarlamak iyi olabilir. Bu özelliğin False **olarak ayar** Excel varsayılan değerleri kullanmama neden olur.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyinde özelleştirmeyle ilişkili bir çalışma kitabını kaydetmek için

1. sınıfının <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> yöntemini `ThisWorkbook` çağırma. Aşağıdaki kod örneğini kullanmak için sınıfında `ThisWorkbook` çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Etkin çalışma kitabını bir çalışma VSTO kaydetmek için

1. Etkin çalışma <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> kitabını yeni bir yola kaydetmek için yöntemini çağırma. Aşağıdaki kod örneğini kullanmak için, bunu bir VSTO `ThisAddIn` add-in projesinde sınıf içinde Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Çalışma kitabının bir kopyasını kaydetme
 Açık çalışma kitabını bellekte değiştirmeden çalışma kitabının bir kopyasını bir dosyaya kaydedebilirsiniz. Bu, çalışma kitabının konumunu değiştirmeden bir yedekleme kopyası oluşturmak istediğiniz zaman kullanışlıdır.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Belge düzeyinde özelleştirmeyle ilişkili bir çalışma kitabını kaydetmek için

1. sınıfının <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> yöntemini `ThisWorkbook` çağırma. Aşağıdaki kod örneğini kullanmak için sınıfında `ThisWorkbook` çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Etkin çalışma kitabını bir çalışma VSTO kaydetmek için

1. Etkin <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> çalışma kitabının bir kopyasını kaydetmek için yöntemini çağırma. Aşağıdaki kod örneğini kullanmak için, bunu bir VSTO `ThisAddIn` add-in projesinde sınıf içinde Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Güçlü programlama
 Çalışma kitabını kaydeden veya kopya alan yöntemlerden herhangi birini etkileşimli olarak iptal etmek, kodunızda çalışma zamanı hatasına neden olur. Örneğin, yordamınız yöntemini çağırsa ama komut istemini Excel devre dışı bırakmıyorsa ve kullanıcınız istendiğinde İptal'e tıklarsa Excel bir çalışma <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> zamanı hatası döndürür. 

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
