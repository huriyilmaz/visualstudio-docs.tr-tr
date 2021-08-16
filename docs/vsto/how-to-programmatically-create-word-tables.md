---
title: 'Nasıl yapılanlar: Program aracılığıyla Word tabloları oluşturma'
description: Bir tablo belgesinde belirtilen aralıkta tablo eklemek için Tablolar koleksiyonunun Add yöntemini Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ffa70b09b233f2f674c457999c6c7669332c100606c2be6f0c3802c967da154b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408740"
---
# <a name="how-to-programmatically-create-word-tables"></a>Nasıl yapılanlar: Program aracılığıyla Word tabloları oluşturma
  Koleksiyon, , , ve sınıflarının bir üyesidir ve bu bağlamdan herhangi biri <xref:Microsoft.Office.Interop.Word.Tables> <xref:Microsoft.Office.Interop.Word.Document> için bir tablo <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> oluşturabilirsiniz. Belirtilen <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> aralıkta bir <xref:Microsoft.Office.Interop.Word.Tables> tablo eklemek için koleksiyonun yöntemini kullanırsınız.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Belge düzeyinde özelleştirmelerde tablo oluşturma

### <a name="to-add-a-table-to-a-document"></a>Belgeye tablo eklemek için

- Belgenin <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> başına üç satırdan ve dört sütundan oluşan bir tablo eklemek için yöntemini kullanın.

   Aşağıdaki kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  Bir tablo oluşturma, konak öğenin <xref:Microsoft.Office.Interop.Word.Tables> koleksiyonuna otomatik <xref:Microsoft.Office.Tools.Word.Document> olarak eklenir. Daha sonra, aşağıdaki kodda gösterildiği gibi özelliğini kullanarak <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> tabloya öğe numarasına göre başvurabilirsiniz.

### <a name="to-refer-to-a-table-by-item-number"></a>Bir tabloya öğe numarasına göre başvurmak için

1. özelliğini <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> kullanın ve başvurmak istediğiniz tablonun öğe numarasını girin.

    Aşağıdaki kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Her <xref:Microsoft.Office.Interop.Word.Table> nesnenin biçimlendirme <xref:Microsoft.Office.Interop.Word.Table.Range%2A> özniteliklerini ayarlamaya olanak sağlayan bir özelliği de vardır.

### <a name="to-apply-a-style-to-a-table"></a>Tabloya stil uygulamak için

1. Word <xref:Microsoft.Office.Interop.Word.Table.Style%2A> yerleşik stillerinden birini tabloya uygulamak için özelliğini kullanın.

     Aşağıdaki kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>Eklentilerde VSTO oluşturma

### <a name="to-add-a-table-to-a-document"></a>Belgeye tablo eklemek için

- Belgenin <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> başına üç satırdan ve dört sütundan oluşan bir tablo eklemek için yöntemini kullanın.

   Aşağıdaki kod örneği, etkin belgeye bir tablo ekler. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  Bir tablo oluşturma, otomatik olarak <xref:Microsoft.Office.Interop.Word.Tables> koleksiyonunun koleksiyonuna <xref:Microsoft.Office.Interop.Word.Document> eklenir. Daha sonra, aşağıdaki kodda gösterildiği gibi özelliğini kullanarak <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> tabloya öğe numarasına göre başvurabilirsiniz.

### <a name="to-refer-to-a-table-by-item-number"></a>Bir tabloya öğe numarasına göre başvurmak için

1. özelliğini <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> kullanın ve başvurmak istediğiniz tablonun öğe numarasını girin.

    Aşağıdaki kod örneği etkin belgeyi kullanır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Her <xref:Microsoft.Office.Interop.Word.Table> nesnenin biçimlendirme <xref:Microsoft.Office.Interop.Word.Table.Range%2A> özniteliklerini ayarlamaya olanak sağlayan bir özelliği de vardır.

### <a name="to-apply-a-style-to-a-table"></a>Tabloya stil uygulamak için

1. Word <xref:Microsoft.Office.Interop.Word.Table.Style%2A> yerleşik stillerinden birini tabloya uygulamak için özelliğini kullanın.

     Aşağıdaki kod örneği etkin belgeyi kullanır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılanlar: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Nasıl kullanılır: Word tablolarını belge özellikleriyle program aracılığıyla doldurmak](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
