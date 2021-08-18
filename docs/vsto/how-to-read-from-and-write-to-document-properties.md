---
title: 'Nasıl yapılır: belge özelliklerinden okuma ve yazma'
description: Microsoft Excel ve Microsoft Word belge özelliklerini almak veya ayarlamak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 981f9da1138034dd108a438a69683f4107358ee4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032725"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Nasıl yapılır: belge özelliklerinden okuma ve yazma
  Belge özelliklerini bir belge ile birlikte saklayabilirsiniz. Office uygulamalar yazar, başlık ve konu gibi çeşitli yerleşik özellikler sağlar. bu konuda, Microsoft Office Excel ve Word Microsoft Office belge özelliklerinin nasıl ayarlanacağı gösterilmektedir.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Excel belge özelliklerini ayarlama
 Excel içindeki yerleşik özelliklerle çalışmak için aşağıdaki özellikleri kullanın:

- Belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> sınıfının özelliğini kullanın `ThisWorkbook` .

- VSTO bir eklenti projesinde, <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

  Aşağıdaki kod örneği, belge düzeyindeki bir projedeki yerleşik **düzeltme numarası** özelliğinin nasıl değiştirileceğini gösterir.

### <a name="to-change-the-revision-number-property-in-excel"></a>Excel 'de düzeltme numarası özelliğini değiştirmek için

1. Yerleşik belge özelliklerini bir değişkene atayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. `Revision Number`Özelliği bir ile artırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Word 'de belge özelliklerini ayarla
 Word 'de yerleşik özelliklerle çalışmak için aşağıdaki özellikleri kullanın:

- Belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> sınıfının özelliğini kullanın `ThisDocument` .

- VSTO bir eklenti projesinde, <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Word.Document> .

  Bu özellikler <xref:Microsoft.Office.Core.DocumentProperties> nesne koleksiyonu olan bir nesnesi döndürür <xref:Microsoft.Office.Core.DocumentProperty> . `Item`Belirli bir özelliği ada veya koleksiyon içindeki dizine göre almak için koleksiyonun özelliğini kullanabilirsiniz.

  Aşağıdaki kod örneği, belge düzeyindeki bir projede yerleşik **Konu** özelliğinin nasıl değiştirileceğini gösterir.

### <a name="to-change-the-subject-property"></a>Konu özelliğini değiştirmek için

1. Yerleşik belge özelliklerini bir değişkene atayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. `Subject`Özelliği "Teknik İnceleme" olarak değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Güçlü programlama
 örneklerde, kodu `ThisWorkbook` bir belge düzeyi projesinde Excel ve `ThisDocument` Word için belge düzeyindeki bir projede bulunan sınıfında yazdığınız varsayılır.

 Word ve Excel ve nesneleriyle çalışabilseniz de Microsoft Office kullanılabilir yerleşik belge özellikleri listesini sağlar. Tanımsız bir özelliğe erişme girişimi bir özel durum oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)
