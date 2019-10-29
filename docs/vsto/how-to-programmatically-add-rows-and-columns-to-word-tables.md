---
title: 'Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc8fbc80a58afcb6f2256c56b1071276c50f319b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985839"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme
  Microsoft Office Word tablosunda hücreler satırlar ve sütunlar halinde düzenlenir. Tabloya satır eklemek için <xref:Microsoft.Office.Interop.Word.Rows> nesnesinin <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> yöntemini ve sütun eklemek için <xref:Microsoft.Office.Interop.Word.Columns> nesnesinin <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemini kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Belge düzeyi özelleştirmesi örnekleri
 Aşağıdaki kod örnekleri, belge düzeyi özelleştirmesinde kullanılabilir. Bu örnekleri kullanmak için projenizdeki `ThisDocument` sınıfından çalıştırın. Bu örneklerde, özelleştirmenizin ilişkilendirildiği belgenin en az bir tablo olduğunu varsaymaktadır.

> [!IMPORTANT]
> Bu kod yalnızca aşağıdaki proje şablonlarından birini kullanarak oluşturduğunuz projelerde çalışır:
>
> - Word 2013 belgesi
> - Word 2013 şablonu
> - Word 2010 Belgesi
> - Word 2010 Şablonu
>
>   Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, **Microsoft. Office. Interop. Word** derlemesine bir başvuru eklemeniz ve sonra tablolara satırlar ve sütunlar eklemek için bu derlemedeki sınıfları kullanmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamalarını hedefleme.

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. Tabloya satır eklemek için <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> yöntemini kullanın.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemini kullanın ve sonra tüm sütunları aynı genişliğe getirmek için <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metodunu kullanın.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>VSTO eklentisi örnekleri
 Aşağıdaki kod örnekleri bir VSTO eklentisi içinde kullanılabilir. Örnekleri kullanmak için, bunları projenizdeki `ThisAddIn` sınıfından çalıştırın. Bu örneklerde, etkin belgenin en az bir tablo olduğunu varsaymaktadır.

> [!IMPORTANT]
> Bu kod yalnızca Word VSTO eklenti şablonlarını kullanarak oluşturduğunuz projelerde çalışır.
>
> Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, **Microsoft. Office. Interop. Word** derlemesine bir başvuru eklemeniz ve sonra tablolara satırlar ve sütunlar eklemek için bu derlemedeki sınıfları kullanmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamalarını hedefleme.

### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için

1. Tabloya satır eklemek için <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> yöntemini kullanın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Tabloya sütun eklemek için

1. <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemini kullanın ve sonra tüm sütunları aynı genişliğe getirmek için <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metodunu kullanın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla Word tabloları oluşturma](how-to-programmatically-create-word-tables.md)
- [Nasıl yapılır: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl yapılır: program aracılığıyla Word tablolarını belge özellikleriyle doldurma](how-to-programmatically-populate-word-tables-with-document-properties.md)
