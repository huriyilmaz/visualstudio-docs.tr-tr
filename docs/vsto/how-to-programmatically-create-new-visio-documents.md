---
title: 'nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma'
description: programlı olarak yeni bir Microsoft Visio çizim belgesi oluşturup bunu açık Visio belgelerinin belgeler koleksiyonuna ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a195996684334cbc658d75f82a5f81f1d69109af45174b3ce6b2f6c996c38ae8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384333"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma
  yeni bir Microsoft Office Visio çizim belgesi oluşturduğunuzda, bu dosyayı `Microsoft.Office.Interop.Visio.Documents` açık Visio belgeleri koleksiyonuna eklersiniz. sonuç olarak, `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi yeni bir Visio çizim belgesi oluşturur. Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Documtları için VBA başvuru belgelerine bakın [ . Yöntem ekleyin](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Yeni boş belge oluştur

### <a name="to-create-a-new-document"></a>Yeni bir belge oluşturmak için

- `Microsoft.Office.Interop.Visio.Documents.Add`Bir şablonu temel alan yeni boş bir belge oluşturmak için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Mevcut belgelerden kopyalanmış belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`yöntemi, varolan bir Visio belgesinin bir kopyası olan yeni bir belge oluşturabilir. Diyagramın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Varolan bir belgeden kopyalanmış yeni bir belge oluşturmak için

- yöntemini çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve Visio diyagramın yolunu belirtin.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Varolan kalıplardan kopyalanmış şablonlar oluşturma
 [Microsoft.Office.Interop.Visio.Documlar. Add](/office/vba/api/Visio.Documents.Add) yöntemi, var olan bir Visio kalıbının kopyası olan yeni bir kalıp oluşturabilir. Kalıbın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Mevcut bir kalıptan kopyalanmış yeni bir kalıp oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve kalıbın yolunu belirtin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Mevcut şablonları temel alan belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`yöntemi, mevcut bir Visio şablonunu (bir *. vst* dosyası) temel alan yeni bir belge ( *. vsd* dosyası) oluşturabilir. Bu yöntem şablon çalışma alanının bir parçası olan kalıpları, stilleri ve ayarları kopyalar. Şablonun dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Mevcut bir şablonu temel alan yeni bir belge oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve şablonun yolunu belirtin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- adlı bir Visio belge `myDrawing.vsd` `Test` , belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

- adlı bir Visio belge `myStencil.vss` `Test` , belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

- adlı bir Visio belge `myTemplate.vst` `Test` , belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [nasıl yapılır: program aracılığıyla Visio belgeleri yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
