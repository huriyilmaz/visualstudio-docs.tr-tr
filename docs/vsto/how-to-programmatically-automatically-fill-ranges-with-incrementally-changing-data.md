---
title: Veri aralıklarını program aracılığıyla artımlı olarak otomatik doldurma
description: Range nesnesinin AutoFill yönteminin çalışma sayfasındaki bir aralığı değerlerle otomatik olarak doldurmayı nasıl olanaklı olduğunu öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9a4dfe4ad526d811d0252816cd0544913328cb9f21e290ae40d653e211cd9e2e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384346"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Nasıl yapılır: Aralıkları artımlı olarak değişen verilerle program aracılığıyla otomatik olarak doldurma
  nesnesinin <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> <xref:Microsoft.Office.Interop.Excel.Range> yöntemi, çalışma sayfasındaki bir aralığı değerlerle otomatik olarak doldurmanıza olanak sağlar. Genellikle yöntemi, <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> bir aralıkta artımlı olarak artan veya azalan değerleri depolamak için kullanılır. Sabitlerden isteğe bağlı bir sabit değer belirterek <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> davranışı belirtabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 kullanırken iki aralık belirtmeniz <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> gerekir:

- Dolgun başlangıç <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> noktasını belirten ve bir başlangıç değeri içeren yöntemini çağıran aralık.

- Doldurmak istediğiniz aralık, yöntemine parametre olarak <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> geçirildi. Bu hedef aralık, ilk değeri içeren aralığı içermeli.

    > [!NOTE]
    > yerine bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi <xref:Microsoft.Office.Interop.Excel.Range> geçemezsiniz. Daha fazla bilgi için [bkz. Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>Kodu derleme
 Doldurmak istediğiniz aralığın ilk hücresi bir başlangıç değeri içermeli.

 Örnek için üç bölge doldurmanız gerekmektedir:

- B sütunu beş haftanın gününü içerecektir. İlk değer için B1 **hücresine Pazartesi** yazın.

- C sütunu beş ay içerecektir. İlk değer için C1 **hücresine Ocak** yazın.

- D sütunu, her satır için iki artırarak bir sayı dizisi eklemektir. İlk değerler için D1 **hücresine 4,** D2 **hücresine 6** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: Program aracılığıyla Excel çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
