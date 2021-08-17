---
title: 'Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma'
description: Program aracılığıyla yeni bir Microsoft Visio oluşturma ve belgeyi açık belgelerden belgeler koleksiyonuna Visio öğrenin.
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
ms.openlocfilehash: 090ae76b96e4bf108a020474e7b21d6eeabcbc34
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106087"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma
  Yeni bir çizim Microsoft Office Visio, belgeyi açık belge `Microsoft.Office.Interop.Visio.Documents` koleksiyonuna Visio eklersiniz. Sonuç olarak, `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi yeni bir çizim Visio oluşturur. Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Documents için [ VBA başvuru belgelerine bakın. yöntemi](/office/vba/api/Visio.Documents.Add) ekleyin.

## <a name="create-new-blank-documents"></a>Yeni boş belgeler oluşturma

### <a name="to-create-a-new-document"></a>Yeni belge oluşturmak için

- Bir `Microsoft.Office.Interop.Visio.Documents.Add` şablonu temel alan yeni bir boş belge oluşturmak için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Mevcut belgelerden kopyalanan belgeler oluşturma
 yöntemi, `Microsoft.Office.Interop.Visio.Documents.Add` mevcut bir belgenin kopyası olan yeni bir belge Visio oluşturabilir. Diyagramın dosya adını ve tam yolunu sağlamak gerekir.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Var olan bir belgeden kopyalanan yeni bir belge oluşturmak için

- yöntemini `Microsoft.Office.Interop.Visio.Documents.Add` çağırma ve şemanın yolunu Visio belirtin.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Mevcut kalıplardan kopyalanan kalıplar oluşturma
 Microsoft.Office.Interop.Visio.Doc[uments. Add](/office/vba/api/Visio.Documents.Add) yöntemi, var olan bir şablonun kopyası olan yeni bir kalıp Visio oluşturabilir. Şablonun dosya adını ve tam yolunu sağlamak gerekir.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Var olan bir kalıptan kopyalanan yeni bir kalıp oluşturmak için

- yöntemini `Microsoft.Office.Interop.Visio.Documents.Add` çağırma ve kalıp yolunu belirtme.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Mevcut şablonları temel alan belgeler oluşturma
 yöntemi, mevcut bir Visio şablonunu `Microsoft.Office.Interop.Visio.Documents.Add` (.vst dosyası) temel alan yeni bir belge *(.vsd dosyası)* oluşturabilir.  Bu yöntem şablon çalışma alanının parçası olan kalıpları, stilleri ve ayarları kopyalar. Şablonun dosya adını ve tam yolunu sağlamak gerekir.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Mevcut bir şablonu temel alan yeni bir belge oluşturmak için

- yöntemini `Microsoft.Office.Interop.Visio.Documents.Add` çağırma ve şablonun yolunu belirtme.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneği için aşağıdakiler gerekir:

- adlı Visio belge, Belgelerim klasöründe (Windows XP ve önceki sürümler için) veya Belgeler klasöründe `myDrawing.vsd` `Test` (Windows Vista için) olmalıdır.  

- adlı Visio belge, Belgelerim klasöründe (Windows XP ve önceki sürümler için) veya Belgeler klasöründe `myStencil.vss` `Test` (Windows Vista için) olmalıdır.  

- adlı Visio belge, Belgelerim klasöründe (Windows XP ve önceki sürümler için) veya Belgeler klasöründe `myTemplate.vst` `Test` (Windows Vista için) olmalıdır.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl Visio: Program aracılığıyla Visio açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
