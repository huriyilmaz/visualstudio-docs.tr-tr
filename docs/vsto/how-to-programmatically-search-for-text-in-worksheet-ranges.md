---
title: 'Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0ffc06c2f50f7a304ef76ac1451ee47419143afb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985815"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama
  <xref:Microsoft.Office.Interop.Excel.Range> nesnesinin <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> yöntemi, Aralık içinde metin aramanızı sağlar. Bu metin, `#NULL!` veya `#VALUE!`gibi bir çalışma sayfası hücresinde görünebilen herhangi bir hata dizesi de olabilir. Hata dizeleri hakkında daha fazla bilgi için bkz. [hücre hata değerleri](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek, `Fruits` adlı bir aralığı arar ve "elmalar" sözcüğünü içeren hücreler için yazı tipini değiştirir. Bu yordam Ayrıca, Aramayı yinelemek için önceden ayarlanmış arama ayarlarını kullanan <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> yöntemini kullanır. Aramadan sonra hücreyi belirtirsiniz ve <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> yöntemi Rest 'i işler.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> yönteminin araması, aralığın sonuna ulaştıktan sonra arama aralığının başlangıcına geri sarar. Kodunuzun, aramanın sonsuz bir döngüde sarılmadığından emin olması gerekir. Örnek yordam, <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> özelliğini kullanarak bunu işlemenin bir yolunu gösterir.

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

4. Bulunan ilk aralığı (`firstFind`) **hiçbir şey**ile karşılaştırın. `firstFind` hiçbir değer içermiyorsa, kod bulunan aralığı (`currentFind`) yerine depolar.

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
