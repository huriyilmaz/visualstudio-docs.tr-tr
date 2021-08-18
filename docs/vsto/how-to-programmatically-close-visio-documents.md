---
title: 'nasıl yapılır: program aracılığıyla Visio belgeleri kapatma'
description: Microsoft.Office.Interop.Visio.Document kullanarak etkin Microsoft Office Visio belgesini nasıl kapatabileceğinizi öğrenin. Close yöntemi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c48b814629e01e370696bb30f8ee15af60098ec3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046652"
---
# <a name="how-to-programmatically-close-visio-documents"></a>nasıl yapılır: program aracılığıyla Visio belgeleri kapatma
  yöntemini kullanarak etkin Microsoft Office Visio belgesini kapatabilirsiniz `Microsoft.Office.Interop.Visio.Document.Close` .

 Bu yöntem hakkında daha fazla bilgi için,Microsoft.Office.Interop.Visio.Document için VBA başvuru belgelerine bakın [ . Close](/office/vba/api/Visio.Document.Close) yöntemi.

## <a name="close-the-active-document"></a>Etkin belgeyi kapat

### <a name="to-close-the-active-document"></a>Etkin belgeyi kapatmak için

- `Microsoft.Office.Interop.Visio.Document.Close`Etkin belgeyi kapatmak için yöntemini çağırın.

     aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Visio için VSTO eklenti projesindeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
