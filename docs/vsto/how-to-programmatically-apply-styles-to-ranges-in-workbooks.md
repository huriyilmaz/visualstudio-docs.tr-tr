---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d6f115468bccc2d805b019b9a0ef15cea3605f36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546165"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama
  Çalışma kitaplarındaki bölgelere adlandırılmış stilleri uygulayabilirsiniz. Excel, önceden tanımlanmış bir dizi stil sağlar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 **Hücreleri** Biçimlendir iletişim kutusu, hücreleri biçimlendirmek için kullanabileceğiniz tüm seçenekleri görüntüler ve bu seçeneklerin her biri kodunuzda kullanılabilir. Bu iletişim kutusunu Excel 'de göstermek için, **Biçim** menüsünde **hücreler** ' e tıklayın.

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki adlandırılmış aralığa bir stil uygulamak için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2. Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim oluşturun, ona metin atayın ve ardından yeni stili uygulayın. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki adlandırılmış bir aralıktan bir stili temizlemek için

1. Aralığa Normal stili uygulayın. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>VSTO eklentideki adlandırılmış aralığa bir stil uygulamak için

1. Yeni bir stil oluşturun ve özniteliklerini ayarlayın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2. Oluşturun <xref:Microsoft.Office.Interop.Excel.Range> , ona metin atayın ve ardından yeni stili uygulayın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>VSTO eklentisi içindeki adlandırılmış aralıktan bir stili temizlemek için

1. Aralığa Normal stili uygulayın.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
