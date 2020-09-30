---
title: 'Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f69a0b2c7191f608e4d18c6c3990c1ce19f1ed7e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584761"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Nesnesinin yöntemi, <xref:Microsoft.Office.Interop.Excel.Range> Aralık içinde metin aramanızı sağlar. Bu metin, veya gibi bir çalışma sayfası hücresinde görünebilen hata dizelerinden herhangi biri de olabilir `#NULL!` `#VALUE!` . Hata dizeleri hakkında daha fazla bilgi için bkz. [hücre hata değerleri](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek adlı bir aralığı arar `Fruits` ve "elmalar" sözcüğünü içeren hücreler için yazı tipini değiştirir. Bu yordam <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> , Aramayı yinelemek için önceden ayarlanmış arama ayarlarını kullanan yöntemini de kullanır. Aramadan sonra hücreyi belirtirsiniz ve <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Yöntem Rest 'i işler.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Metodun araması, aralığın sonuna ulaştıktan sonra arama aralığının başlangıcına geri sarar. Kodunuzun, aramanın sonsuz bir döngüde sarılmadığından emin olması gerekir. Örnek yordam, özelliğini kullanarak bunu işlemenin bir yolunu gösterir <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> .

## <a name="to-search-for-text-in-a-worksheet-range"></a>Çalışma sayfası aralığında metin aramak için

1. Tüm aralığı, bulunan ilk aralığı ve geçerli bulunan aralığı izlemek için değişkenleri bildirin.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Daha sonra arama yapılacak hücre hariç tüm parametreleri belirterek ilk eşleşmeyi arayın.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Eşleşmeler olduğu sürece aramaya devam edin.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Bulunan ilk aralığı ( `firstFind` ) **hiçbir şey**ile karşılaştırın. `firstFind`Değer içermiyorsa, kod bulunan aralığı () yerine depolar `currentFind` .

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Bulunan aralığın adresi, bulunan ilk aralığın adresiyle eşleşiyorsa döngüden çıkın.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Bulunan aralığın görünümünü ayarlayın.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Başka bir arama gerçekleştirin.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   Aşağıdaki örnek, tüm yöntemi gösterir.

## <a name="example"></a>Örnek
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
