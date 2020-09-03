---
title: 'Nasıl yapılır: belge özelliklerinden okuma ve yazma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: adad9ec70290f426ce7c3c59ad13ff8636a69463
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541329"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Nasıl yapılır: belge özelliklerinden okuma ve yazma
  Belge özelliklerini bir belge ile birlikte saklayabilirsiniz. Office uygulamaları yazar, başlık ve konu gibi çeşitli yerleşik özellikler sağlar. Bu konuda, Excel ve Microsoft Office Word Microsoft Office belge özelliklerinin nasıl ayarlanacağı gösterilmektedir.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Excel 'de belge özelliklerini ayarlama
 Excel 'deki yerleşik özelliklerle çalışmak için aşağıdaki özellikleri kullanın:

- Belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> sınıfının özelliğini kullanın `ThisWorkbook` .

- VSTO eklenti projesinde, <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

  Aşağıdaki kod örneği, belge düzeyindeki bir projedeki yerleşik **düzeltme numarası** özelliğinin nasıl değiştirileceğini gösterir.

### <a name="to-change-the-revision-number-property-in-excel"></a>Excel 'de düzeltme numarası özelliğini değiştirmek için

1. Yerleşik belge özelliklerini bir değişkene atayın.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. `Revision Number`Özelliği bir ile artırın.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Word 'de belge özelliklerini ayarla
 Word 'de yerleşik özelliklerle çalışmak için aşağıdaki özellikleri kullanın:

- Belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> sınıfının özelliğini kullanın `ThisDocument` .

- VSTO eklenti projesinde, <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Word.Document> .

  Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

  Aşağıdaki kod örneği, belge düzeyindeki bir projede yerleşik **Konu** özelliğinin nasıl değiştirileceğini gösterir.

### <a name="to-change-the-subject-property"></a>Konu özelliğini değiştirmek için

1. Yerleşik belge özelliklerini bir değişkene atayın.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. `Subject`Özelliği "Teknik İnceleme" olarak değiştirin.

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>Güçlü programlama
 Örneklerde, kodu `ThisWorkbook` Excel için belge düzeyindeki bir projede ve `ThisDocument` Word için belge düzeyindeki bir proje sınıfında yazdığınız varsayılır.

 Word ve Excel ve nesneleriyle çalışabilseniz de Microsoft Office kullanılabilir yerleşik belge özellikleri listesini sağlar. Tanımsız bir özelliğe erişme girişimi bir özel durum oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)
