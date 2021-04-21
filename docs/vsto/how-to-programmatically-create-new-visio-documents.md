---
title: 'Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma'
description: Program aracılığıyla yeni bir Microsoft Visio çizim belgesi oluşturup açık Visio belgelerinin belgeler koleksiyonuna nasıl ekleyebileceğiniz hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825322"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma
  Yeni bir Microsoft Office Visio çizim belgesi oluşturduğunuzda, bu dosyayı `Microsoft.Office.Interop.Visio.Documents` Açık Visio belgeleri koleksiyonuna eklersiniz. Sonuç olarak, `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi yeni bir Visio çizim belgesi oluşturur. Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Documtları için VBA başvuru belgelerine bakın [ . Yöntem ekleyin](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Yeni boş belge oluştur

### <a name="to-create-a-new-document"></a>Yeni bir belge oluşturmak için

- `Microsoft.Office.Interop.Visio.Documents.Add`Bir şablonu temel alan yeni boş bir belge oluşturmak için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Mevcut belgelerden kopyalanmış belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`Yöntemi, var olan Visio belgesinin bir kopyası olan yeni bir belge oluşturabilir. Diyagramın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Varolan bir belgeden kopyalanmış yeni bir belge oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve Visio diyagramının yolunu belirtin.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Varolan kalıplardan kopyalanmış şablonlar oluşturma
 [Microsoft.Office.Interop.Visio.Documlar. Add](/office/vba/api/Visio.Documents.Add) yöntemi, var olan bir Visio kalıbının kopyası olan yeni bir kalıp oluşturabilir. Kalıbın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Mevcut bir kalıptan kopyalanmış yeni bir kalıp oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve kalıbın yolunu belirtin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Mevcut şablonları temel alan belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`Yöntemi, var olan bir Visio şablonuna (bir *. VST* dosyası) dayalı yeni bir belge ( *. VSD* dosyası) oluşturabilir. Bu yöntem şablon çalışma alanının bir parçası olan kalıpları, stilleri ve ayarları kopyalar. Şablonun dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Mevcut bir şablonu temel alan yeni bir belge oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve şablonun yolunu belirtin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- Adlı bir Visio belgesi `myDrawing.vsd` `Test` , Belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *Belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

- Adlı bir Visio belgesi `myStencil.vss` `Test` , Belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *Belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

- Adlı bir Visio belgesi `myTemplate.vst` `Test` , Belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *Belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
