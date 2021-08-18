---
title: Word tablo & program aracılığıyla metin ve biçimlendirme ekleme
description: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6cdb47e1db9893c128850407022eb95a358eb15e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046717"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Nasıl yapılanlar: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme
  Her tablo bir hücre koleksiyonundan oluşur. Her bir <xref:Microsoft.Office.Interop.Word.Cell> nesne, tablodaki bir hücreyi temsil eder. Her hücreye tablodaki konumuna göre başvurabilirsiniz. Bu örnek, ilk satırda ve tablonun ilk sütununda yer alan hücreyi ifade eder; hücreye metin ekler; ve biçimlendirmeyi uygular.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Hücrelere metin ve biçimlendirme eklemek için

1. Tabloda bulunduğu konuma göre hücreye bakın, hücreye metin ekleyin ve biçimlendirmeyi uygulayın.

     Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir. Bu örneği kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılanlar: Program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md)
- [Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Nasıl kullanılır: Word tablolarını belge özellikleriyle program aracılığıyla doldurmak](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
