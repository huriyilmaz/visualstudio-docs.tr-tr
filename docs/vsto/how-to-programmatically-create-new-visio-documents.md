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
ms.openlocfilehash: a5aeddeecf7fb76000817f2c57b90e30465fa4ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964036"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma
  Yeni bir Microsoft Office Visio çizim belgesi oluşturduğunuzda, bu dosyayı `Microsoft.Office.Interop.Visio.Documents` Açık Visio belgeleri koleksiyonuna eklersiniz. Sonuç olarak, `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi yeni bir Visio çizim belgesi oluşturur. Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Documtları için VBA başvuru belgelerine bakın [ . Yöntem ekleyin](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Yeni boş belge oluştur

### <a name="to-create-a-new-document"></a>Yeni bir belge oluşturmak için

- `Microsoft.Office.Interop.Visio.Documents.Add`Bir şablonu temel alan yeni boş bir belge oluşturmak için yöntemini kullanın.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Mevcut belgelerden kopyalanmış belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`Yöntemi, var olan Visio belgesinin bir kopyası olan yeni bir belge oluşturabilir. Diyagramın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Varolan bir belgeden kopyalanmış yeni bir belge oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve Visio diyagramının yolunu belirtin.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Varolan kalıplardan kopyalanmış şablonlar oluşturma
 [Microsoft.Office.Interop.Visio.Documlar. Add](/office/vba/api/Visio.Documents.Add) yöntemi, var olan bir Visio kalıbının kopyası olan yeni bir kalıp oluşturabilir. Kalıbın dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Mevcut bir kalıptan kopyalanmış yeni bir kalıp oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve kalıbın yolunu belirtin.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Mevcut şablonları temel alan belgeler oluşturma
 `Microsoft.Office.Interop.Visio.Documents.Add`Yöntemi, var olan bir Visio şablonuna (bir *. VST* dosyası) dayalı yeni bir belge ( *. VSD* dosyası) oluşturabilir. Bu yöntem şablon çalışma alanının bir parçası olan kalıpları, stilleri ve ayarları kopyalar. Şablonun dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Mevcut bir şablonu temel alan yeni bir belge oluşturmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Add` ve şablonun yolunu belirtin.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

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
