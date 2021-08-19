---
title: 'Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme'
description: Tabloya satır eklemek için Satırlar nesnesinin Add yöntemini kullanmayı öğrenin. Sütun eklemek için Sütunlar nesnesinin Add yöntemini de kullanabilirsiniz.
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
ms.openlocfilehash: 6bf994d622384e52aa98f0192234a749c66ebf24
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083316"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme
  Bir Microsoft Office Word tablosunda hücreler satırlar ve sütunlar halinde düzenlenmiştir. Tabloya satır <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> eklemek için nesnesinin yöntemini ve sütun eklemek <xref:Microsoft.Office.Interop.Word.Rows> için <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> <xref:Microsoft.Office.Interop.Word.Columns> nesnesinin yöntemini kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Belge düzeyi özelleştirme örnekleri
 Aşağıdaki kod örnekleri, belge düzeyi özelleştirmede kullanılabilir. Bu örnekleri kullanmak için projenizin `ThisDocument` sınıfından çalıştırın. Bu örneklerde, özelleştirmeniz ile ilişkili belgede zaten en az bir tablo olduğu varsayıldı.

> [!IMPORTANT]
> Bu kod yalnızca aşağıdaki proje şablonlarını kullanarak oluştursanız da çalışır:
>
> - Word 2013 Belgesi
> - Word 2013 Şablonu
> - Word 2010 Belgesi
> - Word 2010 Şablonu
>
>   Bu görevi başka bir proje türünde gerçekleştirmek için **Microsoft.Office. Interop.Word** derlemesi ve ardından tablolara satır ve sütun eklemek için bu derlemeden sınıfları kullanmelisiniz. Daha fazla bilgi için [bkz. Nasıl Office:](how-to-target-office-applications-through-primary-interop-assemblies.md) Birincil birlikte çalışma derlemeleri aracılığıyla uygulamaları hedefleme ve [Word 2010 birincil birlikte çalışma derleme başvurusu.](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. Tabloya <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> satır eklemek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. yöntemini <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> ve ardından yöntemini kullanarak <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişlikte yapmak için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet96":::

## <a name="vsto-add-in-examples"></a>VSTO Eklenti örnekleri
 Aşağıdaki kod örnekleri bir eklentide VSTO kullanılabilir. Örnekleri kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın. Bu örneklerde, etkin belgenin zaten en az bir tablosu olduğu varsayıldı.

> [!IMPORTANT]
> Bu kod yalnızca Word VSTO Add-in şablonlarını kullanarak oluştursanız projelerde çalışır.
>
> Bu görevi başka bir proje türünde gerçekleştirmek için **Microsoft.Office. Interop.Word** derlemesi ve ardından tablolara satır ve sütun eklemek için bu derlemeden sınıfları kullanmelisiniz. Daha fazla bilgi için [bkz. Nasıl Office:](how-to-target-office-applications-through-primary-interop-assemblies.md) Birincil birlikte çalışma derlemeleri aracılığıyla uygulamaları hedefleme ve [Word 2010 birincil birlikte çalışma derleme başvurusu.](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. Tabloya <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> satır eklemek için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. yöntemini <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> ve ardından yöntemini kullanarak <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişlikte yapmak için yöntemini kullanın.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet96":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılanlar: Program aracılığıyla Word tabloları oluşturma](how-to-programmatically-create-word-tables.md)
- [Nasıl yapılanlar: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl kullanılır: Word tablolarını belge özellikleriyle program aracılığıyla doldurmak](how-to-programmatically-populate-word-tables-with-document-properties.md)
