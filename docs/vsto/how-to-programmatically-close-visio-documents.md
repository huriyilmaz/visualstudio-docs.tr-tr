---
title: 'Nasıl Visio: Program aracılığıyla Visio kapatma'
description: Microsoft.Office.Interop.Visio.Document kullanarak Microsoft Office Visio belgeyi nasıl Microsoft.Office.Interop.Visio.Docöğrenin. Close yöntemi.
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
ms.openlocfilehash: 625b0c6aa9ebf728945afa01655f641a779c1422686c055c986140646c99b0fa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423962"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Nasıl Visio: Program aracılığıyla Visio kapatma
  yöntemini kullanarak etkin Microsoft Office Visio belgeyi `Microsoft.Office.Interop.Visio.Document.Close` kapatabilirsiniz.

 Bu yöntem hakkında ayrıntılı bilgi için,Microsoft.Office.Interop.Visio.Document için VBA [ başvuru belgelerine bakın. Close](/office/vba/api/Visio.Document.Close) yöntemi.

## <a name="close-the-active-document"></a>Etkin belgeyi kapatma

### <a name="to-close-the-active-document"></a>Etkin belgeyi kapatmak için

- Etkin `Microsoft.Office.Interop.Visio.Document.Close` belgeyi kapatmak için yöntemini çağırma.

     Aşağıdaki kod örneğini kullanmak için, bunu bir VSTO add-in projesinde `ThisAddIn` sınıf içinde Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
