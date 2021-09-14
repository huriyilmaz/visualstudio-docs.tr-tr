---
title: 'Nasıl yapılır: program aracılığıyla Word tabloları oluşturma'
description: Microsoft Word bir belgede belirtilen aralıkta tablo eklemek için Tables koleksiyonunun Add metodunu nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 721828123734b82797fa27f720a9e5e0b7d4126f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633942"
---
# <a name="how-to-programmatically-create-word-tables"></a>Nasıl yapılır: program aracılığıyla Word tabloları oluşturma
  <xref:Microsoft.Office.Interop.Word.Tables>Koleksiyon,, ve sınıflarının bir üyesidir <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> Bu bağlamlardan herhangi birinde bir tablo oluşturabileceğiniz anlamına gelir. <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> <xref:Microsoft.Office.Interop.Word.Tables> Belirtilen aralıktaki bir tabloyu eklemek için koleksiyonun yöntemini kullanırsınız.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde tablo oluşturma

### <a name="to-add-a-table-to-a-document"></a>Bir belgeye tablo eklemek için

- <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>Belgenin başlangıcında üç satırdan ve dört sütundan oluşan bir tablo eklemek için yöntemini kullanın.

   Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  Bir tablo oluşturduğunuzda, otomatik olarak <xref:Microsoft.Office.Interop.Word.Tables> <xref:Microsoft.Office.Tools.Word.Document> konak öğesi koleksiyonuna eklenir. Ardından, <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> aşağıdaki kodda gösterildiği gibi özelliğini kullanarak tabloya öğe numarası ile başvurabilirsiniz.

### <a name="to-refer-to-a-table-by-item-number"></a>Öğe numarasına göre bir tabloya başvurmak için

1. Özelliğini kullanın <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> ve başvurmak istediğiniz tablonun öğe numarasını sağlayın.

    Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Her <xref:Microsoft.Office.Interop.Word.Table> nesnenin Ayrıca <xref:Microsoft.Office.Interop.Word.Table.Range%2A> biçimlendirme özniteliklerini ayarlamanıza olanak tanıyan bir özelliği vardır.

### <a name="to-apply-a-style-to-a-table"></a>Tabloya bir stil uygulamak için

1. <xref:Microsoft.Office.Interop.Word.Table.Style%2A>Yerleşik stillerden birini tabloya uygulamak için özelliğini kullanın.

     Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>VSTO eklentilerde tablo oluşturma

### <a name="to-add-a-table-to-a-document"></a>Bir belgeye tablo eklemek için

- <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>Belgenin başlangıcında üç satırdan ve dört sütundan oluşan bir tablo eklemek için yöntemini kullanın.

   Aşağıdaki kod örneği, etkin belgeye bir tablo ekler. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  Bir tablo oluşturduğunuzda, otomatik olarak <xref:Microsoft.Office.Interop.Word.Tables> koleksiyonuna eklenir <xref:Microsoft.Office.Interop.Word.Document> . Ardından, <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> aşağıdaki kodda gösterildiği gibi özelliğini kullanarak tabloya öğe numarası ile başvurabilirsiniz.

### <a name="to-refer-to-a-table-by-item-number"></a>Öğe numarasına göre bir tabloya başvurmak için

1. Özelliğini kullanın <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> ve başvurmak istediğiniz tablonun öğe numarasını sağlayın.

    Aşağıdaki kod örneği etkin belgeyi kullanır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Her <xref:Microsoft.Office.Interop.Word.Table> nesnenin Ayrıca <xref:Microsoft.Office.Interop.Word.Table.Range%2A> biçimlendirme özniteliklerini ayarlamanıza olanak tanıyan bir özelliği vardır.

### <a name="to-apply-a-style-to-a-table"></a>Tabloya bir stil uygulamak için

1. <xref:Microsoft.Office.Interop.Word.Table.Style%2A>Yerleşik stillerden birini tabloya uygulamak için özelliğini kullanın.

     Aşağıdaki kod örneği etkin belgeyi kullanır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Nasıl yapılır: program aracılığıyla Word tablolarını belge özellikleriyle doldurma](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
