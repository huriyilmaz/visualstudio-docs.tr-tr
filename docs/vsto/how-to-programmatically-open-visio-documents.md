---
title: 'nasıl yapılır: program aracılığıyla Visio belgeleri açma'
description: açık veya openex yöntemleriyle bir Visio belgesini program aracılığıyla açmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1c3126f3f5ac73632996079a070c426afc20d656
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725564"
---
# <a name="how-to-programmatically-open-visio-documents"></a>nasıl yapılır: program aracılığıyla Visio belgeleri açma
  mevcut Microsoft Office Visio belgeleri açmak için iki yöntem vardır: Open ve openex. OpenEx yöntemi, Open yöntemiyle aynıdır, ancak çağıranın belgenin nasıl açıldığını belirtebileceğiniz bağımsız değişkenler sağlar.

 Nesne modeliyle ilgili ayrıntılar için bkz. Microsoft. Office için VBA başvuru belgeleri [. Derlemesinde. Visio. Documents. Open](/office/vba/api/Visio.Documents.Open) yöntemi ve [Microsoft. Office. Derlemesinde. Visio. Documents. OpenEx](/office/vba/api/Visio.Documents.OpenEx) yöntemi.

## <a name="open-a-visio-document"></a>Visio bir belge açın

### <a name="to-open-a-visio-document"></a>Visio bir belge açmak için

- yöntemini çağırın `Microsoft.Office.Interop.Visio.Documents.Open` ve Visio belgenin tam yolunu sağlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>belirtilen bağımsız değişkenlerle Visio bir belge açın

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Visio bir belgeyi salt okunurdur ve sabitlenmiş olarak açmak için

- yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.OpenEx` , Visio belgenin tam yolunu sağlayın ve kullanmak istediğiniz bağımsız değişkenleri (bu örnekte, sabitlenmiş ve salt okunurdur) dahil edin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- adlı bir Visio belge `myDrawing.vsd` `Test` , belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
