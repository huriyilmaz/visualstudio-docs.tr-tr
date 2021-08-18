---
title: 'Nasıl kullanılır: Program aracılığıyla Visio yazdırma'
description: Tam bir Microsoft belgeyi yazdırmayı Visio belgede yalnızca belirli bir sayfayı yazdırmayı öğrenin.
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
ms.openlocfilehash: cb428567c5b6e58ec3832917da92e45f7b3ec605
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105905"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Nasıl kullanılır: Program aracılığıyla Visio yazdırma
  Tam bir belgeyi veya Microsoft Office Visio bir sayfayı yazdırabilirsiniz.

 Yazdırma yöntemleri hakkında ayrıntılı bilgi için, aşağıdaki belgelerde yer alan VBA [başvuruMicrosoft.Office.Interop.Visio.Docbakın. Print](/office/vba/api/Visio.Document.Print) metodu ve [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Page.Print](/office/vba/api/Visio.Page.Print) yöntemi.

## <a name="print-a-visio-document"></a>Belgeyi Visio yazdırma

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
- [Nasıl Visio: Program aracılığıyla Visio kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
