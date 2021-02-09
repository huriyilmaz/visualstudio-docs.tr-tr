---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma'
description: Tüm Microsoft Visio belgelerini nasıl yazdırabileceğinizi veya bu belgede yalnızca belirli bir sayfayı yazdırmanızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df2cd5137f05caaf7b8437fb2d903aeecc7d3e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933043"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma
  Tüm Microsoft Office Visio belgelerini veya yalnızca belirli bir sayfayı yazdırabilirsiniz.

 Yazdırma yöntemleri hakkında daha fazla bilgi için,Microsoft.Office.Interop.Visio.Document için VBA başvuru belgelerine bakın [ . Print](/office/vba/api/Visio.Document.Print) yöntemi ve [Microsoft. Office. Interop. Visio. Page. Print](/office/vba/api/Visio.Page.Print) yöntemi.

## <a name="print-a-visio-document"></a>Visio belgesi Yazdır

### <a name="to-print-a-complete-document"></a>Tüm belgeyi yazdırmak için

- Yazdırmak istediğiniz `Microsoft.Office.Interop.Visio.Document.Print` nesnenin yöntemini çağırın `Microsoft.Office.Interop.Visio.Document` .

     Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Visio belgesi sayfası yazdırma

### <a name="to-print-a-page-of-a-document"></a>Belgenin bir sayfasını yazdırmak için

- Yazdırmak istediğiniz `Microsoft.Office.Interop.Visio.Pages.Print` nesnenin yöntemini çağırın `Microsoft.Office.Interop.Visio.Pages` .

     Aşağıdaki kod örneği, etkin belgenin ilk sayfasını yazdırır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
