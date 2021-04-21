---
title: Kod aracılığıyla seçili hücreleri içeren satırlardaki biçimleri değiştirin
description: Metnin kalın olması için seçili hücreyi içeren tüm satırın yazı tipini nasıl değiştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c35a176dd6780e08dafea3da7b051a9733a788e5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827649"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Nasıl yapılır: seçili hücreleri içeren çalışma sayfası satırlarında program aracılığıyla biçimlendirmeyi değiştirme
  Metnin kalın olması için seçili hücreyi içeren tüm satırın yazı tipini değiştirebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Geçerli satırı kalın ve önceden kalın satırı normal hale getirmek için

1. Daha önce seçilen satırı izlemek için bir statik değişken bildirin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet37":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet37":::

2. Özelliğini kullanarak geçerli hücreye bir başvuru alın <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet38":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet38":::

3. Etkin hücrenin özelliğini kullanarak geçerli satırın kalın stilini yapın <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet39":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet39":::

4. Geçerli değerinin 0 olmadığından emin olun `previousRow` . 0 (sıfır), bu kodun ilk kez bu olduğunu gösterir.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet40":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet40":::

5. Geçerli satırın önceki satırdan farklı olduğundan emin olun.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet41":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet41":::

6. Daha önce seçilmiş olan satırı temsil eden bir aralığa başvuru alın ve bu satırı kalın olmayan olarak ayarlayın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet42":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet42":::

7. Sonraki geçişte önceki satıra gelebilmesi için geçerli satırı saklayın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet43":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet43":::

   Aşağıdaki örnek, tüm yöntemi gösterir.

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet36":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet36":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: çalışma sayfaları arasında program aracılığıyla veri kopyalama ve biçimlendirme](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
