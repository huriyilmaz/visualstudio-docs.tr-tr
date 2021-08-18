---
title: 'Nasıl Visio: Program aracılığıyla Visio yazdırma'
description: Tam bir Microsoft belgeyi nasıl yazdırabilirsiniz Visio belgede yalnızca belirli bir sayfayı yazdırabilirsiniz.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f38f6afb5aa6d1735207a851de80bd57d6c4fa811c6d96abbea9ab78b14a0ebd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351817"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Nasıl Visio: Program aracılığıyla Visio yazdırma
  Tam bir belgeyi veya Microsoft Office Visio bir sayfayı yazdırabilirsiniz.

 Yazdırma yöntemleri hakkında ayrıntılı bilgi için,Microsoft.Office.Interop.Visio.Document için [VBA başvuru belgelerine bakın. Print](/office/vba/api/Visio.Document.Print) metodu ve [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Page.Print](/office/vba/api/Visio.Page.Print) yöntemi.

## <a name="print-a-visio-document"></a>Bir belgeyi Visio yazdırma

### <a name="to-print-a-complete-document"></a>Eksiksiz bir belge yazdırmak için

- Yazdırmak `Microsoft.Office.Interop.Visio.Document.Print` istediğiniz `Microsoft.Office.Interop.Visio.Document` nesnenin yöntemini çağırma.

     Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından kodu çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet8":::

## <a name="print-a-page-of-a-visio-document"></a>Bir belgeye Visio yazdırma

### <a name="to-print-a-page-of-a-document"></a>Bir belgenin sayfasını yazdırmak için

- Yazdırmak `Microsoft.Office.Interop.Visio.Pages.Print` istediğiniz `Microsoft.Office.Interop.Visio.Pages` nesnenin yöntemini çağırma.

     Aşağıdaki kod örneği, etkin belgenin ilk sayfasını yazdırır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından kodu çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
