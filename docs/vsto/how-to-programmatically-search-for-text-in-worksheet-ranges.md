---
title: 'Nasıl olur: Çalışma sayfası aralıklarında program aracılığıyla metin arama'
description: Çalışma sayfası aralıklarında Visual Studio için program aracılığıyla arama yapmak için Microsoft Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dd001c197f9c64c5d0fa5c89a3920a40f427cf58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633905"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Nasıl olur: Çalışma sayfası aralıklarında program aracılığıyla Metin arama
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>nesnesinin <xref:Microsoft.Office.Interop.Excel.Range> yöntemi, aralık içinde metin aramanızı sağlar. Bu metin, veya gibi bir çalışma sayfası hücresinde görünen hata dizelerinden herhangi biri `#NULL!` de `#VALUE!` olabilir. Hata dizeleri hakkında daha fazla bilgi için [bkz. Hücre hata değerleri.](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Aşağıdaki örnek adlı bir aralığı arar ve "apples" sözcüğü içeren `Fruits` hücreler için yazı tipini değiştirir. Bu yordamda <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> ayrıca, daha önce aramayı tekrarlamak için ayarlanmış arama ayarlarını kullanan yöntemi de kullanılır. Arama yapılacak hücreyi belirtirsiniz ve geri <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> kalanı yöntemi üstleniyor.

> [!NOTE]
> Yöntemin araması, aralığın sonuna ulaştıktan sonra arama <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> aralığının başlangıcına geri sarmalar. Kodunuz, aramanın sonsuz bir döngüde sarmalanmaz. Örnek yordam, özelliğini kullanarak bunu işlemenin bir yolunu <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> gösterir.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Çalışma sayfası aralığında metin aramak için

1. Aralığın tamamını, ilk bulunan aralığı ve geçerli bulunan aralığı izlemek için değişkenleri bildirebilirsiniz.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. aranacak hücre dışındaki tüm parametreleri belirterek ilk eşleşmeyi ara.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Eşleşmeler olduğu sürece aramaya devam etmek.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. İlk bulunan aralığı ( `firstFind` ) Nothing ile **karşılaştırın.** değer `firstFind` içeriyorsa kod bulunan aralığı () `currentFind` depolar.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Bulunan aralığın adresi ilk bulunan aralığın adresiyle eşılıyorsa döngüden çıkın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Bulunan aralığın görünümünü ayarlayın.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Başka bir arama gerçekleştirin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   Aşağıdaki örnek, tam yöntemini gösterir.

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
