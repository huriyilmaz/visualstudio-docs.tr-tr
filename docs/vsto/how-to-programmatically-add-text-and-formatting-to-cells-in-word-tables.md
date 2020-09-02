---
title: Program aracılığıyla Word tablo hücrelerine metin & biçimlendirme ekleme
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acd43c82c6dae32ef6595b2f63c06fe61f3c6168
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538053"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Nasıl yapılır: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme
  Her tablo bir hücre koleksiyonundan oluşur. Her tek <xref:Microsoft.Office.Interop.Word.Cell> nesne tablodaki bir hücreyi temsil eder. Tablodaki konumuna göre her bir hücreye başvurursunuz. Bu örnek, ilk satırda bulunan hücreyi ve tablonun ilk sütununu ifade eder; hücreye metin ekler; ve biçimlendirme uygular.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Hücrelere metin ve biçimlendirme eklemek için

1. Tablodaki konumuna göre hücreye başvurun, hücreye metin ekleyin ve biçimlendirmeyi uygulayın.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir. Bu örneği kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md)
- [Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Nasıl yapılır: program aracılığıyla Word tablolarını belge özellikleriyle doldurma](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
