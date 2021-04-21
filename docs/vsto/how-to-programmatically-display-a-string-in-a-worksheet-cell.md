---
title: 'Nasıl yapılır: çalışma sayfası hücresinde program aracılığıyla bir dizeyi görüntüleme'
description: Bir Microsoft Excel çalışma sayfası hücresinde NamedRange denetimi veya yerel bir Excel Aralık nesnesi kullanarak bir dizeyi programlı bir şekilde görüntülemeyi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825933"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Nasıl yapılır: çalışma sayfası hücresinde program aracılığıyla bir dizeyi görüntüleme
  Bu örnek, bir hücredeki metnin programlı olarak nasıl görüntüleneceğini gösterir. Hücrede metin göstermek için, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim veya yerel Excel Aralık nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Bu örnek adlı bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim kullanır `message` . Denetim, tasarım zamanında belge düzeyinde bir özelleştirmeye eklenmelidir. Aşağıdaki kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

### <a name="to-display-text-in-a-namedrange-control"></a>Bir NamedRange denetiminde metin göstermek için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>Denetimin değerini **Merhaba Dünya** olarak ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Yerel bir Excel aralığı kullan
 Aşağıdaki kod, programlı olarak yeni bir Aralık oluşturur ve buna bir değer atar.

### <a name="to-display-text-in-an-excel-range"></a>Excel aralığında metin göstermek için

1. **A1** hücresindeki aralığı alın `Sheet1` ve değeri **Merhaba Dünya** olarak ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Windows formu kullanarak veri toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
