---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5117714564fe4d8a52dad6f3663f870ce39209ad
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848278"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma
  Yöntemini kullanarak etkin Microsoft Office Visio belgesini kapatabilirsiniz `Microsoft.Office.Interop.Visio.Document.Close` .

 Bu yöntem hakkında daha fazla bilgi için,Microsoft.Office.Interop.Visio.Document için VBA başvuru belgelerine bakın [ . Close](/office/vba/api/Visio.Document.Close) yöntemi.

## <a name="close-the-active-document"></a>Etkin belgeyi kapat

### <a name="to-close-the-active-document"></a>Etkin belgeyi kapatmak için

- `Microsoft.Office.Interop.Visio.Document.Close`Etkin belgeyi kapatmak için yöntemini çağırın.

     Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Visio için BIR VSTO eklentisi projesindeki sınıfında çalıştırın.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
