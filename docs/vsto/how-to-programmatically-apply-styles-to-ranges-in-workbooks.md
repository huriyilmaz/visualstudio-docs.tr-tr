---
title: 'Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama'
description: Çalışma kitaplarında bölgelere adlandırılmış stiller nasıl uygulayabilirsiniz? Excel önceden tanımlanmış bir dizi stil sağlar.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 25ae70edc79c648fd908b8d357469cc1ebe2af95050cf14292eb4ebc5deaa465
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268124"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama
  Çalışma kitaplarında bölgelere adlandırılmış stiller uygulayabilirsiniz. Excel önceden tanımlanmış bir dizi stil sağlar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Hücreleri **Biçimlendir** iletişim kutusunda hücreleri biçimlendirmek için kullanabileceğiniz tüm seçenekler görüntülenir ve bu seçeneklerin her biri kodunuzdan kullanılabilir. Bu iletişim kutusunu dosyada görüntülemek Excel, Biçim **menüsünde** **Hücreler'e** tıklayın.

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede adlandırılmış bir aralıkta stil uygulamak için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Bir denetim <xref:Microsoft.Office.Tools.Excel.NamedRange> oluşturun, bu denetime metin atfı oluşturun ve ardından yeni stili uygulayabilirsiniz. Bu kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede adlandırılmış bir aralıktan stil temizlemek için

1. Normal stilini aralığına uygulama. Bu kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Bir eklentide adlandırılmış bir aralıkta stil VSTO için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Bir <xref:Microsoft.Office.Interop.Excel.Range> oluşturun, buna metin atfı oluşturun ve ardından yeni stili uygulayabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Bir eklentide adlandırılmış bir aralıktan stil VSTO için

1. Normal stilini aralığına uygulama.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
