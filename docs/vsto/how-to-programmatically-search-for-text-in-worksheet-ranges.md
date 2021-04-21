---
title: 'Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama'
description: Visual Studio 'Yu, Microsoft Excel çalışma sayfası aralıklarında program aracılığıyla metin aramak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 762cb3fc35b43bfd3ad15aea669adff2d370b632
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827948"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Nesnesinin yöntemi, <xref:Microsoft.Office.Interop.Excel.Range> Aralık içinde metin aramanızı sağlar. Bu metin, veya gibi bir çalışma sayfası hücresinde görünebilen hata dizelerinden herhangi biri de olabilir `#NULL!` `#VALUE!` . Hata dizeleri hakkında daha fazla bilgi için bkz. [hücre hata değerleri](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek adlı bir aralığı arar `Fruits` ve "elmalar" sözcüğünü içeren hücreler için yazı tipini değiştirir. Bu yordam <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> , Aramayı yinelemek için önceden ayarlanmış arama ayarlarını kullanan yöntemini de kullanır. Aramadan sonra hücreyi belirtirsiniz ve <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Yöntem Rest 'i işler.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Metodun araması, aralığın sonuna ulaştıktan sonra arama aralığının başlangıcına geri sarar. Kodunuzun, aramanın sonsuz bir döngüde sarılmadığından emin olması gerekir. Örnek yordam, özelliğini kullanarak bunu işlemenin bir yolunu gösterir <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> .

## <a name="to-search-for-text-in-a-worksheet-range"></a>Çalışma sayfası aralığında metin aramak için

1. Tüm aralığı, bulunan ilk aralığı ve geçerli bulunan aralığı izlemek için değişkenleri bildirin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Daha sonra arama yapılacak hücre hariç tüm parametreleri belirterek ilk eşleşmeyi arayın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Eşleşmeler olduğu sürece aramaya devam edin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Bulunan ilk aralığı ( `firstFind` ) **hiçbir şey** ile karşılaştırın. `firstFind`Değer içermiyorsa, kod bulunan aralığı () yerine depolar `currentFind` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Bulunan aralığın adresi, bulunan ilk aralığın adresiyle eşleşiyorsa döngüden çıkın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Bulunan aralığın görünümünü ayarlayın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Başka bir arama gerçekleştirin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   Aşağıdaki örnek, tüm yöntemi gösterir.

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
