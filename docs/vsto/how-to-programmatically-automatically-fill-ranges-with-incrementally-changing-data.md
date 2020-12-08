---
title: Artımlı olarak veri aralıklarını otomatik olarak değiştirme
description: Aralık nesnesinin otomatik doldurma yönteminin, çalışma sayfasındaki bir aralığı otomatik olarak değerlerle doldurmanıza nasıl olanak sağladığını öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc80b4b589eb46aefa9ef6d75384ed17bb1b7c8c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847214"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Nasıl yapılır: artımlı değişen verilerle aralıkları program aracılığıyla otomatik olarak doldur
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>Nesnesinin yöntemi, <xref:Microsoft.Office.Interop.Excel.Range> çalışma sayfasındaki bir aralığı değerleri otomatik olarak doldurmanıza olanak sağlar. Genellikle, <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemi bir aralıktaki artımlı veya azalan değerleri depolamak için kullanılır. Sabit listesinden isteğe bağlı bir sabit sağlayarak davranışı belirtebilirsiniz <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Kullanırken iki Aralık belirtmeniz gerekir <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>Dolgunun başlangıç noktasını belirten ve bir başlangıç değeri içeren yöntemi çağıran Aralık.

- Doldurmanız istediğiniz Aralık, yöntemine parametre olarak geçirilir <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Bu hedef Aralık, ilk değeri içeren aralığı içermelidir.

    > [!NOTE]
    > Yerinde bir denetim geçiremezsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Interop.Excel.Range> . Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Örnek
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Kodu derle
 Doldurmanız istediğiniz aralığın ilk hücresi bir başlangıç değeri içermelidir.

 Örnek üç bölge doldurmanız gerekir:

- B sütunu beş haftanın günü dahil edilir. İlk değer için B1 hücresine **Pazartesi** yazın.

- C sütunu beş ay dahil edilir. İlk değer için C1 hücresinde **Ocak** yazın.

- Sütun D, her satır için iki ile artan bir dizi sayı içerir. İlk değerler için, D2 hücresindeki D1 ve **6** hücresindeki **4** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
