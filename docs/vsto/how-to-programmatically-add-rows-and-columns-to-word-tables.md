---
title: 'Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme'
description: Tabloya satır eklemek için Rows nesnesinin Add metodunu nasıl kullanabileceğinizi öğrenin. Sütunlar eklemek için Columns nesnesinin Add yöntemini de kullanabilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cc4064677d35ada2a03baa1b4212a101bb6bd9a6df20f797596f9c31a961567e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424014"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme
  Microsoft Office Word tablosunda hücreler satırlar ve sütunlar halinde düzenlenir. <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> <xref:Microsoft.Office.Interop.Word.Rows> Tabloya satır eklemek için nesnesinin yöntemini ve <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> <xref:Microsoft.Office.Interop.Word.Columns> sütun eklemek için nesne yöntemini kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Belge düzeyi özelleştirmesi örnekleri
 Aşağıdaki kod örnekleri, belge düzeyi özelleştirmesinde kullanılabilir. Bu örnekleri kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın. Bu örneklerde, özelleştirmenizin ilişkilendirildiği belgenin en az bir tablo olduğunu varsaymaktadır.

> [!IMPORTANT]
> Bu kod yalnızca aşağıdaki proje şablonlarından birini kullanarak oluşturduğunuz projelerde çalışır:
>
> - Word 2013 belgesi
> - Word 2013 şablonu
> - Word 2010 Belgesi
> - Word 2010 Şablonu
>
>   Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, Microsoft. Office 'ye bir başvuru eklemeniz gerekir **. Birlikte çalışma. Word** derlemesi ve sonra tablolara satırlar ve sütunlar eklemek için bu derlemedeki sınıfları kullanmanız gerekir. daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamaları hedefleme.

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>Tabloya satır eklemek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. Yöntemini kullanın <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> ve sonra <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişliğe getirmek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet96":::

## <a name="vsto-add-in-examples"></a>VSTO Eklenti örnekleri
 aşağıdaki kod örnekleri bir VSTO eklentisi içinde kullanılabilir. Örnekleri kullanmak için bunları `ThisAddIn` projenizdeki sınıftan çalıştırın. Bu örneklerde, etkin belgenin en az bir tablo olduğunu varsaymaktadır.

> [!IMPORTANT]
> bu kod yalnızca Word VSTO eklenti şablonlarını kullanarak oluşturduğunuz projelerde çalışır.
>
> Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, Microsoft. Office 'ye bir başvuru eklemeniz gerekir **. Birlikte çalışma. Word** derlemesi ve sonra tablolara satırlar ve sütunlar eklemek için bu derlemedeki sınıfları kullanmanız gerekir. daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamaları hedefleme.

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>Tabloya satır eklemek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. Yöntemini kullanın <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> ve sonra <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişliğe getirmek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet96":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla Word tabloları oluşturma](how-to-programmatically-create-word-tables.md)
- [Nasıl yapılır: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl yapılır: program aracılığıyla Word tablolarını belge özellikleriyle doldurma](how-to-programmatically-populate-word-tables-with-document-properties.md)
