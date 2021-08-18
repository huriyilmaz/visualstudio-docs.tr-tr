---
title: 'Nasıl gösterilir: Çalışma sayfası hücresinde program aracılığıyla dize görüntüleme'
description: NamedRange denetimi veya yerel bir Microsoft Excel aralığı nesnesi kullanarak bir dizeyi program aracılığıyla bir çalışma sayfası hücresinde Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5058a41a40ed834dc715a09de3b28c0e28cf594a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099808"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Nasıl gösterilir: Çalışma sayfası hücresinde program aracılığıyla dize görüntüleme
  Bu örnekte, bir hücrede program aracılığıyla metin görüntüleme gösterilir. Hücrede metin görüntülemek için bir denetim veya <xref:Microsoft.Office.Tools.Excel.NamedRange> yerel bir Excel kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Bu örnekte adlı bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim `message` 2. Denetim, tasarım zamanında belge düzeyi özelleştirmeye eklenmiştir. Aşağıdaki kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange denetiminde metin görüntülemek için

1. Denetimin değerini <xref:Microsoft.Office.Tools.Excel.NamedRange> Merhaba Dünya. 

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Yerel bir Excel kullanma
 Aşağıdaki kod, program aracılığıyla yeni bir aralık oluşturur ve ardından buna bir değer atar.

### <a name="to-display-text-in-an-excel-range"></a>Metinleri tek bir aralıkta Excel için

1. A1 on **hücresinde aralığı** alın `Sheet1` ve değeri Merhaba Dünya.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Bir form kullanarak Windows toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office sorunlarını giderme](../vsto/troubleshooting-office-solutions.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
