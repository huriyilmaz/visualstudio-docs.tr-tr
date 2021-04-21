---
title: 'Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme'
description: Belge ile depolamak istediğiniz ek bilgiler varsa, özel belge özelliklerini nasıl oluşturup değiştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd89cb1e2991f48fefd9984eaa6d5894d9b506c1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826583"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme
  Yukarıda listelenen Microsoft Office uygulamalar, belgelerle depolanan yerleşik özellikler sağlar. Ayrıca, belgeyle birlikte depolamak istediğiniz ek bilgiler varsa özel belge özelliklerini oluşturabilir ve değiştirebilirsiniz.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Özel özelliklerle çalışmak için bir belgenin CustomDocumentProperties özelliğini kullanın. Örneğin, Excel Microsoft Office için belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> sınıfının özelliğini kullanın `ThisWorkbook` . Excel için VSTO eklentisi projesinde, <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> bir nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Excel.Workbook> . Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

 Aşağıdaki örnek, Excel için belge düzeyi özelleştirmesindeki özel bir özelliğin nasıl ekleneceğini gösterir ve bu değere bir değer atar.

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet6":::

## <a name="robust-programming"></a>Güçlü programlama
 `Value`Tanımsız özellikler için özelliğe erişme girişimi bir özel durum oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl yapılır: belge özelliklerinden okuma ve yazma](../vsto/how-to-read-from-and-write-to-document-properties.md)
