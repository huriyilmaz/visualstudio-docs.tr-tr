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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4897008f102600bd222a21761237acc4bcb62a30
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844302"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme
  Yukarıda listelenen Microsoft Office uygulamalar, belgelerle depolanan yerleşik özellikler sağlar. Ayrıca, belgeyle birlikte depolamak istediğiniz ek bilgiler varsa özel belge özelliklerini oluşturabilir ve değiştirebilirsiniz.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Özel özelliklerle çalışmak için bir belgenin CustomDocumentProperties özelliğini kullanın. Örneğin, Excel Microsoft Office için belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> sınıfının özelliğini kullanın `ThisWorkbook` . Excel için VSTO eklentisi projesinde, <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> bir nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Excel.Workbook> . Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

 Aşağıdaki örnek, Excel için belge düzeyi özelleştirmesindeki özel bir özelliğin nasıl ekleneceğini gösterir ve bu değere bir değer atar.

## <a name="example"></a>Örnek
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Güçlü programlama
 `Value`Tanımsız özellikler için özelliğe erişme girişimi bir özel durum oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl yapılır: belge özelliklerinden okuma ve yazma](../vsto/how-to-read-from-and-write-to-document-properties.md)
