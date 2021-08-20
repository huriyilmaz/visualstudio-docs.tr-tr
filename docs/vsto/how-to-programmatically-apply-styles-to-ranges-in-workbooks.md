---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama'
description: Çalışma kitaplarındaki bölgelere adlandırılmış stilleri nasıl uygulayabileceğinizi öğrenin. Excel önceden tanımlanmış bir dizi stil sağlar.
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
ms.openlocfilehash: 32ba588545d401a7c25f56d5a5f7042d62116a25
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122741"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama
  Çalışma kitaplarındaki bölgelere adlandırılmış stilleri uygulayabilirsiniz. Excel önceden tanımlanmış bir dizi stil sağlar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 **Hücreleri** Biçimlendir iletişim kutusu, hücreleri biçimlendirmek için kullanabileceğiniz tüm seçenekleri görüntüler ve bu seçeneklerin her biri kodunuzda kullanılabilir. bu iletişim kutusunu Excel göstermek için, **biçim** menüsünde **hücreler** ' e tıklayın.

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki adlandırılmış aralığa bir stil uygulamak için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim oluşturun, ona metin atayın ve ardından yeni stili uygulayın. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki adlandırılmış bir aralıktan bir stili temizlemek için

1. Aralığa Normal stili uygulayın. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>bir VSTO eklentisi içindeki adlandırılmış aralığa stil uygulamak için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Oluşturun <xref:Microsoft.Office.Interop.Excel.Range> , ona metin atayın ve ardından yeni stili uygulayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>VSTO eklentisi içindeki adlandırılmış aralıktan bir stili temizlemek için

1. Aralığa Normal stili uygulayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
